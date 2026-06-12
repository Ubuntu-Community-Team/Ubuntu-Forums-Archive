---
title: "Ubuntu Server 8.04 (startx Problem)"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by mustimasti on 2008-07-06
Hi, I am completely new to ubuntu infact linux, i want to bring ubuntu in GUI mode, when i type startx i get following error mesaage

"The Program 'startx' is currently not installed.you can install it by typing sudo apt-get install xinit

and when i try this command sudo apt-get install xinit

i get following error E: couldn't find package xinit.

Can any 1 help me, i have installed the iso image from the ubuntu site and i have already installed the server in easy way but cant bring in GUI mode

---

### Post by bjschuma on 2008-07-06
If you try "sudo apt-get install ubuntu-desktop"  it should install the xserver and gnome (the desktop environment Ubuntu usually comes with) for you.

---

### Post by louieb on 2008-07-06
The server doesn't come with X or a GUI. Don't let the titile fool you this page describes some of the various desktop/window managers you can add to your server. [Installation/LowMemorySystems - Community Ubuntu Documentation ]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
BTW my favorite is fluxbox.

---

### Post by mustimasti on 2008-07-07
> **louieb said:**
> The server doesn't come with X or a GUI. Don't let the titile fool you this page describes some of the various desktop/window managers you can add to your server. [Installation/LowMemorySystems - Community Ubuntu Documentation ]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
BTW my favorite is fluxbox.

hi, thanks, i am completely new to this ok if you dont mind can u guide me more

i have download the fluxbox-1.0.0.tar.tar & fluxbox-1.0.0.tar.gz both the files now i have burn on cd now please guide me step my step with command how to install it, it will be great help if u can please

---

### Post by louieb on 2008-07-07
lol: installing from a tar archive  isn't the easiest (tar is kinda like a winzip file in widows). 
 
fluxbox is in the Ubuntu repositories. Do it easy. run

```
sudo aptitude install xorg
```

then

```
sudo aptitude install fluxbox fluxconf
```

now startx or startfluxbox should get you a rather bare fluxbox  session going.

Lots of fluxbox enthusiast here. Heres a good thread by one of them on how to [HOWTO: get a Fluxbox menu (and customization) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox") 

Have fun - Good lick.
lou

---

### Post by hyper_ch on 2008-07-07
why do you want to have a gui on a server?

---

