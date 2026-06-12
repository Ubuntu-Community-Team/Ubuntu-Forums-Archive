---
title: "Jaunty and Dell Inspiron 9400 (E1705) Guide"
date: 2009-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by kayvortex on 2009-06-03
Welcome. This is a guide for anyone installing Jaunty (9.04) on a Dell Inspiron 9400 (E1705). All the other guides and general information seem to be a bit outdated, so I've decided to make a Jaunty guide.

**[SIZE="4"]General Impressions[/SIZE]**

The 9400 has generally worked very well with Ubuntu since I first installed Edgy on it: there is only really one serious problem, which is the operation of the fans; but that has a solution. Jaunty, in particular, seems like a very good release overall, and I'd have few qualms about recommending installing Jaunty on it.

**[SIZE="4"]Installation[/SIZE]**

Some previous versions of Ubuntu required the alternative installer to install successfully, but Jaunty has no such problem: the normal install CD should work fine. Nothing unusual needs to be done with regards to the installation on the 9400 in particular, so you should consult a generic installation guide if you need help with installing. See [Official Installation Guide]("https://help.ubuntu.com/9.04/installation-guide/i386/pr01.html"), or [Installation Guide]("http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-desktop-installation-guide.html"), for example.

**[SIZE="4"]Set-up[/SIZE]**

**Fans**

I've found that the operation of the fans has always been somewhat of a problem in older releases, and, in a sense, Jaunty is no exception. The fans do seem to work somewhat adequately by default; however, I'd still highly recommend installing i8k and using that to control the fans.
First, install i8k:
```
sudo aptitude install i8kutils
```
Then, add the i8k module to the kernel: open the file /etc/modules by typing:
```
gksudo gedit /etc/modules
```
and then append the line:
> i8k force=1
The module can be started straight away by running:
```
sudo modprobe i8k force=1
```
Installing i8k now adds an init.d script by default, so there is no longer any need to mess about with creating an init.d script and making sure that is run on start-up. Simply install it as above and that's all you'll need to do.
*Note: x86_64 update: I recall that there was no i8k program for the x86_64 architecture some time ago. Does anyone know the current situation?*

**Wireless**

I have the Wireless 1500 Draft 802.11n Card (Broadcom BCM4328 Network controller), which now has a linux driver (albeit a closed source one), and so there is no need to install ndiswrapper any more! When the *Hardware Drivers Window* pops up, simply click the *Activate* button to use it (the system will need to be rebooted before it can be used).
*Note: that there appears to be a bug in Jaunty whereby the wireless connection drops every now and again, only to be reconnected straight away most of the time. It may be an ipv6 problem affecting the 2.6.28.11 kernel, and might be fixed after a kernel update.*

**Video Card**

Getting ATI products to work nicely with Linux has always been a problem, and the solution has previously been a choice between basic open source drivers or buggy (or even non-existent) closed source ones. Before, if you wanted to use the visual effects or install Compiz/Beryl before it was provided by default in the release, then you would have to install the propriety drivers. The closed source drivers provided by ATI worked well (by ATI standards) but were a slight pain to install. However, ATI has stopped providing drivers for the Mobility Radeon X1400 card, and the last such driver ([version 9.3]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=English")) apparently doesn't work with Jaunty, so the situation would appear hopeless (See [ATI Jaunty Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") for reference).
However, the open source drivers provided by default are now extremely good and are at least as capable as the 9.x closed source ATI drivers. Therefore, nothing really needs to be done to have desktop effects besides enabling them: go to *System* -> *Preferences* -> *Appearance*, and go to the *Visual Effects* tab, and select the effects level you want.
I would also recommend installing the settings manager:
```
sudo aptitude compizconfig-settings-manager
```
the emerald themes manager if you want those themes:
```
sudo aptitude install emerald
```
and definitely the fusion icon:
```
sudo aptitude install fusion-icon
```
The fusion icon in particular is very useful. To load it by default go to: *System* -> *Preferences* -> *Startup Applications*, and then in the *Startup Programs* tab click on the *Add* button. Then, in the *Name* field, put something like "Fusion Icon", in the *Command* field put "/usr/bin/fusion-icon --no-start", and add something in the *Comment* field, like "Run the fusion-icon program in the panel". Then, click Add and then Close to finish up. Disabling it is as simple as un-checking the box of the fusion-icon entry you've just made.
You can modify your visual effects by typing
```
ccsm
```
into a terminal, or (after a reboot) right clicking on the fusion-icon icon that will now appear near your shutdown button in your gnome panel (top right of your screen by default) and then clicking on *Settings Manager*.

**Multimedia**

First of all, you'll need to install the relevant codecs:
```
sudo aptitude install ubuntu-restricted-extras w32codecs libxine-extracodecs libdvdread4 libxine1-ffmpeg
```
and then run:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
*Note: there are legal implications to installing some of this software, so please check whether you have the necessary rights to install that software. See [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") for more information.*

The multimedia buttons should work with Rhythbox by default. But, if you would like to replace all things Rhythbox with Amarok, then follow the following steps: first, install amarok
```
sudo aptitude install amarok
```
To make the MediaDirect button open Amarok instead of Rhythbox, go to: *System* -> *Preferences* -> *Preferred Applications*, and in the *Multimedia* tab select *Custom* in the *Multimedia Player* drop-down menu, and then in the *Command* field type "/usr/bin/amarok". Note: don't check the box "Run in terminal": you don't need to do that. Now, pressing the MediaDirect Button should open amarok.

To get the multimedia buttons on the front of the laptop to work you no longer need to install the lineak daemon, simply open Amarok, click on *Tools* and then *Script Manager*. Then click the *Get More Scripts* button, and type "gnome" in the search field on the top right of the window that appears. The *Gnome Multimedia Keys 2* script should appear, and simply click on *Install* to enable it. Click *Close*, then *OK* and your multimedia keys should work on a restart (Source: [Multimedia Buttons]("https://answers.launchpad.net/ubuntu/+source/amarok/+question/35744")).

**Suspend and Hibernate**

Works! But, you will have to tell the system to go to suspend on closing the lid (you can also use the Fn-Esc key on my UK keyboard -- look for "Stand by" on one of your keys and hold the "Fn" key and press that Stand-by button if you don't see "Stand by" on your Esc key to go to stand-by by this method). Go to *System* -> *Preferences* -> *Power Management*. On Each of the *On AC Power* and *On Battery Power* tabs, go to the *Actions* section and in the menu *When laptop lid is closed* choose *Suspend* (or something else if you like). 

**[SIZE="4"]Other Issues[/SIZE]**

**Firefox side-scrolling**

To enable side-scrolling, all you need to do is click on *System* -> *Preferences* -> *Mouse* and then on the *Touchpad* tab check the box *Enable horizontal scrolling*. That's it: nothing else needs to be done and no settings in firefox need to be enabled.
	
**Mounting ntfs partitions**

My ntfs partitions were not mounted by default, so I just create a directory for them to be mounted in:
```
sudo mkdir /mnt/windows
```
And change "/mnt/windows" as appropriate (although keep it in /mnt or /media).
Then, open up the fstab file:
```
gksudo gedit /etc/fstab
```
And add the line:
> /dev/sdaX   /mnt/windows   ntfs   defaults,rw,nodev,nosuid,noexec,auto,user,umask=007,gid=46   0   1
You must change "/dev/sdaX" to the partition that you want to add. If you're not sure of your partition number, type:
```
sudo fdisk -l /dev/sda
```
to find out.
The options "defaults,rw,nodev,nosuid,noexec,auto,user,umask=007,gid=46" can be changed as desired, but you will need the entry "gid=46" so that you can access the partitions as a normal user (since that's the number ID of the "plugdev" group, to which you should be a member of by default).

That's all the problems that I've come across so far. If you still have problems, then leave a comment and I'll try to help.

I'd also be especially grateful for any additions, whether it be for hardware that I don't have or any solutions to any other problems.

---

### Post by l-x-l on 2009-06-08
I have the same laptop except with have a NVidia GPU and in Intel wireless card. I luv it. It's been rock solid. But I have had probs with wireless drops in Jaunty. Didn't have it with Intrepid. 

I never knew about Fn-Esc. Thanks.

---

### Post by kayvortex on 2009-06-09
Yeah, I agree: on the whole, I've been really happy with this laptop and it plays pretty happily with Linux.

I've also been noticing that the wireless connection has been dropping every now and again, too. Most of the time it reconnects, but once in a while I have to manually do it. It seems to be a general jaunty bug since quite a few people have been complaining about it. Someone suggested disabling ipv6, but it's not really all that much of a problem for me that I can really be bothered to look that much into it for now. How much is it happening for you?

Oh, since I didn't opt for (i.e. couldn't afford to get!) the NVidia card, was it any trouble getting it to work (not that I expect it to be, seeing as it's NVidia)? What about the Intel card? Anything special needed to get it working?

---

### Post by smitbr@gmail.com on 2009-06-09
I am using KDE and was unable to get the media buttons on the front to work.  It may be that I have an Inspiron 6000, but I would think that the buttons would work the same way.  They have worked all the way up through Hardy (previous version installed).  Any ideas?

---

### Post by kayvortex on 2009-06-09
The multimedia buttons and have always been a part of the dark arts as far as I'm concerned. The first thing you could try is [lineak]("http://lineak.sourceforge.net/"). I'm not exactly sure what to install for KDE, but it looks like you need to install lineakd, klineakconfig, and lineak-kdeplugins. Then, you'd just have to run:
```
lineakd -c DELL-6000
```
And then edit the file in ~/.lineak to do what you want (I'm not exactly sure myself what goes in there for KDE). Run it in a terminal to see if it works, and then make it load on startup if so. Take a look on their website for examples.
Failing that, there are suggestions around the internet on messing about with keycodes, and the [lineak guide]("http://lineak.sourceforge.net/index.php?nav=showdoc&docid=lineakd_README&doctitle=lineakd README") has some troubleshooting suggestions right at the end, but I've never found anything relevant for the 9400. You might find something for the 6000, though. Apart from that, that's all I can suggest really.

---

### Post by l-x-l on 2009-06-09
> **kayvortex said:**
> Yeah, I agree: on the whole, I've been really happy with this laptop and it plays pretty happily with Linux.

Someone suggested disabling ipv6, but it's not really all that much of a problem for me that I can really be bothered to look that much into it for now. How much is it happening for you?

It happens once maybe twice a day. I've tried all kinds of solutions provided in these forums including disabling ipv6. None have worked. At this point, I've just decided to live with it & hope that the next version will fix the issue.

> **kayvortex said:**
> 
Oh, since I didn't opt for (i.e. couldn't afford to get!) the NVidia card, was it any trouble getting it to work (not that I expect it to be, seeing as it's NVidia)? What about the Intel card? Anything special needed to get it working?
 
I've had absolutely no probs with the GPU. Works great. It used to run really hot until I installed i8k. I basically keep the 2nd fan running all the time so my laptop stays cool.

---

