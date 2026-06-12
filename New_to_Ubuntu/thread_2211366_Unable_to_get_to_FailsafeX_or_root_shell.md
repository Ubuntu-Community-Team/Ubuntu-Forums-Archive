---
title: "Unable to get to FailsafeX or root shell"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by ENigma885 on 2014-03-15
**1-** On Ubuntu 13.10, I decided to set up Gnome 3 to test the 3.10 components. So, I added the official ppa by
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
```
**2-** After encountering many problems, I decided that it's hard to handle and revert back using ppa-purge
```
sudo ppa-purge ppa:gnome3-team/gnome3
```
The command displayed the packages to be downgraded and those to be removed, but I didn't pay much attention to the lists.
**3-** After a reboot I get the login window but without the ubuntu logo beside the username. Entering my pw and hitting enter keeps the screen as it is.
[ATTACH=CONFIG]251181[/ATTACH]
**4-** **_The problem is_**
[INDENT]A- When I try to get to FailsafeX or enable networking for using the  root shell, I get the following line and it hangs there.
```
fsck from util-linux 2.20.1
/dev/sda1: clean, 428637/1310720 files, 4646644/5242880 blocks.
``` 
[ATTACH=CONFIG]251182[/ATTACH][ATTACH=CONFIG]251183[/ATTACH]
B- I tried to boot from a live USB and try to install to  my original ubuntu driver by
```
sudo mount /dev/sda1     /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```
but issuing sudo apt-get update, despite reading my original repositories as on the hdd, seems to have a problem in connection (DNS?) for example:
```
W: Failed to fetch http://ppa.launchpad.net/wfg/0ad.dev/ubuntu/dists/saucy/Release.gpg  Could not resolve 'ppa.launchpad.net'
```
Note: I have tested my internet connection by pinging Google in a different terminal window and it's fully functional.[/INDENT]

---

### Post by ENigma885 on 2014-03-16
**_In case someone faced the same issue or similar one, here's how I solved it:_**
**1-** Boot using the Ubuntu Live CD/USB
**2-** Open a terminal window using the dash menu or simply press *Ctrl+Alt+t *
**3-** Now we will mount the original Ubuntu installation to modify it directly from the Live CD
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

```
**_[COLOR="#FF0000"]Note:[/COLOR]_** 
**-** I assumed that sda1 is your root partition, if you are not sure use
```
sudo fdisk -l /dev/sda
```
and find the partition in front of which, an asterisk is present in the *[COLOR="#FF0000"]Boot [/COLOR]*column
something similar to 
```
  
Device    [COLOR="#FF0000"]Boot      [/COLOR]Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520   83  Linux
/dev/sda2        41945088    47187967     2621440   82  Linux swap / Solaris
/dev/sda3        47187968    99616767    26214400    7  HPFS/NTFS/exFAT
/dev/sda4        99616768  1953523711   926953472    5  Extended
/dev/sda5        99618816  1026572287   463476736    7  HPFS/NTFS/exFAT
/dev/sda6      1026574336  1953523711   463474688    7  HPFS/NTFS/exFAT
```
**-** If it's not sda1, you have to replace the sda1 in the ```
sudo mount /dev/[COLOR="#FF0000"]sda1 [/COLOR]/mnt
``` with the system partition of yours.
**4-** In the same terminal window, we will use your original Ubuntu repositories present on your HDD
```
apt-get update
apt-get upgrade
```
[COLOR="#FF0000"]_Note_[/COLOR]: [INDENT]In some cases like mine, an Internet connection couldn't be established resulting in errors like:
```
W: Failed to fetch http://ppa.launchpad.net/wfg/0ad.dev/ubuntu/dists/saucy/Release.gpg  Could not resolve 'ppa.launchpad.net'
```
**-** To work around this DHCP problem we have to edit /etc/resolv.conf using a command line text editor called *nano*
```
sudo nano /etc/resolv.conf
```
**-** and add the following DNS servers, these are OpenDNS's.
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
**-** Press *ctrl+X* after pasting the lines above and press *y* to save the file.
**-** Reissue the commands
```
apt-get update
apt-get upgrade
```
[/INDENT]
**5-** In my case while removing the Gnome 3 ppa components using ppa-purge, some essential libs and apps were removed. So, we are going to re-install them using
```
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get dist-upgrade
```
**6-** After completing the installation, your original Ubuntu installation on the hdd should be functional again. Reboot and access your system normally.

*More info on using the Live USB/CD recovery options can be accessed from [here]("https://help.ubuntu.com/community/LiveCdRecovery").*

---

