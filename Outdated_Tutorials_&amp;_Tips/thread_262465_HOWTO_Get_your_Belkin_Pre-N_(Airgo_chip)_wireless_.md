---
title: "HOWTO: Get your Belkin Pre-N (Airgo chip) wireless card working with Dapper"
date: 2006-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Danni on 2006-09-21
This has been tested with Kubuntu Dapper Drake and a Belkin Pre-N card (F5D8010uk). It probably will work with the other cards that use the same chipset, but I have no way of checking. This is my first how to, so feel free to correct me :)

OK. For this card you need to use ndiswrapper, but the version that comes with dapper doesn't work properly. It gets as far as finding the access point, then doesn't let you get an IP address using DHCP or connect with a static address.

What you need is newest version of ndiswrapper. The version I used is 1.23, and it is available to download at [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) 

I'm now going to shamelessly copy the instructions on what to do from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), as that is what got mine working.

For this, I'm assuming you can have some internet access while you get your wireless working, probably with a cable. If not, I'll try and figure out how you can get them from another computer at some later date, but you will need some internet access for this to work.

First of all we need to install some kernel headers. Why I'm not sure, but when I didn't do it nothing else worked.

From terminal, konsole or whatever you use, type this:
```

sudo apt-get install linux-headers-$(uname -r)

```

You also need to install ndiswrapper's dependencies, and the stuff to make it compile. Again in the terminal, run:
```

sudo apt-get install dh-make fakeroot gcc-3.4 build-essential

```

Right then, now that's done it's time to download ndiswrapper. Download it [here](http://sourceforge.net/projects/ndiswrapper/), then in the terminal change your directory to where it is (using the cd command if necessary).

Next, run these commands (you can press tab after the first few letters of the filename instead of typing it all out):
```

tar xvfz ndiswrapper-[current version].tar.gz
cd ndiswrapper-[current version]

```

Replace [current version] with the version you're using (such as ndiswrapper-1.23) or just press tab after typing a few letters.

Next up we get to do some compiling! Don't worry, this isn't hard as we installed all the dependancies earlier on. In your terminal again, run:
```

sudo make uninstall

```
If you get an error with this about not being able to remove it because it's a directory, run this:
```

rm -r path/to/the/directory/it/can't/remove

```

Make sure it's only the directory it was complaining about though- you don't want to be removing something you shouldn't. Then run the sudo make uninstall again.

Once you get no errors with the make uninstall, run this:
```

sudo make

```
Then run this (I don't know why you run fakeroot, but it works so I'm not arguing):
```

fakeroot
sudo make install

```
Hopefully you shouldn't get any errors. If you do try running the commands again.

Once that's all sorted, it's time to install your driver. You need the one from [here](http://kbserver.netgear.com/products/WPNT511.asp).

Unzip the drivers, and note where they're installed. In terminal change to that directory (mine was 
/home/username/wpnt511_v1104/Utility/Driver but yours could be different) and then run:
```

sudo ndiswrapper -i NETANI.INF

```
That should install the driver. Next we check that everything there has worked ok:
```

ndiswrapper -l

```
With luck it should show:
```

Installed drivers:
netani          driver installed, hardware present

```

Next up we have to load the ndiswrapper module.
```

sudo depmod -a
sudo modprobe ndiswrapper

```
We now check for error messages.
```

tail /var/log/messages

```
No errors? Great! It should now work properly. Just to be sure, check that ifconfig and iwconfig show your wireless card. If they don't, try a restart (mine didn't show till after I'd restarted and modprobe ndiswrapper again). 

With luck you should now be able to connect to your network. The quickest way (for me) was to run these commands:
```

sudo ifconfig wlan0
sudo iwlist scan
sudo iwconfig wlan0 essid [mynetworkessid]
sudo dhclient wlan0

```
If you have security set up on your network, you will have to set that up as well, but that's covered elsewhere.

Hopefully you now have a working wireless card! If I've made any mistakes/missed anything out/it's not clear don't hesitate to yell at me. Any suggestions are also appreciated. If you need help you can always ask, but I'm still quite new to linux so may not know the answers.

Hope this helps,

Danni

---

### Post by T-AA on 2006-11-01
thx very much worked like a charm

---

### Post by wyth on 2006-12-03
Great googly-moogly!  I've had one of these cards for over a year, and couldn't get it to work on a Linux machine, and won't connect to the secure network at my university.  

But this guide, man, it worked in seconds.  I'm so impressed; a nice, fast card working perfectly with Edgy.  I'm a happy user.

---

### Post by x-tomek on 2006-12-28
Thanks very much, worked for me as well (Netgear WPNT511). This is the first and only how-to I've come across so far for configuring Airgo (TrueMIMO 3 gen) based cards.

You might want to consider adding that [FONT="Courier New"]*ndiswrapper*[/FONT] should be added to [FONT="Courier New"]*/etc/modules*[/FONT] so the kernel module is loaded at boot time.

Another area is [FONT="Courier New"]*/etc/network/interfaces*[/FONT] - likely will have to be edited, particularly if wpa_supplicant is used. I'm new to desktop Linux and Ubuntu - just about to try to configure WPA2 :-k ([http://joncellini.com/blog/archives/2005/12/28/howto-wpa2-under-ubuntu-510-with-a-wpc54g-v3-broadcom/](http://joncellini.com/blog/archives/2005/12/28/howto-wpa2-under-ubuntu-510-with-a-wpc54g-v3-broadcom/) is good but outdated) 

What encryption do you use with Belkin, and did you manage to configure it?

---

### Post by saracen on 2007-03-31
I have a Belkin Pre-N Wireless PCMCIA card (model # F5D8010) that I can't get to work on Edgy or on Feisty.  I've followed the steps in this tutorial but instead of downloading and compiling the ndiswrapper source I've installed the ones in the Feisty repositories (version 1.38 ).  I downloaded the driver and installed it successfully using the "ndiswrapper -i" command.  Now when I do "ndiswrapper -l" this is what I get:```
saracen@acer:/etc$ ndiswrapper -l
netani : driver installed
        device (17CB:0001) present
```
Then I run depmod and that works fine, but when I go to load the module it complains:```
saracen@acer:/etc$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```
Does anyone know what the problem is here?

---

### Post by wyth on 2007-04-06
Hi Saracen,

I recently upgraded to Feisty and had some networking issues, so I did the same as you -- installed the repository ndiswrapper. And I'm having the same issue -- fatal error inserting ndiswrapper when I modprobe it.  Did you get a fix on this?

---

### Post by wyth on 2007-04-06
Okay, here's how to get the standard Feisty ndiswrapper working:

First, if you used the above method to install ndiswrapper from sourceforge, you may want to remove everything, just to be safe.  [See the instructions here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall").

Second, at the command line, do the following:

```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```


[Grab the drivers if you don't have them]("http://kbserver.netgear.com/products/WPNT511.asp").  Then install:
```
sudo ndiswrapper -i NETANI.INF
```

Check to see if it installed:
```
ndiswrapper -l
```

You should see something like:
```
netani : driver installed
        device (17CB:0001) present
```

Load up the module:
```
sudo depmod -a
```

NOW: To get modprobe to work, need to use module-assistant:
```
sudo module-assistant prepare
sudo module-assistant auto-install ndiswrapper
sudo modprobe ndiswrapper 
```

Make sure you have ndiswrapper in /etc/modules

Reboot and enjoy your wireless.


Note: I tried the latest version on sourceforge, to no avail.  That was 1.41.  The Feisty one is 1.38, which works perfectly well.  In fact, it seems to be working better on Feisty than it did on Edgy (when I compiled it).

---

### Post by Pedda on 2007-04-07
I tried your guide and it worked, once.

I connected the computer to the wireless network at school and it worked. I turned the computer off and went home.

When I restarted my laptop at home the pc-card is dead. No lights are flashing. Networkmanager just shows a wired connection, no option with wireless.

According to ```
ndiswrapper -l
``` my card is there, but not according to anything else in the computer. What do I do now?
```

netani : driver installed
        device (17CB:0001) present

```

---

### Post by wyth on 2007-04-08
Which guide did you try, Danni's or mine?  (I submitted a new guide as a HOWTO, but it seemed to disappear as soon as I submitted it.)

If you used mine, try this: Right-click on network manager and disable networking, then remove the card.  Put the card back in, right-click on network manager and enable networking, and see if that helps.

I have WPA on my home network and have this happen sometimes.  Stopping everything and re-firing up the networking seems to help (at last for me).

---

### Post by wyth on 2007-04-08
A full Belkin Pre-N Feisty guide is now [available here]("http://ubuntuforums.org/showthread.php?t=402954&highlight=Belkin+Pre-N").

---

### Post by Pedda on 2007-04-09
It worked after I had rebooted and removed the card, then rebooted it once more and then finally rebooting with the card in.

I don't know why, but I haven't hade any problems since.

Thanks anyway

---

### Post by euphro on 2007-04-25
In Feisty, for the Netgear WPNT511 (which uses the same chipset), I followed the instructions above, but I found that I needed to install the other unpacked driver (tmimo3P.inf).

This was on a Toshiba Satellite 4030 CDT.

I did this via "sudo ndiswrapper -i tmimo3P.inf" and by forcing ndiswrapper to use the device id 17CB:0002.

Forcing ndiswrapper to use the device id is achieved with "sudo ndiswrapper -a 17CB:0002 tmimo3p.inf" (note lower case "p" in the command, which differs from the upper case "P" in the unpacked .inf  filename).

After rebooting, and then stopping and restarting the card in "Applications>system>network" it all seems to be working fine.

---

### Post by Pedda on 2007-04-27
I did what you did, but it doesen't work for me. I've got an Compaq Evo N410c, but that shouldn't matter right?

```
pedda@pedda-laptop:~/Driver$ sudo ndiswrapper -i tmimo3P.inf
installing tmimo3p ...
pedda@pedda-laptop:~/Driver$ sudo ndiswrapper -a 17CB:0002 tmimo3p.inf
ls: /etc/ndiswrapper/tmimo3p.inf/: Filen eller katalogen finns inte
driver 'tmimo3p.inf' is not installed (properly)!
```

---

### Post by wyth on 2007-04-27
I don't know if this will help you all or not, but I started [a new thread on this specifically for Feisty]("http://ubuntuforums.org/showthread.php?t=402954").  There's a few different steps, and it may help you.

(Although I'm back on Edgy; couldn't get Feisty to connect to any secured networks.)

---

### Post by jnorris235 on 2007-06-15
I spent so many hours trying to get ndiswrapper to work that I just gave up with Dapper.
Thinking Feisty might be better I tried again.

Thank you (and I DO mean that!) to this guy for taking the time to try to help.
But...
Yet again - failure.

I went to get that package as he suggested. Unzipped it.
In console drilled to the Driver folder and typed
sudo ndiswrapper -i netani.inf
and I get
driver netani already installed

Then
ndiswrapper -l
and I get
invalid driver

I was doing this online of course but then wondered if you had to have the actual hardware in place before installing the drivers.
So went off line, switched the network card and back to Terminal - same results.

I.m trying to use a Belkin Wireless Pre-N Notebook Network Card in the little frame that holds it, in my Desktop. Part FSD8010

Any ideas - desperately need the preN to drive through stone walls!

---

### Post by wyth on 2007-06-15
I don't know if this will help or not, but I recently upgraded to Feisty, and didn't download ndiswrapper at all; it used the previous one already installed, and just worked after the upgrade.  You may try using the ndiswrapper in the repositories; it's pretty much up to date (I used an earlier version on Edgy that worked).  

If it's not taking, though, you may want to purge any past ndiswrapper and netani.inf instances and try it completely fresh; perhaps there's a conflict. 

I did all this on a notebook, not a desktop.  I know the card is the same, but I don't know if the frame the card sits in creates some block that requires a different driver.

---

### Post by lattemonster on 2007-09-07
Hello,

I was unsuccessful at installing Unbuntu (any version) on an old Dell Inspiron 3500 machine so I installed Debian instead.  I thought Ubuntu and Debian were practically the same thing.  I have a Pre-N (Airgo chip) wireless card and am trying to get it working on Debian but have been unsuccessful.  Has anyone tried this with Debian?

Anyone?

Thanks!

Lattemonster

---

### Post by oz-2 on 2007-09-18
Dear Danni

Thanks v much for your how to - most difficult bit was obtaining the pre-n driver from netgear as the link does not take you to the driver download page, and indeed its seems to not be there as described.  My local pc shop guru found it for me.

My further question is this, if you don't mind answering:

How do I get ndiswrapper to load on boot automatically?

How do I get the network wep key to be remembered?

thanks for you help

David:confused:

---

### Post by mgaravelli on 2007-10-06
Hi, I have just installed Ubuntu 7.04 Feisty Fawn in dual boot with XP which i already had in my notebook. I'm able to browse the internet and my home network via ethernet cable but i can't get my Belkin wireless pre-n network card working, it doesn't even light on.
I've installed ndiswrapper and tried to install the windows drivers for this card; this is what i did:
[LIST]
[*]I've downloaded the Netgear drivers (same chipset)
[*]I've unzipped them in a folder on the desktop
[*]I've opened the terminal and typed: sudo -i home/marco/Desktop/wifi/Utility/Driver/NETANI.INF
[*]At this point when I type "ndiswrapper -l" on the terminal the response I get is "netani : invalid driver! as well as after installing "tmimo3p.inf" and "autorun.inf";
[/LIST]
What shall I do now?

---

### Post by radar654 on 2007-10-23
:confused: sorry for a stupid :( question but just I dont understand to the notification UK (like in F5D8010uk)? I could find two models of Belkins with this uk notification.. I need a wifi card for my laptop for travelling internationally.

---

### Post by S4T4N4S on 2007-12-12
Hello,

I've the same problem and have solved with the instructions in this site:
[http://welcometoubuntu.blogspot.com/...i-enabled.html](http://welcometoubuntu.blogspot.com/...i-enabled.html)

... but with the Belkin original drivers found in the CD.

I've uploaded the files here:
[http://77.91.202.10/~alpoimco/Satana...n_pre-n.tar.gz](http://77.91.202.10/~alpoimco/Satana...n_pre-n.tar.gz)

If you follow the instructions change this instruction:
sudo ndiswrapper -i tmimo3P.inf

to ...

sudo ndiswrapper -i NetAni.inf

Hope you solve your problem too...

Sat

---

### Post by wyth on 2007-12-30
Sat's links are broken.

Here's for the first one ( [http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html))

And for the Belkin drivers:
Link #1: [http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz]("http://77.91.202.10/%7Ealpoimco/Satanas/belkin_pre-n.tar.gz")
Link #2: 
[http://www.someawe.com/uploads/belkin_pre-n.tar.gz](http://www.someawe.com/uploads/belkin_pre-n.tar.gz)

But to make it easier, I attached the tar.gz file of the Belkin drivers to this post.

I'm curious about the ndisgtk addition.  I installed it, but found absolutely no use for it.

---

### Post by justinmiller87 on 2008-02-24
Just to let you know, I updated the link above me (also in my sig) to reflect the information. Try that out if you are having issues. The guide works for Edgy through Gutsy and has online and offline instructions.

[HOWTO: Get Airgo-Based WiFi Enabled Using ndiswrapper](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

---

### Post by ThomasRahl on 2008-09-11
Thanks for the tutorials. I've been wrestling with Ubuntu 8.04 and my Netgear WPNT511 since last Wednesday trying to figure out piece by piece what's wrong. It took me a good while to figure out I didn't have build-essential installed, but now I can't get the wireless card to show up in the right places. I tried installing the drivers from the cd, and when they didn't work I used the ones linked in Justin's tutorial. They both install just fine:

ndiswrapper -l
netani : driver installed

But I can't seem to get the hardware to say it's present. It shows up when I enter

lspci -nn
03:00.0 Ethernet controller [0200]: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card [17cb:0002] (rev 01)

I notice now this is slightly different than the output at the start of your howto. Is it so different that my card just won't work? I followed all the directions in Justin's tutorial, so now I'm stuck. How can I give it that last kick in the pants to get it to turn on? I'm getting tired of being chained to the desk :) Thanks.

---

### Post by networkproblems on 2009-05-28
Thanks for the tuts; they work great. The only problem I have now is that I can't standby or hibernate with my wireless card enabled. Anyone know how to fix this?

---

