---
title: "HOWTO: Tascam US-122 in Fiesty"
date: 2007-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by richardjennings on 2007-05-02
I have followed several tutorials that have led to success. However every one I have found requires manually introducing the Tascam to Ubuntu after a reboot or an unplug. 

This following procedure worked perfectly for me in Fiesty, is easy to do, and best of all - allows you to hot plug your Tascam, reboot & just generally take it easy.

I found the original tutorial here : [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)

Unplug the Tascam US-122 USB cable

1) ```
sudo apt-get install fxload alsa-firmware-loaders
```

2) ```
wget http://ftp.mj2.org/pub/alsa/firmware/alsa-firmware-1.0.14rc3.tar.bz2
```

3) ```
tar xjf alsa-firmware-1.0.14rc3.tar.bz2
```

b) ```
sudo mkdir /lib/firmware
```

4) ```
sudo mv alsa-firmware-1.0.14rc3/usx2yloader/ /lib/firmware/
```

4b) ```
sudo cp -r /lib/firmware/usx2yloader /usr/share/alsa/firmware/
```


//revision 1

5)

```

 sudo gedit /etc/udev/rules.d/55-tascam.rules
```

the rules file is now open in gedit..

6) copy the following into the 55-tascam.rules file in gedit

```

 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

```

Save the file.


Plug in your usb cable and your tascam usb led should light up.

//revision 2

assuming it does, you can add another rule to 55-tascam.rules that automatically configures alsa to use the tascam as your default soundcard.

repeat step 5)

add below the previous rule:
```

KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"

```

Save the file

unplug / plug your tascam back in.

Now alsa should be working correctly with the tascam!

---

### Post by GMaq on 2007-05-06
Hi,
     I'm new to Ubuntu Feisty having just switched from MEPIS, I'm still pretty challenged at the console, I've tried your Tascam tutorial and also gone to the original one that you linked and although all the files and folders seem to be where they are supposed to be, i am not getting "the green light" I would guess it has to do with the last step of the tutorial. I would really like to get my US 122 up and running so I can use a MIDI keyboard with QSynth as well as Audio recording. I would really appreciate any guidance. Thanks for your time.

---

### Post by Jeremy23 on 2007-05-07
I'm having a problem with the udev stuff. If I type the commands from udev manually (and replace the %N with the path to the device shown by lsusb) it works fine, but udev will not automatically execute the commands for some reason.

---

### Post by Jeremy23 on 2007-05-07
OK, I got it working by copying-and-pasting the udev rules from [http://alsa.opensrc.org/Tascam_US-122]("http://alsa.opensrc.org/Tascam_US-122") directly into the udev rules file.

Looks like there were issues with the quoting. (hint, hint)

---

### Post by GMaq on 2007-05-07
Jeremy23,
   THANKS!!!!!! That did the trick, One thing I'm still a little confused about is what is the purpose of the alsa-firmware-1.0.14rc3 folder that gets created in step 4?? The udev rules point to the native firmware folder that's already there, Is the downloaded folder supposed to overwrite the original one?? In the guide above a whole new alsa-firmware-1.0.14rc3 folder is created inside the alsa/firmware folder.

---

### Post by daffe on 2007-05-09
People may want to know that this tutorial worked nicely in Feisty 32 bits but I couldn't make it work on 64 bits.  I needed to fxload manually on each reboot to have the us-122 to work in 64 bits.  I f someone knows why, feel free!

---

### Post by jaywalker13 on 2007-05-11
I'm having trouble with this one. Followed all the steps as shown above, but the best I get is that the green light on the US-122 sometimes comes on at start up, but even then the device does not work. In other words, programs like Amarok still play music via the comuter's inbilt sound card, not the US-122.

On the few occasions when the light does come on, the lsusb list says:

Bus 001 Device 004: ID 1604:8006 Tascam US-122 Audio/Midi Interface.

When the light does not come on, that line also has (without fw) at the end of it.

I can't get any consistent pattern of the green light on the US-122 coming on at startup or not coming on.

As a newbie, I would appreciate any advice. Sorry, I don't even know what other relevant information to give.

Thanks

Jay

---

### Post by GMaq on 2007-05-11
Hi,
      I not saying this is the best way but it's what works for me, I use my US-122 with qtjackctl, which is available in the feisty repositories. qtjackctl is a GUI for Jack which is a low latency audio interface to manage connections to and from different software apps, kind of like a software patchbay.I'm not sure if it (Jack)will work with Amarok. I use my internal card with media players etc. and my US-122 for multitrack audio and MIDI. It may be something to try. Hope this helps!

---

### Post by jaywalker13 on 2007-05-12
Thanks for your reply GMaq. 

Trying to install jack. Did apt-install etc and it seemed OK. Then typed "jack" to start the program and got the following:

This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *error* Access of CD device /dev/cdrom resulted in error: No medium found

Can you advise on what to do next? I don't know what this means.

Regards

Jay

---

### Post by dahouse on 2007-05-12
Still not working for me. I'm guessing its the last command. Someone said it had to do with quotations? How would I fix this?

I did usx2loader with the device plugged in, and got this:

usx2yloader: no US-X2Y-compatible cards found

I'm running Ubuntu Studio on a Compaq Presario R3000 with a nforce integrated soundcard and an US-122 hook up via USB

---

### Post by GMaq on 2007-05-13
Hi,
@ jaywalker13,
       I'm sorry I'm really new to linux, I really don't know what the error means, if you have qtjackctl installed you shouldn't need to run it from the terminal it has a GUI with it, the fact that your US-122 isn't coming on all the time is going to cause you problems as well.

@dahouse,
     This is what I did, Open a terminal, type in "sudo gedit" and the path to your "rules.d" folder (i.e. sudo gedit/etc/udev/rules.d/55-tascam.rules) The gedit program should open a new window with your 55-tascam.rules file to edit. Delete any text that is already there.  Copy and paste this:  "BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

Save your 55-tascam.rules file and you should be good to go.

PS: The best thing to do would be to copy the above text string directly from [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122) if mine doesn't work.

---

### Post by dahouse on 2007-05-13
I did that, re did the entire tutorial, experimented with the text by removing the first quotation before the first BUS, and then removing the first and last quotation, all to no avail!

Anymore ideas guys? The light just doesn't wanna turn on.

I'm fairly certain my usb ports are powered.

thanks

---

### Post by jaywalker13 on 2007-05-14
Hi GMaq.

I can't believe it. The US-122 has sprung into life and I am now upsetting the neighbours with very loud music. (Where are you? I'm in Melbourne Australia, so you might not be able to hear it.)

Many thanks for your help.

I must have stuffed up the installation of jack and qtjackctl. Hadn't been able to find them in Synaptic Package Manager so downloaded from a website. Finally found where they showed up in Synaptic Package Manager. Installed both of them.

Opened qtjackctl from the menu as you said. I don't know what happened to make it work, but after a bit of fiddling with both audio and midi settings, it started to work.

The thing about US-122's lights coming on some of the time and not others might be due to a dodgy usb plug on my Dell 9300. It seems OK now (maybe) using a different usb. These machines have 6 usb plugs. Also, I wonder if any of the settings I did referred to one usb plug and not another. Hmm.

Not game to turn off the computer and start again as it might not work. I guess I'll have to leave it powered up until I move house.

Re. dahouse's problems with the quotation marks, I found this too. Copied and pasted the 55-tascam rules stuff and some of the quotes seemed to disappear. Had to carefully read it through and replace them. Must be something that happens with copying and pasting between Firefox and Terminal - maybe.

Cheers

Jay

---

### Post by jaywalker13 on 2007-05-15
OK. I celebrated too soon. Restarted the computer and no lights on the US-122.

Actually what happened on startup was the system did a forced check (on one of the volumes I think) and I was able to read on the screen:

"Starting kernel event manager
udved [2867] add to rules
invalid rule ' /etc/udev/rules.d/55-tascam.rules: 2'"

GMac, could you (or anyone else) advise me on this. Do I have to do something with the kernel? If so, how do I find out what to do?

Also, while it was working, I was only able to play music with Amorak. I could not play a CD in the CD drive or anything else.

Any advice on what to do or where to go to find out more information would be appreciated.

Regards

Jay

---

### Post by richardjennings on 2007-05-15
ok guys firstly I am very sorry for the misinformation in my original post.
I just started from scratch and followed my own instructions.
Indeed - it did not work.
Ok after an hour I have finally realized what the problem is.

the alsa-firmware-loaders package.

this now looks for the firmware /lib/firmware/ not /usr/share/alsa/firmware/




5) ```
 sudo gedit /etc/udev/rules.d/55-tascam.rules
```

the rules file is now open in gedit.. 

6) copy the following into the 55-tascam.rules file in gedit

```
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'" 
```


Save the file.


We need to put the usx2yloader firmware in the /lib/firmware folder

7) ```
 sudo mv /usr/share/alsa/firmware/usx2yloader/ /lib/firmware/
```

---

### Post by dahouse on 2007-05-15
WOOOOO! IT WORKS!!!!!

THANK A MILLION AND A HALF! That's alot of thanks

The light works. I haven't tested it though.


Now, does anybody know a tutorial for selecting the right soundcard? Or is there any software that allows you to select the default card on the fly?

---

### Post by jaywalker13 on 2007-05-16
Curses.

I followed your excellent instructions richardjennings, and made the changes to 55-tascam.rules but still get no green light, Strange because it has sometimes worked before. In fact the light came on when I started off this morning before I made the changes. Then I unplugged and replugged the usb cable - no light. Resarted 3 times - no green light.

I wonder if something else could be happening.

I would sure appreciate any ideas from anyone.

Thanks to all the people who have contributed, especially Richard.

Jay

---

### Post by richardjennings on 2007-05-16
jay i have realized another irregularity with the howto

i have added a 4b) ```
sudo cp -r /lib/firmware/usx2yloader /usr/share/alsa/firmware/
```

this is probably why it didn't work for you. I apologize for the oversight.

---

### Post by richardjennings on 2007-05-16
omfg i have finally made some more progress getting alsa to work correctly

sorry for the omg blah BUT - i am just so happy right this second.

I am finally listening to a video on youtube through my tascam us122


anyways - anyone who has followed the HOWTO so far,

change you 55-tascam.rules

add

```
KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"

```

after the previous rules.

ALSA should now work properly

---

### Post by richardjennings on 2007-05-16
this is the revised howto: aka post1. I'd like to think this is now completely correct. I apologize for previous inaccuracies.

revision 2 /16/05/07

I have followed several tutorials that have led to success. However every one I have found requires manually introducing the Tascam to Ubuntu after a reboot or an unplug. 

This following procedure worked perfectly for me in Fiesty, is easy to do, and best of all - allows you to hot plug your Tascam, reboot & just generally take it easy.

I found the original tutorial here : [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)

Unplug the Tascam US-122 USB cable

1) ```
sudo apt-get install fxload alsa-firmware-loaders
```

2) ```
wget http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2
```

3) ```
tar xjf alsa-firmware-1.0.14rc3.tar.bz2
```

3b) ```
sudo mkdir /lib/firmware
```

4) ```
sudo mv alsa-firmware-1.0.14rc3/usx2yloader/ /lib/firmware/
```

4b) ```
sudo cp -r /lib/firmware/usx2yloader /usr/share/alsa/firmware/
```


//revision 1

5)

```

 sudo gedit /etc/udev/rules.d/55-tascam.rules
```

the rules file is now open in gedit..

6) copy the following into the 55-tascam.rules file in gedit

```

 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

```

Save the file.


Plug in your usb cable and your tascam usb led should light up.

//revision 2

assuming it does, you can add another rule to 55-tascam.rules that automatically configures alsa to use the tascam as your default soundcard.

repeat step 5)

add below the previous rule:
```

KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"

```

Save the file

unplug / plug your tascam back in.

Now alsa should be working correctly with the tascam!

---

### Post by jaywalker13 on 2007-05-16
Excellent help Richard. I am now enjoying old rock and roll music via my us122 now, thanks to your advice. I think it might even have defeated the problem about the us122 only starting sometimes. DVDs and CDs playing OK.

I was getting rather put off with Ubuntu having had problems with my scanner, printer and the us122. Now I feel like continuing with the struggle.

Next step might be to get midi working.

Cheers

Jay

---

### Post by richardjennings on 2007-05-16
Next step:

has anyone succeeded in getting jack working properly?

---

### Post by GMaq on 2007-05-16
richardjennings,
    Thanks for your diligence in tying up the loose ends on this, As a new Linux user it was quite a ride getting my US-122 to work! I have been using qtjackctl with my US-122 since I got it to work, I am using it with QSynth and it seems to be working fine, I have my pictures per period set at 512 with 3 buffers which gives me about 34ms of latency which is unnoticeable. Other than a rare crackle, which could be from the samples or QSynth it seems very stable. The patchbay in qtjackctl is pretty straightforward for routing MIDI and Audio in various configurations. What is not working for you in jack??

---

### Post by shen-an-doah on 2007-05-17
All working fine here, except for one odd bug. When I skip to the next track in Amarok, it switches back to the internal soundcard on my laptop, then when I skip again, it goes back to the US-122. This only happens when I've got Amarok set to crossfade between tracks.

Nothing major, it's just a bit odd...

---

### Post by jaywalker13 on 2007-08-02
Does anyone who used this thread (esp richardjennings) know about the problem described in [this link?]("http://ubuntuforums.org/showthread.php?p=3115196#post3115196")

Users of the us-122 report a loud hum or buzz when pausing many audio applications - not all - Amarok is OK, XMMS is not.

Jay

---

### Post by AzraelSlain on 2007-08-07
Ok, I'm trying to make the US 122 work and i followed the tutorial all the way up to step 4 and heres what i got

mv: cannot move `alsa-firmware-1.0.14rc3/usx2yloader/' to a subdirectory of itself, `/lib/firmware/usx2yloader'

Everything after that i get errors for, any help

---

### Post by elov on 2007-08-15
when i do the second step

wget [http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2](http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2)

i get:

--16:55:29--  [http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2](http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2)
           => `alsa-firmware-1.0.14rc3.tar.bz2'
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to www.alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:55:35 ERROR 404: Not Found.


seems like its not getting to the page to download. what do i do?

---

### Post by richardjennings on 2007-08-15
hi elov

yes it seems that link is no longer valid.

here is a new one: [http://ftp.mj2.org/pub/alsa/firmware/alsa-firmware-1.0.14rc3.tar.bz2](http://ftp.mj2.org/pub/alsa/firmware/alsa-firmware-1.0.14rc3.tar.bz2)

jaywalker13, I do have that same problem & I dont know anyway around it. 

AzraelSlain did you get it to work ok?

---

### Post by elov on 2007-08-15
seems everything worked correctly but i still didnt get anywhere. it's not playing any sounds except when i connect a mic and turn the knob to input.

---

### Post by AzraelSlain on 2007-08-29
i tried the new address but came up with a 404 eror

---

### Post by AzraelSlain on 2007-08-29
Ok, really frustrating, Ive tried everything on here, and i know changes got made along the way to how to do this, can you possibly now have a more final HowTo list and what exactly to get here. Ive done everything and still get errors

---

### Post by AzraelSlain on 2007-09-02
I just got thinking and a few questions came to mind. 
1. Was this FAQ made on a 32 bit system, do you think there would be a difference between the 64 and 32 bit versions for this to work.
2. Does Ubuntu studio come with the usxyloader installed so the tascam can be plug and played?
3. Could a more up to date how to guide be made, I've been itchin to get this to work so i can be a linux man and ditch Winblows all together. I got Hydrogen to work, got JACK figured out, got Ardour to load up, studing up on how linux works more each day.

I think what i might do is format with a 32 bit version and try one more time. It's the only thing i can think of for why this isn't working.

---

### Post by TMSstudio on 2007-09-08
Followed this tutorial and it worked to a tee, following some jigging to get the firmware in the right place. Currently unable to get the soundcard to work with Jack/Ardour though. Any Ideas?

---

### Post by Bjoern on 2007-09-15
Hello,

I followed the steps and get the green light, but when I try to play sound, I only get an error.

gstreamer-properties - Test (Default Output set to ALSA, Device US-X2Y Audio #0, Pipeline: alsasink device="hw:1,0"): 

ALSA - Advanced Linux Sound Architecture: Could not get/set settings from/on resource

aplay US122-24bit-48k.wav (the wav from the alsa wiki):

Playing WAVE 'US122-24bit-48k.wav' : Signed 24 bit Little Endian in 3bytes, Rate 48000 Hz, Stereo
aplay: set_params:965: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S24_3LE
SUBFORMAT:  STD
SAMPLE_BITS: 24
FRAME_BITS: 48
CHANNELS: 2
RATE: 48000
PERIOD_TIME: 56875
PERIOD_SIZE: 2730
PERIOD_BYTES: 16380
PERIODS: (4 5)
BUFFER_TIME: (227541 227542)
BUFFER_SIZE: 10922
BUFFER_BYTES: 65532
TICK_TIME: 4000

It is a notebook (Latitude X1) with an internal soundcard, which also works when I select it.

I also tried editing asound.conf, but I just found out that it just gets overwritten anyway.

Actually I just received another error in gstreamer-properties when trying it: 

Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

Yesterday it was only the "Could not get/set settings" one.

Any ideas what else I could try?

---

### Post by richardjennings on 2007-09-20
have you tried system / preferences / sound to make sure alsa is selected?

---

### Post by TMSstudio on 2007-09-21
Hi
This tutorial worked perfectly for me, currently having some problems with Jack/Ardour though, as others have mentioned above.
When I playback anything through Jack (either things I have recorded with Ardour or MP3s etc using XMMS with a Jack output plug) the playback is slowed down, to the point where everything is about a tone (in pitch) lower than it should be! Any Ideas?

TMS

---

### Post by scorpio21 on 2007-09-29
Hello everybody, I'm new to this forum and just discovered ubuntu a week ago (so far loving it!) anyway, I just follow'd the steps in this tutorial to make my us122 work but when i get to step # 4 I get this error message:

cp: target `/usr/share/alsa/firmware/' is not a directory: No such file or directory

I did the remaining steps just in case but it didn't work, btw I have a sony vaio laptop PCG-GRX550 and I plug the tascam in a usb 2.0 PCMCIA card, thanks in advance for any help you could give to me! Cheers.. :)

---

### Post by luigi6699 on 2007-10-15
i'm going crazy over this.  I followed the howto, but still no USB light.  

lsusb output includes
Bus 003 Device 013: ID 1604:8007 Tascam US-122 Audio/Midi Interface


/etc/udev/rules.d/55-tascam.rules:

```
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
```

both /lib/firmware/usx2yloader/tascam_loader.ihx and /lib/firmware/usx2yloader/us122fw.ihx exist.  

But nothing seems to happen when I plug it in!  if I run 
```
# sudo fxload -D /proc/bus/usb/003/013 -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx

# sudo usx2yloader
```
manually, the fxload runs without errors, and usx2yloader hangs.

Is there a log anywhere I can look at?  I want to see what's happening!  I'm about ready to install Ubuntu studio instead... let that deal with my driver problem.

---

### Post by meowsus on 2007-10-30
> **richardjennings said:**
> this is the revised howto: aka post1. I'd like to think this is now completely correct. I apologize for previous inaccuracies.

revision 2 /16/05/07

I have followed several tutorials that have led to success. However every one I have found requires manually introducing the Tascam to Ubuntu after a reboot or an unplug. 

This following procedure worked perfectly for me in Fiesty, is easy to do, and best of all - allows you to hot plug your Tascam, reboot & just generally take it easy.

I found the original tutorial here : [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)

Unplug the Tascam US-122 USB cable

1) ```
sudo apt-get install fxload alsa-firmware-loaders
```

2) ```
wget http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2
```

3) ```
tar xjf alsa-firmware-1.0.14rc3.tar.bz2
```

4) ```
sudo mv alsa-firmware-1.0.14rc3/usx2yloader/ /lib/firmware/
```

4b) ```
sudo cp -r /lib/firmware/usx2yloader /usr/share/alsa/firmware/
```


//revision 1

5)

```

 sudo gedit /etc/udev/rules.d/55-tascam.rules
```

the rules file is now open in gedit..

6) copy the following into the 55-tascam.rules file in gedit

```

 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

```

Save the file.


Plug in your usb cable and your tascam usb led should light up.

//revision 2

assuming it does, you can add another rule to 55-tascam.rules that automatically configures alsa to use the tascam as your default soundcard.

repeat step 5)

add below the previous rule:
```

KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"

```

Save the file

unplug / plug your tascam back in.

Now alsa should be working correctly with the tascam!

I've tested up to step 6 in Gusty (Ubuntu 7.1) and i've got the most beautiful green light blasting from my Tascam US122.

Eventually, when i figure out the mess of wires clumped behind my machine, i will move on to making the US122 my permanent external sound card.

Kudos, richardjennings. Kudos.

- Curdo 

:guitar:

---

### Post by meowsus on 2007-10-30
> **scorpio21 said:**
> Hello everybody, I'm new to this forum and just discovered ubuntu a week ago (so far loving it!) anyway, I just follow'd the steps in this tutorial to make my us122 work but when i get to step # 4 I get this error message:

cp: target `/usr/share/alsa/firmware/' is not a directory: No such file or directory

I did the remaining steps just in case but it didn't work, btw I have a sony vaio laptop PCG-GRX550 and I plug the tascam in a usb 2.0 PCMCIA card, thanks in advance for any help you could give to me! Cheers.. :)

Hey Scorpio21,

Yeah, i hit that too. What you have to do is create that directory for Ubuntu to be able to copy the necessary files into it. Just before step 4, try this.

```

sudo mkdir /usr/share/alsa/firmware/

```

The idea is that you want to "make" the directory (**mkdir** is short for "make directory") in a folder that only a superuser has write access to (that is where the **sudo** comes in).

Then you'll probably be good to proceed on with step 4. 

- Curdo

---

### Post by RgnKjnVA on 2007-11-19
Thanks already for this great thread. I would have NEVER figured this out on my own. Still have a problem though. To get Ardour to accept the US-122 as input I installed qjackctl because whatever JACK component(s)  come with Ardour2 weren't getting it done. I  was able to figure out how to patch the connections so that I can record and playback however once I'm done and shutdown JACK Controller I lose system sounds. I can still play media but I can't hear my email notification sounds from Thunderbird or the other system sounds for various events. I'm a spoiled WinXP user so I want all that and don't want to compromise. I see that the system sounds appear to run on ESD which I'm guessing is being usurped by ALSA. Anyone know how to have EVERYTHING and not reconfigure when going between Ardour and normal use? Maybe JACK controller can be used to route everything to ALSA?

It was a VERY frustrating weekend trying to get this sorted out with little knowledge of how these sound components work together. At one point I had NO sound whatsoever! It probably doesn't help that my sound device is apparently ancient. This is an off-lease Dell that I got dirt cheap. Eternal gratitude to anyone who can make all sounds, input/output 'just work'....

desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11GL [Quadro2 MXR/EX/Go] (rev b2)
02:07.0 SCSI storage controller: Adaptec AIC-7892A U160/m (rev 02)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78 )

UUGGH!  Also just discovered that the volume control on the toolbar no longer controls the volume. This is maddening.

---

### Post by Schroeder on 2008-01-06
> **meowsus said:**
> I've tested up to step 6 in Gusty (Ubuntu 7.1) and i've got the most beautiful green light blasting from my Tascam US122.

Same here. Followed Steps 1-6 and Gutsy, Tascam US-122 and Ardour are working like a charme. Thanks alot for the how-to! 

:guitar:

---

### Post by passonno on 2008-01-25
So I followed all of the steps (on a fresh Feisty install) and the US122 works fine, but JACK is now the issue.  Here's the error

ALSA: poll time out, polled for 34892754 usecs
DRIVER NT: could not run driver cycle
jack main caught signal 12
no message buffer overruns
zombified - calling shutdown handle

It usually takes a couple of minutes, but JACK crashes hard, and stops.

Any ideas as to why?

---

### Post by RgnKjnVA on 2008-01-25
That's where I'm at too. I've noticed however that if Ardour is already running JACK doesn't lock up my machine. If I try to run JACK Controller without Ardour it locks up my machine hard. Cold reboot the only recourse.

---

### Post by cingo on 2008-01-31
does anyone know how to get the us-428 to work with 64bit?

---

### Post by eel on 2008-03-08
i am at my wits end. really
i tried every how-to on the subject but nothing gives. No green light for me (sob & cry). I caught myself thinking of reinstalling windows for the first time since i changed to ubuntu. 

I got so far that my us 122 shows when i do lsusb and also when i do  cat /proc/asound/cards. Every time i connect/reconnect the card gets a different device number though. And no flashing lights.

I have the feeling something went wrong at the very beginning, for instance i have no 'firmware' folder in my usr/share/alsa but an 'alsa-firmware-1.0.15'. If i remember correctly this was because some download link was broken and i had to get the stuff somewhere else. Also i have been trying so many howtos that are all slightly different that i get the feeling that they all work half but some of the files i am supposed to create already exist with the same name but not necessarily the same content. Maybe. 

i just want to make music but i have been spending the last 2 days doing nothing but learning a lot about linux which is nice too but not nearly as satisfying as my primary goal. 

So anyone who has a thought on this or is willing to help me in general do not hesitate to make yourself heard :)

if you help me get my soundcard working you will be liked & memorized for as long as i live.

---

### Post by RgnKjnVA on 2008-03-08
Instead of going back to XP, I would try reinstalling Ubuntu and starting over if you think the problem is too many half-solutions, a phenomenon I'm familiar with as well. Other than that, it's hard to help without much info.

I'm curious to see if Hardy Heron makes audio connectivity easier. If I'm not mistaken the PulseAudio integration is supposed to make the audio config easier though I don't know what it will do to latency in a recording configuration. PA kinda sounds like JACK to me but I'm no pro at this stuff. JACK allegedly will give you a real-time environment but it simply doesn't play well with Gutsy in my experience and my latency is still running at 26ms (i.e. unacceptable). If Hardy doesn't deliver I'm considering the following as I've read it is what the Ardour dev/qa teams use...

> What is Planet CCRMA at Home?

Planet CCRMA at Home is a collection of software packages that you can add to a computer running RedHat 9 or Fedora Core 1, 2, 3, 4 or 5 to transform it into an audio/video oriented workstation (only on the 32 bit versions, Planet CCRMA has not yet been built on 64 bit versions of the underlying operating system). Here at CCRMA we use a consistent and well defined Linux environment for our daily work in audio and computer music and research. With the Planet CCRMA at Home package collection, you can easily install most of that environment on your own Linux system. 

[http://ccrma.stanford.edu/planetccrma/software/introduction.html](http://ccrma.stanford.edu/planetccrma/software/introduction.html)

---

### Post by pliktrologos on 2008-03-08
please check my last reply before trying to re-install Ubuntu: [http://ubuntuforums.org/showthread.php?p=4479394#post4479394]("http://ubuntuforums.org/showthread.php?p=4479394#post4479394")

---

### Post by theinnercityhippy on 2008-03-20
Hiya,

Just a quick update to this, the package/source in step 2 no longer exists.

It seems the latest version is found at [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)

so you'll need to add this into your code when you go through the tutorial.

Just using it now with gutsy and my trusty tascam us-122 so I'll let eveyone know if it goes well

:-)

---

### Post by passonno on 2008-04-06
Gonna post this again just in case anyone has had similar trouble.

So I followed all of the steps (on a fresh Feisty install) and the US122 works fine, but JACK is now the issue. Here's the error

ALSA: poll time out, polled for 34892754 usecs
DRIVER NT: could not run driver cycle
jack main caught signal 12
no message buffer overruns
zombified - calling shutdown handle

It usually takes a couple of minutes, but JACK crashes hard, and stops.

Any ideas as to why?
_________________

I am going to go ahead and try to delete the udev rule and connect manually to see what happens, but I don't have much hope.

---

### Post by Kisil on 2008-04-26
I just upgraded to Hardy Heron, and now my US-122 doesn't work any more.  The udev rules don't appear to be triggering at all.  When I plug in my card and run lsusb, I get:
```
Bus 001 Device 007: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw)
```

I can run fxload manually:
```
$ sudo /sbin/fxload -D /dev/bus/usb/001/007 -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx
```
and it works; lsusb returns
```
Bus 001 Device 008: ID 1604:8007 Tascam US-122 Audio/Midi Interface
```
so the firmware is loading.  The problem is that usx2yloader doesn't see the card:
```
$ sudo usx2yloader
usx2yloader: no US-X2Y-compatible cards found
```

But according to lsusb the card is there, so I'm kind of at a loss.  Anyone have any advice?

---

### Post by Kisil on 2008-04-26
It turns out I'd copied my firmware /lib/firmware/ rather than /lib/firmware/usx2yloader/ - [this thread]("http://ubuntuforums.org/showthread.php?t=734730") explains.  My lights are on and my music is playing.

---

### Post by pliktrologos on 2008-05-22
I was wondering... what will happen if I rename the **-tascam.rules with a lower number ( etc. 41-tascam.rules) instead of "/etc/udev/rules.d/55-tascam.rules" ?
Is this going to give a better priority to the usb-sound device or it will mesh it up?

---

### Post by Kisil on 2008-05-22
If I understand udev rules, and there's a good chance that I don't, the numbering affects the order in which devices load (or more precisely, the order in which their udev scripts execute).  Lowering the number will make the script run before higher numbered scripts at boot time, which really shouldn't matter except if a) other things depend on this driver, or b) this driver depends on other things.

If you're talking about runtime priority, then no, it won't change that.

---

### Post by pliktrologos on 2008-05-23
I think you're right, so if I want to change the priority that the system/kernel/cpu would use for my Tascam I'll probably have to "Renice Process..." from the System Monitor (KDE4) or the KsysGuard (KDE3). But which process is the one that manages my usb-soundcard?

---

### Post by jazzman on 2008-06-30
Just a quick observation. I had a bear of a time getting the US-122 to work with Jack. Here was the solution: I was trying to use a powered usb port. I unplugged from that and plugged directly into the computer usb port and ... PTL.... it worked! Hope this helps someone else.

---

### Post by Intolucidity on 2008-07-21
I kind of need some help. Running hardy heron, ran through the directions on the ALSA site for the tascam US-122 and the hardy heron fix. Not sure which udev rules to use. When I plug in, i get the green light, but nothing can detect it. lsusb gives me something from TEAC corp, and not the Tascam 122 interface. Did I do something wrong in the directions? Is there a log I can post to help?

---

### Post by RgnKjnVA on 2008-07-21
If you don't have any TEAC components on your machine, maybe you downloaded the wrong driver from the ALSA page. (?) I can't recall all the hoops I had to go through but seems odd that a TEAC usb device would be showing up. It wasn't listed when you initially ran lsusb I presume? 

BTW I was able to upgrade to Hardy and set up Pulseaudio using the "Almost perfect Pulseaudio set up" thread on these forums and it pretty much just worked. I was pleasantly surprised and it solved all of my Gutsy audio problems. I can pause without an annoying buzzing sound, my software mixer works now, I can play audio from multiple apps at the same time and I no longer get XINE errors in Amarok. I still don't know how to get real-time monitoring going when recording in Ardour but that's my last challenge audio-wise but I suspect I can't do it with a usb audio interface.

---

### Post by Intolucidity on 2008-07-22
I believe it initially listed a TEAC device. What would be the best way to correct this (fix driver, etc.)?

---

### Post by RgnKjnVA on 2008-07-22
oh then nevermind. I thought you meant after you'd followed the instructions a TEAC device appeared. 

Unfortunately, I'm not an expert just another US-122 user who muddled through installation. You may have already seen these in your travels but here are a couple links I bookmarked on the subject in addition to this thread. Hope it helps...

[http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

---

### Post by Intolucidity on 2008-07-22
Here is the problem, it appears that my computer is not recognizing the tascam interface...

Here are the udev rules I have
> BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"


When I lsusb, I get

Bus 005 Device 004: ID 0644:800e TEAC Corp. 
Bus 005 Device 003: ID 05ca:1836 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

But it should be

Bus 005 Device 004: ID 8006:1604 Tascam US-122 Audio/Midi Interface

Somehow, the ID numbers aren't correct...

sudo usx2yloader gives
usx2yloader: no US-X2Y-compatible cards found

cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2300000 irq 23

which is my sound card, but no Tascam. Also maybe something with /etc/asound.conf?

---

### Post by pliktrologos on 2008-09-23
> **RgnKjnVA said:**
> If you don't have any TEAC components on your machine, maybe you downloaded the wrong driver from the ALSA page. (?) I can't recall all the hoops I had to go through but seems odd that a TEAC usb device would be showing up. It wasn't listed when you initially ran lsusb I presume? 

BTW I was able to upgrade to Hardy and set up Pulseaudio using the "Almost perfect Pulseaudio set up" thread on these forums and it pretty much just worked. I was pleasantly surprised and it solved all of my Gutsy audio problems. I can pause without an annoying buzzing sound, my software mixer works now, I can play audio from multiple apps at the same time and I no longer get XINE errors in Amarok. I still don't know how to get real-time monitoring going when recording in Ardour but that's my last challenge audio-wise but I suspect I can't do it with a usb audio interface.

Well, did you managed to get Pulseaudio working on Hardy using TASCAM US-122 or with another usb audio card?

---

