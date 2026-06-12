---
title: "Can't logon following updates"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by josh_eckert on 2014-01-20
I have been using lubuntu for a couple of days now as a VM under virtualbox. After installing a few updates I rebooted the machine and entered my password to login. Upon hitting enter the login dialogue disappeared as I would expect however nothing else happens!

I can reach the terminal using Ctrl + Alt + F1 but I would really like my GUI back :(

I tried the following which was recommended on another forum.

sudo apt-get install lubuntu-desktop
sudo mv -v .Xauthority .Xauthoritybak
sudo shutdown now -r

After trying this when logging in I get a black screen with some text that displays to quickly to read. I am then returned to the login prompt. Again I can still access the terminal but it seems I've made things worse?

Any help would be much appreciated

---

### Post by newb85 on 2014-01-20
Try booting with one version older kernel.

---

### Post by josh_eckert on 2014-01-20
I just tryed using the older linux version. I selected ubuntu, with linux 3.11.0-12-generic instead of 3.11.0-15-generic.

Unfortunatly that didnt work however im now concerned that the commands below that I mentioned in my previous post have messed things up further :(

Does anyone know what these do?

sudo mv -v .Xauthority .Xauthoritybak
sudo shutdown now -r

---

### Post by Ubi_one_2014 on 2014-01-20
what happends when you execute the command  'startx', form terminal?

---

### Post by josh_eckert on 2014-01-20
I gave 'startx' a go earlyer but that just caused the screen to go black

---

### Post by Ubi_one_2014 on 2014-01-20
[http://askubuntu.com/questions/159663/how-to-reset-the-xorg-xserver](http://askubuntu.com/questions/159663/how-to-reset-the-xorg-xserver)

---

### Post by rburkartjo on 2014-01-21
this worked for me. no promises. open virtual termanl ctr + alt +F1. login and then type rm.xauthority (you might have to type sudo su to become root user. then type in shutdown -r now. good luck.

---

### Post by josh_eckert on 2014-01-22
> **rburkartjo said:**
> this worked for me. no promises. open virtual termanl ctr + alt +F1. login and then type rm.xauthority (you might have to type sudo su to become root user. then type in shutdown -r now. good luck.

tryed that both with and without sudo i just get command not found.

---

### Post by Costovski on 2014-01-22
I'm monitoring this thread, I'm getting the same issue as OP. Something that might be worth noting is that if I leave the terminal open, warnings keep appearing: "ieee80211 phy0: rt61pci_txdone: Warning - TX status report missed for entry #", with # being 7 different numbers as of now.

---

### Post by Ubi_one_2014 on 2014-01-22
> **josh_eckert said:**
> tryed that both with and without sudo i just get command not found.

[http://askubuntu.com/questions/299127/why-do-i-have-so-many-xauthority-files-in-my-home-directory](http://askubuntu.com/questions/299127/why-do-i-have-so-many-xauthority-files-in-my-home-directory)

---

### Post by bapoumba on 2014-01-22
When you are in the console, please check your home or other directory is not full
```
df -h
```

---

### Post by josh_eckert on 2014-01-23
> **bapoumba said:**
> When you are in the console, please check your home or other directory is not full
```
df -h
```

Turned out the drive was full, I used the terminal to free up some space and now I'm in!

Thanks for your help thats restored my faith in Linux.

I am still however interested to know what these commands did:

```
sudo mv -v .Xauthority .Xauthoritybak
sudo shutdown now -r
```

Im not really a fan of blindly typing into a terminal

---

### Post by bapoumba on 2014-01-23
> **josh_eckert said:**
> Turned out the drive was full, I used the terminal to free up some space and now I'm in!

Thanks for your help thats restored my faith in Linux.
Glad to see you got it fixed. One thing to remember is that Linux systems cannot open user sessions (or sometimes even boot) if some sensitive directories are full or almost full (/home, /, /boot if you have one, otoh).

> **josh_eckert said:**
> 
I am still however interested to know what these commands did:

```
sudo mv -v .Xauthority .Xauthoritybak
sudo shutdown now -r
```

Im not really a fan of blindly typing into a terminal


First command : .Xauthority is a cookie that is created when you start a Xserver session. It tells you have rights to access the X server. Sometimes, permissions on this file get messed up and you can log in but not start the X server, then you go back to the login screen. Renaming the cookie (to Xauthoritybak) allows to keep a copy of the old one and create a new one on login as there is none to use. It sometimes helps to fix problems.

Second command : safely shuts down the system and reboots.

Edit : I should add that you can check the manual for each command and see what it does. I admit it can sometime sound cryptic but you will never learn if you never start reading :)
Type man <command> in the terminal.

You can also read man pages on the internet, I like [http://linux.die.net/man/](http://linux.die.net/man/)

---

### Post by newb85 on 2014-01-24
Just be careful when reading man pages on the net. Sometimes those pages are for different versions of the commands, and so the syntax are different.  Ideally, you get your man pages from a source designed for your distro and release. (Unless you're talking third party software...)

---

### Post by rburkartjo on 2014-01-24
my bad the command i gave you should have rm .Xauthority (there is a space between rm and .Xauthority. you have corrupted .Xauthority file in your home folder. by deleting it it will automaticly be rebuilt when you reboot. check you home folder and you will see the file.

[http://www.ubuntuask.com/q/answers-logged-out-out-immediately-after-login-367260.html](http://www.ubuntuask.com/q/answers-logged-out-out-immediately-after-login-367260.html)

---

### Post by bapoumba on 2014-01-24
> **newb85 said:**
> Just be careful when reading man pages on the net. Sometimes those pages are for different versions of the commands, and so the syntax are different.  Ideally, you get your man pages from a source designed for your distro and release. (Unless you're talking third party software...)

Yes, of course, thanks :)

---

