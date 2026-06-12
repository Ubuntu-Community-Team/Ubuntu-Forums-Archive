---
title: "Sudo password for user"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by betinhoweck on 2013-03-04
Hey,

I was trying to install steam for ubuntu and the terminal says that steam need to install additional packages (libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386) but it asks for a password, which, I don't have. Is it a default password? this message appears everytime I try to use the Terminal. :(

Thanks in advance.

---

### Post by zika on 2013-03-04
It is password that You've chosen when installing Ubuntu, for that user...

---

### Post by sudodus on 2013-03-04
> **betinhoweck said:**
> Hey,

I was trying to install steam for ubuntu and the terminal says that steam need to install additional packages (libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386) but it asks for a password, which, I don't have. Is it a default password? this message appears everytime I try to use the Terminal. :(

Thanks in advance.
Welcome to the Ubuntu Forums :-)

The sudo password is the same as the log in password for the user, provided the user has the privilege to run superuser processes.

In other words, if your user account is enabled to use sudo, you can use your normal password. Otherwise you must ask your system administrator, if you can get superuser (alias root) privileges.

---

### Post by betinhoweck on 2013-03-04
Well, I am supposed to be the administrator, and the password i chose during installation was "123" but it is not working. I've tried to edit it in the accounts settings but it keeps asking a password for permission. 

I'm sorry for being such a noob :P

Thanks for fast reply

---

### Post by uzumakifahim on 2013-03-04
If you want to change the account setting, then you also have to enter your password. After giving the correct password, you'll be able to change the user settings.

---

### Post by sudodus on 2013-03-04
[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]If your password is not working, you can reset it according to this link[COLOR=#ff0000]

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)[/COLOR]

I think you need at least 6 characters (and it should not be a word in a dictionary), better with at least 8 characters and at least one non-alphanumeric character (not a-z,A-Z,0-9).

---

### Post by betinhoweck on 2013-03-04
I have ubuntu dual-boot with windows 7, and I can't see any recovery mode in the boot menu...

---

### Post by sudodus on 2013-03-04
> **betinhoweck said:**
> I have ubuntu dual-boot with windows 7, and I can't see any recovery mode in the boot menu...

Please list the alternatives in your boot menu! (Is it a grub menu or a Windows boot menu?)

Is it dual boot or wubi install?

---

### Post by betinhoweck on 2013-03-04
the alternatives are:
Windows 7
Ubuntu
It is a windows like menu and I've installed Ubuntu through Wubi.

---

### Post by sudodus on 2013-03-04
> **betinhoweck said:**
> the alternatives are:
Windows 7
Ubuntu
It is a windows like menu and I've installed Ubuntu through Wubi.
I haven't run Wubi, but I guess that Ubuntu is booted from that first Windows menu, and maybe via a hidden grub menu. If this is the case maybe you can try pressing the shift key after selecting Ubuntu according to the tip in the Psychocats link.
>  First, you have to reboot into *recovery mode*. 

 If you have a single-boot (Ubuntu is the only operating system on your computer), to get the boot menu to show, you have to hold down the *Shift* key during bootup. 


If no go, 
1. Backup your ***/etc/default/grub*** file
```
cp -p /etc/default/grub /etc/default/grub.0
```
2. Edit your ***/etc/default/grub*** file. Change the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to 
```
GRUB_CMDLINE_LINUX_DEFAULT="recovery nomodeset"
```
3. Run
```
sudo update-grub
```
and reboot

---

### Post by betinhoweck on 2013-03-04
Thanks guys, finally did it, it appeared that my user had no password at all, or a blank one idk... now it is working... One last question, I have some questions about installing drivers and stuff, should I open a new thread?

thanks a lot!

---

### Post by betinhoweck on 2013-03-04
Thanks guys, finally did it, it appeared that my user had no password at all, or a blank one idk... now it is working... One last question, I have some questions about installing drivers and stuff, should I open a new thread?<br><br>thanks a lot!

---

### Post by sudodus on 2013-03-04
> **betinhoweck said:**
> Thanks guys, finally did it, it appeared that my user had no password at all, or a blank one idk... now it is working... One last question, I have some questions about installing drivers and stuff, should I open a new thread?

thanks a lot!
Congratulations :KS

and yes, a new thread with a good descriptive title will attact people who know about that particular problem.

---

