---
title: "I can't find/launch keybase app"
date: 2023-06-07
forum: New to Ubuntu
---

### Post by dmacpeak on 2023-06-07
I am unable to launch/find Keybase. It says it's installed when I check the software store but it does not show up in stored applications and I cannot launch it from the command line as it says "unable to locate package:.
I eager to learn about encryption. Any assistance would be appreciated.

Best,
D9780

---

### Post by Holger_Gehrke on 2023-06-07
> **dmacpeak said:**
> I am unable to launch/find Keybase. It says it's installed when I check the software store but it does not show up in stored applications and I cannot launch it from the command line as it says "unable to locate package:.


Since you installed it through the software store and it isn't in the normal repositories, what you installed is probably [this snap]("https://snapcraft.io/keybase"). I've checked keybase.io and they don't mention installation as a snap at all, so this is not an official release by them. That package is from March 2022 and there have been updates on the keybase github since then. Also the snap claims it's under a proprietary license while according to the github it's under the three-clause BSD-license ... They do give [installation instructions]("https://keybase.io/docs/the_app/install_linux") for Ubuntu and they involve downloading an apt-package and installing it from the command-line.

Holger

---

### Post by dmacpeak on 2023-06-07
ubuntu2@Linux-Laptop:~$ run_keybase 
run_keybase: command not found
ubuntu2@Linux-Laptop:~$ curl --remote-name [https://prerelease.keybase.io/keybase_amd64.deb](https://prerelease.keybase.io/keybase_amd64.deb)
sudo apt install ./keybase_amd64.deb
run_keybase
Command 'curl' not found, but can be installed with:
sudo snap install curl  # version 8.1.2, or
sudo apt  install curl  # version 7.81.0-1ubuntu1.10
See 'snap info curl' for additional versions.
[sudo] password for ubuntu2: 
Reading package lists... Done
E: Unsupported file ./keybase_amd64.deb given on commandline
run_keybase: command not found
ubuntu2@Linux-Laptop:~$ # if you see an error about missing `libappindicator1` from the next
# command, you can ignore it, as the subsequent command corrects it
sudo dpkg -i keybase_amd64.deb
sudo apt-get install -f
dpkg: error: cannot access archive 'keybase_amd64.deb': No such file or directory
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
ubuntu2@Linux-Laptop:~$

---

### Post by deadflowr on 2023-06-08
Install curl as suggested in the output
```
sudo apt install curl
```
then re-run the commands you tried before.

It basically failed at the start, since you do not have curl installed.

---

