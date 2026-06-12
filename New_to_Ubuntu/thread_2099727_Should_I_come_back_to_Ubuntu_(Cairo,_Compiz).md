---
title: "Should I come back to Ubuntu (Cairo, Compiz)?"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by misswham on 2012-12-30
I just bought a sony vaio all in one with an nvidia GE FORCE GT240 graphics card. I have never been able to use compiz or cairo dock since helena 8. When I try to use compiz or dock, when I restart, I always have gotten a black screen or my desktop goes crazy and I have to reinstall the distro. I liked linux because I could tweak the OS. I have tried in mint 12 (all distros) 13 all distros now 14 and Im getting the same results. I have done this on 3 different pcs and I went and bought this pc last wk thinking that it would be fine and yet the same thing. So I left compiz alone and went 2 cairo dock. Got it working fine and as soon as I restarted the computer, I got the default screen with no panels and all of my files were gone and this was just with cairo dock. I have reinstalled mint14.1 3 times in one day trying to do this.

Should I go back to Ubuntu to be able to use cairo and compiz again? If so, what Distro should I download and Im sure I have to start the adding the codes again?

---

### Post by misswham on 2012-12-30
Now just put 12.10 on my usb and tried 2 boot from it and this is what I got when i pressed f11 like i always did 2 boot from usb.

error: no such device:80d2d8e2 - 673d-4551-9821-c88a406d9a2fgrub rescue>

I booted from the usb with this same file last night.  What has happened do u think?

---

### Post by Bashing-om on 2012-12-30
misswham; Hi !

In all probability, last night when you shut your system down you failed to properly (un)mount the usb drive.This might have corrupted the files.

Screen problems: What boot options have you employed at the grub kernel command line ?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[INDENT][INDENT][INDENT]just try'n to help < == BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by misswham on 2012-12-30
what can i do to rectify the problem?  i have installed mint three times since I did ubuntu and hand no problems.

---

### Post by Bashing-om on 2012-12-30
misswham;

Problem usb corrupted ?? -> Reformat the drive and (re)burn the .iso .
Screen problem ?? -> Boot up the install media -> try ubuntu: What results ???

(Need to get the appropriate graphics driver loaded, and this is where I start in order to see what help is needed).

[INDENT][INDENT]willing to help <== BDQ

[/INDENT][/INDENT]

---

### Post by misswham on 2012-12-30
im a novice at this.  I know u said reformat harddrive, how do I do that?  I went back and erased the usb drive and reinstalled ubuntu and same thing and then mint again and same thing.  do I need 2 use another flashdrive?  Im feel so silly now.  sorry  I can still boot normally and grub comes up and I can boot into mint again but just cant boot from harddrive with another os again.

---

### Post by Bashing-om on 2012-12-30
misswham;

Being a novice is no sin, we were all there at one time.
I am at this time confused as to what your problem is.
1. Can you boot up -ubuntu- on the usb drive in the "try ubunty" mode ?
2. Is it your desire to install ubuntu onto the hard disk ?(now-a-days that takes a few hoops to jump through[technological advances]) 

[INDENT][INDENT]waiting <-- BDQ

[/INDENT][/INDENT]

---

### Post by misswham on 2012-12-30
I've now gotten my pc to boot from usb again now my original question was about compiz and cairo dock.  I tried both and they mess up my system on 3 versions of mint in every distro on 3 different computers.  It did work fine in mint 8 helena but after that had to reinstall over and over again because they mess up my system.  I just played with ubuntu 12.10 and I see its kind of like cinnamon in mint.  I didnt see where i could move the panel from the side or it doesnt seem to have the freedom of other distros in linux to change the desktop.  i wanted to know which distro will work for my sony vaio with nvidia card and i want the freedom to rearrange the whole desktop if I choose and cairo and compiz wont send my pc into craziness?

---

### Post by Bashing-om on 2012-12-30
misswham;

Glad ya got the os back up. I have no experience with the sony vaio, so can not directly relate.
ubuntu desktops: unity is configurable using config tools(d/l and install) to do so. 
There are a number of alternatives for the desktop besides having to run unity. I have not ran any others in 12.04 so again I am at a loss as what I can advise.

A search of the forum will provide opinions and options, google even more.
[INDENT][INDENT]hth <== BDQ 
[/INDENT][/INDENT]

---

### Post by Paddy Landau on 2012-12-30
You have problems with Compiz and Cairo; you also want to tailor your desktop to a large degree.

I think that Ubuntu is not the best way to go. Rather try one of the alternatives:
[LIST]
[*][Lubuntu]("http://lubuntu.net/"): Fast and lightweight, uses LXDE. Somewhat limited in what you can do with the desktop, but likely to work.
[*][Xubuntu]("http://xubuntu.org/"): Also lightweight, though not as light as Lubuntu, uses XFCE. More scope to tailor your desktop.
[*][Kubuntu]("http://www.kubuntu.org/"): A good alternative to Ubuntu, may do what you need.
[*][Bodhi]("http://www.bodhilinux.com/"): Fast and very lightweight, an unofficial Ubuntu family member, but probably too limited for your tailoring needs.
[/LIST]
There are, of course, [many other distros]("http://distrowatch.com/") out there for you to try.

Incidentally, you may want to start with the LTS (12.04) rather than the latest version (12.10).

---

### Post by misswham on 2012-12-30
Just downloaded 12.10 before I read the post right above this one.  I have an Nvidia Corporation:  GT216(GeForce GT 240M}.  Am I supposed to change the driver?

Using X.OrgXserver-Nouveau display driver from xserver-xorg-video-nouveau(open source) is already checked.  Am I supposed to check something else?

Also I see a video on 10 things to do when first installing 12.10 and I dont see MyUnity nor gnome-shell.  Where is it?

---

### Post by BlinkinCat on 2012-12-30
Hi,

I may be wrong but I thought MyUnity was not an option for 12.10

You should be able to install Gnome Shell via the Software  Center.

Cheers - :p

---

### Post by Sef on 2012-12-30
> Just downloaded 12.10 before I read the post right above this one. I have an Nvidia Corporation: GT216(GeForce GT 240M}. Am I supposed to change the driver?

The driver should show up in top right, or you could go to settings (the gear and wrench/spanner) > hardware > additional drivers from the left side dock.

---

### Post by Bashing-om on 2012-12-30
Seems to me I read that Additional Drivers in 12.10 was moved to a tab in software sources . (??)

[INDENT][INDENT]merrily on <== BDQ

[/INDENT][/INDENT]

---

### Post by misswham on 2012-12-30
yes i know where they are, but what i posted above is what is check there now, but am i supposed to check something else and i downloaded gnome shell and it downloaded but i cant find it.  also i tried to download new themes into the ubuntu tweak and it said successful but they arent there and i cant change the pointer.  any suggestions?

---

### Post by BlinkinCat on 2012-12-30
For Gnome Shell, try logging out and then back in - it should then show up on the logon screen as far as I know. You will need to select Unity or Shell via the graphic symbol.

I hope that helps - :P

---

### Post by misswham on 2012-12-31
I logged back in and it has a few gnome selections but no unity or gnome shell.  also my cairo dock isnt functioning, ie the animations.  What do I need to do without messing up my computer to get the animations to work?

---

### Post by BlinkinCat on 2012-12-31
Hi,

Unity shows up simply as ubuntu and gnome shell is shown simply as gnome. As for your other problems, I am not sufficiently experienced to assist. Personally I am on 12.04 which I have chosen for it's stability. There have been some users as far as I know who have some problems with the 12.10 environment.

Hope that helps in a small way - :)

---

### Post by mc4man on 2012-12-31
> **misswham said:**
> I logged back in and it has a few gnome selections but no unity or gnome shell.  also my cairo dock isnt functioning, ie the animations.  What do I need to do without messing up my computer to get the animations to work?
You seem to be jumping around a little with ?'s, so concerning video drivers

Did you install the nvidia- drivers?

**If so** then on a fresh 12.10 install the drivers will fail to build if you don't install linux-headers-generic **1st**
([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)

So if you **did install the nvidia drivers** remove them.
```
sudo apt-get purge nvidia-*
```

Then 
```
sudo apt-get install linux-headers-generic
```
After that feel free to re-install the nvidia driver from software sources, when done reboot, try either the ubuntu (unity) or gnome (gnome-shell)  session from login screen

---

### Post by misswham on 2012-12-31
I have just installed 12.04 over 12.10 and everythings working wonderfully.  Im loving this Unity.  A big change from mint.  Thanks so much and I will just stick with 12.04 for a while.  It does WAYYY more than I expected.  Took all day to get used to it.  I fumbled with this for 14 hrs yesterday and enjoyed every minute of it.

Again,
THANK U ALL

ps.  How do I mark a thread solved?

---

### Post by Paddy Landau on 2012-12-31
> **misswham said:**
> I have just installed 12.04 over 12.10 and everythings working wonderfully.
Fantastic, I'm pleased you got what you need.

> **misswham said:**
> Im loving this Unity.
I love it too, despite its current problems. It had so much hate posted about it, but it's much quicker to use than the old-style menus.

> **misswham said:**
> How do I mark a thread solved?
Here's how you [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

