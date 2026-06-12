---
title: "Before I Begin, I Have a Few Questions"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Kiwi76 on 2008-05-15
I want to try Ubuntu. For now, I'll just be playing around with it and using Windows XP as my primary operating system, so the use of Ubuntu will be general. I'll use it for media (music, pictures), Internet, and depending on what it's like for Ubuntu, maybe some gaming. I have three questions before I dig in and try it on my own and start reading the overwhelming guides.

By the way, I'm new to Ubuntu, but I'm pretty knowledgeable with computers and hardware in general.

1. Does 64-bit offer anything over 32-bit? I hear the advantage of the former is still negligible in most things, especially for my use, and that the latter has better stability. Is that still true? I have 4GB of RAM and my Windows XP installation only sees 3.25GB, so I know you need a 64-bit CPU and operating system to get more.

2. After downloading, how do I burn it? With what software and what settings? I remember trying to burn it before twice and neither disc would boot (but would work fine with autoplay, not that that can do much). Maybe it was just that computer or something, but maybe I didn't make it correctly? I don't burn too often so I wouldn't doubt it.

3. Would I run into anything specific with any of this hardware in the way of drivers?

ASUS Maximus Formula motherboard
Intel Core 2 Duo E8400 CPU
4GB of RAM
nVidia GeForce 8800GT video card (I hear ATi is lacking with Linux drivers?)
SupremeFX II (SoundMAX HD) sound
2Wire (not sure of exact make/model) USB wireless adpater

Thanks in advance, and looking forward to Ubuntu!

---

### Post by Xiong Chiamiov on 2008-05-15
Before doing anything drastic, run off the CD for a little bit and see how it works.  You can also use [Wubi]("http://wubi-installer.org/"), which sounds quite excellent, though I have not used it myself.  And please don't just accept Gnome because it's the default; try out Kubuntu and Xubuntu as well - you might find that you like one better.

1.  I'm running quite happily on a 32-bit OS with a 64-bit processor.  There are some gains to be had, but some have also had problems with applications.  I install things like a madman, so I'd like to be able to install anything I can (and hopefully have it work).
2.  [Here's]("http://www.snapfiles.com/Freeware/gmm/fwcdburn_r.html") a good place to look.  My favorite is [ISO Recorder]("http://www.snapfiles.com/get/ISORecorder.html"), because after you install it, you just have to right-click on an .iso -> burn ISO.
3.  I think you'll be fine, though there have been some [odd issues]("http://ubuntuforums.org/showthread.php?t=785074") for some of us with Hardy and NVIDIA.  ATI has had terrible linux support in the past, but now that they've been bought by AMD, they're starting to shape up.

---

### Post by subzero316 on 2008-05-15
> 1. Does 64-bit offer anything over 32-bit? I hear the advantage of the former is still negligible in most things, especially for my use, and that the latter has better stability. Is that still true? I have 4GB of RAM and my Windows XP installation only sees 3.25GB, so I know you need a 64-bit CPU and operating system to get more.


Of course 64 bit will be faster...But you wont notice the differnce in simple applications...I never had any stability issues with 64 bit only driver issues which had been fixed so there`s nuting to worry about...And also only a 64 bit CPU can support 64 bit os.

> After downloading, how do I burn it? With what software and what settings? I remember trying to burn it before twice and neither disc would boot (but would work fine with autoplay, not that that can do much). Maybe it was just that computer or something, but maybe I didn't make it correctly? I don't burn too often so I wouldn't doubt it.


You just burn the image that`s how you do it then it`l  boot on with that disk..Make sure in your BIOS setting you have the DvD- ROM as first boot option.



> 3. Would I run into anything specific with any of this hardware in the way of drivers?

ASUS Maximus Formula motherboard
Intel Core 2 Duo E8400 CPU
4GB of RAM
nVidia GeForce 8800GT video card (I hear ATi is lacking with Linux drivers?)
SupremeFX II (SoundMAX HD) sound
2Wire (not sure of exact make/model) USB wireless adpater


Well about the drivers you wont have any issues . But am not sure about the WIFI adapter you mentioned. But dont worry even if doesnt work out of the box you can get it easily insatlled

---

### Post by Kiwi76 on 2008-05-15
I'm going to put in an old separate hard drive (though it is IDE) and install Ubuntu on that. I don't plan to mess around with partitions or hard drives with existing data. I want to keep it simple.

As for burning the disc, I have Nero 7 Essentials which came with my DVD-RW drive, so I was hoping to use that. I think what it was was last time I used Windows built-in burning which copied the .iso, but didn't take care of the boot.ini, so the disc would never load, or something like that. I'll just have to watch for that, but Nero (and other actual programs) takes care of that, I believe.

If the internet proves troublesome, I have wires I can use in the meantime until it's sorted.

Thanks for the advice!

I guess I'm off to try it and see what it's like.

---

### Post by ZabiGG on 2008-05-15
Re: Your RAM :)

I've got 8 gig worth, and my 64-bit Ubuntu (my system did not digest the 32-bit version at all, so I installed the 64) sees it very well and distributes the load efficiently between my quad processors (Phenom 9500)

Hope this helps ;)

---

### Post by Xiong Chiamiov on 2008-05-15
Nero should of course work for burning ISOs; the main thing is to make sure that you are burning as an image file, rather than a data CD.

> **subzero316 said:**
> 
You just burn the image that`s how you do it then it`l  boot on with that disk.

:)

---

### Post by hellion0 on 2008-05-15
> **Kiwi76 said:**
> As for burning the disc, I have Nero 7 Essentials which came with my DVD-RW drive, so I was hoping to use that. I think what it was was last time I used Windows built-in burning which copied the .iso, but didn't take care of the boot.ini, so the disc would never load, or something like that. I'll just have to watch for that, but Nero (and other actual programs) takes care of that, I believe.Nero should work fine (I've used it in the past to burn discs from Windows machines), although other programs sometimes can work better. Just make sure to pick the right mode to burn in.

---

### Post by hyper_ch on 2008-05-15
you could use a different 32-bit kernel... the server kernel is compiled with PAE if I'm not mistaken hence you can use more than 4GB ram on 32bit using that kernel.

---

### Post by Kiwi76 on 2008-05-16
Okay, I got it installed, and I'm typing from within it right now. Now that I got it up, I have even more questions (P.S. This font is definitely different).

1. Initial impression is mixed. It's almost relieving, if it weren't for the constant amount of times you get prompted for the password, or the countless times I see something like this.

[img]http://img162.imageshack.us/img162/417/screenshottq6.png[/img]

That particular one happened when I tried moving a wallpaper to the same directory the rest are in.

How do I...

A) Assume ownership over everything since I'm the only one using computer?

B) Disable password promopts?

I use Windows XP, and seeing the whole Vista permission system in Linux was the last thing I expected.

2. After I first installed it, after five minutes, the hard drive started thrashing something fierce (remember that this is an old IDE drive, and a noisy one at that). I didn't notice any slowdown, but I wasn't doing much at the time. I checked the system monitor and it showed nothing except that the CPU was being half used, but it wouldn't show by what (nothing was listed as taking CPU cycles). swap space was listed as nothing being used, and only 300-some of my 4GB was listed as in use. After another five minutes, the CPU useage stopped, as did the hard drive thrashing. What was that? Is it normal after an install or something?

3. Drivers. It says I have a "new_nVidia" driver, and that's it. I assume the rest is installed? Obviously I can see I have no real hardware acceleration since I can't enable any of the supposed desktop effects.

4. Resolutions. I can select a few, but not many. It goes from 1024 x 768 to 1600 x 1200 with none between (but some higher than lower). The former is too low, the latter is good, but I prefer 1400 x 1050, as text is just a tad too small on 1600 x 1200.

5. Gnome is good, and I may stick with it, but I've seen screenshots of another (call Enlightenment or something) and it looks like it's worth a try. How do I install and change this stuff?

I have other things I'm dealing with, but those are the major ones right now. I got my wireless adapter working, though with a bit of trouble, and it only seems to be at half strength.

---

### Post by Delever on 2008-05-16
5. I suggest to stick with gnome until you learn more
3. Search for nVidia drivers in Programs->Add/Remove, there are descriptions near every driver, select to install the one which supports your card. If that fails, you can install propietary drivers using envyng (open terminal ant type: "sudo apt-get install envyng-gtk", when it is installed you can start it from Programs menu)
4. Check again resolutions after acceleration is working.

---

### Post by Delever on 2008-05-16
You can't change owner of folders if you do not have rights to do that. Ubuntu comes with administrator (root in linux) account disabled. However, user can act like administrator by issuing commands using sudo (read: super user do). For command line tasks it is sudo, for GUI applications in GNOME, it's gksudo.

Your default filesystem explorer in ubuntu is called nautilus. To run nautilus (or any other program) as root, enter this in console:

gksudo nautilus

Now you can change rights/owner for any folder.

---

### Post by Bigtime_Scrub on 2008-05-16
There are lots of ways to customize your desktop. When you feel comfortable with Linux try out a few themes. 

This is a great step by step on how to do it, 
[http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml](http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml)

I use a a theme called Dark Gnome with AWN. Its gives me a dock instead of a taskbar. So my computer looks kinda like a Mac.

---

### Post by hyper_ch on 2008-05-16
> **Kiwi76 said:**
> A) Assume ownership over everything since I'm the only one using computer?
You don't... rather you shouldn't... [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **Kiwi76 said:**
> B) Disable password promopts?
You shouldn't either...

> **Kiwi76 said:**
> I use Windows XP, and seeing the whole Vista permission system in Linux was the last thing I expected.
It's way different and VISTA tries to imitate linux on it...

Give it at chance... normally you don't need to access folders where you don't have permission to by default... and disabling password prompts is just about the worst thing you can do with regard to security.



> **Kiwi76 said:**
> 2. After I first installed it, after five minutes, the hard drive started thrashing something fierce (remember that this is an old IDE drive, and a noisy one at that).
It might have been Tracker indexing the documents...

> **Kiwi76 said:**
> 3. Drivers. It says I have a "new_nVidia" driver, and that's it.
Check in the restricted driver manager whether the proprietary drivers for nVidia are enabled.

---

### Post by Delever on 2008-05-16
> **hyper_ch said:**
> 
Check in the restricted driver manager whether the proprietary drivers for nVidia are enabled.

Forgot that. Yes, this is the first step: System->Administration->Hardware drivers

---

### Post by Kiwi76 on 2008-05-16
Okay, I got the drivers, but now resolution support is worse. There's more resolutions, but most of them are locked to 60hz (some lower). I KNOW this monitor can do 1600 x 1200 at 100hz, and 1400 x 1050 at at least 100hz. It won't even let me go above 60hz unless I go as low as 1024 x 768, and then it only goes as high as 75hz. What's going on? Also, every resolution above 1600 x 1200 is now gone.

@Bigtime_Scrub, that's why I was interested in Enlightenment. I saw screenshots of it with that dock instead of a taskbar. That's what I wanted to do. Page bookmarked! Thanks!

Things are starting to come together now.

---

### Post by hyper_ch on 2008-05-16
Kiwi:

you can add more resolutions/refresh rates if you want to... edit the /etc/X11/xorg.conf file for that - however before you change anything in there, make a backup and edit must be as root/sudo
```

sudo gkedit /etc/X11/xorg.conf

```

---

### Post by Kiwi76 on 2008-05-16
Command not found, or so it says. I looked up the file manually but have no idea what to do with it.

---

### Post by hyper_ch on 2008-05-16
ups... it should be:
```

gksu gedit [...]

```

---

### Post by Kiwi76 on 2008-05-16
Okay, that just brings it up which I've already done manually. I have no idea what to do with it.

---

### Post by hyper_ch on 2008-05-16
well, have a look at it, read man pages for it... you have somewhere resolution and refresh rates... just add a new one and set it as default... it's been a long time since I did something like that... there's good documentation out there for that.

AND just make a backup of the file first before you change anything ;)

---

