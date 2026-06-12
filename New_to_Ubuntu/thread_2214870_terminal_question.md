---
title: "terminal question"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by sammykur on 2014-04-03
When i open terminal the command prompt is 

user@user-MS-7599:~$

when going to root it is

root@user-MS-7599~#

is this normal ???

I tried a search and all I found was the 7599 appears to refer to my motherboard (msi 870A-g54)

sorry if this is already been asked but when searching it seems all I can find is terminal commands to identify your motherboard with the terms i used.

---

### Post by bapoumba on 2014-04-03
Yes, it is normal.
<your_username>@<the_machine_name_you_choose_for_this_install> is you regular identification.
$ means you are logged as a regular user.
# means you are logged as root

Here is mine for ex:
```
bapoumba_lxde@SonyBlue:~$ sudo su
[sudo] password for bapoumba_lxde: 
root@SonyBlue:/home/bapoumba_lxde#
```

Be careful when logged as root, please use sudo in front of commands instead : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

May be your machine name was suggested during the install process and you did not change it to something more personal :)

---

### Post by slickymaster on 2014-04-03
> **sammykur said:**
> When i open terminal the command prompt is 

user@user-MS-7599:~$

when going to root it is

root@user-MS-7599~#

is this normal ???

I tried a search and all I found was the 7599 appears to refer to my motherboard (msi 870A-g54)

sorry if this is already been asked but when searching it seems all I can find is terminal commands to identify your motherboard with the terms i used.
Generically it's _username @ hostname_ (the name that you gave your computer).

The terminal prompt contains the name of the user, the name of the computer and the name of the current directory (i.e., the directory in which the user is currently working).

---

### Post by Double.J on 2014-04-03
Hi there! 

Welcome to the forums!!

glad you're enjoying Ubuntu, as slickymaster and bapoumba have stated, completely normal!!

the terminal is actually showing you where you are. 

```
 username@hostname:/where_you_are/in_the/fs 
```

The name of the motherboard just got set at the hostname during install just because it's how the bios identified itself to the OS during install. You can call it whatever you like! The host name can be found in /etc/hostname, but you'll also have to correct /etc/hosts so ecerything works okay. More info [here]("http://askubuntu.com/questions/9540/how-do-i-change-the-computer-name").

changing your username if you so wish is pretty easy, and there's a great answer on [askununtu]("http://askubuntu.com/questions/34074/how-do-i-change-my-username")

googling will show you you can change the hostname with the hostname command - this is only for servers and machines that would be too much hassle to reboot. This command only changes the hostname until reboot when the original hostname would be read from /etc/hostname 

As previously stated, it is not recommended to run as root, sudo and gksudo are more than sufficient. Also take special care if you ever find yourself opening a file browser with gksudo - remember that you'll be starting from the root user's /home.

jj

---

### Post by sammykur on 2014-04-03
Thank you All much thanks

---

### Post by Warren Hill on 2014-04-03
Your computer has both a computer name and each user has a user name.

Your user name is 'user' and your computer name 'user-MS-7599'

As others have pointed out the the default prompt is for a normal user is:
username@hostname:/where_you_are/in_the/fs$

Where as the default prompt for root is:

root@hostname:/where_you_are/in_the/fs#

The final character '$' indicates you are a normal user while a final character '#' indicates you are logged on as root.
This is an important warning because when you are logged on as root you can do anything you want to the system - including really mess it up.
The '#' warns you be careful I'm not checking if what ask for is dangerous; the computer is trusting you implicitly.

You can change the prompt if you wish by changing the environment variable PS1.  Many people don't bother but if you are interested there is more detail here:

[PS1 prompt explained]("http://www.linuxnix.com/2013/04/linuxunix-shell-ps1-prompt-explained-in-detail.html")

---

### Post by Lars Noodén on 2014-04-04
If you do change the PS1 prompt and you like the changes, the place to store the changes permanently is usually .bashrc.

---

