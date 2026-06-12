---
title: "ubuntu 18.04.1 update help"
date: 2018-10-20
forum: New to Ubuntu
---

### Post by magenhdd on 2018-10-20
Hello all,
I am currently seeking help recovering my ubuntu machine which I recently updated from 17 to 18.04.1 x64 via the update function of ubuntu. Upon updating a rebooting it seems that the desktop has been corrupted when attempting to log in a little red notice appears above the password field which reads "failed to start session".
I followed the advice given here ([https://ubuntuforums.org/showthread.php?t=2396375](https://ubuntuforums.org/showthread.php?t=2396375))
```

sudo apt-get install ubuntu-desktop
``` 
this command had several failed install notice

I have tried to repair ubunut using the steps here ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but had no luck same problem.
I believe im missing some dependencies / packages

anyway here is the pastbin ling that was generated any help that you could provide would be great,
[http://paste.ubuntu.com/p/QzrZxwqBms/](http://paste.ubuntu.com/p/QzrZxwqBms/)

Thank in advance.

---

### Post by magenhdd on 2018-10-20
So im just gonna go down the list and provide as much info as i can because i want to be able to fix this nonsense

anyway loaded up my machine pressed ctrl + alt + f1
and typed in command
```
 sudo apt upgrade
```

and the following was the response,
```

ubuntu-desktop :
Depends: gdm3 but it is not installed
Depends: gnome-control-center but is not installed
Depends: gnome-settings-daemon but is not installed
Depends: gnome-shell but is not installed
Depends: ubuntu-session but is not installed
Recommends: deja-dup but it is not installed
Recommends: gnome-calendar but it is not installed
Recommends: gnome-getting-started-docs but it is not installed
Recommends: gnome-instal-setup but is not installed
Recommends: gnome-todo but it is not installed
Recommends: nautils-share but it is not installed
Recommends: shotwell but it is not installed
Recommends: ubuntu-docs but it is not installed
```

Then I tryed
```
apt --fix-broken install
```
and i get a bunch of errors and failed to fetch urls

---

### Post by dino99 on 2018-10-20
I have some doubts:
- was your previous install a 64 bits one ?
- how have you upgrded to 18.04.1 ?

The boot sectors are corrupted on sda2 and sda5: by the way, you should not have a boot sector there.

But you might be able to open a terminal, via ctrl+alt+F? (2 -> 9), and then do some tweaks:

- sudo apt-get purge grub
- sudo apt-get install grub  (install on /dev/sda)

- sudo apt-get autoremove
- sudo apt-get autoclean

- sudo apt-get update
- sudo apt-get install -f
- sudo dpkg --configure -a

- sudo reboot 

If you still get problems, then post the output of:
- sudo blkid
- cat /etc/fstab

---

### Post by magenhdd on 2018-10-20
Hay so ive always used the x64 bit installation image and the only reason i updated was because it poped up with a ubuntu update notice then installed 18.04.01.
not sure if you saw my response above right before you posted your response

so typing 
```
sudo blkid
```
i get
```

/dev/mapper/sda5_crypt: UUID="xDxhFa-QDO0-oumk-Co91-KTEG-jX9A-c3rIqq" TYPE="LVM2_member"
/dev/mapper/ubuntu--vg-root: UUID="66ad068e-c4bb-4688-bd99-2c015cbd1e0c" TYPE="ext4"
/dev/sda1: UUID="2dbe3183-7494-4444-b631-382d1bcf0e2b" TYPE="ext4" PARTUUID="87738fc7-01"
/dev/sda5: UUID="a4743c&a-11b9-43ac-ad31-e66e91079edb" TYPE"crypto_LUKS" PARTUUID="87738fc-05
/dev/mapper/ubuntu--vg-swap_1: UUID="ea8e3cd4-342d-40eb-b26d-40eb-b26d-3b8ef47cdc2c" TYPE="swap"
```

---

### Post by magenhdd on 2018-10-20
is there anyway that i could mount this drive and recover the files on it then just reformat and reinstall ubuntu?

---

### Post by dino99 on 2018-10-20
Maybe boot repair script is itself faulty due to your config (luks/lvm2)
Even not sure something is broken. Check via gparted to find possible error.

The easiest way to understand your issue is to check 'journalctl -b' (or m)

About fetching urls, please post the output of 'cat /etc/apt/sources.list'

gdm3 needs to be installed indeed. If you cant, then you might have some old packages/settings to purge first.

---

### Post by magenhdd on 2018-10-20
Okay,
Firstly Gparted
```
sudo gparted
```
then listed that gparted was not installed but could be installed by
```
apt get gparted
```

Then it spat back
```

Depends: gdm3 but it is not installed
Depends: gnome-control-center but is not installed
Depends: gnome-settings-daemon but is not installed
Depends: gnome-shell but is not installed
Depends: ubuntu-session but is not installed
Recommends: deja-dup but it is not installed
Recommends: gnome-calendar but it is not installed
Recommends: gnome-getting-started-docs but it is not installed
Recommends: gnome-instal-setup but is not installed
Recommends: gnome-todo but it is not installed
Recommends: nautils-share but it is not installed
Recommends: shotwell but it is not installed
Recommends: ubuntu-docs but it is not installed
```

journalctl-b / journalctl-m <- both where invalid 

as for the output of 
```
 cat/ect/apt/sources.list

```
there was no such file directory

---

### Post by Impavidus on 2018-10-20
17.10 reached end-of-life 3 months ago, so it's good you upgraded, although it's best if you upgrade before the old release goes end-of-life. Whenever a release upgrade goes wrong, the best action is often a fresh install. Broken release upgrades can be very hard to fix (but sometimes it's not so hard).

A few things to check: Can you login as a different user? Can you login using the guest session? Can you get into a root shell, booting in recovery mode? Can you login on the command line (ctrl+alt+F2, use ctrl+alt+F7 to get back to the GUI. Or did they change that to one of the other function keys?)? I guess so, as you can use the command line.

gparted is available on the live disk. It's always a good idea to have a live disk lying about somewhere. And you had typos in your commands:```
journalctl -b
cat /etc/apt/sources.list
```

---

### Post by oldfred on 2018-10-20
Gparted does not work on LVM volumes, just the partition the volume is inside of.
Boot-Repair does work on LVM, but if encrypted you normally have to decrypt it separately so Boot-Repair can find / inside LVM.

II do not know LVM nor encryption but have these links.
       Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)
[URL="https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line"]https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line
      [/URL]
 Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621) 
    [URL="https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line"]
[/URL]

---

