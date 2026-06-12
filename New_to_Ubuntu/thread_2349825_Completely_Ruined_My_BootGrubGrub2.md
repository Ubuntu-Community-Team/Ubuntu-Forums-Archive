---
title: "Completely Ruined My Boot/Grub/Grub2"
date: 2017-01-18
forum: New to Ubuntu
---

### Post by ganderbird on 2017-01-18
Ok, long story short. I had Windows 10, Ubuntu 14.04, ParrotSec, and Mint all installed on 1 harddrive.

They all booted fine, I believe booting through Ubuntu as Legacy Rom.

Then I installed Fedora 25. and I think it installed as UEFI and somehow ruined everything.

In trying to fix that, I ruined it all more and got to the point where I couldn't get a damn thing to boot.

Now, I've got all the distros wiped, and only have Ubunutu 16 and Windows 10 installed, but can only get Ubuntu to boot, through Legacy.

Can't get Windows 10 to boot. Can't even get a Live USB to boot. Just this Ubunutu.

How can I fix everything. Haha... I know that's broad... but I'm willing to basically wipe everything except my windows partition.

---

### Post by oldfred on 2017-01-18
You have to get a live installer to boot, so we can see your configuration.

Did you leave fast start up on in UEFI/BIOS?
That skips all checks for hardware or operating system settings changes and just immediately jumps to booting default.
You often then do not have time to press a key to get into UEFI to change boot order or use one time boot key like f10 or f12 (check your manual).

Often cold boot uses a normal UEFI boot. And press correct key immediately to get into UEFI.
That is then full shutdown and drain all power by holding power switch for 10 sec or so.
If laptop remove battery.
Some tablets have pinhole reset on bottom.
And some systems need pins jumpered on motherboard. See manual.

Once you can boot live installer.
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ganderbird on 2017-01-18
```
gander@gander:/etc/grub.d$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
gander@gander:/etc/grub.d$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 285 not upgraded.
751 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 237144 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



I get this error when I try to install boot-repair.

---

### Post by oldfred on 2017-01-19
That error is some conflict in dpkg.
Did you add any ppa to install or include telepathy or account-plugin-google?

 Check sources & ppas
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

---

