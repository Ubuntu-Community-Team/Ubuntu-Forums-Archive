---
title: "How to install the Microsoft VX-1000 webcam"
date: 2009-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by N_Nick on 2009-11-21
I recently bought a Microsoft VX-1000 webcam and spent a few hours trying to install it.  Since i was successful (at least for the video part) i wanted to share the steps i followed with everyone:
 

1. Download the gspca driver from: linuxtv.org
```
# wget http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz
```

2. Navigate to the directory where you saved the driver and extract it:
```
# tar zxvf tip.tar.gz
```

3. Enter  the new directory and the v4l subfolder:
```
# cd v4l [tab]
# cd v4l

```
4. ```
# make
```

If make returns errors edit the .config created in the same directory and change:

```
CONFIG_DVB_FIREDTV=m
```

to

```
CONFIG_DVB_FIREDTV=n
```

save and run “make” again.

5.```
 # sudo make install
```

6. Blacklist the sn9c102 module by editing /etc/modprobe.d/blacklist-custom and adding:
```
blacklist sn9c102
```

Save and reboot.

Your webcam should work now. Test it with Cheese.


**[SIZE="4"]Skype[/SIZE]**

Here's what i did to make it work with Skype:

1.  Create a file - i named it webcamSkype - with the following in it:
```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so && skype
```
2.  Make it executable:
```
# chmod +x webcamSkype
```
3. Create a launcher on your panel to launch that script.

Your webcam should work with Skype now.

Since the gspca driver supports a lot of webcams i am assuming this would work with other webcams as well. 

I couldn't get the microphone to work yet, if someone got it to work please let us know how.

Thanks to Andrè and Danny for the help

---

### Post by zillacles on 2010-03-11
Run cat /proc/asound/pcm

My result:

> zillacles@zillacles-linux-PC:~$ cat /proc/asound/pcm
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 3
00-01: AD198x Digital : AD198x Digital : playback 1 : capture 1
01-00: USB Audio : USB Audio : capture 1


Look for the USB audio one (could be more than one but try them all with the next step), and note the number in front.

Then run: alsamixer -D hw:1

where 1 is from the "01-00" in front of the device name. 

Press m in the first screen, then press tab and turn the capture all the way up.

Now sound is working for me as well as video in Karmic x64 with the VX-1000 cam in Skype.

---

### Post by executorvs on 2010-03-13
this was a no go for sound in lucid with the vx-3000 :-(

---

### Post by zillacles on 2010-03-14
What does cat /proc/asound/pcm show?

---

### Post by executorvs on 2010-03-16
s@SDF-1:~$ cat /proc/asound/pcm
00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1
00-02: ALC888 Analog : ALC888 Analog : capture 1
01-00: USB Audio : USB Audio : capture 1


sorry for the delay I seem to have forgot to mark the thread to notify me... oops

---

### Post by zillacles on 2010-03-16
what about when you run :

alsamixer -D hw:1 ??


BTW, somehow my mic works in the Skype call tester, but not in an actual call. Haven't figured that out yet

---

### Post by executorvs on 2010-03-16
I tend to use the gnome-alsa-mixer application myself but same info, capture set at max auto gain is off.

---

### Post by zillacles on 2010-03-20
Hmm not sure. In the sound preferences I can see the mic is picking up sound. Haven't actually tried to record anything though, only time I've heard something played back to me is in the Skype test call thing. In an actual call somehow the meter in sound preferences ceases to show anything being captured :/

---

### Post by executorvs on 2010-03-20
Other places you can check to make sure it show up are:
@comp:~$ arecord --list-devices gives
@comp:~$ cat /proc/asound/camera/stream0
@comp:~$ cat /proc/asound/pcm
@comp:~$ lsmod | grep snd

sound wise I've also checked every setting I can think of alsa-mixer, padevchooser, gstreamer-properties, asoundconf-gtk(couldn't get this one to load), paprefs, and gnome volume. camera is shown in all, set as default input in all, capture and volume are turned up in all, and still nothing.

sense you hear yours in skype sometimes maybe one of these will help you.

---

### Post by zillacles on 2010-03-20
Shows up in all of em[B]

zillacles@zillacles-linux-PC:~$ arecord --list-devices[/B]
> **** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: camera [USB camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zillacles@zillacles-linux-PC:~$ cat /proc/asound/camera/stream0
USB camera at usb-0000:00:1d.7-4.1, full speed : USB Audio

Capture:
  Status: Stop
  Interface 2
    Altset 1
    Format: S16_LE
    Channels: 1
    Endpoint: 4 IN (NONE)
    Rates: 8000, 16000

[B]
zillacles@zillacles-linux-PC:~$ cat /proc/asound/pcm
[/B]> 00-00: AD198x Analog : AD198x Analog : playback 1 : capture 3
00-01: AD198x Digital : AD198x Digital : playback 1 : capture 1
01-00: USB Audio : USB Audio : capture 1
[B]
zillacles@zillacles-linux-PC:~$ lsmod | grep snd
[/B]> snd_hda_codec_analog    81408  1 
snd_hda_intel          31264  2 
snd_usb_audio         102496  1 
snd_hda_codec          89888  2 snd_hda_codec_analog,snd_hda_intel
snd_usb_lib            20608  1 snd_usb_audio
snd_pcm_oss            44096  1 
snd_mixer_oss          18944  2 snd_pcm_oss
snd_pcm                91912  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3556  0 
snd_seq_oss            33632  0 
snd_seq_midi            8320  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                61312  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            27104  2 snd_usb_lib,snd_seq_midi
snd_timer              25840  2 snd_pcm,snd_seq
snd_hwdep               9448  2 snd_usb_audio,snd_hda_codec
snd_seq_device          8500  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    77576  18 snd_hda_codec_analog,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_usb_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi,snd_timer,snd_hwdep,snd_seq_device
soundcore               9088  3 snd
snd_page_alloc         10960  2 snd_hda_intel,snd_pcm



Thanks for that padevchooser, seems handy. Though the volume meter in that shows the mic working o.O . 

I think I might be having a different problem though, because even when I plug in an actual mic into the 3.5mm port, I can't hear any feedback. Haven't really looked into it much though. Have no time so I just have to restart into Windows to use Skype :shock:

---

### Post by kyleabaker on 2010-03-22
I have a vx-1000 and I'm seeing the same output as you @zillacles. Still no sound though.

Anything else to check?

EDIT: I'm running Lucid x64 btw.

---

### Post by mhouston100 on 2010-04-19
Video working fine, had this cam for a while but only just plugged it in on an up-to-date install of karmic 32 bit (Kernel 2.6.31-21-generic).

Video worked out of the box no problems so far, mic shows up fine but no input detected no matter what app is used.  Followed quite a few different approaches but still no good. 

Anyone end up with a working response for sound?

Interestingly, running a Win XP virtual machine, the mic and cam both are working fine, but still no good on the host system, strange.

---

### Post by kyleabaker on 2010-04-19
> **mhouston100 said:**
> Video working fine, had this cam for a while but only just plugged it in on an up-to-date install of karmic 32 bit (Kernel 2.6.31-21-generic).

Video worked out of the box no problems so far, mic shows up fine but no input detected no matter what app is used.  Followed quite a few different approaches but still no good. 

Anyone end up with a working response for sound?

Interestingly, running a Win XP virtual machine, the mic and cam both are working fine, but still no good on the host system, strange.

I'm following several vx-1000 webcam threads and thus far none of them seem to have a solution to the microphone issues. I wish we could get someone knowledgeable to take a look deeper into this. Until that happens, I'm afraid you've hit the end of the road for this webcam and audio. Audio isn't working in Ubuntu 10.04 either. :/

---

### Post by mhouston100 on 2010-04-20
I still find it pretty incredible that it will work under a client OS in Virtualbox but not on the host Ubuntu os... obviously the hardware is working etc, may just be a problem with the mixer instead...

---

### Post by kyleabaker on 2010-04-20
> **mhouston100 said:**
> I still find it pretty incredible that it will work under a client OS in Virtualbox but not on the host Ubuntu os... obviously the hardware is working etc, may just be a problem with the mixer instead...

I've dug around long enough to lose some hair over it, but if you come across a setting that enables the mic then please do share! I've tried everything I could find dealing with the mixer, but I could have missed something.

---

### Post by EkoBR on 2010-05-25
Same problem with mic here on ubuntu 10.4

Note:  that it work under ubuntu 9.04.

The update broken it :mad:

---

### Post by kyleabaker on 2010-05-25
With no solutions to this problem in sight, I'm beginning to think that the last resort would be to contact the developer(s) behind v4l and see if they know what is wrong and why this webcam isn't registering the mic as it should.

Anyone know how to get in touch with the v4l developer(s)?

---

### Post by ubam on 2010-06-03
Any solutions for 10.04 32 bits? My mic stills off...:mad:

---

### Post by executorvs on 2010-06-10
For the VX-3000,
I've got the mic working in lucid. I have tested it in sound recorder and used it in skype. I'm sure of two steps used in getting it to run, but there may be remnants from weeks of tinkering I'm not sure of.

1.)I am using kernel 2.6.35-1.1 from the kernel testing ppa
2.)in order to get sound in skype you must install padevchooser and run it before opening skype.

if someone could try these steps and let me know how things go it would be appreciated. I'm going to try isolating what exactly is enabling the mic and will post more later.

---

### Post by Mr Roboto on 2010-06-11
You are a legend!!

I installed the latest kernel from the PPA, and the mic on my VX-1000 works now.
For those playing at home I added the PPA:

```

sudo apt-add-repository ppa:kernel-ppa/ppa
sudo apt-get update

```

Then add the kernel:
```

sudo apt-get install linux-image-generic-lts-backport-maverick
sudo update-grub2

```

I'm not sure if that's the appropriate kernel to use, but it does get you the latest one so I think it's right.  The second line is because my installation doesn't seem to update grub after installing a new kernel.

Reboot (a couple of times to get the nVidia drivers going, but that's not relevant here!) and the mic is working.  I did not need to use padevchooser.

I still have a drama in Skype where pressing the 'test' button in the video settings causes a segfault (which it never used to do, and I'm using the v4l compat library preload like before), but the sound works now.  Video still works in Cheese.  So that's my new challenge to solve.

---

### Post by executorvs on 2010-06-11
I'm using linux-image-2.6.35-1-generic version 2.6.35-1.1~lucid1 and am not having any seg faults. I'm also running 64bit.

the reason I need to use padevchooser is because pulseaudio isn't detecting the mic correctly and I need to run a local sound server in order to pass the alsa input through to pulse. If skype let me select something other than pulseaudio for my sound it might not be an issue.

---

### Post by Mr Roboto on 2010-06-11
Okay.  Turns out my nVidia drivers hadn't been installed properly because I didn't include the kernel headers when I installed the new kernel.  I was using the Nouveau drivers by default.  When I moved to the nVidia drivers the segfaults stopped and the video test worked.  The mic also worked in the pulseaudio controls, and I could do a Skype loopback test call fine.

...BUT... the mic only works until the camera is turned on.  Once I do the video test, the mic stops working.  The audio level in the pulseaudio settings doesn't move from zero.  So that's pretty odd - the mic works until you turn the video on, then it stops.  That's got me stumped.

---

### Post by Mr Roboto on 2010-06-14
Just to clarify...
1. Install kernel 2.6.35-2-generic #3~lucid1-Ubuntu SMP
2. Open Sound Preferences, and select Input tab.
3. Make noise - input level meter goes up and down.
4. Start video app (doesn't matter which) in this case Cheese.
5. Video displayed on screen, but making noise no longer moves input level meter in Sound Preferences.
6. Close down Cheese, and input level meter still not responding.

---

### Post by Mr Roboto on 2010-06-14
Okay, with a bit of further testing I can confirm that this has something to do with the gspca_sonixj module.

When the sound stops working I remove it:
```
sudo rmmod gspca_sonixj
```

Microphone is still not working in PA.  Add the module back in:
```
sudo modprobe gspca_sonixj
```
and the microphone starts working again.

So I think I need to report this bug, but I'm not sure it's an Ubuntu bug but more of an upstream kernel module bug.  Anyone have any suggestions as to where to report it?

---

### Post by kyleabaker on 2010-07-05
> **Mr Roboto said:**
> Okay, with a bit of further testing I can confirm that this has something to do with the gspca_sonixj module.

When the sound stops working I remove it:
```
sudo rmmod gspca_sonixj
```

Microphone is still not working in PA.  Add the module back in:
```
sudo modprobe gspca_sonixj
```
and the microphone starts working again.

So I think I need to report this bug, but I'm not sure it's an Ubuntu bug but more of an upstream kernel module bug.  Anyone have any suggestions as to where to report it?

I'm testing in Maverick right now, but to keep this on topic...my kernel build is only a bit newer than the one you've tested with and I'm getting the exact same mic problem you're getting.

I posted some log info here for the Maverick forum:
[http://ubuntuforums.org/showthread.php?t=1516541](http://ubuntuforums.org/showthread.php?t=1516541)

Where should this bug be reported? I've joined the gspca mailing list and posted to it about this, but am not expecting them to reply with any help. Any ideas?

---

### Post by kyleabaker on 2010-07-07
The webcam driver maintainer has suggested a way to fix this if anyone else wants to try and help me get something working. I'm sure if we get this working he will push an update soon. More details here:

[http://ubuntuforums.org/showthread.php?t=1516541&p=9560552](http://ubuntuforums.org/showthread.php?t=1516541&p=9560552)

---

### Post by kyleabaker on 2010-07-12
I've posted a patch to fix the Microsoft LifeCam VX-1000 where the microphone stops working or doesn't work at all.

Please test this patch and let me know if it fixes your webcam. It may also fix the Microsoft VX-3000 if it is having mic problems where the microphone stops working.

All the details are here:
[http://ubuntuforums.org/showthread.php?p=9581593#post9581593]("http://ubuntuforums.org/showthread.php?p=9581593#post9581593")

---

