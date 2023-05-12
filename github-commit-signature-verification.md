
## Links:

- [About commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)

## Instruction:

1. Prepare your email address in [settings/emails](https://github.com/settings/emails ) for use in the following stages
   - Select Primary email address for use
   - Or (optional): to keep your email address private, use your GitHub-provided no-reply email address
     1. Turn on the checkbox `[x] Keep my email addresses private`
     2. Then use your github email address listed under the checkbox in the format: `1234567+myusername@users.noreply.github.com`
2. Install GPG tool ([read more](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key))
   - For Windows: https://www.gpg4win.org/
3. Generate a new GPG key ([read more](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key))
    ```
    gpg --full-generate-key
    ```
    Get and save your private keys in a safe place
    ```
    gpg --list-secret-keys --keyid-format=long
    ```
    Get your `GPG public key`
    ```
    gpg --armor --export 3AA5C34371567BD2
    ```
4. Go to [Settings / Keys](https://github.com/settings/keys) and create New GPG key
   1. Paste your `GPG public key` from step 3  
   2. Turn on the checkbox `[x] Flag unsigned commits as unverified` ([read more](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits))
5. Set your git config:
    ```
    git config --global user.email "your_email"
    git config --global user.name "Your Name"
    git config --global commit.gpgsign true
    ```
    where email - **primary** email address or **no-reply** email address (see step 1)