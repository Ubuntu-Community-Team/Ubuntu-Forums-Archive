---
title: "[SOLVED] Looking for FLAC&amp;gt;mp3 converter"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by paker on 2008-08-11
I installed SoundConverter. It does convert FLAC>mp3 but at 160 bit rate only. However I change mp3 encoding setting, it wouldn't budge.

If you know a better converter or solution to this problem, please help. Thanks.

---

### Post by tech0007 on 2008-08-11
'sudo apt-get install soundkonverter'

---

### Post by cozmicharlie on 2008-08-11
PACPL is another option - it offers a lot of options. It is command line but it is very easy to use.  This tutorial will help.
[http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl)

---

### Post by mc4100 on 2008-08-11
> **paker said:**
> I installed SoundConverter. It does convert FLAC>mp3 but at 160 bit rate only. However I change mp3 encoding setting, it wouldn't budge.

If you know a better converter or solution to this problem, please help. Thanks.

Have you tried changing the settings in Edit -> Preferences?
I can set MP3 to Constant Bitrate, Variable Bitrate, Average Bitrate and also change the quality (64kbps up to 256 kbps). I'm using SoundConverter 1.3.2

---

### Post by paker on 2008-08-11
Thanks for the suggestions.
1) I will install SoundKonverter and try it.
2) Commandline I really am uncomfortable with. Let me try SoundKonverter first.
3) SoundConverter 1.3.2: I downloaded SoundConverter-1.3.2.tar.gz from the source, untarred it (tar xfvz), and installed it (apt-goet install). But what I get is 1.0.1. I don't know what's going on. 

With 1.0.1, I can change bit rate for CBR. But for VBR and ABR, the max bit rate I can get is 158-159. Is SoundConverter free for low bit rate and with fee for high bit rate? HOW DID YOU GET 1.3.2?

---

### Post by mc4100 on 2008-08-11
> **paker said:**
> HOW DID YOU GET 1.3.2?
I'm testing the next release of Ubuntu, Intrepid Ibex; It's in Alpha stages (and has it's catastrophes every now and then), and that's the version in the Repo.
SoundKonverter seems like a good idea, but, although I don't recommend it due to weird dependency problems that can happen, you could manually grab the .deb from the Intrepid Repo and try to install it:
[http://packages.ubuntu.com/intrepid/soundconverter](http://packages.ubuntu.com/intrepid/soundconverter)

---

### Post by paker on 2008-08-12
I give up on SoundConverter. I downloaded 1.3.2 and installed it. But when I open SoundConverter > Help >About Sound Converter, I get version 1.0.1. I still cannot get bit rate higher than 159.

I tried SoundKonverter. It seemed to work well, but I just cannot locate the converted mp3 file. I designated the output directory (same as the source) but the mp3 file is nowhere to find. ???? Pls help.

EDIT: I restarted SoundKonverter and I got the file. Thanks for the suggestion.


PS: SECOND THOUGHT: I remember SoundConverter website reads "if gstreamer LAME plugin is in place" or something of that effect. How do I get that done?

---

### Post by cozmicharlie on 2008-08-12
> **paker said:**
> I give up on SoundConverter. I downloaded 1.3.2 and installed it. But when I open SoundConverter > Help >About Sound Converter, I get version 1.0.1. I still cannot get bit rate higher than 159.

I tried SoundKonverter. It seemed to work well, but I just cannot locate the converted mp3 file. I designated the output directory (same as the source) but the mp3 file is nowhere to find. ???? Pls help.

EDIT: I restarted SoundKonverter and I got the file. Thanks for the suggestion.


PS: SECOND THOUGHT: I remember SoundConverter website reads "if gstreamer LAME plugin is in place" or something of that effect. How do I get that done?

SoundKonverter is much better than Soundconverter IMHO.  You need to install the gstreamer plug ins to get mp3 support.  If you go to Synaptic and search gstreamer you will find them.  You will first need to enable the medibuntu repository.  These are the steps in the terminal.

Enable to medibuntu repository:  (these assume you have Hardy if you don't, then substitute your version where it says Hardy.  All the steps require you start with an open terminal.  Copy and paste the following.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
Install the gstreamer plug ins (and a few extras you will probably need)
```
sudo apt-get install alsa-oss faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs flac mencoder lame lame-extras
```

Alternatively you can install the Ubuntu Restricted Extras from Synaptic.

Enjoy

---

### Post by Drakkor on 2008-08-22
Yeah, I was interested in the same thing, but soundKonverter, with a bitrate of 320 turned the flac into 283, why, I have no idea......... :)

---

### Post by mcduck on 2008-08-22
> **paker said:**
> 
3) SoundConverter 1.3.2: I downloaded SoundConverter-1.3.2.tar.gz from the source, untarred it (tar xfvz), and installed it (apt-goet install). But what I get is 1.0.1. I don't know what's going on. 

"apt-get" doesn't install packages you download yourself. It only installs packages from repositories. So what you did is you downloaded the program source code, extracted it and then installed the version from repositories.

To install from source code you should read the instructions included in the package. In most cases the istallation requires compiling the program (running "./configure" -> "make" -> "sudo make install" in the directory where the source code is. You need the "build-essential"-package to do this.)

---

### Post by Vivaldi Gloria on 2008-08-22
I prefer foobar2000 in wine. By far the best audio conversion tool.

---

### Post by doug1212 on 2008-08-22
Or how about a perl script,

[HTML]http://robinbowes.com/filemgmt/viewcat.php?cid=4[/HTML]

Doug.

---

### Post by paker on 2008-08-30
> **Vivaldi Gloria said:**
> I prefer foobar2000 in wine. By far the best audio conversion tool.
I am trying foobar2k. How did you give the location of FLAC or LAME?

---

### Post by nothingspecial on 2008-08-30
Flac2mp3 [http://projects.robinbowes.com/flac2mp3/trac](http://projects.robinbowes.com/flac2mp3/trac)
converted a library of over 20.000 songs for me with a few keystrokes (the process took days). I can not recommend this enough. If you add 1 more album to your flac collection, flac2mp3 will find it an convert it.

However, and I`ve not tried this yet.  If you are simply converting your flacs to a format that is more compatible with mp3 players, I`m not sure about this, I believe there are a number of programs that will convert flac to mp3 on the fly. 
 I believe banshee-1, exaile and amarok will do this. ie just drag the flac into your ipod icon amd they convert it for you.
 Not tried myself `cause I already converted them yo mp3. oh well

---

### Post by Vivaldi Gloria on 2008-08-31
> **paker said:**
> I am trying foobar2k. How did you give the location of FLAC or LAME?

I attached lame. Extract it to somewhere and find lame.exe in it when foobar2000 asks.

I don't exactly remember what I did with flac. I guess I downloaded the windows version from 

[http://flac.sourceforge.net/download.html](http://flac.sourceforge.net/download.html)

and installed it somewhere using wine and showed the folder when foobar asked.

---

### Post by paker on 2008-08-31
Thank you. I will check out flac2mp3. I don't have a large music library but so far I have come up with various needs of convserion and manipulation. I have to use 4 or 5 different programs and line commands. If I can install ape, flac, and lame under wine, I will use foobar2000. It seems to be the most comprehensive audio program.

I have another question on running foobar2000. I have downloaded foobar2000.exe to desktop. It is an installation program. Should I do "wine foobar2000exe" each time I run foobar?

---

