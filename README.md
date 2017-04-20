# honeybash

####Description

If you are running Bash on a *nix system you can turn its binaries into a honey binaries. 
Binaries that are replaced will only run normally if a secret environment variable and value is present in your session.

####Configuration

1. **DIR:** The binary store location. This is where original binaries will be stored
2. **LOG:** The log file. This is the file that events will be logged to.
3. **SECRET_VAR:** A secret variable that you want.
4. **SECRET_VAL:** A scret value to go with your secret variable.
5. **DEFAULT_BINARIES:** A list of binaries that should be replaced with honey binaries when running ```-i|--init```
6. **AUTO_KILL:** The honey binaries will end the session after a random (1-10s) sleep.
7. **FAKE:** The honey binaries will give fake responses. These responses are in ```template```
8. **COMPILE:** If you have [SHC](http://www.datsi.fi.upm.es/~frosal/) installed on the system
the honey binaries will be compiled as well.

Default Configuration
```
#PATHS
DIR="/binaries/"
LOG="/tmp/hb"

#SECRETS
SECRET_VAR="SECRETVAR"
SECRET_VAL="SECRETVAL"

#OPTIONS
DEFAULT_BINARIES="chattr,lsattr"
AUTO_KILL="TRUE"
FAKE="FALSE"
COMPILE="FALSE"
```

####Quick Start
***Note:*** Commands should be run from the same directory as the ```honeybash``` script. Also, make sure you source your ```.secret``` file in every new session you start unless you enjoy pain.

1. Make sure ```CONFIG``` is setup the way you would like it to be.
2. Run ```./honeybash -s``` to generate a ```.secret``` file and source the file in your session.
3. Run ```./honeybash -i``` to initiate the binary store.
4. If you had default binaries set in ```CONFIG``` you should see them by running: ```./honeybash -l```.
5. If you want to make the command ```date``` a honey binary you would run: ```./honeybash -H date```.
6. To restore the ```date``` binary run: ```./honeybash -r date```
7. You can import a list of binaries (one per line) to replace by running: ```./honeybash -f < file```.
8. ```tail -f``` is your friend for the log.
9. To reset everything back to normal run: ```./honeybash -c```.
