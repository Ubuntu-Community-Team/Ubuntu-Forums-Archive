---
title: "I installed Ubuntu, now I'm lost, pls help"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by makewayhomer on 2008-06-24
so I installed Ubuntu to dual boot with XP on an old laptop. that went mostly smooth, as I can now boot into either.

in ubunto, the mouse and keyboard work as does the wired internet connection. however, the wireless card doesn't work out at all, and the resolution on the monitor is messed up. I guess I need to install drivers, but have no idea how to go about doing that. where do I find them? what do I do once I find them? I have no idea what terminal windows or kernels are or to change directories or anything like that.

fyi I have a Toshiba Satellite 1405-S151

tyia

---

### Post by bumanie on 2008-06-24
Wireless, I probably can't help with. To improve your graphics, go to System --> Administration --> Hardware Drivers and enable the graphics driver there. Most gpu's are supported by ubuntu.

---

### Post by superprash2003 on 2008-06-24
for wireless.. go to the terminal and type iwconfig and post output here

---

### Post by Methuselah on 2008-06-24
Try System->Preferences->Screen Resolution to see if you can set a better resolution there.

---

### Post by makewayhomer on 2008-06-25
> **superprash2003 said:**
> for wireless.. go to the terminal and type iwconfig and post output here

thanks, this is what I got:

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by makewayhomer on 2008-06-25
> **Methuselah said:**
> Try System->Preferences->Screen Resolution to see if you can set a better resolution there.

the highest option I get is 800x600, which is the problem. I know the resolution can go higher, but the option to set it that high is not there

---

### Post by Canis familiaris on 2008-06-25
Which graphics card are you using?

---

### Post by Tomatz on 2008-06-25
<snip>

---

### Post by Canis familiaris on 2008-06-25
> **Tomatz said:**
> Open the restricted drivers manager in ***System, Administration, Restricted Drivers Manager*** and install your restricted drivers. Your wireless card drivers may be in there.

Isn't that changed to System->Administration->Hardware Drivers in Hardy?

---

### Post by Tomatz on 2008-06-25
> **Anurag_panda said:**
> Isn't that changed to System->Administration->Hardware Drivers in Hardy?

Yup :)

My bad.

---

### Post by Tomatz on 2008-06-25
Open the restricted drivers manager in ***System, Administration, Hardware Drivers*** and install your restricted drivers. Your wireless card drivers may be in there along with your graphics drivers.

---

### Post by immortal_asim on 2008-06-25
can also configure ur x server to check/improve resolution

kill the xserver  by ctrl+alt+backspace

ctrl+alt+f1 will drop u to a commandline 
now type in:-
             sudo init 3
             sudo Xorg -configure

the file x.org.conf.new should appear in ur directory
type the following to test start the serevr

sudo X -xf86config /root/xorg.conf.new  

if this works then back up ur earlier file and copy this one to
/etc/X11/xorg.conf

by commands like this one:-
#cp /root/xorg.conf.new /etc/X11/xorg.conf

[FONT="Arial Black"][COLOR="Red"]make sure to back up ur xorg.conf file at /etc/X11 [/COLOR][/FONT]

---

### Post by immortal_asim on 2008-06-25
use synaptics package manager for installing softwares and drivers

system-> administration->synaptic package manager

---

### Post by cespinal on 2008-06-25
For the screen resolution, you just have to download the drivers for your graphic card. 

For wireless, maybe you need to install NDISWRAPPER, do a little search on the forums on this topic. 

Don't panic, you are just passing trhough a very common phase when installing ubuntu for the firts time. You will get to solve it. 

cheers.

---

### Post by makewayhomer on 2008-06-25
wow, thanks for the help everyone.

re: the resolution, I found another thread [here]("http://ubuntuforums.org/archive/index.php/t-763964.html") which has helped me out. I can now select the right resolution from the menu in "Resolution" but the problem is that the window is so big for my screen that I can't click on the "Apply" button, and I can't figure out how to resize that window.

---

### Post by Canis familiaris on 2008-06-25
> **makewayhomer said:**
> wow, thanks for the help everyone.

re: the resolution, I found another thread [here]("http://ubuntuforums.org/archive/index.php/t-763964.html") which has helped me out. I can now select the right resolution from the menu in "Resolution" but the problem is that the window is so big for my screen that I can't click on the "Apply" button, and I can't figure out how to resize that window.
Press Alt+A to apply

---

### Post by makewayhomer on 2008-06-25
> **Anurag_panda said:**
> Press Alt+A to apply

sweet, tx , I will try that when I get home tonight

---

### Post by Tomatz on 2008-06-25
> **makewayhomer said:**
> wow, thanks for the help everyone.

re: the resolution, I found another thread [here]("http://ubuntuforums.org/archive/index.php/t-763964.html") which has helped me out. I can now select the right resolution from the menu in "Resolution" but the problem is that the window is so big for my screen that I can't click on the "Apply" button, and I can't figure out how to resize that window.

Put the **mouse pointer over the window**, hold down **<alt>** then hold down **L-mouse**. Then you will be able to move the window.

Did you install your hardware drivers?.

---

### Post by makewayhomer on 2008-06-25
> **Tomatz said:**
>  
Did you install your hardware drivers?.

I basically went through the process in that thread I linked. I guess I installed the drivers, yeah? I'm not sure bc in Windows, you have to download them, but in Ubuntu it looks like I just needed to select them? I didn't download anything, I guess they came with the install?

---

### Post by Tomatz on 2008-06-25
> **makewayhomer said:**
> I basically went through the process in that thread I linked. I guess I installed the drivers, yeah? I'm not sure bc in Windows, you have to download them, but in Ubuntu it looks like I just needed to select them? I didn't download anything, I guess they came with the install?

They do download (from the repositorys anyway) but the difference is, it's done for you automatically using the hardware drivers app. You could achive the same results using the synaptic package manager, manually if you wanted.

Welcome to Linux ;)

---

### Post by Tomatz on 2008-06-25
What graphics card/chip does your laptop have? Is it a trident?

---

### Post by makewayhomer on 2008-06-25
> **Tomatz said:**
> What graphics card/chip does your laptop have? Is it a trident?

I think so, yes

---

### Post by makewayhomer on 2008-06-25
ok, so my screen resolution now looks ok! thanks everyone!

on to wireless...

I used the Synaptic Package Manager to install ndiswrapper. I downloaded the driver (an .exe file) from the Belkin site. but, I can't figure out how to use ndiswrapper to open the driver...any ideas?

---

### Post by brons2 on 2008-06-25
also install ndisgtk from the Synaptic Package Manager if you haven't already.  That will give you a GUI menu in System | Administration called "windows wireless drivers", then try to point it at that .exe file.

---

### Post by miesnerd on 2008-06-25
I might be a little late to the party here, but have you:
a) run lspci in the terminal, found your wifi card, and pasted it here
b) given us the specific model of your laptop
c) otherwise specified what model it is that your laptop uses

It looked to me that your laptop recognizes the card at least, so you should only need the right driver-- which ubuntu should be able to get for you.

---

### Post by makewayhomer on 2008-06-25
> **miesnerd said:**
> I might be a little late to the party here, but have you:
a) run lspci in the terminal, found your wifi card, and pasted it here
b) given us the specific model of your laptop
c) otherwise specified what model it is that your laptop uses

It looked to me that your laptop recognizes the card at least, so you should only need the right driver-- which ubuntu should be able to get for you.

I did this and got

ken@ken-laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)


I'm not sure my wireless card shows up there? It's a Belkin F5D7010. I did download the gui to ndiswrapper and pointed it at the belkin driver I downloaded (exe) but that didnt work...the gui didnt like it

---

### Post by cariboo on 2008-06-25
You want the .inf file from your downloaded driver file. if you double-click on the .exe file-roller may open and allow you to extract the files from the .exe file

Jim

---

### Post by makewayhomer on 2008-06-25
> **cariboo907 said:**
> You want the .inf file from your downloaded driver file. if you double-click on the .exe file-roller may open and allow you to extract the files from the .exe file

Jim

tx but no dice

---

### Post by Tomatz on 2008-06-26
> **makewayhomer said:**
> I did this and got

ken@ken-laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)


I'm not sure my wireless card shows up there? It's a Belkin F5D7010. I did download the gui to ndiswrapper and pointed it at the belkin driver I downloaded (exe) but that didnt work...the gui didnt like it

I have the same adaptor :)

If you just insert the adaptors install disc and navigate to the folder DRIVER (on the cd). You will find the files needed (.inf .sys).


Mine used to work "out of the box" in gutsy. Not sure why it doesn't in hardy?

---

### Post by Elfy on 2008-06-26
> Mine used to work "out of the box" in gutsy. Not sure why it doesn't in hardy?

An improvement ;) - nice to see the little sweetie instead of the big mouth :D

---

### Post by Tomatz on 2008-06-26
DUPLICATED FOR POSTER AS WE WENT OT ;)


> **makewayhomer said:**
> I did this and got

ken@ken-laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)


I'm not sure my wireless card shows up there? It's a Belkin F5D7010. I did download the gui to ndiswrapper and pointed it at the belkin driver I downloaded (exe) but that didnt work...the gui didnt like it

I have the same adaptor :)

If you just insert the adaptors install disc and navigate to the folder DRIVER (on the cd). You will find the files needed (.inf .sys).


Mine used to work "out of the box" in gutsy. Not sure why it doesn't in hardy?

---

### Post by Tomatz on 2008-06-26
DUPLICATED FOR POSTER AS WE WENT OT ;)


> **makewayhomer said:**
> I did this and got

ken@ken-laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)


I'm not sure my wireless card shows up there? It's a Belkin F5D7010. I did download the gui to ndiswrapper and pointed it at the belkin driver I downloaded (exe) but that didnt work...the gui didnt like it

I have the same adaptor :)

If you just insert the adaptors install disc and navigate to the folder DRIVER (on the cd). You will find the files needed (.inf .sys).


Mine used to work "out of the box" in gutsy. Not sure why it doesn't in hardy?

---

### Post by makewayhomer on 2008-06-26
> **Tomatz said:**
> DUPLICATED FOR POSTER AS WE WENT OT ;)




I have the same adaptor :)

If you just insert the adaptors install disc and navigate to the folder DRIVER (on the cd). You will find the files needed (.inf .sys).


Mine used to work "out of the box" in gutsy. Not sure why it doesn't in hardy?

that CD has gone missing. anyway I can get to it from the .exe I downloaded?

---

### Post by Tomatz on 2008-06-26
> **makewayhomer said:**
> that CD has gone missing. anyway I can get to it from the .exe I downloaded?

Give me 30 mins as i'm doing something and i will attach the files you need to my next post :)

---

### Post by Kralizec on 2008-06-26
If you right click on the driver .exe file and choose Open With Other Application, and select Archive Manager, it should allow you to extract the files from the .exe.

---

### Post by Tomatz on 2008-06-26
The files you need are in the .zip attached :)

---

### Post by djb6 on 2008-06-26
I followed these [directions]("http://ubuntuforums.org/showpost.php?p=4808350") and my wireless card works great now...I have a compaq presario v6000.  My wireless card is a BCM43xxx...and I've heard that is what is being installed on most computers.

---

### Post by makewayhomer on 2008-06-26
> **Tomatz said:**
> The files you need are in the .zip attached :)

great, thanks.

I used ndisgtk to open the .inf. I'm not sure what to do with the other 2 files?

ndisgtk still tells me that the 'hardware is not present' even though the 2 green lights on the belkin card are on

---

### Post by Tomatz on 2008-06-27
> **makewayhomer said:**
> great, thanks.

I used ndisgtk to open the .inf. I'm not sure what to do with the other 2 files?

ndisgtk still tells me that the 'hardware is not present' even though the 2 green lights on the belkin card are on

You may have a different version 7010 to me. Can you find out which version you have?

---

### Post by makewayhomer on 2008-06-27
> **Tomatz said:**
> You may have a different version 7010 to me. Can you find out which version you have?

the 54mbps g version

looks just ike this

[IMG]http://catalog.belkin.com/images/product/F5D7010/STD1_F5D7010.jpg[/IMG]

---

### Post by Tomatz on 2008-06-27
> **makewayhomer said:**
> the 54mbps g version

looks just ike this

[IMG]http://catalog.belkin.com/images/product/F5D7010/STD1_F5D7010.jpg[/IMG]

There should be a sticker on it saying:

```
Ver.7
```


The number will be from **1-7**


;)

Once you find that we will be sorted.

---

### Post by makewayhomer on 2008-06-27
> **Tomatz said:**
> There should be a sticker on it saying:

```
Ver.7
```


The number will be from **1-7**


;)

Once you find that we will be sorted.

the sticker says

VER.1000v

---

### Post by Tomatz on 2008-06-28
I think i have found it now :)

It was hard to find as the one from belkin was garbage so i had to get this from Dell support.

Sorry for the wait.

---

