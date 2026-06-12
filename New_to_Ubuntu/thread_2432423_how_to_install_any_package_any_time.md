---
title: "how to install any package any time"
date: 2019-12-02
forum: New to Ubuntu
---

### Post by victorftp on 2019-12-02
good afternoon everyone,


I work with ubuntu 16.04, whenever I need to install anything is a "delivery", because the server already has several services installed.
or some error or mysql service already installed.
Briefly: I have no confidence to install server packages.


I want to learn how to install or remove anything I want on ubuntu 16.04.
what do you recommend me? because it is something generic I can not find any article talking or something.
For example today I need to install these packages below, but I have no confidence because I do not know what will happen if I install "understand the question? Follows the example packages:
[COLOR=#333333][FONT=&quot]apt install libncursesw5-dev[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]apt install mmdb-bin[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]apt install libtokyocabinet-dev[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]apt install libssl-dev[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]apt install intltool e etc
[/FONT][/COLOR]Today I installed libncursesw5-dev in fright, and it already stopped my mysql.


if you could help me by telling me where I have to look to learn to install / uninstall anything you want on linux without conflict.
Thanks in advance

i'm brazillian sorry for the english

---

### Post by TheFu on 2019-12-02
There is no guarantee. Sorry.

Linux package management automatically pulls in any dependencies that aren't already on the system.  You could specifically request that no dependencies be pulled in, or just required dependencies and not the "recommended" dependencies.  These are all documented commands in the apt-get manpage.  Every command on your linux systems should have manpages installed with the package which explains how each command works, tips, caveats, warnings, and a clear description of the options.

This is why people have development, test, pre-production, disaster recovery AND production environments.  Also, having excellent backups further reduces any risks that updates will impact a system longer than 30 minutes.  If you setup LVM on your server, then you can use snapshots as a way to freeze the file system BEFORE doing any update/new package installation trials.  LVM-Snapshots are good for getting clean backups too.  Using LVM is an intermediate skill for administrators. There are other ways that people create snapshots, but none of those are ready for production use on physical hardware installations.

You might consider using virtual machines, since those can be swapped out in under 1 minute and have a different sort of "snapshot" capability.

90% of all Unix systems are very similar.  95% of all Linux servers are similar, but that last 5% is different usually in the package management area.

BTW, please be certain that you do a **sudo apt update  && sudo apt dist-upgrade** before trying to install any packages. This will get the system patched into a known state, which is important.  If the file, /var/run/reboot-required, exists, then you also need to reboot after those patches.  At least once a month, you probably want to run **sudo apt autoremove ** and **sudo apt autoclean** so that extra kernels are removed and /boot/ doesn't fill up.
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) has an overview of weekly maintenance for Ubuntu.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a general Linux book. There is a Portuguese translation in progress. You might contact the guy leading that effort to help.

---

### Post by SeijiSensei on 2019-12-02
Do not worry about installing "dependencies" like libssl-dev and any other programs or libraries a package relies on.  The beauty of package managers like apt is that they know which dependencies are required and will bring them in automatically.  

[https://help.ubuntu.com/lts/serverguide/apt.html](https://help.ubuntu.com/lts/serverguide/apt.html)

---

### Post by victorftp on 2019-12-02
> **TheFu said:**
> This is why people have development, test, pre-production, disaster recovery AND production environments.

I'm on production server. This is the big "problem". I'm going to study how creating LVM snapshots seems to be interesting. thank you

---

### Post by TheFu on 2019-12-02
> **victorftp said:**
> I'm on production server. This is the big "problem". I'm going to study how creating LVM snapshots seems to be interesting. thank you

Clone the production machine onto another machine and do your testing there.
LVM can't really be added to an existing OS. It has to be selected at install time.
LVM can be added for data partitions post-install, but not the OS.

---

### Post by SeijiSensei on 2019-12-02
Install a copy of [VirtualBox]("https://virtualbox.org/") on another machine and recreate the server environment there. VB can run on Windows, Macs, and Linux and support any of those operating systems inside a virtual machine.  16.04 will only be [supported]("https://wiki.ubuntu.com/Releases") through April of 2021.

A VirtualBox VM exists simply as a couple of files in $HOME/VirtualBox VMs/[name of VM]. For instance, I have an instance of 18.04 Server on this machine.  It lives in the "Ubuntu Server 18.04" directory under /VirtualBox VMs/.  If you make a copy of that directory after you install Ubuntu, you can always retrieve it and get back your original environment if you mess things up.

---

