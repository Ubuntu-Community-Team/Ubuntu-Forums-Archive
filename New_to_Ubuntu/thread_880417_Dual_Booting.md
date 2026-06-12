---
title: "Dual Booting"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by unicycleboy2 on 2008-08-05
Hey, I chose the dual booting option for installing ubuntu. Pretty much the only reason I even want ubuntu is because it has all those cool animation things like when you close a window and move it around. when I go to preferences and go to the desktop animation option thing, it says I cant. Is this because I chose dual booting?

---

### Post by Paqman on 2008-08-05
You might need to install your graphics card drivers. Check System > Admin > Hardware Drivers.

---

### Post by unicycleboy2 on 2008-08-05
Ok thanks I'll try it. I also have one more question, I went to youtube and it said I had to install flash and when I did it had 3 or 4 formats and I had no idea which to download, whenever I tried using any of them it just wouldnt work... so any tips on that? Am I always going to run into problems with compatability if I use ubuntu?

---

### Post by bpowell2005 on 2008-08-05
> **unicycleboy2 said:**
> Hey, I chose the dual booting option for installing ubuntu. Pretty much the only reason I even want ubuntu is because it has all those cool animation things like when you close a window and move it around. when I go to preferences and go to the desktop animation option thing, it says I cant. Is this because I chose dual booting?

Should have nothing to do with your dual-boot setup. When Ubuntu boots, it has exclusive use of the computer resources; Windows is just a set of files on the hard drive.

If you go to System, Preferences, Appearance, and the Visual Effects tab, you select "Extra" and Ubuntu says "No"? Does it give any other reason? 

Are you running very old hardware, maybe the video card isn't up to the task? Or not enough RAM?

---

### Post by Paqman on 2008-08-05
> **unicycleboy2 said:**
> Ok thanks I'll try it. I also have one more question, I went to youtube and it said I had to install flash and when I did it had 3 or 4 formats and I had no idea which to download, whenever I tried using any of them it just wouldnt work... so any tips on that? Am I always going to run into problems with compatability if I use ubuntu?

Best way to get Flash, multimedia support and a bunch of other good stuff is to install [ubuntu-restricted-extras (click to install)](apt:ubuntu-restricted-extras)

Once your system is set up there should be very little that causes you compatibility problems.

---

### Post by hotrod6657 on 2008-08-05
Or, is your hardware really new?  Like bleeding edge stuff.  It indeed does not have anything to do with the dual booting.

Post your video card info and we'll see if we can't get somewhere.

hotrod

---

### Post by unicycleboy2 on 2008-08-05
I have a computer that is only a few months old, 4 GB ram, 2.4 Ghz @Q660 processor 8600 nvidia video card, When I go to System, Preferences, Appearance, Visual Effects tab then Extra it says "Desktop effects could not be enabled." When I go to System, Admin Hardware Drivers it says nvidia_new enabled but not in use.

---

### Post by unicycleboy2 on 2008-08-05
*also my processor is quad core, just thought I would add that.

---

### Post by unicycleboy2 on 2008-08-05
One more problem (last one) when I download something, it says choose program to open the installer and I honestly have no idea what to use or where to look.

---

### Post by unicycleboy2 on 2008-08-05
> Best way to get Flash, multimedia support and a bunch of other good stuff is to install ubuntu-restricted-extras (click to install)

"Can not find 'ubuntu-restricted-extras' " 

?????? Why does nothing work!

---

### Post by mangy_mathan on 2008-08-05
> **unicycleboy2 said:**
> Ok thanks I'll try it. I also have one more question, I went to youtube and it said I had to install flash and when I did it had 3 or 4 formats and I had no idea which to download, whenever I tried using any of them it just wouldnt work... so any tips on that? Am I always going to run into problems with compatability if I use ubuntu?

Personally, I've tried a few of them, but unfortunately only Adobe's proprietary plugin will do the job. swfdec can handle youtube videos, but other things, like Facebook's photo uploader, simply won't work.

To get Adobe's Flash Player 9, just type 

*sudo aptitude install flashplugin-nonfree*

into a terminal.

Also, I'm not sure if it's an Adobe or a Linux thing (though I suspect it's Adobe), Flash Player 9 tends to crash firefox when it begins to play something, like a youtube video or a new track on your project playlist.

I found a fix that worked for me. You can find it at

[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

Pretty much what you do is uninstall flash, install a netscape wrapper, and reinstall flash. Since doing this, flash has not crashed for me at all. Hope this helps you.

---

### Post by bpowell2005 on 2008-08-05
> **unicycleboy2 said:**
> One more problem (last one) when I download something, it says choose program to open the installer and I honestly have no idea what to use or where to look.

If you're downloading a .deb file (for Linux) you'd most likely want to use synaptic package manager to open the file...if you're downloading a .exe file, then you'll need to install Wine and use Wine to open the .exe files.

---

### Post by unicycleboy2 on 2008-08-05
Nvm about that last post I followed this:



Go to Applications &#8594; Add/Remove...


Set Show: to All available applications

Search for ubuntu-restricted-extras

---

### Post by wickstopher on 2008-08-05
The easiest way to get this working in Hardy (I have the same GPU) is to install envyng-gtk.

First, make sure you have all of the restricted repositories enabled in Synaptic.  Go to System > Administration > Synaptic Package Manager.

From within Synaptic, click on the Preferences menu and choose Repositories.  You should get a window that says "Downloadable from the Internet" followed by a list of checkboxes.  Make sure that they are all checked, except for the box marked "Source Code."  Close the window, and hit the "Refresh" button.

From here, you have two options for installing the software.

1) Still in Synaptic, click on the "Search" button, and enter envyng as your search criteria.  Select envyng-gtk (or, if you're using KDE/Kubuntu, select envyng-qt).

OR

2) From a terminal, type:

```
sudo apt-get install envyng-gtk
```

Once installed, select EnvyNG from the System Tools menu and it will download and install the correct driver for your GPU.

From there, you should be good to go!

Edit:
once you have these repositories enabled, you will also be able to install the ubuntu-restricted-extras metapackage.

---

### Post by hotrod6657 on 2008-08-05
Okay, first lets try and get the video card working.  You're going to want to go to the terminal.  (Applications, Accessories, terminal)

From there type:

```
sudo apt-get install envyng-core envyng-gtk
```

It will prompt you for your root password.  Enter it, and press enter.  When everything is done go to Applications, System Tools, EnvyNG.  That will launch the program, click through and follow it's instructions and it should install everything you need.  No promises but the same method works perfectly for me with a 9600 GSO.

---

### Post by hotrod6657 on 2008-08-05
wickstopher beat me to the punch!  sweet!

---

### Post by unicycleboy2 on 2008-08-05
[IMG]http://s39.photobucket.com/albums/e177/unicycleboy_2008/?action=view&current=Screenshot-OpenFiles.png[/IMG]

This is what happens when I try to install a flash player.

---

### Post by unicycleboy2 on 2008-08-05
woops the picture link didnt work
here it is

[http://s39.photobucket.com/albums/e177/unicycleboy_2008/?action=view&current=Screenshot-OpenFiles.png](http://s39.photobucket.com/albums/e177/unicycleboy_2008/?action=view&current=Screenshot-OpenFiles.png)

---

### Post by hotrod6657 on 2008-08-05
Try what unicycleboy2 recommended.  Go to Applications, add remove programs, set it to show all available applications and search for "ubuntu-restricted-extras" (no quotes).

Once it shows up, click the check next to it and click apply changes at the bottom of the window.

That should install flash player, the codecs you need for playing movies and music, and other stuff that because of the free nature of Ubuntu can't be included with the operating system.

hotrod

---

### Post by hotrod6657 on 2008-08-05
personally though, i would get the graphics thing working first just in case it messes anything up, you won't have spent time setting up a lot of other stuff already.  But both these things are pretty simple once you get used to the interface.  Let us know how it goes.

hotrod

---

### Post by unicycleboy2 on 2008-08-05
I have tried everything that people have said and I just get new errors, ubuntu interests me, but not enough for me to pursue it any longer. Perhaps in the future it will spark my interest again and I will take another go at it but for now I am finished. You have all been a great help, thank you very much this is a great community with lots of helping members.

See ya later

---

### Post by jualin on 2008-08-05
If you haven't give up yet maybe we can help you out taking a different approach. Feel free to ask again if you desire.

---

### Post by Paqman on 2008-08-05
> **unicycleboy2 said:**
> "Can not find 'ubuntu-restricted-extras' " 

?????? Why does nothing work!

Do you have the multiverse repo enabled? Go to System > Admin > Software sources and see if it's checked.

---

### Post by hotrod6657 on 2008-08-05
I'm sure that we can get those issues ironed out with a little more time.  If you are done with Ubuntu for now i do hope you come back at somepoint.  It takes a little getting used to but once you get over those hurtles it's a lot of fun.

---

### Post by hotrod6657 on 2008-08-05
> **Paqman said:**
> Do you have the multiverse repo enabled? Go to System > Admin > Software sources and see if it's checked.

Oh!  good point.  I think mine were enabled by default when I installed 8.04 but I never thought to suggest that.

---

### Post by jualin on 2008-08-05
> **hotrod6657 said:**
> Oh!  good point.  I think mine were enabled by default when I installed 8.04 but I never thought to suggest that.

I think it comes enabled by default but who knows, good point either way!

---

