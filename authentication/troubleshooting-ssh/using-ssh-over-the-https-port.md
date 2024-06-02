# Using SSH over the HTTPS port

- Sometimes, firewalls refuse to allow SSH connections entirely.

- If using HTTPS cloning with credential caching is not an option, you can attempt to clone using a SSH connection made over the HTTPS port.

- To test if SSH over the HTTPS port is possible, run this SSH command:

    ```shell
    $ ssh -T -p 443 git@ssh.github.com
    ```

- Now, to clone the repository, you can run the following command:

    ```shell
    $ git clone ssh://git@ssh.github.com:443/YOUR-USERNAME/YOUR-REPOSITORY.git
    ```

## Enbling SSH connections over HTTPS

- If you are able to SSH into `git@ssh.github.com` over port 443, you can override your SSH settings to force any connection to GitHub.com to run through that server and port.

- To set this in your SSH configuration file, edit the file at `~/.ssh/config`, and add this section:

    ```
    Host github.com
        Hostname ssh.github.com
        Port 443
        User git
    ```

- You can test that this works by connecting once more to GitHub.com:

    ```shell
    $ ssh -T git@hub.com
    ```
