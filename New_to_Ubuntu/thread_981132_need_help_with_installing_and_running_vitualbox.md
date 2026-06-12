---
title: "need help with installing and running vitualbox"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by shouboushi on 2008-11-13
hi, this is my first post, ive been a linux user, going on 3 days now. i love it. challenging but worth it to get rid of windows.

now, i love playing games. im having the hardest time trying to find a way to get my games running. so i thought id look at getting virtualbox, if it fixes my problem. most of my games are ripped versions, if that matters

anyway my question is, how do i begin, install, and run the virtualbox, i am absolutely confused. ive downloaded

[http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb](http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb)

and it installed i guess. now what do i do

thanks in advance

---

### Post by overdrank on 2008-11-13
> **shouboushi said:**
> hi, this is my first post, ive been a linux user, going on 3 days now. i love it. challenging but worth it to get rid of windows.

now, i love playing games. im having the hardest time trying to find a way to get my games running. so i thought id look at getting virtualbox, if it fixes my problem. most of my games are ripped versions, if that matters

anyway my question is, how do i begin, install, and run the virtualbox, i am absolutely confused. ive downloaded

[http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb](http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb)

and it installed i guess. now what do i do

thanks in advance

Hi and welcome, if you would like to play games then I would suggest dual booting with windows. Virtual Box does not support graphics acceleration.

---

### Post by shouboushi on 2008-11-13
ok glad i didnt get rid of windows yet then. as for my virtualbox question anyway, in case id like to run some windows programs besides gaming, what do i do

---

### Post by Falcorian on 2008-11-13
Also, depending on what games, they may work with wine.

Steam does an ok job under wine, most Blizzard games are flawless (WoW, D2, Star Craft...), Fallout 2 works...

But if you want to play the newest, flashiest FPS titles, you're going to need to dual boot.

---

### Post by MuH4hA on 2008-11-13
I think your searching for something like 'wine'...

The first step after installing virtualbox would be to start it, make a new virtual machine and install the OS you want on it. It's like you would install windows on a real machine but like overdrank said, you won't be happy with it if you want to play 3D-games..

Note, that there are also games available for Linux, like Warsow... :P

---

### Post by tdreyer1 on 2008-11-13
> **shouboushi said:**
> ive downloaded

[http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb](http://download.virtualbox.org/virtualbox/2.0.4/virtualbox-2.0_2.0.4-38406_Ubuntu_intrepid_amd64.deb)

and it installed i guess. now what do i do

thanks in advance

You shouldn't have to download virtualbox manually. Just install it from the repositories by typing into a console:

```
sudo apt-get install virtualbox-ose
```

Virtual box will then be downloaded & installed automatically. 

Once it is installed, just run virtualbox from the accessories menu. Virtualbox is pretty good at walking you through creating your first virtual machine, but if you need help, you can look [here]("http://www.virtualbox.org").

---

### Post by farsight on 2008-11-13
Hi, what you want to do it go in to the repository and search for virtualbox. What you will probably want to do is download the relevant other packages too, which are called generic, virtual etc. You need to download the additionals that correspond to your Ubuntu install. So when you load Ubuntu up you will see something like Ubuntu.......Generic, and therefore you want to go down the list of virtualbox extras and install all the other packages that are designed for the generic version (this stops a HUGE list appearing when GRUB loads). 
Then all you need is a .iso file for the operating system you want to run. I normally have the .iso file on a CD and therefore go in to Virtualbox, follow the instructions for setting up a virtual machine (i.e naming it and creating a dynamically expanding/fixed virtual hard drive) and then go in to settings. From there I go to the CD/DVD menu and then enable CD/DVD and click the iso image button. Save and boot up that box :) 

I hope this helps you, I'm writing this from Windows (gasp) and so can't be more specific. If you have any more questions then get them on this forum, I'm sure you're not the only one wondering the same thing :)

Farsight

---

