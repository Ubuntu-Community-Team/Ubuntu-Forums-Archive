---
title: "Wacom tablets"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by lile001 on 2012-05-21
Ubuntu 12.04 broke the drivers for the Wacom tablet, apparently.  Once the smoke was clear, and 12.04 was installed, my tablet doesn't work properly.  

There was a [long thread here]("http://ubuntuforums.org/showthread.php?t=967147") that is now defunct, only applies to old versions of Ubuntu. At the very least, this thread held information that was pretty frustrating to non-programmers, or downright arcane.  One was expected to know how to compile programs from source, as if this is something every grandma does before starting her knitting, for example. 

There is a graphical configuration program installed by default in Ubuntu, that affects only the most basic parameters, does not affect the touch panel, and does not allow many of the options needed to use the Wacom tablet properly.  

There is a new [mediawikipage here]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page"), that is more obfuscated, if that is possible, than the old thread.   This documentation is written by programmers, for programmers only. Regular folks need not apply.  Each page starts off with the most obscure information first, such as "here is what changed from the last version" rather than starting off with basics, which are needed by normal people to understand what is needed. Am I even reading a page that applies to my problem?  Who knows: reading this gibberish is like translating Mayan.  

The newer mediawiki page has little or nothing in the way of support forums, as far as I can tell.  

There are graphical tools for referenced configuring Wacom tablets, but they don't work on versions newer than 11.10.  

Someone obviously wrote the graphical interface that appears in Ubuntu 12.04.  Is there a support page for it?  Is there any way to find out more about how to configure it?  I need this tablet because of a handicap.  I cannot use a standard mouse due to carpal tunnel - the pain is unbearable.  The tablet is a lifesaver, but now I can't figure out how to get it working properly again.  Where do I go for some suggestions as to how to proceed?

---

### Post by madjr on 2012-05-21
Did you upgrade from 11.10 to 12.04 ? maybe it was a bad upgrade.

Is always advisable to try any new versions of ubuntu (or any OS) first with your hardware. Is easy to try a new ubuntu version with an usb stick, load it up and see if everything works. If everything works then proceed to update or fresh install (recommended).


Anyway, other than that solution, maybe this thread here has a possible workaround for your problem:

[http://ubuntuforums.org/showthread.php?t=1974099](http://ubuntuforums.org/showthread.php?t=1974099)

---

### Post by Favux on 2012-05-21
Hi lile001,

You tell us you are in 12.04 which is good but you don't tell us which Wacom tablet and model you have.  And you don't tell us what is wrong with your tablet.

Wacom tablets work better than ever in 12.04 now that the GNOME has finally started replacing the old wacomcpl gui with their Wacom Graphics Tablet applet in System Settings.  Precise has the second version.  Still early days but now with libwacom going (tablet metadata) should see more improvement with next release.

You start with:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up)
Most of the user stuff is in:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)
> This documentation is written by programmers, for programmers only.
I take a little offense at this one.  I am not a programmer and I did not write the pages I contributed for programmers.  :)

---

### Post by lile001 on 2012-05-22
> **Favux said:**
> Hi lile001,

You tell us you are in 12.04 which is good but you don't tell us which Wacom tablet and model you have.  And you don't tell us what is wrong with your tablet.

Wacom tablets work better than ever in 12.04 now that the GNOME has finally started replacing the old wacomcpl gui with their Wacom Graphics Tablet applet in System Settings.  Precise has the second version.  Still early days but now with libwacom going (tablet metadata) should see more improvement with next release.

You start with:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up)
Most of the user stuff is in:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

I take a little offense at this one.  I am not a programmer and I did not write the pages I contributed for programmers.  :)

Thanks, Favux!  I look forward to reading some clear and understandable documentation then!

---

### Post by lile001 on 2012-05-22
> **Favux said:**
> Hi lile001,

You tell us you are in 12.04 which is good but you don't tell us which Wacom tablet and model you have.  And you don't tell us what is wrong with your tablet.

OK here is a specific task (there are a few others, let's tackle one at a time.)  I'd like to turn on the touchpad to work like a scroll wheel.  This was working before the upgrade to 12.04.  I am using the Wacom Intuos 3 PTZ630 model tablet. 

[This page]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up")  doesn't really address the touchpad, so I moved on. 

[This page]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO") doesn't have anything directly about the touchpad, but has some hints. 

Drilling down into some of the links there,  I find out that I can do this

```
 xsetwacom list
Wacom Intuos3 6x8 stylus        	id: 8	type: STYLUS    
Wacom Intuos3 6x8 eraser        	id: 12	type: ERASER    
Wacom Intuos3 6x8 cursor        	id: 13	type: CURSOR    
Wacom Intuos3 6x8 pad           	id: 14	type: PAD   
```

and one of those things listed may or may not be the device I need to do something with.  That's about as far as I have been able to get. 

There is apparently a file called xorg.conf.d that needs something edited. I haven't been able to locate this file. 

Apparently you can enter some xsetwacom commands from a terminal, however, when I have tried this I am typing something wrong and cannot get any of that to work. I have read a number of other pages and man pages about the subject but haven't made any sense of them yet.

So you can see, I have been struggling to understand the documentation I can find, but really am in over my head.

---

### Post by Favux on 2012-05-22
Good, you have an Intuos3 tablet.

So by touchpad you mean touchstrip?  Touchstrips, buttons, scroll wheels etc. are on the pad device.  An example of how to configure those is here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Intuos3](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Intuos3)

From your xinput list your <device name> is:
> "Wacom Intuos3 6x8 pad"
You use the quotes in an xsetwacom set command e.g.
```
xsetwacom set "Wacom Intuos3 6x8 pad" Parameter Value
```
You can get many of the Parameters by running ***man xsetwacom*** in a terminal.

What remains is to figure out what commands will work for scroll.  "key Prior" and 'key Next" maybe if the ones there don't work.  And probably have to change the button numbers from 12345678 to 1238910,11,12.  That's because X.org started reserving 4 thru 7 for scroll.  So in xorg.conf.d you could probably use 4 and 5 for the scroll Option Values.

Two xorg.conf.d files:
Distro's:  /usr/share/X11/xorg.conf.d
User's:  /etc/X11/xorg.conf.d

That's from the beginning of:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)

You can get many of the Options available by running ***man wacom*** in a terminal.

---

### Post by lile001 on 2012-05-22
> **Favux said:**
> 

Two xorg.conf.d files:
Distro's:  /usr/share/X11/xorg.conf.d
User's:  /etc/X11/xorg.conf.d


Yep, this is where I start to get confused. 

A search of my computer finds no file called xorg.conf.d. 

[Documentation]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d") doesn't match what what I find in the brainbox. 

/usr/share/X11/xorg.conf.d  There is no file by this name.  There is a folder by this name, with a bunch of other files in it: 

```
-rw-r--r-- 1 root root 1099 Apr 20 00:14 10-evdev.conf
-rw-r--r-- 1 root root  590 Mar 15 10:55 11-evdev-quirks.conf
-rw-r--r-- 1 root root  364 Mar 15 10:55 11-evdev-trackpoint.conf
-rw-r--r-- 1 root root  956 Apr 24 04:40 50-synaptics.conf
-rw-r--r-- 1 root root  115 Mar 22 11:50 50-vmmouse.conf
-rw-r--r-- 1 root root  842 Mar 30 05:15 50-wacom.conf
-rw-r--r-- 1 root root  590 Apr 24 04:39 51-synaptics-quirks.conf

```


/etc/X11/xorg.conf.d  There is also no file by this name.  There is a file in this directory called xorg.conf, but it doesn't look familiar after looking at the references cited.  

So this is one of the reasons I can't follow the documentation, there is no such file, and I don't know enough to proceed. Perhaps the documentation is out of date vis-a-vis Ubuntu 12.04?

---

### Post by lile001 on 2012-05-23
[This page]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Intuos3") mentions something about creating a 52-wacom-options.conf file in  /etc/X11/xorg.conf.d/, however the link that describes that file links back [to this page]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d") describing xorg.conf.d, which talks about lots of options to change said file, however, I don't have anything to start with. It never really comes out and says "This is what you started with", only assumes you already have that information and want to change it. I do not have sufficient knowledge to confidently create this stuff from scratch, or even from the [examples here]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Configuring_X#Static_xorg.conf_Setup") 

  It is like the old joke after this point - If there is a piece of bread missing on the trail of bread crumbs, I spend the next hour looking under the streetlight, as the old joke goes, because there is more light there, but I never find the trail again.

---

### Post by Favux on 2012-05-23
You have to have a /usr/share/X11/xorg.conf.d if you are in Natty (11.04).

What is the output of the following command in a terminal:
```
Xorg -version
```

---

### Post by lile001 on 2012-05-23
> **Favux said:**
> You have to have a /usr/share/X11/xorg.conf.d if you are in Natty (11.04).

What is the output of the following command in a terminal:
```
Xorg -version
```

I am using Ubuntu 12.04

```
Xorg -version

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
Current Operating System: Linux DianeFossey 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=c1231a18-734c-4df2-b917-c7d8177fea45 ro quiet splash vt.handoff=7
Build Date: 20 April 2012  05:12:02AM
xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
```

Perhaps there needs to be an update of some of this documentation to apply to the changes in Ubuntu 12.04? Could that be part of the reason I have not been able to follow it?  (of course there is the problem that I am little smarter than my hero Homer Simpson, and am the Grandson of Sargent Murphy.  I always find the right way to do something, because I try everything else first.)

---

### Post by Favux on 2012-05-23
Yep, that's Precise.

So prove to yourself xorg.conf.d is there.  Let's show the path to a couple of .conf files in it.  Open a terminal and enter:
```

locate 10-evdev.conf
or
locate 50-wacom.conf
```

For the user's xorg.conf.d, where the user is suppose to make changes, you may need to create the directory if it is not already there.

So if there is no xorg.conf.d in /etc/X11 in a terminal enter:
```
sudo mkdir /etc/X11/xorg.conf.d
```

---

### Post by lile001 on 2012-05-23
> **madjr said:**
> 

Is always advisable to try any new versions of ubuntu (or any OS) first with your hardware. Is easy to try a new ubuntu version with an usb stick, load it up and see if everything works. If everything works then proceed to update or fresh install (recommended).


Upgrading to 12.04 was a 6 by 6 choice - it solved some other problems I was having (even some showstoppers!) but created new ones.  It was 6 of one, 6 of the other, as they say, so I went ahead with it hoping we could clean up the problems later.

---

### Post by lile001 on 2012-05-23
> **Favux said:**
> Yep, that's Precise.

So prove to yourself xorg.conf.d is there.  Let's show the path to a couple of .conf files in it.  Open a terminal and enter:
```

locate 10-evdev.conf
or
locate 50-wacom.conf
```

For the user's xorg.conf.d, where the user is suppose to make changes, you may need to create the directory if it is not already there.

So if there is no xorg.conf.d in /etc/X11 in a terminal enter:
```
sudo mkdir /etc/X11/xorg.conf.d
```

50-wacom.conf is, as I indicated above, in a directory called xorg.conf.d, but there is no file called xorg.conf.d.  When I noticed that, I started asking dumb questions, since I couldn't figure out where to go next.  


```
ls /usr/share/X11/xorg.conf.d
10-evdev.conf             50-synaptics.conf  51-synaptics-quirks.conf
11-evdev-quirks.conf      50-vmmouse.conf
11-evdev-trackpoint.conf  50-wacom.conf

```

---

### Post by Favux on 2012-05-23
They aren't dumb questions.  I'm the one who goofed by typing files instead of folders.

---

### Post by lile001 on 2012-05-24
So do we do something with creating this 52-wacom.conf file?  I see just enough info in the examples to have a vague idea of how to proceed, but not enough that I am sure of what I am doing.

---

### Post by Favux on 2012-05-24
Sure, but we can get to that later.  Let's get back to the touch strips which is the first thing you wanted to address.

From the wiki here is a sample **xsetwacom.sh** script:
```
xsetwacom set "Wacom Intuos3 6x8 pad" Button 1 "key r"  # rectangular selections
xsetwacom set "Wacom Intuos3 6x8 pad" Button 2 "key ctrl shift a"  # select none
xsetwacom set "Wacom Intuos3 6x8 pad" Button 3 "key p"  # paintbrush
xsetwacom set "Wacom Intuos3 6x8 pad" Button 4 "key tab"  # toggle docks
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "key minus"  # zoom out
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp "key shift plus"  # zoom in

xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key alt down"  # brush radius (must be mapped in GIMP)
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightUp "key alt up"
xsetwacom set "Wacom Intuos3 6x8 pad" Button 5 "key shift control left"  # prev/next brush (must be mapped in GIMP; disables float)
xsetwacom set "Wacom Intuos3 6x8 pad" Button 6 "key shift control right"
xsetwacom set "Wacom Intuos3 6x8 pad" Button 7 "key ctrl shift e"  # fit Image in window
xsetwacom set "Wacom Intuos3 6x8 pad" Button 8 "key F11"  # fullscreen
```
So right click on the Desktop and create a blank text file and copy and paste the script into it.  Save as **xsetwacom.sh** or **intuos3-xsetwacom.sh** or whatever.  Then right click on the saved file and select Properties and go to the Permissions tab and click on the make it executable box.  You now should have a working script.  Except they went ahead and reserved buttons 4-7 for scroll like I mentioned.  They being the kernel folks or maybe X.org.  So that means we now have two types of button numbers, the Physical button numbers and the X button numbers.  Yes this is a pain, but outside the LWP's control.

To figure out the X button number you would use the get command on a system with no extra configuration applied so you have the default setup.  Like:
```
xsetwacom get "Wacom Intuos3 6x8 pad" Button 4
```
And see what value it returned.  And do the same with the rest of the buttons.  And hope a developer didn't mess with the button assignments in the kernel.  Yes another pain and you got me on that one.

Anyway unless you were using Lucid my guess is your script should now look like:
```
xsetwacom set "Wacom Intuos3 6x8 pad" Button 1 "key r"  # rectangular selections
xsetwacom set "Wacom Intuos3 6x8 pad" Button 2 "key ctrl shift a"  # select none
xsetwacom set "Wacom Intuos3 6x8 pad" Button 3 "key p"  # paintbrush
xsetwacom set "Wacom Intuos3 6x8 pad" Button 8 "key tab"  # toggle docks
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "key minus"  # zoom out
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp "key shift plus"  # zoom in

xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key alt down"  # brush radius (must be mapped in GIMP)
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightUp "key alt up"
xsetwacom set "Wacom Intuos3 6x8 pad" Button 9 "key shift control left"  # prev/next brush (must be mapped in GIMP; disables float)
xsetwacom set "Wacom Intuos3 6x8 pad" Button 10 "key shift control right"
xsetwacom set "Wacom Intuos3 6x8 pad" Button 11 "key ctrl shift e"  # fit Image in window
xsetwacom set "Wacom Intuos3 6x8 pad" Button 12 "key F11"  # fullscreen
```
Just added four to every button number after 3.

Now to finally get down to it.  Let's take the right strip:
```
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key alt down"  # brush radius (must be mapped in GIMP)
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightUp "key alt up"
```
and change it too:
```
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key Next"
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightUp "key Prior"
```
Then to apply the script just dbl. click on it and choose Run.  Does the strip now "scroll"?

---

### Post by lile001 on 2012-05-24
We are getting there.  I implemented these lines:

```
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key Next"
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightUp "key Prior"
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "key Next"
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp "key Prior"
```

and made it executable, which does work after a reboot if I click on it.  However, my lame attempt at making this run at startup didn't work. 

The scrolling works, for example, in Chrome and Libreoffice, but isn't working in Gimp and Draftsight (A CAD program)yet. Thanks for your help so far, we are getting somewhere! 



OK, so where would I have found this information on my own? Let's follow the breadcrumb trail:

So in my struggles to understand this stuff, I keep running into missing breadcrumbs. You've noted elsewhere that there are folks controlling [these wiki pages]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page") whose philosophy is that "everyone using Linux should be a Linux engineer", despite your objections, and it shows. 

Digging back into the wiki documentation and the Xsetwacom program I find a couple of places where these missing breadcrumbs occurred:

1.  X11 events:

```
~$ xsetwacom list parameters

StripLeftUp      - X11 event to which left strip up should be mapped. 
StripLeftDown    - X11 event to which left strip down should be mapped. 
StripRightUp     - X11 event to which right strip up should be mapped. 
StripRightDown   - X11 event to which right strip down should be mapped. 

 
```  I could find out that I needed to do something with StripLeftUp etc, and map it to an "X11 event" but there I hit a dead end.  Researching "X11 events" opened up a can of worms.  

2. Examples seem irrelevant to the uninitiated:

[This page of examples]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") is where you picked the script you started with above, out of an example for Gimp configuration.  Not needing to configure anything for Gimp specifically, I had skipped over that example many times in reading this stuff.  Reading the words "key Next" and "key Prior" don't really jump out at a guy as something related to a scroll wheel, either.

Perhaps it is possible with this kind of ammunition to convince the Wiki Gods to lighten up on us mortals a bit?

---

### Post by Favux on 2012-05-24
```
However, my lame attempt at making this run at startup didn't work. 
```
Right click on the Desktop and create new folder called **bin**.  Copy the executable script into **bin**.   Then paste bin into Home in Nautilus.

Right click on the gear in the top right corner and choose Startup Applications...  Then click on Add.  For the name call it say "xsetwacom startup script".  Then in command use the full path name to the script, i.e.:
```
sh /home/yourusername/bin/xsetwacom.sh
```
Using whatever name you called xsetwacom.sh (the script) and your user name.

Now you have it on startup and a copy on your Desktop you can run after a hotplug.  I put the one on the Desktop into a launcher along with some specific Profiles.

On the wiki page in Profiles:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Profiles](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Profiles)  I tell you where to look in Gimp for settings like that:
> To select different pad button assignments you should become familiar with the keyboard shortcuts available in the program you are interested in. For e.g. with Gimp look in Edit > Keyboard Shortcuts or Edit > Preferences > Interface > Configure Keyboard Shortcuts. For Inkscape it's Help > Keys and Mouse reference which takes you to the keyboard shortcuts online. Some of the pad sections above contained possible Gimp and Inkscape button assignments. 
Obviously it is not reasonable for me to write a Gimp tutorial on a Wacom driver wiki.  So you need to use one of the many Gimp tutorials to finish setting it up, likely with a Gimp Profile.
> So in my struggles to understand this stuff, I keep running into missing breadcrumbs. You've noted elsewhere that there are folks controlling these wiki pages whose philosophy is that "everyone using Linux should be a Linux engineer", despite your objections, and it shows. 
No that's not what I'm saying.  You're beginning to come to grips with the problem.  The situation actually can change from release to release in a given Distro.  Add the complication of multiple Distro's.  Now you start to see the challenge.

I've just led you through some Ubuntu specific stuff, for your release.  Now how do I write a "clear and simple" wiki when I have to cover so many variables?

What I have there actually took a lot of experience and thought to come up with.  The developer's perspective is they want the user to understand the basics so they can then figure out how to apply it to the Distribution and release they are using.  That said the wiki stuff can always be improved to be clearer and better.

I actually started out with "drop in" example scripts for many tablets.  It took a big struggle to keep what's left of that.  The developers wanted to completely nuke them as they did not want to deal with inevitable endless questions about bugs in the scripts because the user did not understand how to modify them to fit their situation.  That's why I cite sources, give links, and explain, so you can understand how to build a script.  And there is no getting around you have to invest an hour or two of reading and another hour or two of experimenting until you get it.  After that the only time consumer is figuring out what the individual applications need.

What you are asking for is a simple guide for your exact situation.  Sure could do it.  Then need to write about 50 more "duplicates' for other releases and Distros.  And keep adding to them as the Distro's put out new releases.  Not going to happen.

The simplification being introduced is the GNOME Graphics Tablet applet.  Still early days for it but hopefully in the next release or two it'll be good enough that most users can just use it as a graphical frontend and not have to deal with plumbing like the scripts etc.

---

### Post by madjr on 2012-05-25
> **lile001 said:**
> Upgrading to 12.04 was a 6 by 6 choice - it solved some other problems I was having (even some showstoppers!) but created new ones.  It was 6 of one, 6 of the other, as they say, so I went ahead with it hoping we could clean up the problems later.

i would also try a fresh ubuntu 12.04 in an usb stick

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

and see if your wacom works properly as with 11.10.

---

### Post by lile001 on 2012-05-25
Well here is where we are at so far:

1. Startup script worked, the tablet is now programmed at boot to have some customizations

2.  Scroll strip works in browsers, Libreoffice, and some other programs

3.  Scroll strip did not work in Gimp, because of some specifics that Gimp uses, not because of any fault of the tablet.  Hack is posted below.

4. Scroll strip does not work in Draftsight.  It does try to scroll the text window, so it is talking to the program, just not very pretty.  Scrolling a mouse in CAD programs repetitively for years was one of the things that got me into Carpal Tunnel problems in the first place, so this is bad news. 

I've got a xsetwacom.sh script with a bunch of notes in it, including that hack that allows it to talk pretty to Gimp.  There are other ways to solve the problem with Gimp, this is the one that I chose to use.

See hack below.

---

### Post by lile001 on 2012-05-26
And after a bit of fatfingering, here is the script I am using:

```

#this scrolls by pagedown, too fast. 
# This will work as a Zoom in Gimp if you hack Gimp a little:
# in Gimp go to Edit > Preferences > Interface > Configure Keyboard Shortcuts >
# View > Zoom In > Click on the Shortcut Column (This defaults to +) change to #PGdn
# Likewise set Zoom Out to Pgup
# I have the Right hand strip set to PGup PGdn, lefthand strip set to Up Down
# So Gimp works with the Right hand strip only
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key Next"
# 'key next" and "key prior" are the same as pgdn, pgup
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightUp "key Prior"

# this works to scroll in browsers and libreoffice.  
#I like the speed of it better than pgup and pgdn, w
#hich are too fast for me.
#Will work with a shift key held down in Gimp
# Occasionally there is a browser window this doesn't 
#work in. Dunno why. However, the pgup and pgdn in the right hand 
#strip seem to work for these pages, another reason to leave it that way.
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "core key down"
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp "core key up"

# Other settings I have tried but didn't like
# this works to move the scrollbar up and down (not zoom) in gimp
#xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "core key SHIFT up"
#xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp "core key SHIFT down"
# this works to zoom in Gimp with Gimp's default key mapping. 
#I rejected this one because essentially no other program I use has
#+ and - as a zoom key.  
#xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "core key minus"
#xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp "core key SHIFT plus"

#Still no luck scrolling in Draftsight.  
#Strip just scrolls text window. 
#Probably no solution available.

```

Perhaps these notes will be useful to someone else.  At least here are several different ways of solving the same issue, and why it works differently in some programs. 

Man, I wish there was a simple, graphical interface that just set all this stuff for ya.

---

### Post by lile001 on 2012-06-01
As I noted above, I was able to get the strips to emulate the scroll wheel in general programs (browsers, Libreoffice, etc), in Gimp with a little hack, but was not able to get them to work properly in Draftsight, an AutoCad clone.  In Draftsight, using the toushstrips scrolls the text window, not zoom the graphics window as happens with a real mouse wheel.  So far no solution for Draftsight, other stuff seems to be working. 

Hopefully this thread will be useful for the next guy trying to get this wacom stuff to work.   If anyone has any other suggestions for Draftsight, please post.

---

