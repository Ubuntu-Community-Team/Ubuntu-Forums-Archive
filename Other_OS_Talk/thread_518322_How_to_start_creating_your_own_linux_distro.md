---
title: "How to start creating your own linux distro?"
date: 2007-08-05
forum: Other OS Talk
---

### Post by jseiser on 2007-08-05
How does one go about making a linux distro?  I know what I want to be included in it, and what i dont want.  I just dont know how to start.  I would not want to start from scratch, just take an existing distro, and take out the parts i dont want, and put in by default the parts i do want and then make a .iso out of it.  I doubt the distro i would want to make would have appeal to many people but myself, but that is the beauty of linux, i could have a set-up that works for me and i could install it to all my computers, without additional time spent setting up.  I want a a very basic OS.

evilwm (with xbindkeys installed with binds set up by default)
cplay with mpg123
mplayer (without gui)
urxvt
links2 (graphic mode in frame biffer)
Iceweasel with java
mc
nano
leafpad
conky with dbe enabled with a very basic defaualt set-up.   one line, just showing kernel, cpu, ram,, swap, usage, space on / and /home.
Id like feh to be my image viewer and set my background.  I would like to write a script that would be called say wallpaper, and when ran it just asks the path to the image and then sets feh --bg-scale "image here" in your xinit.

ubuntu based would be nice because of the ability to aptitude install other apps you might want.  But then i thought i might just want to install everything from source, since i do normally.  the only problem is dependecy's, is there a package manager that install from source and can tell you what dependecy's you are missing? so you can then go out and install them?  I know im far from being savy enough to do this, but i just want to know where to start and how to go about learning to do this.  Thanks and please comment on what else one would need to construct a distro.

---

### Post by init1 on 2007-08-05
Slax is nice. You can make you own modules from scratch, or convert them from debian modules. 
Also consider live helper. It was designed to help one make a custom debian distro. You will have full control over the packages used. 
Actually, I was thinking of making a live USB image so I can have a minimal system available. All I need is Links2, basic commands, and preferably some music players. 
[http://www.slax.org/](http://www.slax.org/)
[http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/](http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/)

---

### Post by smoker on 2007-08-05
it would be neat to have a bare-bones ubuntu (or whatever) available for such as this. i think maybe the closest would be to do a server install, then install a DE, then the apps you require. you could also remove whatever server stuff you found unneeded once the install is done.

i have never tried this though, but if you do, i'd appreciate you posting how you get on,

best of luck.

---

### Post by fistfullofroses on 2007-08-05
I have been looking into creating my own distro as well, and further more want almost the exact same thing, though I want to make a GoboLinux variant. The link provided is a site that contains scripts for a live disc based upon Slackware, and there is a PDF there that walks you through the process. Good luck.

[http://www.linux-live.org/](http://www.linux-live.org/)

---

### Post by kagashe on 2007-08-06
Have a look at [Linux from Scratch]("http://www.linuxfromscratch.org/") and [T2]("http://www.t2-project.org/") for ideas.

[Linux from Scratch]("http://www.linuxfromscratch.org/") is good to learn how Linux Distribution is built.

[Puppy Linux]("http://www.puppylinux.org/") is a distribution which is not depending upon any leading distribution for base. It is built on [T2]("http://www.t2-project.org/") at present but also leaning towards Slackware slightly. You can also build your own distribution from [Puppy]("http://www.puppylinux.com/pfs/index.html").

Hope it helps.

kagashe

---

### Post by CowzRule on 2007-08-06
Have a look at [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37"). It will allow you to customize Ubuntu and make a LiveCD

---

### Post by johnny4north on 2007-08-06
thanks Cowz i will create a masterpiece and call it .. hmmm RainCountry.  it will have cool Alaskan themes w/ wallpaper/pics to boot.  i just need to think of a new age native design for the cover of cd.  hemlock and spruce trees on a hill w/ a new age native design cloud raining down on them:).  based on slackware or debian. Or maybe a custom puppy linux.:cool:

---

### Post by xpod on 2007-08-06
> it would be neat to have a bare-bones ubuntu (or whatever) available for such as this. i think maybe the closest would be to do a server install, then install a DE, then the apps you require. you could also remove whatever server stuff you found unneeded once the install is done.

i have never tried this though, but if you do, i'd appreciate you posting how you get on,

best of luck.

I`ve been meaning to do exactly that for a wee while now:)
I`ve had that partition with the mini iso server install sitting on an old Dell for a few weeks now but thats as far as i`ve got.:)

The laptop also has Puppy & Wolvix on it too but i`d really like the minimal Ubuntu flying along at a similar rate of knots if at all possible.....then once i`ve got it right it i hope to repeat on my main pc for normal use. 

I will get round to it one o these days.Any time off work just now is usually well booked up so i`ll leave it all till i have a couple of  days peace & tranquiilty.
There are a couple of threads floating about on the subject and Aysiu`s Psychocats site has a good guide too if your interested smoker.

Good luck with the homemade jobs folks.
XP.O.D Distro........mmmmm,sounds good:lolflag:

---

### Post by jseiser on 2007-08-06
Ill def. look into what you all posted, thanks!  The only problem with doinga server install then taking out what i dont want is that creates problems updating.  It would be nice to just have those programs and then when i sudo aptitude update/upgrade just have those programs updated and not have ubuntu-desktop try re-instaling everything.  Also, a server install gives you the server kernel, which then requires the extra step of swapping it out for the desktop kernel if you want to use the nvidia/ati drivers.  I would really like to base this on slackware, but i cant even get slackware to boot when i go to install it :/  So debian seems the way to go.  Is there a way to pick and choose every thing installed on a debian system? Like a net install that prompts me the whole time, or maybe a package list i can edit to just certain things and have the installer check those packages and only install those?

---

### Post by igknighted on 2007-08-06
> **jseiser said:**
> Ill def. look into what you all posted, thanks!  The only problem with doinga server install then taking out what i dont want is that creates problems updating.  It would be nice to just have those programs and then when i sudo aptitude update/upgrade just have those programs updated and not have ubuntu-desktop try re-instaling everything.  Also, a server install gives you the server kernel, which then requires the extra step of swapping it out for the desktop kernel if you want to use the nvidia/ati drivers.  I would really like to base this on slackware, but i cant even get slackware to boot when i go to install it :/  So debian seems the way to go.  Is there a way to pick and choose every thing installed on a debian system? Like a net install that prompts me the whole time, or maybe a package list i can edit to just certain things and have the installer check those packages and only install those?

It sounds like what you really want is Gentoo (source based package manager that handles deps.).  You could set your install up and then create the image from that.  Gentoo is complex, but if you regularly install from source it should make life easier for you.

---

### Post by jseiser on 2007-08-06
In gentoo, i can just install each file individually?  Then save that image, that would be awesome.  I want to pick and choose everything the installer wants me to install, pretty much, en language, networking, kernel, then what i listed, that it.  That would be awesome.  I havemessed around with gentoo before but it was just the live cd with then gives you the choices of gnome/kde/fluxbox which i dont want anythingto do with :)

---

### Post by igknighted on 2007-08-06
> **jseiser said:**
> In gentoo, i can just install each file individually?  Then save that image, that would be awesome.  I want to pick and choose everything the installer wants me to install, pretty much, en language, networking, kernel, then what i listed, that it.  That would be awesome.  I havemessed around with gentoo before but it was just the live cd with then gives you the choices of gnome/kde/fluxbox which i dont want anythingto do with :)

Gentoo does not have any built in tool for making an image... but I think they are available as a third party thing.  Also, forget the liveCD... its crap.  Print the manual (or better yet have a second computer up while you do the install) and do a stage3 install.  You get the very very basic install and nothing else (kernel, some CLI tools, portage, bootloader... thats it).  Then you can compile in what you need via portage.

The only problem with compiling and then making a distro is that if you compile it specifically for your system it may not work on other computers, and if you don't customize the compiler settings, why bother compiling?  The more I think about this the more I think you might be better off doing a minimal Debian install or something and perhaps custom compiling a kernel for what you need and nothing more.

EDIT: See this page for more distro-creation tools: [http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources](http://www.livecdlist.com/wiki/index.php/LiveCD_Creation_Resources) (thanks laroza)

---

### Post by kagashe on 2007-08-07
[Absolute]("http://www.pcbypaul.com/absolute/") is a Slackware based distribution and the latest version has been released recently. Look at what is says about making your own distro [here]("http://www.pcbypaul.com/absolute/help/rollyourown.html").

kagashe

---

### Post by fistfullofroses on 2007-08-07
Don't forget GoboLinux. With Gobo you can select which packages you want installed during the install process. It also comes with tools to make a live cd of your current setup. Could be just what you are looking for.

---

### Post by vexorian on 2007-08-07
If you choose not to use ubuntu then Slax sounds as the rightmost option, it really doesn't take any time to take frodo, choose DE, then the things you want and etc.

--
Anyways, is it all right to redistribute Java?

---

### Post by igknighted on 2007-08-07
> **vexorian said:**
> If you choose not to use ubuntu then Slax sounds as the rightmost option, it really doesn't take any time to take frodo, choose DE, then the things you want and etc.

--
Anyways, is it all right to redistribute Java?

I think you need to contact Sun to get a license to distribute the JRE/JDK for Java6.  However, I think OpenJDK is out (or will be soon), and once it is then it will be like any other FOSS app with no restrictions.

Link: [http://www.sun.com/software/opensource/java/](http://www.sun.com/software/opensource/java/)

---

### Post by jseiser on 2007-08-07
absolute 12 wont install on the 2 pc's i tried, well it installs and tells me sounds works but the screen is all crazy.  Just lines of ****, so i tried safex and still the same.  Tried to make it match my ubuntu xorg and stillthe same thing.

---

### Post by Ultra Magnus on 2007-08-07
Ha ha.. I want to create my own Linux distro too - I've been trying out LFS but I can't get past adjusting the toolchain... I've done something wrong somewhere - Anyway I was gonna call mine "Jimux" or ******* linux

---

### Post by Frak on 2007-08-07
Either, Ubuntu Minimal
LFS
Gentoo
or Reconstructor
Which have all been listed above.

---

