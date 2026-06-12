---
title: "permissions problem"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by bamh1d on 2013-07-14
I am experiencing a problem that I don't understand.  I am logged in as the system administrator.  When I attempt to run update manager, I get an error message saying that various files in the /var/lib directory could not be opened.  While I am indeed able to open this directory, when I check properties/permissions on specific subdirectories and files in this directory I get a message saying that I am not the owner and cannot change the permissions.  I thought that as the administrator I had all access and permissions.  :confused: 

Any help would be appreciated.

---

### Post by steeldriver on 2013-07-14
Hello and welcome to the forum

The Linux 'sudo' mechanism doesn't work quite the same as a Windows 'administrator' account - when you log in with an account that is a member of the 'sudo' group, it doesn't mean that everything you do is done with administrative privileges - it means you *may obtain* administrative privileges temporarily (by running commands with 'sudo' or 'gksudo' as appropriate) 

See --> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Impavidus on 2013-07-14
Do you know this? [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In short, the administrator doesn't have the right to modify any system files, but he does have the right to become root temporarily and root does have the right to modify those files.

Concerning your problem with the update manager, maybe the problem is some other package manager is already active. Close any software centre, synaptic, apt-get or whatever may be running and try again. Rebooting is also a way to make sure no other package manager is running.

---

### Post by bamh1d on 2013-07-14
Thanks very much for your help, steeldriver and impavidus.  I should have mentioned that I am running the Unity desktop on top of Ubuntu 12.04.  If I have understood the information in your link, I need to run gksudo from a terminal before launching any system functions such as update manager.  Correct?

While I'm at it, I'm also having a (possibly related) problem with the Ubuntu software center.  When I try to launch it from Unity, it starts to load and then just terminates, without any explanation.  Do I need to run gksudo before launching the Ubuntu software center?

---

### Post by bamh1d on 2013-07-14
Also, here is the error message I get from the Update Manager: 
E: problem opening /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_packages, E: the package lists or status file could not be parsed or opened. This usually means that your installed packages have unmet dependencies.

---

### Post by CinTUX on 2013-07-16
> **bamh1d said:**
> Also, here is the error message I get from the Update Manager: 
E: problem opening /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_packages, E: the package lists or status file could not be parsed or opened. This usually means that your installed packages have unmet dependencies.

I looked up for the error you get from the Ubuntu Store.
 It may be a bug. (src: [https://bugs.launchpad.net/ubuntu/+bug/1010860](https://bugs.launchpad.net/ubuntu/+bug/1010860))

You could try out these commands:
$ sudo rm /var/lib/apt/lists/*
$ sudo apt-get update

Good Luck!

---

### Post by dannyboy79 on 2013-07-16
just an FYI also, you don't want to run Update-Manager with gksudo. If you launch it normally it should already prompt you to enter your password. You have a separate issue going on which CinTUX pointed out

---

### Post by CinTUX on 2013-07-16
> **dannyboy79 said:**
> just an FYI also, you don't want to run Update-Manager with gksudo. If you launch it normally it should already prompt you to enter your password. You have a separate issue going on which CinTUX pointed out

Indeed, but he also had problems with Ubuntu Software Centre, that could be a solution for that.

---

### Post by bamh1d on 2013-07-16
I tried executing the first command and got this message:

rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
I'm not sure what to do about this.  I don't know why it wouldn't remove a directory.

When I ran the sudo apt-get update command, I get this error message:

Reading package lists... Error!
E: Unable to synchronize mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.


Help!

---

### Post by Impavidus on 2013-07-17
**rm** removes ordinary files, **rmdir** removes empty directories and **rm -r** removes directories along with everything inside.

---

