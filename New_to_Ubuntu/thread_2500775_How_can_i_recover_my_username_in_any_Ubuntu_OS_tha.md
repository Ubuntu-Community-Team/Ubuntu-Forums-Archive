---
title: "How can i recover my username in any Ubuntu OS that is compatible with a mbs ram PC"
date: 2024-09-11
forum: New to Ubuntu
---

### Post by elreydelaswasas2 on 2024-09-11
[COLOR=#0C0D0E][FONT=-apple-system]Int this situation: the username that i want to recover belongs to myselft, [/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]i can´t find your username/password and i can´t get access to your username/password, i don´t know which version of Ubuntu i am using but i need the answer to solve my issue for every version of Ubuntu compatible with a up to 4 mb ram PC, i am not sure if i am the admin and i am not sure which version of ubuntu is it, i only know i am the unique username created in ubuntu installation[/FONT][/COLOR]

---

### Post by TheFu on 2024-09-11
Sorry. Don't understand the question.  If there is a username, it will be in the local or NIS or NIS+ or LDAP password DB.  If the system is properly configured, running 
**getent passwd** will show all users and home directories.  If the sysadmin didn't specifically setup NIS, NIS+ or LDAP, then that isn't being used.

This is for any Unix-like OS, not just Ubuntu or Linux.  Look for uid numbers over 500 for the ones that are likely to be for humans.

As for accessing the password, that's not possible.  They are encrypted using a 1-way method.  If you have sudo/root access on the system (or for the external LDAP/NIS/NIS+ DBs), you can just override the existing password for the specific user, so you know the password going forward.

If you don't have root/sudo access inside the system AND the OS of the system isn't encrypted, you can find techniques for setting a new password for any normal user account all over the internet. There are multiple methods.  If the OS is encrypted and you don't know the decryption passphrase/method, I don't know of any method to do what you want.

---

### Post by elreydelaswasas2 on 2024-09-11
i edited my message so you can understnad it

---

### Post by Holger_Gehrke on 2024-09-11
I really hope the 'mb' in the title is a typo. I don't think there ever was a version of Ubuntu that would have run in 4 megabyte. I ran some of the earliest Linux distros back in the mid to late 90s and my machine back then had 16 Mb and was swapping quite heavily.

User names are stored in '/etc/passwd' (despite the name of that file there are no passwords in there; those are in /etc/shadow or rather their hashes are). If you can get to a root shell you can use 'getent passwd' to list all users. For the steps to get to a root shell look in [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by elreydelaswasas2 on 2024-09-11
i edited my message agian now it is enough clear

---

### Post by elreydelaswasas2 on 2024-09-11
now i specified it is a up to MBs RAM PC, i don´t know how much ram exactly

---

### Post by elreydelaswasas2 on 2024-09-11
[FONT=Verdana]how to recover my username in every Ubuntu version if also: i can´t find your username/password, i can´t get access to your username/password, i am not sure if i am the admin, i only know i am the unique username created in ubuntu installation ?[/FONT]

---

### Post by TheFu on 2024-09-12
> **elreydelaswasas2 said:**
> now i specified it is a up to MBs RAM PC, i don´t know how much ram exactly

The link from Holger_Gehrke is the best advice, but if a system hasn't been used in a very long time, there is little reason to bother with any of this. Just get a copy of Lubuntu 22.04.x and create a bootable flash drive with that ISO and install that release.  

TL;DR version .... 
In 1991, a basic Linux would barely run in 4mb of RAM on a 386sx CPU.  In the early 2000s, Linux support dropped all CPUs before the i686 CPU and by that point, every PC sold had hundreds of MB to a few GB of RAM. Ubuntu was first released in June 2006, when a common PC had 1G to 2G of RAM.

So, **there have never been any versions of Ubuntu that ran on a 4MB system.**  I think a minimal Ubuntu Server needed at least 128MB in the first release.

But none of that helps you.  We cannot guess a username on your system. Sorry. Could be almost anything, provided it starts with an alphabet letter and has letters and/or numbers following that first letter.  Usernames are case-insensitive.  If a GUI login screen is launched on the computer, often, the last username will be displayed or you can click on the space where the username should go and a list of possible names will show up.   I prevent this for security reasons, but I don't think it is the default on Ubuntu GUIs.  If there is no GUI, you'll see a black screen with a login prompt that waits for the username to be entered, then it will ask for the password.

The amount of RAM has nothing to do with what usernames can be used, so that is completely unrelated.  I seriously think the 4MB of RAM amount is incorrect unless the computer is 25 yrs old. If it is, no version of Ubuntu will run on it anyway. It will probably have the wrong type of CPU.

If you have a really old computer and need/want to run a version of Linux, there are some specialized releases, not from Canonical, made for those types of systems.  The one I used for online banking needs just 64MB of RAM and only has a web browser on a very light GUI.  It loads the entire OS into RAM and runs **crazy fast**.  Of course, with 128MB of RAM it is even faster, which is hard to believe.

---

### Post by yancek on 2024-09-12
> [COLOR=#0C0D0E][FONT=-apple-system]i don´t know which version of Ubuntu i am using but i need the answer to solve my issue for every version of Ubuntu[/FONT][/COLOR] 

The first release of Ubuntu was 20 years ago which would mean 40 releases.  Are you asking how to get this information simply because you don't know which release you have or do you actually have all 40+ releases installed on various computers?  You don't indicate that information nor do you indicate whether you are able to boot any of them so answer that.  If you can boot and, you should be able to get the release version by running one of the commands below which simply open a text file:

> cat /etc/issue
cat /etc/lsb-release
cat /etc/os-release

If you cannot boot any of the Ubuntu systems you have, you will need to get some Linux 'live' usb to boot, then mount the partition which has the root filesystem for the OS and access those files.  I would expect one of these commands to work but I don't know about older versions.

Passwords are not stored in plain text anywhere on the system as that would be pointless so your option is to reset the password.  It is the responsibility of the user to remember his/her password.  Resetting a password from a 'live' Linux is described at any number of sites online including the one at the link below.

[https://www.blackdown.org/forgot-ubuntu-password-reset/](https://www.blackdown.org/forgot-ubuntu-password-reset/)

The command in post 2 should show the user names on the system but if you can't boot it, you will need a 'live' Linux OS to mount the / root filesystem partition to get it.

---

