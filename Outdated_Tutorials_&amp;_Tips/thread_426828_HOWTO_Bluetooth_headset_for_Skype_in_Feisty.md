---
title: "HOWTO: Bluetooth headset for Skype in Feisty"
date: 2007-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Roner on 2007-04-28
The 2.6.20 vanilla kernel no longer includes the module snd_bt_sco (the Ubuntu stock kernel does, but that does not help those of us who must use a custom kernel - see Whoopie's comment below). The Bluetooth Alsa project uses now a userspace program named Plugz to communicate with bluetooth headsets. Although the new implementation works great (when it works), it poses a problem: the bluetooth headset is no longer recognized as a real alsa device. The btsco module and command are deprecated.

1. Download the Debian package Bluetooth-Alsa from [here]("http://packages.debian.org/unstable/sound/bluetooth-alsa").  Make sure you have all of the dependencies installed. The libsbc0 package is not included in the Ubuntu repositories (the rest are), so follow the link and download it as well. Install the packages.

2. Due to some bugs, the 2.6.20 kernel must be patched for the headset to work (HiFi will work without the patch). I assume you have the kernel source in /usr/src, and that you symlinked the directory to /usr/src/linux. 

Download the patch attached to this message. Extract it in /usr/src. Apply it:
```
sudo cat sco-flowcontrol-v3.0.diff | patch -p0 --dry-run

```
If the dry run succeeds, repeat the command without the --dry-run switch.
**UPDATE:** See [post no. 26]("http://ubuntuforums.org/showpost.php?p=3627597&postcount=26") in this thread for a patch that seems to work in Gutsy against kernel 2.6.23.

Compile and install the patched kernel.

3. Download the a2dprc attachment, and extract it to your home directory. Do the same to the asoundrc attachment (both files).

Edit the 3 files to include the mac address of your headset in the proper locations. You can find it, after putting it in discoverable mode, by running
```
hcitool scan
```

Now, copy the default asoundrc file:
```
cp ~/.asoundrc.default ~/.asoundrc
```

NOTE: If you already have your own .asoundrc file, add the sections from the one provided to it.

4. The howto in [this thread]("http://ubuntuforums.org/showthread.php?t=75978"), which helped me greatly, is outdated. It does help, however, in pairing the headset to your computer. Note that bluepin, bluez-pin and kbluepin are no longer necessary (or, in fact, working). Install from the Ubuntu repositories all that has to do with gnome and bluetooth (mostly gnome-bluetooth and the bluetooth manager). Follow the instructions in that howto and pair the headset (I am sure you can do it now without the KDE components - please add to this guide your method, if you managed to do so).

5. Now, that the headset is paired, it is time to check the HiFi component. You can find instructions at the [Bluetooth-Alsa build page]("http://bluetooth-alsa.sourceforge.net/build.html"). In my experience, the "Configure vlc" instructions work well.

Here is where we hit the first bump. Since the headset is not a real Alsa device, you cannot select it in any gui. You must edit config files, as described in that page (and that includes xmms, despite what they claim).

Before you run your application of choice, remember that you must have a terminal running 
```
sudo a2dpd
```
at the same time.

HiFi is a lousy name. Bluetooth headsets will not manage to give you a good, non-choppy sound, for anything above 96kbps.

6. Time to test the headset component. First, run the command
```
headsetd
```
You may want to add it to your session startup commands, or create launch scripts to applications using the headset.
Now, try to record yourself:
```
arecord -Dplug:pcm.headset test.wav
```

Use ctrl-c to stop the recording.

Let's see if it worked:
```
aplay -Dplug:pcm.headset test.wav
```

If this worked, we can move on to Skype.

7. Figuring out how to use Skype took me a while. Here we don't even have config files we can change, so we must trick Skype into thinking the default Alsa device is the headset. This is where the .asoundrc.skype comes into play. When you make it into your .asoundrc file, and set Skype to use Alsa, Skype will use your headset (segmentation faults did happen to me, but not often). 

The problem is that with this .asoundrc, the headset is the default for all of your system. This is why I created the skype-headset script attached here (don't forget to edit it to reflect your home folder's name, and to chmod it to executable) - it copies the .asoundrc.skype to .asoundrc, activates the headsetd daemon and launches Skype. When you quit Skype, it restores the default .asoundrc file.

Use the Skype test contact to see if all works.

That's it. Please let me know if I forgot anything or if anything is not working.

---

### Post by Whoopie on 2007-04-29
Hi,

two remarks:

1. the snd_bt_sco kernel module is still in the ubuntu kernel. You can use the bluez-btsco package with it.
2. the mentioned patch is also in the ubuntu kernel. See [http://git.kernel.org/?p=linux/kernel/git/bcollins/ubuntu-feisty.git;a=commitdiff;h=a3e22dab227fcdc2778f19c462476bf3c6186938]("http://git.kernel.org/?p=linux/kernel/git/bcollins/ubuntu-feisty.git;a=commitdiff;h=a3e22dab227fcdc2778f19c462476bf3c6186938")

So the only thing is to build the userspace tools or use the debian package.

Best regards,
Whoopie

---

### Post by Roner on 2007-04-29
Thanks for the comment. I had no way of knowing that, due to the fact that my wonderful Socket CF Bluetooth Card is NOT supported by the Ubuntu kernel. It requires a patch which I found and posted [here]("http://ubuntuforums.org/showthread.php?p=2559828"), plus an hciattach command. I found the patch in a discussion of its maker regarding how he is trying to send the patch upstream and fails.

In any case, I cannot use the Ubuntu kernel, and last time I tried to build it from git, the modules would not compile.  So I must use a vanilla kernel, and therefore had no idea about the module and the patch. Ironic.

---

### Post by overridex on 2007-06-15
I tried this method, the headset pairs successfully (I'll post how without kde later) but when trying to play a sound, the headset simply beeps once, plays no other audio and aplay hangs... any ideas?

p.s. arecord does work, and records pretty well through the headset...

---

### Post by Roner on 2007-06-15
I don't know what to tell you.  Usually the beep would mean bad pairing, but you say you can record...  All hardware is different, and I had no such difficulties.  See if erasing the devices from each other's memories and re-pairing helps.

---

### Post by overridex on 2007-06-15
Just an update... I tried a friend's bluetooth usb dongle instead of mine and it works instead of doing the beeping issue... not sure why mine won't work, it's a Jabra a320s that doesn't work.  The one that works is an Iogear... hmm.

---

### Post by overridex on 2007-06-15
Any luck getting this to work with teamspeak?  I tried the aoss wrapper, but while that works for xmms, teamspeak doesn't seem able to access the audio device...

---

### Post by overridex on 2007-06-16
Ok, I actually stepped back and used the "legacy" method described on the bluetooth-alsa build page... I modprobed snd-bt-sco and ran btsco <mac address> then entered the pin in the gnome applet to pair it, and that works well... 

This seems to work easier since I have another alsa device for the headset to choose in apps like ekiga, and it also uses the kernel oss emulation giving me another /dev/dsp device for the headset, which works with teamspeak...

I'm not sure why it's depreciated for the new way which takes so much more configuring rather than just having a device for the headset...

---

### Post by overridex on 2007-06-17
Just a quick note for anyone experiencing the same problem of the single "beep" and no audio playing/audio apps hanging when trying to play something through their headset.  I fixed it on my Jabra a320s adapter by adding this to the file /etc/modprobe.d/bluez:

options hci_usb force_scofix=1

if you already had the adapter plugged in, you can either reboot or unplug the adapter and run sudo rmmod hci_usb then plug it back in for the option to take effect.

This fix will probably help for other broadcom based bluetooth dongles as well.

---

### Post by gaspar on 2007-06-18
Hi there,
I'm trying to follow this howto, but when I try to install the bluetooth-alsa package, I got a message complaining about libc6. According to the listed dependencies, I need the >= 2.5-5 version, and seems  feisty is using 2.5; I tried to install the 2.5-5 found at debian, but I get a conflict with tzdata...
I'm a bit confused here, can someone help?
Thanks!

---

### Post by bretticus on 2007-06-21
Well, I think I'll buy a bluetooth headset and a dongle and give this a whirl! That being said I just wanted to pass on some useful information...

I currenty boot Feisty with kernel version: 2.6.20-16-386

I found a neat little tool at [Stéphane Graber's website]("http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/") called gbtsco. I downloaded and installed the [deb package]("http://www.stgraber.org/download/projects/gbtsco/gbtsco_0.1.1-0ubuntu1_all.deb") and there's a nice little "Enable Bluetooth Headset Support."

[IMG]http://img146.imageshack.us/img146/4729/screenshotbluetoothheaddc5.png[/IMG]

When I checked dmesg I saw:

```
[10222.624000] snd-bt-sco revision 1.16 $
[10222.628000] snd-bt-sco: snd-bt-scod thread starting
```

Then I went and got the latest [Skype download]("http://www.skype.com/download/skype/linux/") for Linux (still in Beta) and installed it. Now when I go to Options I see:

[IMG]http://img207.imageshack.us/img207/1582/screenshotoptionsqc1.png[/IMG]

Notice the BTHeadset options! Can It really be this easy? And to think, there was a woot headset the other day that I didn't get. :D

---

### Post by toorima on 2007-06-22
Yeah I use that tool and it is that easy :)

---

### Post by bretticus on 2007-06-25
> **toorima said:**
> Yeah I use that tool and it is that easy :)

Excellent!. My adapter and headset are on the way.

---

### Post by basicuser on 2007-06-26
That gbtsco is great - but once my bt headset is connected - how can I listen to audio? I'm using rhythmbox on feisty and it just keeps booming out and waking the kids up.

Thanks

---

### Post by wieman01 on 2007-06-26
This HOWTO got Skype up & running via Bluetooth. Thank you.

One slight problem though... the recording quality is fairly poor so that others are barely able to understand me. Any idea why?

FYI: No kernel patch was required.

---

### Post by wieman01 on 2007-06-27
I have gone back to using [COLOR="DarkRed"]"btsco"[/COLOR] which works fine for me. Sound quality is much better I guess it will be supported for another while. Hope Ubuntu will improve in that respect in future.

Thanks for the HOWTO anyway. Got me right on track.

---

### Post by apollo2011 on 2007-07-02
Hi everyone!

I have my headset connected through gbtsco and working with Skype. However, I really want to get it working as a microphone for Unreal Tournament 2004. How can I get it so that alsa will use it as the default microphone. I can't find anywhere where I can select the Bluetooth headset for anything except in Skype. Thanks for the help!

P.S. The headset is a Jabra BT135 I got from Verizon Wireless.

---

### Post by gaspar on 2007-07-02
Okay, I'm trying the gbtsco tool, it detects my headset; but when I try to connect, I got this error:

Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Can't connect RFCOMM channel: Permission denied

I can see the headset listed in skype,  just like in bretticus' screenshots, but I hear no sound when I make a call...
Any ideas, guys?
Thanks...

---

### Post by dnns on 2007-07-04
I have the same problem with my headset, a Logitech HS02-07. I once got it connected manually but still did not manage to get any sound through it. Why is bluetooth support so abysmal in ubuntu? Does it have to do with manufacturers not releasing specs on their products? The one time that I tried KDE, bluetooth seemed better integrated. So is it a gnome problem?

---

### Post by chipaca on 2007-07-05
> **gaspar said:**
> Hi there,
I'm trying to follow this howto, but when I try to install the bluetooth-alsa package, I got a message complaining about libc6. According to the listed dependencies, I need the >= 2.5-5 version, and seems  feisty is using 2.5; I tried to install the 2.5-5 found at debian, but I get a conflict with tzdata...
I'm a bit confused here, can someone help?
Thanks!

you should use [the bluetooth-alsa package from testing]("http://packages.debian.org/testing/sound/bluetooth-alsa") (which is the version that the HOWTO intends, probably):

---

### Post by gaspar on 2007-07-06
> **chipaca said:**
> you should use [the bluetooth-alsa package from testing]("http://packages.debian.org/testing/sound/bluetooth-alsa") (which is the version that the HOWTO intends, probably):

I was trying to use this one...

---

### Post by vico79 on 2007-07-14
> Okay, I'm trying the gbtsco tool, it detects my headset; but when I try to connect, I got this error:

Error: Failed to connect to SDP server: Permission denied
Assuming channel 2

Can't connect RFCOMM channel: Permission denied

I can see the headset listed in skype, just like in bretticus' screenshots, but I hear no sound when I make a call...
Any ideas, guys?
Thanks...

Hi everibody, I've the same problem with ubuntu feisty 7.04. :confused::confused:
 I solve it seeing the following wiki:

[http://wiki.ubuntuusers.de/Bluetooth_Headset]("http://wiki.ubuntuusers.de/Bluetooth_Headset")

In details, I go in the /var/lib/bluetooth/XX:XX:XX:XX:XX:XX directory and I manually removed the entries in all files which have the mac address of my handset.

Then I start gbtsco and it works. :lolflag::lolflag:

---

### Post by bretticus on 2007-07-14
> **bretticus said:**
> Well, I think I'll buy a bluetooth headset and a dongle and give this a whirl! That being said I just wanted to pass on some useful information...

Notice the BTHeadset options! Can It really be this easy? And to think, there was a woot headset the other day that I didn't get. :D

Well, I got my cheap Encore bluetooth dongle and my cheap Nokia BH-200 headset about a week ago. I was able to download some windoze software for the dongle which lets me make my headset the primary sound device. I can thus, make calls on my PC via Skype. However, when I boot Ubuntu (which I do about 29 out of 30 times) on that PC, I cannot make it work. I've been in circles trying pretty much everything. Imagine my shock when on my laptop with Ubuntu, I simply went and downloaded gbtsco (the updated version) and switched my audio setting in Skype (just as described in my first post) and it worked right out of the gate! (computers confuse me every now and then...more often than not I think :) )

However...playback has quite a bit of static and microphone is the same (and pretty quiet...both much more so in Ubuntu than Windoze.) I read somewhere about somebody else having this issue and fixing it (maybe there is hope yet.)

---

### Post by chicoBean on 2007-09-16
Adding a post by request of the original-
"I am sure you can do it now without the KDE components - please add to this guide your method, if you managed to do so"

env-
   Fiesty Fawn 7.04
   TRENDnet TBW-105UB (broadcomm chipset look above for mod param)
   Motorola H500

libs-
    bluez-utils

1. Create a small script in any directory. The below script will be /etc/bluetooth/pin.

#!/bin/sh
echo "PIN:0000"

---------------------------------- 
2. Put the headset device in pair mode. Use the following command to view the MAC address of the device-

hcitool scan

----------------------------------
3. From the command line the following worked

passkey-agent --default /etc/bluetooth/pin &
hcitool cc [MAC ADDRESS]
hcitool auth [MAC ADDRESS]
hcitool con

----------------------------------
4. If the setup from the original post is complete then the following commands should be ready to run.

a2dpd -d
headsetd

-----------------------------------
5. Do a small test

arecord -D plug:pcm.headset test.wav
aplay -D plug:pcm.headset test.wav
-----------------------------------

Thank you for all the posts above. This post would have never occurred without them.

---

### Post by boarderpatrol on 2007-09-16
Thx for Howto:
 subscribing to thread.

---

### Post by Roner on 2007-10-25
**UPDATE:**

I have been trying to get an updated sco-flowcontrol patch for kernel 2.6.23 (2.6.23.1, actually) and Gutsy.  Version 4.3 of the patch, which I found through Google, did not patch very well, so I went through the files individually and tried to fix the patch so it would work. I got the patch to work, the kernel to compile, and seemingly - everything is working, but I am no programmer, so I am attaching here both the original patch, and my modifications.  

Uncompress (sudo tar -xvf) the file of your choice to /usr/src, make sure /usr/src/linux is a symlink to your 2.6.23 source directory, and use sudo patch -p0 --dry-run FILENAME to check the patch.  Leave out the --dry-run switch if everything worked and you want to apply the patch.

Programmers out there: please do compare my revision to the original patch.  I have no clue if I did it right.

---

### Post by freek_zero on 2007-11-05
So i followed the very short and sweet instructions in [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices) and got the headset playing from Rhythmbox. It sounds like it is stereo, but the quality is horrid, like it's using headset profile (not a2dp). How do I figure out whether it is using a2dp or not? If so, I can only guess that the quality (bandwidth settings?) is set rather low. How do I adjust that?
This is on a new 7.10 Gutsy install.
Thx

---

### Post by Evanlec on 2007-11-13
> **Roner said:**
> **UPDATE:**

I have been trying to get an updated sco-flowcontrol patch for kernel 2.6.23 (2.6.23.1, actually) and Gutsy.  Version 4.3 of the patch, which I found through Google, did not patch very well, so I went through the files individually and tried to fix the patch so it would work. I got the patch to work, the kernel to compile, and seemingly - everything is working, but I am no programmer, so I am attaching here both the original patch, and my modifications.  

Uncompress (sudo tar -xvf) the file of your choice to /usr/src, make sure /usr/src/linux is a symlink to your 2.6.23 source directory, and use sudo patch -p0 --dry-run FILENAME to check the patch.  Leave out the --dry-run switch if everything worked and you want to apply the patch.

Programmers out there: please do compare my revision to the original patch.  I have no clue if I did it right.

can anyone else confirm that this patch works?
is this the only way to get the new "sco" thing working for vanilla kernel users (not the snd_bt_sco kernel module way) ?

so far i've gotten audio to play for me through rhythmbox
but have no idea how to set it up for VoIP which is what i would like it for

runing kernel 2.6.23.1 Ubuntu Gutsy x86_64

thanks very much

---

### Post by freek_zero on 2007-11-15
regarding my previous post 2 up, after i restart rythmbox the audio quality is great. have to do this every time i boot the machine. don't know wth is going on, but it does the trick. i finally have good audio. and i'm not experiencing the dreaded .5 to 1s delay so many people complain about with this headset

---

### Post by Evanlec on 2007-11-18
> **freek_zero said:**
> regarding my previous post 2 up, after i restart rythmbox the audio quality is great. have to do this every time i boot the machine. don't know wth is going on, but it does the trick. i finally have good audio. and i'm not experiencing the dreaded .5 to 1s delay so many people complain about with this headset

well that's all fine and good, but has anyone gotten voIP to work without the old (bt-sco) module method?

---

### Post by Fadsjeik on 2007-12-04
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

also enabled A2DP for me, the music quality is fantastic. However with skype it just doesn't work. It outputs the sound only to the left earpad en the quality is really bad. The microphone doesn't seem to be working at all. Is there a way to get VOIP to work without the old drivers?

---

### Post by tpol on 2008-02-01
Great HOWTO Roner, thanks.

I was able to follow it successfully up to the aplay test command.  I can get it to play a sample WAV file to my headet (a Jabra BT350) fine.  mplayer to the headset works fine as well.

But when I do the arecord command, it always produces an empty WAV file of 44 bytes.

The second, perhaps related, problem is when I go to run Skype.  In the terminal, I get the following message, repeated:

ALSA lib pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_sco.so

---

Any ideas would be greatly appreciated.  Thanks!

---

### Post by aeg37 on 2008-02-22
I have found the pairing method here: [http://gentoo-wiki.com/HOWTO_use_a_bluetooth_headset#Configure_the_system](http://gentoo-wiki.com/HOWTO_use_a_bluetooth_headset#Configure_the_system)
worked for me under Gutsy/Gnome.  After completing the steps, I finally was able to solicit a pairing request dialog from Gnome.

---

### Post by yekibud on 2008-03-30
At first I tried the method that Roner suggested, without the patch (thought maybe Gutsy 2.6.22 wouldn't need it).  Didn't work, and then I saw bretticus' post using gbtsco.  Worked like a charm, but I need to launch gbtsco and pair my device (sony-ericsson HBH-602) every time I shut down or suspend.

So, is there a way to use the gbtsco method without having to pair every time?  Or do I need to do the kernel patch and try Roner's method again?

Thanks for the tips.

---

### Post by s_spiff on 2008-08-10
hey, for all noobs.. here's the HowTo step by step. Worked for me. on a Hardy 32bit and a Motorola S9 Headset.

[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)

> 
ust bought myself a cheap Bluetooth headset, so here's a HowTo on how to hook it up to Ubuntu and redirect your music and [[COLOR=dodgerblue][COLOR=dodgerblue ! important][FONT=verdana][COLOR=dodgerblue ! important][FONT=verdana]media [/FONT][/COLOR][COLOR=dodgerblue ! important][FONT=verdana]players[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://forums.overclockers.com.au/showthread.php?t=694010#") to it. This guide is based on the guides at Ubuntu Forums with some modifications to be more step-explicit and thus newbie-friendly.

**Purpose:** To play your audio such as MP3's and movie output through a Bluetooth-connected audio headset.

**Scenario:** You are too lazy to plug in a cable to your [[COLOR=dodgerblue][COLOR=dodgerblue ! important][FONT=verdana][COLOR=dodgerblue ! important][FONT=verdana]PC[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://forums.overclockers.com.au/showthread.php?t=694010#"). You want to walk around your house without a long cable after you. You want to look cool to your mates. You want to psyche out your non-tech parents by listening to music without any audio device or cables attached to you. Problem is, very few Linux apps have direct support for directing sound to any other device.

**Solution:** Redirect all audio using the PulseAudio Server on Ubuntu Hardy.

_Prerequisites:_
[LIST]
[*]Bluetooth interface to your PC. This can be inbuilt, such as on a modern notebook PC, or a USB dongle such as the [one I use]("http://www.jaycar.com.au/productView.asp?ID=XC4892&CATID=&keywords=bluetooth&SPECIAL=&form=KEYWORD&ProdCodeOnly=&Keyword1=&Keyword2=&pageNumber=&priceMin=&priceMax=&SUBCATID=").
[*]Ubuntu Hardy 8.04 (I'm using 8.04.1 64-bit in this example).
[*]Internet access or other such access to the Ubuntu repositories to install extra [[COLOR=dodgerblue][COLOR=dodgerblue ! important][FONT=verdana][COLOR=dodgerblue ! important][FONT=verdana]software[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://forums.overclockers.com.au/showthread.php?t=694010#") from.
[*]Suitable Bluetooth headset. The unit I bought is a TDK BT100 pair of buds. Supports Bluetooth 1.2 and 2.0, does headset, handsfree A2DP and AVRCP functions (typical function set of any headset/handsfree unit these days). Though the sound quality of these things isn't that great, it was only $49 at my local PC shop. You can get cheaper units through sites such as [Catch of the Day]("http://www.catchoftheday.com.au/Philips_SwitchStream_BlueTooth_Headsets-p-677.html")
[/LIST]
**Pros:**
[LIST]
[*]You are cable free! You can walk around the house (as far as the range of your Bluetooth adapter goes) and listen to music/movies.
[*]If your headset also has a mic, you can use that too for [[COLOR=dodgerblue][COLOR=dodgerblue ! important][FONT=verdana][COLOR=dodgerblue ! important][FONT=verdana]VOIP[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://forums.overclockers.com.au/showthread.php?t=694010#") apps and the like.
[/LIST]

**Cons:**
[LIST]
[*]A Bluetooth headset is generally more expensive than a cabled one.
[*]Most headset batteries only last four hours in continuous use before needing a recharge (though the TDK unit I have plugs into mini-USB to recharge and can still be used whilst recharging, which is convenient).
[*]Audio quality is generally not as good as a dedicated cabled headset.
[*]For those headsets that have battery-saving functions when idle, some are known to clip the start of the audio playback when turning back on (my set causes Ubuntu to wait until it's up and running before streaming the audio, thus no clipping).
[*]There are some known issues with using this method with 32-bit Skype under 64-bit Ubuntu, which I won't go into detail here (since I don't use Skype). Refer to the Ubuntu Forums for more details about it.
[*]At least on my headset, there is an ever-so-slight delay in audio sync when watching video.
[/LIST]

These instructions should be adaptable to other distributions.

[LIST=1]
[*]Fire up/install Ubuntu as normal.
[*] Plug in or enable your Bluetooth adapter. Your Bluetooth adapter will be automatically detected and drivers loaded - there is nothing for you to do manually here.
[*]If you have NEVER used Bluetooth on your Ubuntu setup before, then go to the next step, otherwise skip to Step 11 because you're probably already setup properly.
[*]Get into a terminal.
[*]Verify that your Bluetooth adapter is running with:
 	Code:
 	$ hciconfig -a 
If you get details about hci0 listed including manufacturer's name, then your adapter is working.
.
[*]Type in the following to edit your Bluetooth configuration file:
 	Code:
 	$ sudo gedit /etc/bluetooth/hcid.conf 
This will bring up the Bluetooth configuration into the GEdit text editor.
.
[*]Near the top of the file you will see the following:
 	Code:
 	# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user; 
Change the **security user** line to **security auto**
.
[*]A few lines beneath this is a section that reads as follows:
 	Code:
 		# Default PIN code for incoming connections
	passkey "1234"; 
Change the **1234** to something else, eg: **4493**. This is the pin number required for other Bluetooth devices to connect to you and it would be insecure to leave it at the default.
.
[*]Save and exit.
[*]Now restart Bluetooth by typing in:
 	Code:
 	$ sudo /etc/init.d/bluetooth restart 
When you do this, an informational bubble will appear in your task bar saying **<hostname>-0 Device has been made connectable**, eg: if your PC's name is "gordon", the message would say "gordon-0 Device has been made connectable".
.
[*]Turn on your Bluetooth headset, but don't go into pairing mode just yet.
[*]In your terminal, type in the following:
 	Code:
 	$ hcitool scan 
Your PC will now scan for local Bluetooth devices and your headset should appear in the resulting list after a few seconds (along with anyone's Bluetooth-enabled mobile phones that are in range). The output will look something like:
 	Code:
 	$ hcitool scan
Scanning ...
	00:11:22:AA:BB:CC	Nokia N95
	00:33:44:DD:EE:FF	BT81
$ 
In this example, my PC has found my Nokia mobile phone and my Bluetooth headset and shown me the MAC addresses for both of them.

NOTE: If your headset does NOT appear, you probably already have it paired with something else, like your mobile phone. In this case, switch the headset to pairing mode and then run the scan again.
.
[*]Highlight and copy the MAC address of the headset to the clipboard using your mouse and CTRL + SHIFT + C.
[*]Now type in:
 	Code:
 	sudo gedit ~/.asoundrc 
**Note the period before "asoundrc".** This will create a new hidden text file called .asoundrc in the root of your Home directory and open GEdit so you can add to it. The file is hidden because of the leading period.
.
[*]In the text editor, type in the following, replacing the MAC address with the one you copied earlier (paste with CTRL + V):
 	Code:
 	pcm.bluetooth {
  type bluetooth
  device 00:33:44:DD:EE:FF
  profile "auto"
} 
*NOTE: Depending on your distro, you may find that the word "Bluetooth" is reserved. If, when you get to Step 23, you hear anything BUT the audio you are playing, change the "pcm.bluetooth" bit above into something else, eg: "pcm.btheadset" and try your audio again. Remember then to change every typed reference in this guide from "bluetooth" to "btheadset".*
.
[*]Save and exit.
[*]Now type in:
 	Code:
 	$ sudo hciconfig hci0 voice 0x0060
$ sudo modprobe snd_bt_sco
$ sudo modprobe sco 
This will enable sound on your adapter and load the modules necessary to carry bluetooth audio. Note that the two modprobe lines will only enable Bluetooth audio temporarily until you reboot. If you would like to load the drivers automatically on each boot, only add the two modprobe lines above to the end of the /etc/modules file (sudo gedit /etc/modules).
.
[*]Now we need to tell PulseAudio that your Bluetooth headset exists:
 	Code:
 	$ pactl load-module module-alsa-sink device=bluetooth
$ pactl load-module module-alsa-source device=bluetooth 
Note that this enables your Bluetooth headset for PulseAudio only temporarily. To enable it permanently, create a new file using **gedit ~/.pulse/default.pa** and paste the two lines above into it and then save. [COLOR=red]NOTE: I've just noticed this tends to break PulseAudio because the bonding of your headset needs to have occured **before** issuing the above commands, or PulseAudio refuses to start upon reboot. Don't create this file (or delete/rename if you've already created it) and PulseAudio works fine again. To keep using your Bluetooth headset, move the file you created to your [[COLOR=dodgerblue][COLOR=dodgerblue ! important][FONT=verdana][COLOR=dodgerblue ! important][FONT=verdana]Desktop[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://forums.overclockers.com.au/showthread.php?t=694010#") and make it executable. Once your Desktop has loaded and you've paired your headset, then execute the file by double-clicking on it to notify PulseAudio about the headset. [/COLOR]
[*]We're almost ready to pair with the headset and hear some basic audio, but before we do that, do a right-mouse click on the Bluetooth icon in your system tray and choose "Preferences".
[*]Now click on the Services tab and ensure Audio Service is enabled. If not, check the box and then close the window.
[*]Now type in:
 	Code:
 	$ sudo cat /proc/asound/cards 
...and you should see output similar to the following:
 	Code:
 	 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xea400000 irq 22
 1 [Headset        ]: Bluetooth SCO - BT Headset
                      BT Headset 1 
This shows us that the [[COLOR=dodgerblue][COLOR=dodgerblue ! important][FONT=verdana][COLOR=dodgerblue ! important][FONT=verdana]system[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://forums.overclockers.com.au/showthread.php?t=694010#") is ready to use the Bluetooth headset as device 1 (but we haven't paired it yet, so technically it won't be able to use it just yet).
.
[*] The best way to trigger a pairing is to provoke the unit into a response as the normal methods don't always work. Switch your headset into pairing mode (refer to your headset's manual).
[*]While the headset it in pairing mode, type in the following:
 	Code:
 	$ aplay -D bluetooth -f s16_le /usr/share/sounds/login.wav 
This will attempt direct communication with your headset, and within a second or so, an information bubble will appear under the Bluetooth icon in the system tray asking you for the PIN number to access the headset. Click on the button to enter the PIN and then type it in. For most headsets, the PIN is **0000**, but refer to your headset's manual.

Ubuntu should soon after confirm that it has "bonded" with the headset and you should suddenly hear the familiar Ubuntu login sound play through your headset! Hooray! We have sound!

Unfortunately only aplay will play anything through your headset. All other sounds are still coming through your speakers. Unless the [[COLOR=dodgerblue][COLOR=dodgerblue ! important][FONT=verdana][COLOR=dodgerblue ! important][FONT=verdana]application[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://forums.overclockers.com.au/showthread.php?t=694010#") in question can redirect audio to another detected device, it will always play through the standard-out, so applications such as Totem and Rhythmbox will still output via your speakers and not give a hoot about your Bluetooth headset. To fix this, we need to make use of the PulseAudio Server which can redirect output to another device.
.
[*]The PulseAudio Server is already installed by default in Ubuntu Hardy, so we just need to install some tools to manipulate it. Go back to your terminal and type in the following:
 	Code:
 	$ sudo apt-get install paprefs paman padevchooser 
This will install the PulseAudio Preferences app, the PulseAudio Manager app and the PulseAudio Device Chooser app.
.
[*]Once installed, go to the System->Preferences->Sound. The Sound prefs window will appear.
[*]Under the Devices tab, change the "Sound playback" option for Sound Events, Music and Movies, and Audio Conferencing from "Autodetect" to "PulseAudio Sound Server".
[*]Click Close.
[*]Play something, be it an MP3 or video to ensure that your audio still works in general through your speakers. This confirms PulseAudio is working in general.
[*]Now go to Applications->Sound & Video->PulseAudio Device Chooser. This will add a black microphone jack icon to your system tray.
[*]Do a left-click on the jack icon and a menu appears. In this menu, choose "Manager". A new window appears.
[*]If it's not already connected, click on the "Connect" button to connect to your local PulseAudio server. When connected, you will see details about it listed.
[*]Click on the Devices tab. Under "Sinks" you should see an entry for "alsa_output.bluetooth". This is picked up directly from your .asoundrc file.
[*]Now go to the Sample Cache tab. At the bottom is a "Playback on" drop-down. Choose Bluetooth from this list and click on the Play button. You should hear the Ubuntu login sound through your speakers. This proves to us that PulseAudio can play through your Bluetooth headset (but this is NOT the redirection - this is just a test).
[*]Close the PulseAudio Manager.
[*]Do another left-click on the mic jack icon in your system tray.
[*]Go to "Default Sink" and then choose "Other" from the sub-menu. A window appears.
[*]In this window, type in "alsa_output.bluetooth" and click OK.
[*]Play a sound from somewhere, eg: MP3 or movie in Totem. You should now hear your audio coming through your Bluetooth headset!
[*]To switch back to your speakers, simply click on the mic jack icon again, choose "Default Sink" and choose "Default" from the sub-menu. The next audio stream played will go back through your speakers.
[*]To make the PulseAudio Device Chooser start automatically on startup, click on the mic jack icon again, choose Preferences from the menu and then click on "Start applet on Session Login" in the window.
[*]Enjoy! [IMG]http://forums.overclockers.com.au/images/smilies/tongue.gif[/IMG]
[/LIST]



---

