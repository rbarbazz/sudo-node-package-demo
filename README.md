## Instructions

This is a demo to show how running `npm install` with root privileges can potentially be harmful.

1. Create a tarball of the package:

    ```shell
    npm pack
    ```

2. Install the package globally with `foreground-scripts` enabled:

    ```shell
    npm i -g --foreground-scripts=true sudo-node-module-demo-1.0.0.tgz
    ```

    With `foreground-scripts` enabled, scripts for installed packages will share the standard output with the main process and you will see the commands being run in the background.

3. Observe the `pwned` file created in your home directory:

    ```shell
    ls -l ~
    ```

4. Cleanup:

    ```shell
    npm uninstall -g sudo-node-module-demo
    rm ~/pwned
    ```

Running the command from step 2 with `sudo` allows potential malicious scripts to run with elevated privileges and can be harmful to your system (e.g.: `rm -rf /`, changing the default DNS resolver).

## Solution

If your current Node setup requires you to run global installations with `sudo`, [delete your current installation](https://stackoverflow.com/questions/11177954/how-do-i-completely-uninstall-node-js-and-reinstall-from-beginning-mac-os-x) and [reinstall Node using NVM](https://github.com/nvm-sh/nvm#installing-and-updating).
