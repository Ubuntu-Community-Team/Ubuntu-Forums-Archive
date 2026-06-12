---
title: "Audio and Video issues/install"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by DarkReign16 on 2008-07-01
So I just installed wubi the other night, 8.04, and everything is going nicely.

I update everything, reboot, log in, and open up firefox. I notice everything is very fuzzy, so I tinker with the desktop settings, and change to subpixel smoothing for LCD's. It helps, but not much, videos, images, and text are all fuzzy and hard to read (even after tinkering with DPI).

I also notice by now that the version of firefox that came with ubuntu is a beta version, so I go to the firefox site to update to the latest full version.

I click the folder, and immediately, I run into trouble.

It turns out, as everyone here probably knows, that you have to open up the terminal and enter about 20 commands just to install something as basic as firefox, so I try following the instructions for a .tar.gz (or whatever it is) and it refuses to work.

I changed the directory with the cd command,extracted, I did sudo make install, ./configure, all that, but nothing works.

So I give up, and just check synaptic and add/remove, but it tells me it's already been installed. However, I know for a fact that it looks nothing like firefox 3 full non-beta.

So I go over to YouTube, only to find that I need flash. I download it, and discover that .rpm's don't seem to work with debian based ubuntu, so I download the .tar.gz version, and commense entering 20 different commands to install basic flash (yes, I searched add/remove, to no avail), and it seems to have worked, because the video now showed up.

I go to watch a movie, but the video quality is SO horribly fuzzy and terrible compared to windows that it's just outrageous to bother watching. And to top it all off, I have no sound.

I find out that the people over at creative have released beta drivers for ubuntu, and so I commense entering the long boring commands yet again to install a basic driver, and I still have no sound. But hey, I can't blame ubuntu for that...but I CAN blame them for the annoying way stuff is installed if it isn't .deb.

So now here I am, fuzzy picture, no audio, hard to read text, difficulty installing ANYTHING, even basic flash, and I have no reason to continue using ubuntu if everyhing is going to be fuzzy, and without sound.

So please, help me, is there any way to get my x-fi soundcard working, and is there any way to install things by simply clicking them, and letting it auto install? Also, is there honestly no way to get visual quality and text quality as high as it is in windows?

I am honestly wanting help, as you may have noticed, I spent hours reading and researching this stuff just last night, and it got me nowhere. I mean, I literally had to spend an hour of my life just learning how to install stuff, so I don't expect the solutions to my other problems to be anywhere near fast, or simple....

help....:confused:

Specs:

P4 3.0ghz/HT
3GB RAM
Nvidia 7900GTX OC 512mb video card PCI-E
Creative X-FI Xtreme Gamer Sound Card
750GB (2 hdd, 1 250gb, 1 500gb)

Monitor: Dell 24" widescreen, 1920x1200
I'm using my D: drive (500GB) with a 30GB partition for ubuntu wubi...

---

### Post by silkstone on 2008-07-01
Well you really don't have to jump through all those hoops. FF is installed by default, and provided you run update Manager you will have the latest version in the repos - there's no need to install it independently. Similarly most of the 'non free' codecs and drivers can be installed from the Synaptic package manager, although it's quicker to copy and paste some terminal commands. They can't distribute all this with Ubuntu because of copyright issues.

I would read this very carefully and follow the guide...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by DarkReign16 on 2008-07-01
Is there any way to install non .deb stuff without having to enter command after command? That is seriously my biggest peeve (bigger than not having audio).

And that page looks like a homework assignment....

---

### Post by nothingspecial on 2008-07-01
> **DarkReign16 said:**
> And that page looks like a homework assignment....

That page is how you do it.It`s written and maintained in someone`s spare time and has helped countless beginners get the best from Ubuntu. Don`t like it? Watch a dvd.

I suggest rereading it, following it and see if it helps your situation. Don`t be intimidated by the command line. It`s a learning curve. Once you know what you`re doing it`s easy.

---

### Post by DarkReign16 on 2008-07-01
> **nothingspecial said:**
> That page is how you do it.It`s written and maintained in someone`s spare time and has helped countless beginners get the best from Ubuntu. Don`t like it? Watch a dvd.

I'm just saying, new users shouldn't have to read an encylopedia to just watch YouTube for crying out loud.

And this is a common theme with ubuntu fanboys, they get so hostile at anyone who dares to question ubuntu's ease of use. I mean seriously, they treat anyone who says anything bad about Ubuntu as if they just punched their mother.

It's a freaking piece of software man, you need to chill, I am just giving feedback here. I recommend that it be way more user friendly, and streamlined in the future. And that starts with not having to read a book to learn how to INSTALL flash.

And all I wanted to know is if there was some kind of program package that I can get that streamlines the install process, like it works with .deb stuff.

---

### Post by nothingspecial on 2008-07-01
Don`t mean to sound hostile, I`m just saying if you want to use something new read the instructions provided.:)

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by nothingspecial on 2008-07-02
Ok. Installing stuff in Ubuntu is easier than in windows 95% of the time, or so I`m lead to believe. You have synaptic package manager and add/remove which automates the whole process just like the .deb installer. 
 The command apt-get isn`t necessary, it just installs what is in synaptic. However when you are used to typing commands it is infact easier and quicker than click, click, click, click............

eg I`ve seen one of the IT guys at work install vlc..... download the file, then have to click all sorts of boxes accepting licencess and stuff and do you want updates and on + on + on. (just so my boss can watch the new man utd dvd I`d loaded on to a thumb drive for him, because windows media won`t play it). In ubuntu however I just   press Ctrl+shift+T  (my shortcut to open a terminal) then 

```
sudo apt-get install vlc 
``` 

then my password. That`s it. Done.


 To fix your video issues.

1. Goto System > Administration > Software Sources and check all the boxes in the first tab. Click on the second tab (Third Party), click add then copy and paste this line in -

```
deb http://packages.medibuntu.org/ hardy free non-free
```

Repeat with this line
```

deb-src http://packages.medibuntu.org/ hardy free non-free
```

Open a terminal and paste this -
```

sudo apt-get install flashplugin-nonfree
```

Goto youtube and you`ll be able to watch it.
You have now enabled those repositories and will never have to do it again. For any programs in those software sources it`s just a case of sudo apt-get.....

For high quality video viewing, copy and paste this line -
```

sudo apt-get install alsa-oss faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-java7-jre icedtea-java7-plugin liblame0 non-free-codecs 


```

Thats it they are installed. For anything that requires these packages they are here now, you don`t have todo it again.
Now
```
sudo apt-get install vlc
```

Watch your videos with vlc, top quality I promise.

The thing is, when you install Ubuntu you have to do a bit of tweaking, but once it`s done it`s done. It`s not like that for every package you want to install.

Can`t help you with your soundcard though.

---

