---
title: "HOWTO: Installing lmms in Breezy"
date: 2005-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by SFN on 2005-10-04
The instructions I had posted here are terribly outdated and incorrect. You should use the instructions [here]("http://ubuntuforums.org/showthread.php?t=91620&highlight=lmms") now.

As a matter of fact, should an admin wish to delete this thread entirely, they may do so.

---

### Post by SFN on 2005-10-05
Having played with this a bit now, I can say that it appears to be quite stable. My familiarity with Fruity Loops is somewhat limited but I seem to be able to do all of the things that I've done in Fruity Loops with lmms.

The interface is functionally similar to Fruity Loops in that you do the same tasks in pretty much the same way in both programs. The difference is that lmms is more cartoonish in a KDE sort of way, whereas the Fruity Loops interface has more of a slcik, professional angle to it. In this case though, the cartoons work as it's easier (for me anyway) to find things when they have Big Shiny Buttons(tm). After getting used to where everything is, I may find the lmms interface a bit garish. (Hmmm, skinning would be nice)

The preset sounds that come with lmms are a little more amateurish than with Fruity Loops but that seems to be no big deal as the samples are just OGGs grouped together using an XML file. I'd imagine that creating my own packs would be very simple.

All in all, I'd recommend this to those wanting the abilities of Fruity Loops in Ubuntu.

---

### Post by Stealth on 2005-10-12
Hmm, I've compiled my own LMMS w/o disturbing that libqt3 under Kubuntu 5.10. Should I try and post it up somewhere and see if it works? I used checkinstall so it gave me a nice lil deb...

---

### Post by SFN on 2005-10-12
[QUOTE=Stealth]I used checkinstall so it gave me a nice lil deb...[/QUOTE]

Odd. I used the deb that the lmms folks posted. So the deb and the tar have different dependencies? 

At any rate, yes. Go ahead and post what you've got. Anything to make the process smoother.

---

### Post by Fade on 2005-10-12
I compiled and installed LMMS (lmms-0.1.1) without a prob.

Except I ran into a prob getting it 'started'.

I went threw the setup dialog fine, but now when I go to run the LMMS the splash screen shows up and it poops out on me.

When I tried it from the command line I received the fallowing:


audioOSS: failed opening audio-device
Mutex destroy failure: Device or resource busy
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
Playback open error: Device or resource busy
Mutex destroy failure: Device or resource busy
Segmentation fault

Any ideas? :???:

[ EDIT ]

My sound on my comp seems to be working fine and all my players seem to function fine also. I've rebooted and still same error from LMMS. I did have a small issue with XMMS when I first installed it... I had to set the audio to ESD from OSS.

[Re-Edit] Blah., its working fine now :-S LoL... must have been a fluke.

---

### Post by halus on 2005-10-18
[QUOTE=Stealth]Hmm, I've compiled my own LMMS w/o disturbing that libqt3 under Kubuntu 5.10. Should I try and post it up somewhere and see if it works? I used checkinstall so it gave me a nice lil deb...[/QUOTE]

Ey, I want that deb :) 
Any luck posting it somewhere?
Can you possible attach it to this thread?
Or send it to me as Private Message?

Tried to compile it myself, but compilers never likes me, and/or I do not understand anything :(
@ubuntu:~/lmms-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

---

### Post by halus on 2005-10-19
Ok, I needed some compile-programs (not sure exactly which), and have LMMS installed now. I think I like what I see after a couple of minutes playing. Big thanks for the pointer.

Also thanks for the pointer to checkinstall. simple(if you have the required compiler programs that is):
,/configure
make
sudo checkinstall
sudo dpkg -i some.deb

and package is installed and ready to run. I am no longer afraid of compiling programs my self. Thanks

---

