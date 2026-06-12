---
title: "Stuck in text mode after trying to install Nvidia driver"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by joker0n3 on 2008-11-08
Intrepid installed fine. Downloaded all the updates and necessary drivers and whatnot. Then when i went to install the Nvidia driver and restart my comp i get stuck in text mode and cant get back to the os GUI. PLOX HALP! I got my XP install cd on standby.

---

### Post by Skripka on 2008-11-08
First thing to try, login in at the prompt then:

```
 sudo /etc/init.d/gdm start
```

substitute "gdm" with "kdm" if on Kubuntu.

---

### Post by joker0n3 on 2008-11-08
> **Skripka said:**
> First thing to try, login in at the prompt then:

```
 sudo /etc/init.d/gdm start
```

substitute "gdm" with "kdm" if on Kubuntu.
I've tried that option already.
And when i do gdm status, it says its running.
Go figure, im still in text hell.

---

### Post by tvtech on 2008-11-08
first of all. threats are not welcomed 

second off to regain control of your visual ubuntu system type the following at the command prompt 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will reconfigure your xorg.conf file which seems to have broken due to the nvidia proprietary driver and your hardware.  you may want to do some research as to why this is and not give up so easily.  Linux is more about the learning and playing than the stable functional OS, unless you purchased a computer pre-configured with Linux then it is all about the functional OS.

---

### Post by ad_267 on 2008-11-08
How did you try to install the nvidia drivers? Did you go to System - Administration - Hardware Drivers to enable them?

You can reconfigure your X server to default settings by running "sudo dpkg-reconfigure -phigh xserver-xorg"

Oh, before you do that, what happens if you press "Ctrl + Alt + F7"? You said GDM was already running so you might just be on another tty.

---

### Post by joker0n3 on 2008-11-08
> **tvtech said:**
> first of all. threats are not welcomed 

second off to regain control of your visual ubuntu system type the following at the command prompt 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will reconfigure your xorg.conf file which seems to have broken due to the nvidia proprietary driver and your hardware.  you may want to do some research as to why this is and not give up so easily.  Linux is more about the learning and playing than the stable functional OS, unless you purchased a computer pre-configured with Linux then it is all about the functional OS.
Threats? lol.
OK.
Ill play the game.
Ill try this line and see what i get. I used Hardy and the nvidia driver seemed to work fine.

---

### Post by ad_267 on 2008-11-08
> **joker0n3 said:**
> Threats? lol.
OK.
Ill play the game.
Ill try this line and see what i get. I used Hardy and the nvidia driver seemed to work fine.

Try pressing Ctrl+Alt+F7 first.

---

### Post by fooman on 2008-11-08
could also boot into recovery mode and give the xfix option a try.

---

### Post by joker0n3 on 2008-11-08
> **joker0n3 said:**
> Threats? lol.
OK.
Ill play the game.
Ill try this line and see what i get. I used Hardy and the nvidia driver seemed to work fine.

Line didnt work. I could try recovery now but im too lazy i have to keep restarting my comp to use my Gimpdows to check forums. Ill try it later. And i have looked online, seems this is my best resource so far for finding answers. If anything else ill just reinstall Hardy; never had any probs with it and it doesnt seem like 8.10 is a major upgrade anyhow. But thanks to all. :)

---

### Post by joker0n3 on 2008-11-08
63 views ...can i get a bean for that? lol
Only my 2-3 post on forums ever.

---

### Post by cariboo on 2008-11-08
Trolling doesn't help

> I got my XP install cd on standby. 

If you aren't willing to do as the previous posters have suggested, maybe Linux is not for you. Have a look here:

[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

May be this will help you decide if you've got what it takes to use Linux.

Jim

---

### Post by handydan918 on 2008-11-08
> **joker0n3 said:**
> Intrepid installed fine. Downloaded all the updates and necessary drivers and whatnot. Then when i went to install the Nvidia driver and restart my comp i get stuck in text mode and cant get back to the os GUI. PLOX HALP! I got my XP install cd on standby.

I feel your pain. 
In the future, please direct any hateful comments to [http://www.nvidia.com/page/support.html]("http://www.nvidia.com/page/support.html")

Maybe they will Open theit drivers so that Ubu can include them in the (Debian!) kernel.

Thank you for your support.
:popcorn:

---

### Post by bodhi.zazen on 2008-11-08
I am sorry you are having problems with your nvidia card, yes this is frustrating, and yes we will help.

Would you mind providing some additional information ?

What nvidia card are you using ?

When you say you installed the nvidia drivers , what did you do exactly ?

---

