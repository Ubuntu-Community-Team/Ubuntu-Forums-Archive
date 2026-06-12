---
title: "[SOLVED] How to actually enable restricted drivers."
date: 2008-10-31
forum: New to Ubuntu
---

### Post by GreyArea2 on 2008-10-31
I have just upgraded to Ubuntu 8.10. I am in desperate need of hardware drivers for my graphics card. I have a 8800 GTS 640MB. 

I go to hardware drivers, and hit activate, and enter my password. A progress bar comes up, completes... and nothing happens. The drivers do not enable.

So how do I tell my computer to actually use the drivers?

I have minimal experience with Linux, so please be specific. And nothing risky, please. I've only upgraded because I screwed up my 8.04 install so bad it barely booted. ;)

---

### Post by sharkster2007 on 2008-10-31
I have a similar problem with a Nvidia 6600GT I have a thread at [http://ubuntuforums.org/showthread.php?t=964375](http://ubuntuforums.org/showthread.php?t=964375) 

I believe we need the "propriety" drivers as the "open source" don't support 3D.

I too have the activation problem the drivers are in place and confirmed but the hardware drivers do not activate.

---

### Post by GreyArea2 on 2008-10-31
Well, it's nice to know I'm not alone. Strenght in numbers, right? :)

Anyway, I rebooted, and tried to activate them again. Same deal: it acts like they're going to activate, but ultimately, it never truly activates them. Still a grey dot next to my driver.

Isn't this the kind of problem beta testing is supposed to fix?

---

### Post by sharkster2007 on 2008-10-31
Thats what I was thinking too greyarea2

We are both brand new, I have located the website and drivers I think we need on my thread. I have the same issue: Acts like its going to activate, Never does. still a grey dot next to my driver too.

Like you I have the Ubuntu 8.10 (Final) I too think this may be a bug. I'd settle for a command line to activate the blasted thing manually as long as it worked.

Hopefully together we will get this resolved. ;-)

---

### Post by GreyArea2 on 2008-10-31
Well, I'm trying something right now, but my internet is soooooo sloooooowwww. I'll probably have to make a thread about that later. 

Initial impression of 8.10: not good. :-?

---

### Post by sharkster2007 on 2008-10-31
Me too Greyarea2

I may downgrade back to 8.04LTS and try again on that,on this issue Ubuntu 8.10 seems to be more of a "downgrade" than "upgrade" to me.

I am not impressed at all, they are supposed to be making improvements to this easier not harder for new users. Many other 8.10 users have this problem an I fear that the new x system that has been implemented in the new version has sacrificed previous 3D compatibility with nvidia cards.

Not good at all (Definately not the way forward) :-(

I keep checking back, If i get a solution i'll let you know good luck, I think we need it on this one :-(

---

### Post by Sealbhach on 2008-10-31
Hi, try this command to enable the driver from the command line:

```
sudo nvidia-glx-config enable
```


.

---

### Post by GreyArea2 on 2008-10-31
The output is as follows:

sudo: nvidia-glx-config: command not found

Thank you for your post, though. Any help is always appreciated.

---

### Post by forger on 2008-10-31
[http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/appendix-a.html)
>  GeForce 8800 GTX
 0x0191

GeForce 8800 GTS
 0x0193

GeForce 8800 Ultra
 0x0194

GeForce 8800 GTS 512
 0x0600

GeForce 8800 GT
 0x0602

GeForce 8800 GS
 0x0606

GeForce 8800M GTS
 0x0609

GeForce 8800M GTX
 0x060C

GeForce 8800 GS
 0x060D

GeForce 8800 GT
 0x0611


Reply with the the output of this command in terminal:
```
lspci -nn | grep -i nv
```

---

### Post by GreyArea2 on 2008-10-31
Got it! :)

Here's my fix:

- Go to System > Administration > Software Sources

- Go to the Third-Party Software tab

- You should see 2 checkboxes; check both.

- Go to System > Administration > Update Manager

- Check for and apply updates. This will take awhile. I reccomend a good book to pass the time. :)

- Now try again to activate the drivers. If your problem is the same as mine, it should now work.


EDIT: My apologies, forger, you posted while I was typing my post, so I didn't see your message. Here's the output, if you're still interested:

00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
00:07.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03bb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [GeForce 8800 GTS] [10de:0193] (rev a2)

---

### Post by forger on 2008-10-31
:confused: Which two checkboxes are you talking about? :confused:
What are they saying?

---

### Post by diablo75 on 2008-10-31
> **GreyArea2 said:**
> Got it! :)
- You should see 2 checkboxes; check both.


Just curious, but what words were next to the check boxes?

---

### Post by forger on 2008-10-31
> 01:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [GeForce 8800 GTS] [10de:[COLOR="Red"]0193[/COLOR]] (rev a2)

Cool: **0193** -> 0x0193 - > GeForce 8800 GTS -> supported by **nvidia-glx-[COLOR="Red"]177[/COLOR]** ;)

If you didn't get it fixed, go to the terminal and type:
```
sudo apt-get install nvidia-glx-177 nvidia-settings
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig
```

Reboot your computer, login, then execute this:
```
gksu nvidia-settings
```
"X Server Display Configuration" > Click "Detect displays", choose your resolution, click "Save to X configuration file" and click Quit

reboot once more :)

---

### Post by Sealbhach on 2008-10-31
> **forger said:**
> :confused: Which two checkboxes are you talking about? :confused:
What are they saying?

He means Third Party Software sources. They had not been added - so that fixed his problem.


.

---

### Post by crjackson on 2008-10-31
> **forger said:**
> :confused: Which two checkboxes are you talking about? :confused:
What are they saying?

Seems he just needed to enable the additional repositories that pull in the needed restricted drivers. This isn't unique to 8.10

---

### Post by GreyArea2 on 2008-10-31
So... I did what? Sorry, but could you explain what it is I did in layman's terms? I'd like to get better at using Linux and Ubuntu, and this seems important.

---

### Post by sharkster2007 on 2008-10-31
Glad you got there Greyarea2 

Well done, I too would like to know what the particular files where? As I am not on the internet and use another pc to download my files and install manually from USB drive.

I know I am trying the hard way but I don't really have another option :-(

---

### Post by Sealbhach on 2008-10-31
> **GreyArea2 said:**
> So... I did what? Sorry, but could you explain what it is I did in layman's terms? I'd like to get better at using Linux and Ubuntu, and this seems important.

To make the drivers available to download you had to open up the channels for them - in other words make available the repositories where these drivers are kept.

You did that by ticking those extra Third Party software sources. 


.

---

### Post by crjackson on 2008-10-31
> **sharkster2007 said:**
> Glad you got there Greyarea2 

Well done, I too would like to know what the particular files where? As I am not on the internet and use another pc to download my files and install manually from USB drive.

I know I am trying the hard way but I don't really have another option :-(

You should connect the problematic Ubuntu PC to the internet for a few minutes if possible. I posted the rest of what you should do in Your thread about the same problem.

---

### Post by sharkster2007 on 2008-10-31
[COLOR="Lime"]NONE INTERNET CONNECTED USERS: MANUAL SOLUTION[/COLOR]

6th November 2008 UPDATE

Previous posted "Manual Solution" instructions have been removed, by myself a better more easy to use guide for Ubuntu 8.10 beginners is available at My new thread: 
[http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038) 

It contains details of how to manually download, install & Activate Nvidia 173 or Nvidia 177 Drivers, compizsettings (Inc. Minor Troubleshooting)& Nvidia settings. Hope it helps :-)

Sharkster2007

---

### Post by sharkster2007 on 2008-10-31
Hey Greyarea2

Well done my friend, I have now sussed the manual way to do it to hope this helps you. 

The 3 green high-lighted files are all you need to enable it manually, so if you want to back them up to cd these are the ones to back up. 

We did it together 2 new linux users and a brilliant Linux community.

You now have both ways of doing it

PS My card is a Nvidia 6600GT (AGP) Version

PENGUIN POWER

---

### Post by jhenager on 2008-11-01
00:0d.0 VGA compatible controller [0300]: nVidia Corporation GeForce 6150SE nForce 430 [10de:03d0] (rev a2)

This integrated graphics controller was working great in 8.04.
Following the instructions, I get this from sudo nvidia-xconfig:

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a
                  Driver line.
This whole section is missing from my xorg.conf.

---

### Post by Sealbhach on 2008-11-01
> **jhenager said:**
> 00:0d.0 VGA compatible controller [0300]: nVidia Corporation GeForce 6150SE nForce 430 [10de:03d0] (rev a2)

This integrated graphics controller was working great in 8.04.
Following the instructions, I get this from sudo nvidia-xconfig:

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a
                  Driver line.
This whole section is missing from my xorg.conf.

This is the Device section in mine:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"

```

You could try appending that to your xorg.conf. 

Also, this thread is marked solved so to get more responses you should start a new thread.


.

---

### Post by stonecoldjha on 2008-11-01
you can also go for installing envy,open a terminal and type:

sudo apt-get install envyng-gtk

after it is installed,type sudo envyng -t
this would initiate a text only interface,follow the instructions,as they are damn easy,install the 177 driver,and reboot.

i had the same issue,but i could solve it this way.

---

### Post by jhenager on 2008-11-02
Thank you and Stonecold. Being the impatient type, I did a clean install of Intrepid, and that did the trick.
I can only burn so many hours before I give up and use the sledgehammer approach.

---

### Post by ogee on 2008-11-02
Opening up the 3rd party repositories cured my nVidia problems. Thanks .

---

### Post by dustybrown on 2009-01-19
> **GreyArea2 said:**
> So... I did what? Sorry, but could you explain what it is I did in layman's terms? I'd like to get better at using Linux and Ubuntu, and this seems important.

I just installed 8.10 on my laptop today.  Earlier, I booted from the disc and ran the operating system just to play around.  I got the wireless working with the B43legacy driver by activating it in the hardware manager.  No problems.  

So, I decided to install the program.  Once installed on the hard drive, I couldn't get the hardware drivers GUI to show the B43legacy driver that I needed.  I've been searching the web for three hours trying to figure out how to activate that driver.  

I followed what you said by checking those two boxes.  30 seconds later the driver shows up in the hardware driver GUI.  

Thanks!

---

