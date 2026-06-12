---
title: "ok i got a new vid card, and compiz still dount want to work? just my luck!"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by SchindlerShadow on 2008-07-19
ok about 2 min ago i installed a new video card, its a 3DFuzion GeForce FX 5500 256mb. before some1 told me that my on board vid card was not compadable with compiz b/c from support from the vender. but why dose it still say that desktop effects could not be enabled? this is pissing me off, i dount want to go back to micro$oft! help me! :confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by JillSwift on 2008-07-19
Have you activated the restricted driver for your new card? Typically you have to do that to get 3D support, which Compiz needs.

---

### Post by SchindlerShadow on 2008-07-19
yes i did and look at this!

glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

wtf is wrong? o and thanks 4 helping!

---

### Post by arpanaut on 2008-07-19
Did you go into your bios and deactivate your on-board card, then activate the AGP?
And you will need to use the driver from System>Administration>Hardware Drivers.
as said before.

Good Luck

---

### Post by JillSwift on 2008-07-19
This assumes you've followed the above suggestions from **arpanaut** first:
The next step is to reconfigure your X server:```
sudo dpkg-reconfigure xserver-xorg
```Reboot after. This will turn off the restricted driver, so next turn that back on.
Hopefully that will get you squared away.

---

### Post by SchindlerShadow on 2008-07-19
> **arpanaut said:**
> Did you go into your bios and deactivate your on-board card, then activate the AGP?
And you will need to use the driver from System>Administration>Hardware Drivers.
as said before.

Good Luck

2 things, 1 its pci not agp, 2 i did check the bios and it says its using pci as its vid thingy (something like that XD)

sudo dpkg-reconfigure xserver-xorg
[sudo] password for : 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080719211556

give me a min im restarting.

ok it dident do anything diff than it was b4

---

### Post by SchindlerShadow on 2008-07-19
it still dount work XD

 glxgears | grep direct
Xlib:  extension "GLX" missing on display ":0.0".

compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

 glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


sudo apt-get install xserver-xgl
[sudo] password for: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1884kB of archives.
After this operation, 4682kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe xserver-xgl 1:1.1.99.1~git20080115-0ubuntu1 [1884kB]
Fetched 1884kB in 24s (77.9kB/s)                                               
Selecting previously deselected package xserver-xgl.
(Reading database ... 162420 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20080115-0ubuntu1_i386.deb) ...
Setting up xserver-xgl (1:1.1.99.1~git20080115-0ubuntu1) ...

loged out and back in..... still no dice. :(

lspci | grep VGA
00:08.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

hmmmmm........

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

ok can some1 tell me wtf is wrong?????

---

### Post by SchindlerShadow on 2008-07-19
> **JillSwift said:**
> Have you activated the restricted driver for your new card? Typically you have to do that to get 3D support, which Compiz needs.

./compiz-check

 More than one graphics chip detected -- sorry, the script can not handle that.
 Aborting.

???????????????? :confused::confused::confused::confused::confused:

---

### Post by w4ett on 2008-07-19
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

Reboot into your BIOS setup and disable your onboard video chipset...(if you have an older motherboard, this also might entail a jumper setting)....then connect your VGA cable to your new card, boot into Ubuntu, then install the restricted drivers.

---

### Post by arpanaut on 2008-07-19
> ./compiz-check

More than one graphics chip detected -- sorry, the script can not handle that.
Aborting.

???????????????? 

Like I said, Somewhere in your BIOS you need to disable the on-board graphics.
The error above indicates two cards active, and is probably the reason that the restricted driver is not installing right.
Do some searching on the forums, seems there may be some issues with your video card, and I have noticed VIA chipsets can be iffy with Linux setups too.

But I think the main stumbling block is the onboard video still being activated.

---

### Post by SchindlerShadow on 2008-07-19
> **arpanaut said:**
> Like I said, Somewhere in your BIOS you need to disable the on-board graphics.
The error above indicates two cards active, and is probably the reason that the restricted driver is not installing right.
Do some searching on the forums, seems there may be some issues with your video card, and I have noticed VIA chipsets can be iffy with Linux setups too.

But I think the main stumbling block is the onboard video still being activated.
in the bios onbord video can only be changed to auto, 8mb 16mb 32mb and 64mb what do i do?? and what is onbord 1394?? btw i have an hp paivlion a635w.

---

### Post by SchindlerShadow on 2008-07-19
> **arpanaut said:**
> Like I said, Somewhere in your BIOS you need to disable the on-board graphics.
The error above indicates two cards active, and is probably the reason that the restricted driver is not installing right.
Do some searching on the forums, seems there may be some issues with your video card, and I have noticed VIA chipsets can be iffy with Linux setups too.

But I think the main stumbling block is the onboard video still being activated.
i cant! in the bios onbord video can only be set to auto, 8mb 16mb 32mb 64mb! what do i do? whats onbord 1394? im useing an hp pavilion a635w.
sorry 4 dubller post XD

---

### Post by zipperback on 2008-07-19
> **SchindlerShadow said:**
> 
lspci | grep VGA
00:08.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


Reboot your system. Go into your bios and **DISABLE** the on board video.

Save the changes and then reboot your system.

Once you have done that, log back into your system and provide the output of:

[code]
lspci
[/quote]

Thank you
-zipperback
:popcorn:

---

### Post by SchindlerShadow on 2008-07-20
> **zipperback said:**
> Reboot your system. Go into your bios and **DISABLE** the on board video.

Save the changes and then reboot your system.

Once you have done that, log back into your system and provide the output of:

[code]
lspci


Thank you
-zipperback
:popcorn:
read my last post..... it dosent give me that option!

---

### Post by w4ett on 2008-07-20
> **zipperback said:**
> Reboot your system. Go into your bios and **DISABLE** the on board video.

Save the changes and then reboot your system.

Once you have done that, log back into your system and provide the output of:

[code]
lspci

The onboard video disable toggle is probably under "advanced options" or "chipset options" depending on the bios manufacturer.....

I also did some research on your motherboard, (most probably a Gigabyte...or bit as the case may be) and some proprietary branded boards autodetect only AGP cards, not PCI.  Yours may be one of those.

---

### Post by arpanaut on 2008-07-20
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=425875&docname=c00007413](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=425875&docname=c00007413)

this is a link to a manual on HP's site, See Item #6
the control for the primary video adapter is under the advanced tab of the bios, looks like a toggle between onboard and PCI

hope this helps.

---

### Post by SchindlerShadow on 2008-07-20
> **arpanaut said:**
> [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=425875&docname=c00007413](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=425875&docname=c00007413)

this is a link to a manual on HP's site, See Item #6
the control for the primary video adapter is under the advanced tab of the bios, looks like a toggle between onboard and PCI

hope this helps.
yes it is a troggle, it says PRIMEARY video "pci" i can change it to onbord/AGP

---

### Post by SchindlerShadow on 2008-07-20
> **arpanaut said:**
> [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=425875&docname=c00007413](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=425875&docname=c00007413)

this is a link to a manual on HP's site, See Item #6
the control for the primary video adapter is under the advanced tab of the bios, looks like a toggle between onboard and PCI

hope this helps.
yes its a troggle, it says PRIMEARY video "pci" i can change it to onbord/AGP, and yes its in adv but as i seaid erler it doesent eive me that opton. oh and btw thats not what my bios look like. XD

opp srry XD

---

### Post by arpanaut on 2008-07-20
Well that sucks,,,
I'm outa ideas.
Sorry

---

### Post by jimv on 2008-07-20
I (almost) guarantee that this will fix the problem.  Use Envy to install the drivers.

To get Envy, open a terminal and type:

sudo apt-get install envyng-gtk

Then run this command:

envyng -t

Enter your password and press 1.  Let the program do it's thing and then restart.  Compiz should work at this point.

---

### Post by SchindlerShadow on 2008-07-20
> **arpanaut said:**
> Well that sucks,,,
I'm outa ideas.
Sorry
well this isent the thing, its that compiz wont work! and do u guys know the dell gx27 capasater problom? well the comp (my other 1 not the 1 w/ the vid pci chip) go to black screen of death when it uses its vid chip to the fullest, like when useing compiz.... any way, do u think that if i put this pci vid chip in it itll stop going to the black screen of death?

---

### Post by SchindlerShadow on 2008-07-20
> **jimv said:**
> i (almost) Guarantee That This Will Fix The Problem.  Use Envy To Install The Drivers.

To Get Envy, Open A Terminal And Type:

Sudo Apt-get Install Envyng-gtk

Then Run This Command:

Envyng -t

Enter Your Password And Press 1.  Let The Program Do It's Thing And Then Restart.  Compiz Should Work At This Point.

Omg Omg Omg I Love U!! It Works!!!!!!!!!!!!!!!!!!!!!!! Thank You So Much!!!! U Dount Know How Long Iv W8ted!! :ks:ks :ks :ks :ks :ks :ks :ks :ks :ks :ks :ks :ks :ks :ks

OH BTW DOSE ANY1 KNOW WHERE I CAN FIND ALL OF THE COMPIZ KEYBORD SHORTCUTS?? SORRY 4 THE CAPS! LOL!!

---

### Post by Canis familiaris on 2008-07-20
> **SchindlerShadow said:**
> 
OH BTW DOSE ANY1 KNOW WHERE I CAN FIND ALL OF THE COMPIZ KEYBORD SHORTCUTS?? SORRY 4 THE CAPS! LOL!!

compizconfig-settings-manager

I can list a few:
Ctrl+Alt+Hold Left Mouse Button = Move the Cube
Ctrl+Alt+Right/Left Cursor Keys= Move the Cube
Alt+Shift+Up Key = Show all open Windows (Scale)
Super + E = Expose (Easily move your Windows from one workspace to another)
Ctrl+Alt+Up = Switch b/w Workspace (another way)
Win + Tab = Switcher

---

### Post by akaalias on 2009-04-23
Hi. I seem to have a similar problem. same card, too. I gave envy a try, but when i run it to install NVIDIA-driver, I get this:

EnvyNG - Version 1.1.1
Traceback (most recent call last):
  File "interface.py", line 17, in <module>
    objects.mainmenu()
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 622, in mainmenu
    menu1.process()
  File "/usr/lib/python2.5/site-packages/Envy/interfaceclasses.py", line 55, in process
    objects.nvinstconfirm()
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 521, in nvinstconfirm
    confirmation.gotoop = nvidiainstall()
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 306, in nvidiainstall
    compat = compatible.check()#COMPATIBILITY CHECK
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 690, in check
    raise Exception(error)
**Exception: EnvyNG ERROR: Nvidia card not found**


Does anyone have some ideas here?

---

### Post by akaalias on 2009-04-23
for the record: 

sudo lshw -C video

gives:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2

---

