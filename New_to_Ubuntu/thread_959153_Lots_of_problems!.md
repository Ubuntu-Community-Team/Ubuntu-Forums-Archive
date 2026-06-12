---
title: "Lots of problems!"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Stalker72 on 2008-10-26
Hi,

I moved from Vista to Ubuntu today, and I've encountered a lot of problems! I went through a guide and did everything I was told to do ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)).

1. I can't set the resolution to 1680x1050. I can only choose between 800x600 and 640x480!

2. Whatever I do, I get the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

3. Text is blurry.

4. There is no audio. Is Bose Companion 5 supported?

5. I can't use my wireless adapter, only wired.

6. Graphics are bad.

--

Wireless adapter: D-Link DWA-556 Xtreme N
GPU: EVGA GeForce 9800 GX2
CPU: Intel Core 2 Quad Q9300
RAM: 4GB Patriot Viper 1333MHz

Tell me if you need more info!

Sincerely,

Stalker72

---

### Post by mike555 on 2008-10-26
Have you installed the restricted driver for your graphics card ?   your wireless card might not be supported , you might want to post in the networking  forum , also you could do a search for your network card , perhaps others have already figured it out....

---

### Post by Stalker72 on 2008-10-26
> **mike555 said:**
> Have you installed the restricted driver for your graphics card ?
How do I install that driver?

Stalker72

---

### Post by Zularan on 2008-10-26
In the main menu 'System->Administration->Hardware Drivers' will list any proprietary drivers you should use for your nVidia, just activate one there.

Which version of Ubuntu are you using? 

Also, make sure to update as bugs, fixes are out daily from the community.

---

### Post by Stalker72 on 2008-10-26
> **Zularan said:**
> In the main menu 'System->Administration->Hardware Drivers' will list any proprietary drivers you should use for your nVidia, just activate one there.

Which version of Ubuntu are you using? 

Also, make sure to update as bugs, fixes are out daily from the community.
When I try to activate it, I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

...the same with Update Manager, etc.

I'm 99% sure that I use Ubuntu 8.04. How can I check?

(I installed all available updates earlier today.)

Stalker72

---

### Post by Nepherte on 2008-10-26
The error already suggests what you have to do. Type this in a terminal:
```
sudo dpkg --configure -a
```

---

### Post by Stalker72 on 2008-10-26
> **Nepherte said:**
> The error already suggests what you have to do. Type this in a terminal:
```
sudo dpkg --configure -a
```
Thanks, I didn't know about the "sudo" thing!

Stalker72

---

### Post by prismpirate on 2008-10-26
I guess you solved your package manager problem. As for the text, you could attempt installing restricted extras (Open Add/Remove Programs, search for Ubuntu Restricted Extras) which will install microsoft like font smoothing. Or you could always follow the instructions here to have Mac OS X like font rendering.

[Mac OS X Font Rendering]("http://rewind.themasterplan.in/2007/07/15/sexy-smooth-fonts-on-kubuntu/")

As for your graphics, do you mean the theme is ugly? I guess that's not a problem, as you can easily visit

gnome-look.org for better themes.

---

### Post by Nepherte on 2008-10-26
1. Try this as told before: System->Administration->Hardware Drivers. I'm not sure whether ubuntu will detect your rather new graphics card. If the previous suggestion doesn't work, you can always try envy:
```
sudo apt-get install envyng-gtk
```

---

### Post by Stalker72 on 2008-10-26
Thanks for all the help guys! :)

Everything but the wireless network is working perfectly! :)

I think the audio will be fixed if I install the GStreamer plugins. What do you think?

Also, I need some help with Compiz Fusion and Wine!

(...bye bye Windoze...)

Sincerely,

Stalker72

---

### Post by Stalker72 on 2008-10-26
After installing the GStreamer plugins, the audio still doesn't work in Rhythmbox Music Player. My songs are in the .mp3 format. I went from iTunes.

Thanks for any help,

Stalker72

---

### Post by Xiong Chiamiov on 2008-10-26
> **Stalker72 said:**
> Thanks, I didn't know about the "sudo" thing!

Stalker72
As a general rule, if you try something and get some sort of permission error, then you need to do it as root (eg, using sudo).  The easiest way to do this is
```

sudo !!

```
which will repeat the previous command, but as root.  Be careful, though!  Always know what you're doing when you're root, else you can screw things up badly.  Ask here if you're not sure.

Compiz will not work unless you have the proprietary nvidia drivers installed.

---

### Post by Xiong Chiamiov on 2008-10-26
> **Stalker72 said:**
> After installing the GStreamer plugins, the audio still doesn't work in Rhythmbox Music Player. My songs are in the .mp3 format. I went from iTunes.

Thanks for any help,

Stalker72
Go through [this guide]("http://ubuntuforums.org/showthread.php?t=205449") and tell us any problems you have.

---

### Post by Stalker72 on 2008-10-26
> **Xiong Chiamiov said:**
> As a general rule, if you try something and get some sort of permission error, then you need to do it as root (eg, using sudo).  The easiest way to do this is
```

sudo !!

```
which will repeat the previous command, but as root.  Be careful, though!  Always know what you're doing when you're root, else you can screw things up badly.  Ask here if you're not sure.

Compiz will not work unless you have the proprietary nvidia drivers installed.
Thanks. I got the drivers. But how do I play around in Compiz Fusion?

Stalker72

---

### Post by Stalker72 on 2008-10-26
> **Xiong Chiamiov said:**
> Go through [this guide]("http://ubuntuforums.org/showthread.php?t=205449") and tell us any problems you have.
I reconnected my speakers (pulled out the USB cord, and put it in). I heard some African tune. So the audio works, but not in Rhythmbox Music Player.

Stalker72

---

### Post by ubername on 2008-10-26
> **Stalker72 said:**
> Thanks. I got the drivers. But how do I play around in Compiz Fusion?

Stalker72

Have you installed compizconfig-settings-manager from synaptic or otherwise?
and simple-cssm for effects like a desktop sphere.

---

### Post by SunnyRabbiera on 2008-10-26
> **Stalker72 said:**
> I reconnected my speakers (pulled out the USB cord, and put it in). I heard some African tune. So the audio works, but not in Rhythmbox Music Player.

Stalker72

well for screen resolution if you are using Hardy in a terminal put this command in:
gksudo gtk-displayconfig
As for your audio playback in rhythmbox, are your songs from itunes purchased by any chance?

---

### Post by Stalker72 on 2008-10-26
> **ubername said:**
> Have you installed compizconfig-settings-manager from synaptic or otherwise?
and simple-cssm for effects like a desktop sphere.
No...

Stalker72

---

### Post by Stalker72 on 2008-10-26
> **SunnyRabbiera said:**
> well for screen resolution if you are using Hardy in a terminal put this command in:
gksudo gtk-displayconfig
As for your audio playback in rhythmbox, are your songs from itunes purchased by any chance?
The drivers fixed the resolution problem.

My songs are not purchased from iTunes.

Stalker72

---

### Post by Stalker72 on 2008-10-26
After installing all the updates found by the Update Manager, Ubuntu won't boot.

I get a lot of text, some of it saying:

kinit: No resume image, doing normal boot...

--

...and it just stays there. No activity at all!

Stalker72

---

### Post by Xiong Chiamiov on 2008-10-26
Just to make sure, do the same files play in, say, VLC?  Also, since Totem also uses the gstreamer backend, can you play them in Totem (it's listed as Video Player or somesuch nonsense)?

---

### Post by SunnyRabbiera on 2008-10-26
> **Stalker72 said:**
> The drivers fixed the resolution problem.

My songs are not purchased from iTunes.

Stalker72

alright making sure as songs on itunes are often DRM'ed

A suggestion I can make to get more multimedia working on your system is try medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Stalker72 on 2008-10-26
> **Xiong Chiamiov said:**
> Just to make sure, do the same files play in, say, VLC?  Also, since Totem also uses the gstreamer backend, can you play them in Totem (it's listed as Video Player or somesuch nonsense)?

> **SunnyRabbiera said:**
> alright making sure as songs on itunes are often DRM'ed

A suggestion I can make to get more multimedia working on your system is try medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Thanks. First of all, I need to be able to boot into Ubuntu! ;)

[http://ubuntuforums.org/showpost.php?p=6037991&postcount=20](http://ubuntuforums.org/showpost.php?p=6037991&postcount=20)

Stalker72

---

### Post by ubername on 2008-10-26
> **Stalker72 said:**
> No...

Stalker72

Sorry, I should have been more helpful. To use compiz, install the packages mentioned above, then from system>preferences play with 'advanced desktop effects settings' and 'simple compizconfig settings manger'

Hint: for a desktop cube, go to the general options in advanced desktop effects settings, select the desktop size tab and set the horizontal virtual size to 4 (or however many sides you want your 'cube' to have). Leave the number of desktops as 1. This baffled me, but it's how it works.


Then make sure ou enable desktop cube and, if you want, desktop rotate.

Glad to post my compiz settings file if it will help.

Edit: Doh - just saw your post about not being able to boot. It is on the previous page of posts, is my excuse!

If you go for Intrepid (It works fine for me bar the odd problem with headphones) you will still need to use the above advice.

---

### Post by SunnyRabbiera on 2008-10-26
as for your current issue, I have seen issues like this before with hardy unfortunately and maybe there might be a true resolution for you on this end.
I have seen hardy have errors like the one you described thats why i dont use it.
For me I would actually suggest another distro most of the time, such as my current favorite linux mint that is based on Ubuntu but is often way more stable

---

### Post by Stalker72 on 2008-10-26
> **SunnyRabbiera said:**
> as for your current issue, I have seen issues like this before with hardy unfortunately and maybe there might be a true resolution for you on this end.
I have seen hardy have errors like the one you described thats why i dont use it.
For me I would actually suggest another distro most of the time, such as my current favorite linux mint that is based on Ubuntu but is often way more stable
I've heard about that one before.

Anyways, I'll just try a reinstallation of Ubuntu.

Let's hope Intrepid Ibex is more stable than Hardy Heron! :)

Stalker72

---

### Post by SunnyRabbiera on 2008-10-26
> **Stalker72 said:**
> I've heard about that one before.

Anyways, I'll just try a reinstallation of Ubuntu.

Let's hope Intrepid Ibex is more stable than Hardy Heron! :)

Stalker72

its unsure, Ibex doesnt seem to be that great of a release.
These days Ubuntu is win some, loose some I have found.
Granted Ubuntu is a great distro mainly because of its community and support but it sometimes doesnt do the job people need it to.
For some people Ubuntu might not be the distro to use.
But lucky for you Ubuntu is not the only fish in the sea, there are other linux variants that are equal or better then Ubuntu for the new user.
Such as Mandriva or Linux Mint.

---

### Post by Xiong Chiamiov on 2008-10-26
Can you boot with one of the old kernels?  The grub menu should keep at least the one previous kernel in the menu.  There might be a keypress to show the menu; if so, then there should be some text that tells you so.

---

### Post by Stalker72 on 2008-10-26
> **SunnyRabbiera said:**
> Ibex doesnt seem to be that great of a release.
Aren't there numerous bug fixes?

Stalker72

---

### Post by Stalker72 on 2008-10-26
> **Xiong Chiamiov said:**
> Can you boot with one of the old kernels?  The grub menu should keep at least the one previous kernel in the menu.  There might be a keypress to show the menu; if so, then there should be some text that tells you so.
Well, yes, but I've already started a reinstallation of Ubuntu. Let's see how it goes! ;)

Stalker72

---

### Post by SunnyRabbiera on 2008-10-26
> **Stalker72 said:**
> Aren't there numerous bug fixes?

Stalker72

Eh, not all the time.
Releases can sometimes even cause more bugs then repair them, I have seen it happen with every OS i have used.
Though most of the time I have seen linux update better then OSX or windows, a good percent of the time Linux is able to update more consistantly then its high priced counterparts.
But that doesnt meant there wont be issues as sometimes linux can be temperamental.
Anyhow try what Xiong Chiamiov said and at your boot screen when grub starts hit escape and see if the older kernel will work if its listed.
Edit: ah you are reinstalling, well when all else fails its worth a shot in any case :D
Sometimes ubuntu works better on a reinstall.
But it depends on the personality of your computer and what you do.
But one suggestion i can make is be careful this time, dont just rush in with installing things, let ubuntu update first before installing more advanced graphics drivers and such and also be cautious on what you load in.
This sort of stuff is true on any OS

---

### Post by Nepherte on 2008-10-27
> **Stalker72 said:**
> Well, yes, but I've already started a reinstallation of Ubuntu. Let's see how it goes! ;)

Stalker72
Next time, just wait a little with reinstalling. Sometimes it happens that an update of the kernel breaks your system. They are thoroughly tested before making it available in the repositories, but for some people they still cause trouble. That's where the older kernels come in. They aren't removed when an update is installed, and you can select them from the boot menu. If an older one still works, Just stick with that one. It's not that bad to use an older kernel.

---

### Post by Stalker72 on 2008-10-27
I changed my mind and installed Linux Mint. I love it, but the sound doesn't work, as in Ubuntu!

Stalker72

---

### Post by Stalker72 on 2008-10-27
My speakers are connected by USB (there's a sound card in the subwoofer, so the motherboard's sound card isn't used at all). What can I do to get the sound to work?

Stalker72

---

### Post by Stalker72 on 2008-10-27
I managed to get sound by going to Sound Preferences and selecting USB Audio. :)

Now I have no issues at all in Linux Mint (thanks SunnyRabbiera!). :)

Stalker72

---

