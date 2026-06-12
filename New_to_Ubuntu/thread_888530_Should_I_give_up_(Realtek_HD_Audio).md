---
title: "Should I give up? (Realtek HD Audio)"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by meisetsu33 on 2008-08-13
Hi, this is my first post so please me nice :)

So I've just started using Ubuntu, and like a lot of other people, I'm having problem getting sound out of my desktop, which has a Gigabyte mobo with Realtek HD Audio integrated sound card.

sudo lspci and sudo aplay -l both detect no sound card.

I've updated the ALSA drivers (to at least 1.0.16), and also tried installing the Realtek driver for linux from their website. Both didn't work, since it asked if there was any ISA card from a list, and since none of them were mine I can't go on.

I've also tried [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and ALSA update did not work.
I can't perform the Manually Specify Module Parameters section and beyond, since the command line: "cat /proc/asound/card0/codec#* | grep Codec" does not work (says that dir grep and Codec do not exist).

I've also reinstalled Ubuntu with no luck at all.

My question is, is it time that I give up? Or is there any other way to get this sound card to be acknowledged? I really want to learn and use Ubuntu one way or another...

Any comments and answers would be wonderful. Thank you!

---

### Post by nothingspecial on 2008-08-13
I remember posting the same question when I was new to linux. Got it working though.
There`s nothing like the sound of those drums when you get your sound working.
Do you know exactly which soundcard you have.

---

### Post by nothingspecial on 2008-08-13
This is the important part of the how to - 

    * Open /etc/modprobe.d/alsa-base with the following command: 

sudo nano /etc/modprobe.d/alsa-base

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

options snd-hda-intel model=MODEL

    * Reboot 

If your computer is a toshiba try ```
toshiba
``` etc

---

### Post by meisetsu33 on 2008-08-13
Thanks for your reply! It's definitely reassuring.

As far as a I know, I have an Intel ICH9 High Definition Audio. Its the one integrated into a GIGABYTE G35-DS3L rev 2.0:
[http://www.gigabyte-usa.com/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2583&ProductName=GA-P35-DS3L](http://www.gigabyte-usa.com/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2583&ProductName=GA-P35-DS3L)
but that's as far as I can say.

Hope that's of any use.

---

### Post by trucker33377 on 2008-08-13
are you using 7.10 or 8.04 ? and do you have a sound icon on your tool bar? and it helps if you can give as many details as you can about your sys, your sound will work i'm sure look thru your device pref to be sure nothing is muted we have mobos that are pretty close. i have surround sound and must enable it to get sound working your sound should work out of the box

---

### Post by nothingspecial on 2008-08-13
Sorry for 3 posts in a row but I`ve just realised your probably using Hardy which I believe uses Pulse Audio and not Alsa.
As I`m on Gutsy I know nothing of pulse audio however that how to and this one
[http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound](http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound)
Worked for me.
I`m not sure myself how to use alsa with Hardy but that might be your best bet. I`ve got to go to bed now but I`ll check back later. Hopefully you`ll have solved it by then.:)

---

### Post by meisetsu33 on 2008-08-13
Ok here's some extra info that I hope would help.

Ubuntu ver.: 8.04 Hardy Heron
CPU: Intel Dual Core 2 E8400 OC 3.6GHz
Mobo: Gigabyte G35-DS3L with Intel HD audio integrated
Video: Nvidia GeForce 8800 GT

The speaker icon does show up on the top, except with a red "stop" icon on the bottom right corner of it.
When I click it, I get this message:
"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the control panel by right-clicking the speaker icon on the panel and selecting 'Remove from panel' from the menu."

I'm positive that all the GStreamer plugins are installed.

System sounds are not muted or broken or anything, since I'm using Ubuntu through VirtualBox, and Windows XP has sound without problem.

I'm going to try Hda Intel method again later after I try reinstalling Ubuntu.
Also, is Pulse Audio something that needs to be updated like ALSA?

---

### Post by trucker33377 on 2008-08-13
I dont know anything about VB mine is installed to the HD .and my updates are auto, do you by chance have the live CD? I just did install on this box this morning. it puts me thru the hoops turning things on but i didnt have to install anything to get it to work I have had what your talking about happen in the past with a Gateway laptop tho. for sure its not finding your card. with the X on that the volume icon.

---

### Post by ingrid_ozikem on 2008-08-13
I have a hardware that is almost identical to your GA-P35 setup.. sound does work for me but not in every output (it works from the connectors behind the computer but the front panels on the case can be fussy about which apps work with them..)

Hang in there, it'll work eventually,, I spent a week fixing related sound problems from Pulseaudio - ALSA conflicts.

---

### Post by Methuselah on 2008-08-13
I have the DS3R which has a Realtek ALC889A chip.
I was checking if you have the same chip but it says the DS3L has Realtek ALC888.
Do a search for linux/ubuntu and the realtek alc888 and see what you come up with.
I got a few hits that might be helpful but I don't know what you've already tried.

---

### Post by nicedude on 2008-08-13
Hardy can use alsa and mine did so by default, please run the following command and see if your volume is turned up

sudo alsamixer

it will open a simple GUI with sound levels for your various components and see if they are muted and if so turn them up.

---

### Post by meisetsu33 on 2008-08-14
Ok, I did some searches on ALC888, but the driver install I've done it before and it doesn't do anything.

The sudo alsamixer command gives "alsamixer: function snd_ctl_open failed for default: No such file or directory".
This is after I installed the alsamixer gui from Synaptic Package Manager.

So I reinstalled Ubuntu and tried the HDA Intel how to and no luck.
Heck, I can't even tell if the new ALSA drivers,libs,utils did get installed correctly. Is there a way to tell?
I also tried alsaconf, but it didn't show my soundcard type.

lspci and aplay -l still show no sound card.

Any other ideas?

---

### Post by nicedude on 2008-08-14
OK I checked this out and you have a ALC888 audio chipset from realtek on that motherboard. Apparently you need to download the driver package for linux from realtek and install it. Here is a link follow it click to agree with realtek eula thing and then scroll down to the Linux driver and download form one of the 3 mirrors it gives. Once you have these downloaded you should unzip the compressed file ( right click -> extract here ) and then you probably should cut and paste the newly opened directory somewhere else where you can save it ( like maybe your home folder ). Then you need to open a command line and cd to where you copy it. Once in the drivers directory in a terminal you just have to type "sudo ./install" without quotes to run the auto installer that is contained within the download and it should install its self.

heres the link to realtek drivers
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)


If you can't figure out how to copy the driver source or cd into the directory then PM me or post here where you copied to and what the driver folder you unzipped is named and I will help you.

nicedude

---

### Post by meisetsu33 on 2008-08-14
Thanks for the reply!
I've actually already installed that. Problem is, the installation leads to a alsaconf, which first states no PnP or PCI card found.
Then it leads to a list of cards I have to choose as a ISA device, but none of which I actually have.
I tried one of them (soundblaster) but as expected, nothing happens.

Should I try configuring into the other card options?

---

### Post by nothingspecial on 2008-08-14
> **meisetsu33 said:**
> 

Should I try configuring into the other card options?

I would think so.

---

### Post by nothingspecial on 2008-08-14
From another thread I have learned that you can change from pulse to alsa by going to  System -> Preferences -> Sound Preferences.
Never seen it though - still on Gutsy. 
Hang in there, your sound will work.

---

### Post by meisetsu33 on 2008-08-14
I'll try that configuration change over to Pulse. If that doesn't work I'll try the other card drivers.
I'll report back with results later.

Sadly I'm still at work... Wishing I was back to working on Ubuntu :)

---

### Post by meisetsu33 on 2008-08-15
Ok, so none of the alsaconf drivers or the pulse audio setting worked.

But what I did found out was that the sound works when live cd is running (as in not in virtualbox but actually off the cd in the computer)!
But now I'm having problems setting up a dual boot, so I'll go ahead and try to figure that out first and come back if the sound thing comes up again.

For now, thank you everyone for helping out! I'm sure you'll see more of my noob questions flying around here in the future :)

---

### Post by nothingspecial on 2008-08-15
If sound works on the live cd there is a 0.01 % chance it wont on install.

---

### Post by Riffer on 2008-08-15
Done a little research and it seems that your sound is a bit of bear to get working.  My suggestion is to buy a sound card that is Ubuntu/Linux compatible.  Sound Blaster would be a good one.

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)

Will give you the complete list.

Good Luck

---

### Post by CEB2nd on 2008-08-15
I have the exact same mobo GA-P35-DS3L rev 2.  The sound works with live CD, was auto detected during the install to the hard drive partition (not wubi) and has always worked.  I don't know if any of the info below will help.  Good luck!

On edit: Azalia is set to auto in my BIOS, don't know if this has anything to
do with your problem.



**This is a copy of my alsa-base file:**

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388



**The output of lspci**

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)



**The output of aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

