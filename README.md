# devmachineconfig
Configuring a new dev machine (Debian on Windows with WSL)

## On PowerShell (administrator mode)
```
wsl --install -d Debian
```

This will install Debian and ask for a username and password. 

## To add a new user for development only (lower privileges than the root user)

```
useradd <username>
```

## To switch between users

```
su <username>
```

## To add the new user to the sudoers list
Switch to root user. Then
```
sudo visudo
```

This will open sudoers in the default editor. Navigate to this line:
```
%sudo ALL=(ALL:ALL) ALL
```

The 'sudo' in the above line could be another word (like wheel). Use this word in the next command:
```
sudo usermod -aG sudo <new-user-name>
```

This should enable the new user id to sudo.

## Update apt
```
sudo apt update
sudo apt -y upgrade
```

## Now let's install pip
```
sudo apt install -y python3-pip
```

# Good reference material for setting up dev environments quickly on a new machine (or porting to cloud)
https://www.codemag.com/Article/1811021/Docker-for-Developers
https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-programming-environment-on-debian-11#step-2-setting-up-a-virtual-environment