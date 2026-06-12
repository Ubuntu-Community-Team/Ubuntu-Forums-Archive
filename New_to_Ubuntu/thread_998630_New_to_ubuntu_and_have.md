---
title: "New to ubuntu and have ??"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by spider1468 on 2008-12-01
Have always used windows but had this disk on hand when my XP machine had a meltdown from sp3, I am really happy with this so far but I'd really like to know the best place to learn about linux. i'd also like to know the dif between Ubuntu and Kubuntu and which if either would be best for my Acer laptop (am leaning towards ridding myself of vista too)

 laptop specs - AMD athlon 64X2 TK-55, RAM 1024MB DDR2, HD 120 gig etc.


any help welcome, thank you

---

### Post by EXCiD3 on 2008-12-01
Either one would work great for you. The difference between the two is the desktop environment, Ubuntu uses Gnome and Kubuntu uses KDE which looks a lot more like Windows than the latter. Its all personal preference but both should run well. I prefer Gnome myself.

---

### Post by sujoy on 2008-12-01
while both are same, you may find the apps name in Kubuntu a bit unusual :D
i prefer gnome too, seems a lot more stable to me than kde4 at the moment

---

### Post by hardyn on 2008-12-01
have a little distro infidelity... try both, heck try a few differnent distros... see what works for you.

the underlying os for most distros is for all intents and purposes the same, but many distros chose to massage the GUIs a little differently.

---

### Post by SunnyRabbiera on 2008-12-01
I suggest installing Ubuntu Hardy, its LTS and there really isnt much that ibex offers that makes me want to use it.
Kubuntu is hit or miss, yes KDE is more windows like but really Gnome isnt that hard to get used to.
If you just need a beginners distro to get your feet wet I suggest trying out a distro like Linux mint, works just as well or better.

---

### Post by EXCiD3 on 2008-12-01
Forgot to mention, try this first. Install Ubuntu, then install KDE on Ubuntu. You can choose which to login to at the login screen and try them both out. You could do this the other way as well, Kubuntu with Gnome. This lets you test them out, and then you can remove the other desktop if you decide on one you like the best or you can just leave them both installed, it won't hurt anything. :)

---

### Post by SunnyRabbiera on 2008-12-01
> **EXCiD3 said:**
> Forgot to mention, try this first. Install Ubuntu, then install KDE on Ubuntu. You can choose which to login to at the login screen and try them both out. You could do this the other way as well, Kubuntu with Gnome. This lets you test them out, and then you can remove the other desktop if you decide on one you like the best or you can just leave them both installed, it won't hurt anything. :)

To me this is the best way to try out alternate DE's, you can load packages like kde in a ubuntu system and gnome packages in kubuntu without any major issues (just extra space taken up but its not much)

---

### Post by ndefontenay on 2008-12-01
There will be a few more unusual things than that.

For example, the file system is organized differently.

There's no more C: D: drives like windows would.

There's just a / (root) with a bunch of main folders. Your data will usually be in /home/[username] and your cd rom will be located in /media 

Try to have a look at the main folders located in / and there use.

Nico

---

### Post by newbee70 on 2008-12-01
> **ndefontenay said:**
> There will be a few more unusual things than that.

For example, the file system is organized differently.

There's no more C: D: drives like windows would.

There's just a / (root) with a bunch of main folders. Your data will usually be in /home/[username] and your cd rom will be located in /media 

Try to have a look at the main folders located in / and there use.

Nico


there is C: and D: drives if you want them, you just have to rename the storage devices. check out my d and e drives on the screenshot.

makes it easier to type /media/D or /media/E than /media/storage device.

---

### Post by david819 on 2008-12-01
If you're pretty sure you want Ubuntu, but aren't sure about which desktop environment to choose from, instead of installing several different options for yourself, I suggest you simply burn yourself a copy of kubuntu, and ubuntu, and boot them from cd just to see what you think.  personally I'm a gnome guy, but in all fairness I didn't give kde a real chance.  Just chose gnome and went with it.  My compaq is very similar to your acer, if I remember correctly we have the same wireless card too.  Everything works decently well on mine.  You WILL have fun with the wireless at first though.  Good luck.

---

### Post by markbuntu on 2008-12-01
KDE4 is cool but definitely not noob ready.

---

### Post by kansasnoob on 2008-12-01
Look at this section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Replacing Nautilus 

of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

I like the suggestion of trying different live CD's! Always a smart way to go! Then migrate slowly, like with a dual boot!

---

### Post by dwasifar on 2008-12-02
> **EXCiD3 said:**
> Forgot to mention, try this first. Install Ubuntu, then install KDE on Ubuntu. You can choose which to login to at the login screen and try them both out. You could do this the other way as well, Kubuntu with Gnome. This lets you test them out, and then you can remove the other desktop if you decide on one you like the best or you can just leave them both installed, it won't hurt anything. :)

So far no one has actually said how to do this.  :)

Once Ubuntu is installed and running, open a terminal and do this:
```
sudo apt-get install kubuntu-desktop
```

After that, you should be able to choose whether you want your session to use Gnome or KDE each time you log in; it'll be the sessions menu at the lower left side of your logon screen.  During the install, it will ask you which one you want to be the default; gdm (Gnome) or kdm (KDE).


I will probably draw flames for saying this, because it's kind of an oversimplification, but out-of-the-box KDE is more Windows-like whereas Gnome is more Mac-like.

My preference has always been Gnome.  You can still run packages designed for either one, no matter which one you choose.  I use a lot of KDE packages under Gnome and they run just fine.

---

