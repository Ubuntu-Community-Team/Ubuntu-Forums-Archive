---
title: "Ubuntu 8.04 working but cannot connect to wireless network"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-04-27
I have installed Hardy Heron successfully with dual boot with xp media center edition. i can still connect to my wireless network fine in windows(hence why im able to connect here). but  while logged into Ubuntu I cannot access my wireless nor search. I have an Hp Dv6000 laptop and my wireless light is not turning on  to show i have my wlan enabled any suggestions. i really want to succeed in this asap

---

### Post by Ambiguity on 2008-04-27
When I upgraded to hardy I found that my wireless drives were not installed anymore. I downloaded the Atheros drives from [http://packages.ubuntu.com](http://packages.ubuntu.com) to a usb flash drive and installed them manually.

---

### Post by PatrickMoore on 2008-04-27
Many thanks, I'm going to try that right now hopefully I will be talking from my new Ubuntu OS in a new moment

---

### Post by PatrickMoore on 2008-04-27
Im not finding anything that is helping me or looks like it would help me.

---

### Post by PatrickMoore on 2008-04-27
any other suggestions i cant find anything recent about broadcom wireless with hardy heron

---

### Post by everah on 2008-04-27
I just installed 8.04 today and ran across what you did. I followed the instructions at [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/) and was up and running at the next boot.

I just cannot find where the "View wireless networks" screen comes into play.

---

### Post by everah on 2008-04-27
OH HELLS YEAH!

Ok, after following those directions in that link and clicking once on the network icon I was able to select my wireless network and connect to it.

I am writing this now over my wireless connection. Sweet.

---

### Post by NooTooUbuntoo on 2008-04-29
So, here's the deal.  I have a PC that had Vista installed.  One day I got so tired of all of the popups, security measures, the snail-like speed, that I saw a few posts about Ubuntu on Reddit, downloaded it, and installed it.  

The installation went fine, but trying to connect to wireless has been impossible for me.  I went to this url as posted in this thread, [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/), but nothing worked.  In fact, typing the commands into Terminal elicited nothing but error messages.  

My other comp is a Mac, so I assumed that connecting would be as easy as it is there.  I was wrong. 

Are there any newbies out there, completely clueless as to how to use a computer to do anything but connect to the internet, and use MS Office who successfully overcame this issue? 

Thanks!

---

### Post by everah on 2008-04-29
[http://www.robert-gonzalez.com/2008/04/26/going-wireless-with-ubuntu-804-a-broadcom-card/](http://www.robert-gonzalez.com/2008/04/26/going-wireless-with-ubuntu-804-a-broadcom-card/)

Outlines the things I did. There were a few inconsistencies with the article I posted. The steps I followed has me up and running in a few minutes.

---

### Post by DarkRookie on 2008-04-29
Neither of those techniques worked. Any other advise?

---

### Post by everah on 2008-04-29
Do you have an internet connection?

---

### Post by DarkRookie on 2008-04-29
Yes. I am on a ethernet connection as I write this. The little light on my WLAN switch is orange, indicating off.

---

### Post by everah on 2008-04-29
What model card does your computer use? The instructions I posted were for a Broadcom card.

---

### Post by DarkRookie on 2008-04-29
It is a broadcom card. I don't know any details beyond that.

---

### Post by everah on 2008-04-29
So let's start from the beginning and see where things get knackered.

Do you have the build-essential package installed? If not, can you install it?

---

### Post by NooTooUbuntoo on 2008-04-29
> **everah said:**
> So let's start from the beginning and see where things get knackered.

Do you have the build-essential package installed? If not, can you install it?

I have a question.  I cannot connect via ethernet or wireless with Ubuntu.  Can one simply download this build to a mem stick and upload?  None of the commands in Termanl worked for me in this regard. 

Thanks

---

### Post by everah on 2008-04-29
If you have no internet you are going to have to get the files for this in some other way.

The bc cutter app will not be on the Ubuntu installation CDs/DVD (I think, since it is not part of the Ubuntu core OS).

It might be easier to find a wired network connection somewhere that you could plug in to just to handle this part of the setup. 

Seriously, once the wireless card is setup you should be golden after that. But I needed to be wired to the internet in order to do this.

---

### Post by NooTooUbuntoo on 2008-04-29
so I installed the build essential package from system>admin>synaptic package manager after reloading the packages while connected via ethernet, but nothing.  I have the network indicator in the top right corner, but the only options are manual config and edit wireless networks.  the only options there are "wired connection" and "point to point connection".  The location dropdown box is empty. there is no potion to set wireless connections. I am at a loss.

---

### Post by andybob on 2008-04-29
> **NooTooUbuntoo said:**
> so I installed the build essential package from system>admin>synaptic package manager after reloading the packages while connected via ethernet, but nothing.  I have the network indicator in the top right corner, but the only options are manual config and edit wireless networks.  the only options there are "wired connection" and "point to point connection".  The location dropdown box is empty. there is no potion to set wireless connections. I am at a loss.

I am at the same point with mine as well.


Andybob

---

### Post by NooTooUbuntoo on 2008-04-29
> **andybob said:**
> I am at the same point with mine as well.


Andybob

Anyone have any suggestions?  Everything I've seen thus far as far as inputting terminal commands and what not have not worked as advertised in the thread.  I keep getting a "permission denied" error when attempting to use it with certain commands. 

To reiterate, I'm a complete novice when it comes to this stuff; I can count on two fingers the times I've used terminal in windows or mac.  Can having input commands in Terminal at this point, not really knowing what I'm doing, corrupted the OS?  

This is quite a learning experience.

---

### Post by everah on 2008-04-29
If you are getting permission denied errors try prepending the first command with a "sudo " (no quotes).

It may be that you need to have root permissions to install software. After you are in the sudo mode you should have no problem with the rest, but if you do, keep throwing down sudo.

If I am reading right so far, you have the build essential package installed. Now you just need to get the files needed for build and build them. Is that right?

---

### Post by tyblu on 2008-04-29
"build-essentials" just gives you many cpu language libraries, compilers (g++,etc), and probably a few other goodies. It gives you the ability to change many things, but will not fix anything by itself.

Issues with broadcom cards often come up. I kicked mine with ndiswrapper, but my situation may be different with a newer (4.1) macbook.

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by everah on 2008-04-30
build-essential gives you the ability to build the bc cutter driver. That is why you need it. The cutter needs to be "make"ed, then it is used in the last step which is adding the firmware to your system.

---

### Post by DarkRookie on 2008-04-30
build essential installed just fine

---

### Post by everah on 2008-04-30
Ok, so if the build-essential IS installed, try these steps next (each line is a different instruction - if any of these fail, add sudo to the beggining of the line):

This gets the tarball that contains the cutter code
```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
```

This unpacks the code
```
tar xjf b43-fwcutter-011.tar.bz2
```

This takes you into the directory with the source code
```
cd b43-fwcutter-011
```

This compiles the source code
```
make
```

This takes you back to the directory where the tarball lives
```
cd ..
```

This gets the Broadcom wireless driver tarball
```
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
```

This unpacks the tarball
```
tar xjf broadcom-wl-4.80.53.0.tar.bz2
```

This takes you to the directory where firmware that is needed lives
```
cd broadcom-wl-4.80.53.0/kmod
```

This uses the cutter to install the firmware
```
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o
```

Note: For me all of these steps worked without a sude call (until the last step, hence the sudo). This may not be your case. You might have to use sudo right up front or perhaps for every step. Keep that in mind.

On a side note, I created in my home directory a directory for Downloads where all of this is taking place. Not that it matters where the files are, but for clean management of files you may want to contain all of them into the same spot. For me it is **/home/robert/Downloads**.

---

### Post by rxbanditboy1112 on 2008-05-04
In the last line I think you made a mistake in the command...
Shouldn't it be:

```
sudo ../../b43-fwcutter -w /lib/firmware wl_apsta.o
```

That worked for me.

Also I think the thing that completely stumps people is that you need to be connected to the internet before you can receive any of these files, and ironically the very reason they are doing any of this is because the want to become connected to the internet. 

Once I found out i needed a wired connection I reloaded synaptic and installed build essential. Everything was smooth sailing from then on out. Thanks for the help!

---

### Post by everah on 2008-05-04
> **rxbanditboy1112 said:**
> In the last line I think you made a mistake in the command...
Shouldn't it be:

```
sudo ../../b43-fwcutter -w /lib/firmware wl_apsta.o
```

That worked for me.
I think this depends on where you unpack the tarball. Unpacking it without specifying a path unpacks it to the path that I mentioned. But if you what you did worked for you all the better. As long as it worked.

> **rxbanditboy1112 said:**
> Also I think the thing that completely stumps people is that you need to be connected to the internet before you can receive any of these files, and ironically the very reason they are doing any of this is because the want to become connected to the internet. 
You know, it never occurred to be to mention that. Sorry about that. You are indeed correct. In fact I should mention that I was wired to the internet when doing this and it was only after connecting my wireless device that I actually disconnected my wired connection.

---

### Post by Hal Story on 2008-05-10
I am totally new to linux/unix operating systems. Hardy Heron seems to work quire well, except that I cannot get wireless to work. My blue light is on, but Firefox complains that it has no access to the internet.  I tried the instructions above, but I am still not getting it right. I have no idea where to look next.  I really had my hopes up after reading all the positive responses.  Computer is HP laptop zv5227wm, wireless is Broadcom 4306 rev.3. CPU is pentium 4.

---

### Post by everah on 2008-05-10
Have you connected yourself to your wireless network yet?

---

