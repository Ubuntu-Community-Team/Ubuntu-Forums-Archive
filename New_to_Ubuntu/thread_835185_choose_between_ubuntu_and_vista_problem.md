---
title: "choose between ubuntu and vista problem"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ignorant fool on 2008-06-20
when i played ubuntu from the disk, everything was ok. when i booted my computer, it said: choose between OS's (or something)
and i could choose between vista and ubuntu, and if i didnt choose in 10 secs, it'd choose vista automatically. thats how i want it.
but when i installed ubuntu on my computer, it did something different. when i booted my computer i suddenly had to choose between 5 operating systems. and the names suddenly became very long. kernel ubuntu/somethingsomething. which was just ubuntu. 2 of which i didnt understand. and there was windows xp and vista. while i dont even have xp. and when i didnt do anything it started ubuntu again. and when i said start vista, i hate to choose again between ubuntu and vista (the way it was in the beginning. does anyone know how i can bring this back to how it was when i put the cd in? and maybe, if i ever wanted ubuntu to be my main os, how to change the main os into ubuntu?
thank you.

Edit: I typed this in the terminal:
sudo aptitude install startupmanager

now it said this:
sudo: timestamp too far in the future: Jun 20 16:38:13 2008

it's 15:27 at my place right now. what does this mean?

---

### Post by Joeb454 on 2008-06-20
Ok hit Alt+F2, then enter ```
gksudo gedit /boot/grub/menu.lst
``` And post the contents of that file back here in [noparse]```

```[/noparse] tags :)

---

### Post by ignorant fool on 2008-06-20
what? now? im on vista btw. when do i have to press alt-F2?

---

### Post by drs305 on 2008-06-20
To sort out some of your problems, I recommend (while in linux) installing Startup-Manager and editing your boot menu from there. It will allow you to choose which OS to boot to, how long to see the menu, and how many kernels you want to see. 

Install StartUp-Manager with the following command:
```
sudo aptitude install startupmanager
```

Open it from System > Administration > StartUp-Manager

Learn how to use it and edit other options of the boot menu from reading this:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Joeb454 on 2008-06-20
drs305's answer will probably be better :) And you need to be in Ubuntu to do this :)

---

### Post by ignorant fool on 2008-06-20
what? i dont get the command? where do i put it? i dont know alot about computers. and i cant find system>administration>startup-manager. are u talking about vista?

---

### Post by Joeb454 on 2008-06-20
No talking about Ubuntu.

In Ubuntu click Applications &#8594; Accessories &#8594; Terminal, and enter the command there :)

It will ask for your password, so enter that (don't worry it's safe). And don't be alarmed when it doesn't show anything being typed, that's normal too

---

### Post by aeiah on 2008-06-20
in linux, as has been said twice already. 

to install the startup manager, whilst in ubuntu linux use the menu to go applications > accessories > terminal

in the terminal, type (or copy and paste)
```
sudo aptitude install startupmanager
```
this will download and install the startup manager. it'll ask you for your password etc. when you've done, you can start it up by using the menu to go: System > Administration > StartUp-Manager

and from there you can set which OS to default to, and the other things mentioned.

it seems like you're going through two layers of the grub menu instead of just the normal one, although this might be a seperate issue. see how you get along with the startup manager. by the way, make sure the ubuntu cd is out of the cd drive now that you've installed ubuntu already.

---

### Post by ignorant fool on 2008-06-20
sorry. i began typing that post before it was said. 

edit: never mind internet works now, i dont know why it didnt just an hour ago.
i did it again, now it said this:
sudo: timestamp too far in the future: Jun 20 16:38:13 2008

it's 15:27 at my place right now. what does this mean?

edit: allright i dont know why but i tried again a couple of days after and now it works (it said amsterdam was +2 hours, but it's +1.

---

