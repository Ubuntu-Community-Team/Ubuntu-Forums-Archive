---
title: "Noob Question:  The user created while installing does not have SUDO access rights"
date: 2024-01-09
forum: New to Ubuntu
---

### Post by brunogenovese on 2024-01-09
It has been one or two decades since I used Linux and it is my first time on Ubuntu.   I installed on VirtualBox and it asked me to create a user (presumably to avoid using root).

But... I saw no sign of the root account password (or even how to switch user to it) and the created username does not have SUDO access, nor the access rights to add itself to the SUDO list.

How do I fix this?
(and hopefully don't laugh too hard at my ignorance :) )

---

### Post by TheFu on 2024-01-09
The first user DOES have sudo capability, unless you didn't get a normal ISO from Canonical.

Check the groups for the user with the 'id' command.  Don't look for "wheel", that isn't the sudo group for Ubuntu, 'sudo' is.

Ubuntu doesn't use root directly and it is designed to work that way.

[https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) is a useful reference, assuming you can just skim the first 250 pgs and know that content.

---

### Post by yancek on 2024-01-09
Ubuntu doesn't use a 'root' user but the primary user created during the installation is given root privileges.  You need to prepend any command with sudo to make system changes and anything that requires root privileges.  If the user you created during the installation cannot use sudo, I would suggest reinstalling and perhaps reading through some tutorials on installing it because something major went wrong during the install.

---

### Post by brunogenovese on 2024-01-10
> **TheFu said:**
> The first user DOES have sudo capability, unless you didn't get a normal ISO from Canonical.
When I googled "Ubuntu download" I found no links for a domain "canonical.???".  All of the links were for ubuntu.com.

I downloaded "Ubuntu Desktop 22.04.3 LTS" from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop).

After install I got user "vboxuser" (probably since I was installing from VirtualBox) which is what I logged in with.

When I try to sudo with that user I get "vboxuser is not in the sudoers file.   This incident will be reported."



Since this Ubuntu install does not seem to behave the way it should, I am going to create a new install from the same downloaded ISO and see what happens.  If it still fails I will try the other version available 23.10, even though it seems to be a newer/DEV version and appears to rely on a "Legacy Desktop Installer".

---

### Post by ActionParsnip on 2024-01-10
What is the output of:
```

groups; grep 1000 /etc/passwd

```
Thanks

---

### Post by TheFu on 2024-01-10
> **brunogenovese said:**
> When I googled "Ubuntu download" I found no links for a domain "canonical.???".  All of the links were for ubuntu.com.

I downloaded "Ubuntu Desktop 22.04.3 LTS" from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop).

After install I got user "vboxuser" (probably since I was installing from VirtualBox) which is what I logged in with.

When I try to sudo with that user I get "vboxuser is not in the sudoers file.   This incident will be reported."



Since this Ubuntu install does not seem to behave the way it should, I am going to create a new install from the same downloaded ISO and see what happens.  If it still fails I will try the other version available 23.10, even though it seems to be a newer/DEV version and appears to rely on a "Legacy Desktop Installer".

virtualbox has ZERO to do with the installation or users inside the VM.  During the install, you were asked for a username and password. That is what you need to be using.  Do not use vboxuser.  Think "bruno" - all lowercase.  

Also, you probably want to change the default hostname to be descriptive, short, all-lowercase too.

Before you go too far, you do realize that support for 23.10 ends in June, right?  People new to Linux should be using LTS releases - 22.04 is the current LTS.
I think there was an issue with the 23.10.0 ISO. It was just for 1 platform and I don't remember which, but if there's a 23.10.1, get that.  Non-LTS releases like 23.10 don't normally get a .1 ISO release, so this is odd and just for clarity that they named it 23.10.1.

---

### Post by brunogenovese on 2024-01-10
Thanks to all.   I was able to solve the issue as follows:

1) Completely uninstalled Ubuntu and deleted the VirtualBox machines for it.  In other words, starting from scratch.

2) Installed 23.10 (DEV) Ubuntu in a fresh VirtualBox VM.  This time it did prompt me for a new username (besides vboxuser which is created by VirtualBox BEFORE launching the install) and a bunch of other details during install.  The new user and sudo work fine on 23.10.1.

3) Attempted several fresh install of 22.04.3 LTS.  _The installer used for this version is definitely bugged_.  
At least when installing from VirtualBox the LTS installer does not go through the series of screens where the install should be prompting for things like language, hostname, username, etc.  (the 23.10.1 version does it just fine)

Summary:  I got 23.10 working, sticking to that one until a fix comes out for the LTS installer.

---

