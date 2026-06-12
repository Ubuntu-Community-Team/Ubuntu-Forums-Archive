---
title: "[SOLVED] How to play .dat file?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by bhadotia on 2008-05-13
I am trying to watch a movie from vcd  . The files are .dat.


I've tried  to open them with vlc ,mplayer, totem , but nothing seems to work. I've got gstreamer, w32 codecs.

Please help.

---

### Post by Inxsible on 2008-05-13
VLC does work with .dat files. I have played them.

Have you installed all the gstreamer plugins? Search for gstreamer in Add remove and install all of 'em.

How did you install VLC? did you use the medibuntu repos? If not, you will have to install the restricted codecs yourself...libdvdcss2 etc.

---

### Post by bhadotia on 2008-05-13
Yes , I've got all of them.

---

### Post by ejpyle on 2008-05-13
The problem is that so many different programs use ".dat" that it really doesn't tell you anything about the file, what it contains, or what program it belongs to. There is no standard format, and there is no standard way to interpret the contents. ".dat" is only a name and nothing more.


If you don't know what program created it.....its useless to you.

---

### Post by Inxsible on 2008-05-13
Ok. How are you starting the file to play? Are you double clicking on the .dat file? If so, have you made sure that .dat files need to be opened by VLC ?

you can do that by right clicking a .dat file and then selecting Properties. Then on the Open With tab, select VLC as the application from the list.

If VLC is not an option in the list, you can add it by searching for vlc under /usr/bin

---

### Post by Samhain13 on 2008-05-13
Try this (in VLC):

1) In the "Open..." window, select the "Disc" tab and "VCD" as Disk type.
2) Change "vcdx:///dev/cdrom0" in the Customize field into "vcd:///dev/cdrom0", removing the "x". (/dev/cdrom0 would be your CD-ROM drive, of course).
3) Tick "Stream/Save" and hit "Settings...". Tick "Play locally".

---

### Post by bhadotia on 2008-05-13
Ok I've tried the idea above (by samjh), and its still not working . I have just now tried playing the vcd on a friend's pc and its working there with wmp.

---

### Post by ejpyle on 2008-05-13
> **bhadotia said:**
> Ok I've tried the idea above (by samjh), and its still not working . I have just now tried playing the vcd on a friend's pc and its working there with wmp.

what format....on the win pc...
find that out and you can rename that DAT file to the extionsion that played on windows on your ubuntu box


another thing that you can is download this on ubuntu
[http://www.videohelp.com/tools/GSpot](http://www.videohelp.com/tools/GSpot)

it establishes what video and audio codecs are required to play any video file....

---

### Post by bhadotia on 2008-05-14
Sorry for the late reply but I went to sleep(it was geting late).

I'm still unable to play the vcd .

Any other suggestions?

---

### Post by bhadotia on 2008-05-14
Sorry , I forgot to tell: when I try opening the .dat files with Mplayer the following message comes:

   ```
Seek failed
```

---

### Post by billgoldberg on 2008-05-14
Did you install vlc from the medibuntu repo's? 

Have you tried xine instead of gstreamer?

You should really find out what type of file it is (someone gave a link for that).

*btw: who still uses vcd's?*

---

### Post by opendevlite on 2008-05-14
To play VCD on VLC

In VLC Click on File>Open Disc>VCD

Clear or Empty Device Name:

Audio Track: 0

Change vcdx in Customize to vcd

Click Ok

---------------------------------------
If you got bad audio

To fix the VCD audio

In VLC go to Settings->Preferences->Audio->Output Modules

Click on "Advanced Options" to view "Audio Output Modules"

in Audio Output Modules, select "ALSA audio output"

Click on "Save"

---

### Post by bhadotia on 2008-05-14
Hey thanks , man its playing with gxine. I tried it playing with xine but video was playing without any sound . So ,I tried opening it with gxine and it is working fine. 

Why didn't I think of trying xine:lolflag:


Anyway thanks a lot dude.

---

### Post by bhadotia on 2008-05-14
By the way opendevlite , I've tried your idea its not working.

---

### Post by opendevlite on 2008-05-15
It takes a while to load, you'll just have to wait until the video shows up.

---

### Post by bhadotia on 2008-05-15
Anyway , if gxine plays it without delay , I won't bother about using vlc.

Still, thanks.

---

### Post by bhadotia on 2008-06-22
opendevlite, thanx a lot man your idea regarding vlc really does work. But I was having problem with audio ,but  it was fixed  after following your suggestion .

---

### Post by footsoldier on 2008-11-22
hi opendevlite,

i still hv bad audio after trying your ALSA solution, the sound is like sputtering...any other options ?

---

### Post by alfannani on 2011-04-06
Hello guys.

I got problem here. I can play DAT files with mplayer and vlc both. But the problem is, it just show green screen. What step should i take to solve this problem? I tried to play it with gxine and it shows :

The xine engine failed to start. 
No demuxer found - stream format not recognised.

Anyone can help?:(

---

### Post by bhadotia on 2011-04-30
> **alfannani said:**
> Hello guys.

I got problem here. I can play DAT files with mplayer and vlc both. But the problem is, it just show green screen. What step should i take to solve this problem? I tried to play it with gxine and it shows :

The xine engine failed to start. 
No demuxer found - stream format not recognised.

Anyone can help?:(
Did you try openinig the file with totem. If you have the required gstreamer plugins totem should be able to play the file. Use the follwoing command to install all the gstreamer plugins:
```
apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by cyberfic on 2011-11-02
/dev/cdrom0 was not working for me with vlc - i tried /dev/sr0 and it worked!!!

---

