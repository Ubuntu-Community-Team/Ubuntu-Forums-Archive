---
title: "Pulseaudio is Destroying Linux Audio"
date: 2009-05-25
forum: Recurring Discussions
---

### Post by rookcifer on 2009-05-25
Why do some of the major Linux distros feel it is imperative that they destroy Linux audio by forcing the notoriously buggy Pulseaudio down our throats?  I left Fedora because Pulseaudio is giving me kernel failures on Fedora 11 (it's still in Beta but it is being released in like a week, so this is unacceptable).  And when I tried to remove Pulseaudio, I found out that I have to remove the entire desktop.  Pulseaudio has itself so deeply entrenched into Fedora that its just unbelievably sad.  If anyone thinks I am exaggerating (and if you have a Soundblaster Live! soundcard), then I suggest you download Fedora 11 Preview and see for yourself.  It is unusable due to kernel failures.  And a SB Live! is NOT a rare soundcard at all.  A little old, yes, but far from rare.  One person on the Fedora help forums actually told me to go buy a new soundcard!

Now, I don't mean to turn this into a Fedora bashing session, and I realize this isn't Ubuntu's problem, but it's just a matter of time before a similar pulseaudio bug hits Ubuntu and causes all hell to break loose over here.  After all, Ubuntu is, like Fedora, forcing Pulseaudio on its users. 

For instance, I installed Jaunty and then tried to remove Pulseaudio.  Well, it wanted to take "ubuntu-desktop" with it.  I allowed it to remove it and I still have a working desktop (luckily), but it can't be good to have to remove "ubuntu-desktop" nor should it be necessary.

The Pulseaudio devs must be good salesmen because they sure have sold Fedora and Ubuntu a bridge to nowhere.  Pulseaudio is good for absolutely nothing other than streaming audio to different devices or over a network, etc.  It is NOT needed for at least 90% of users with one machine and one soundcard.  So, I must ask, why is it the default when ALSA has worked so well for years?  The PA devs argue that ALSA is too complicated, but they fail to recognize that ALSA is no more complicated than installing sound drivers and using the mixer in Windows!  Essentially what they are saying is that Linux users are dumber than Windoze users.   

Bottom line: Pulseaudio is not ready for prime time and we all are being used as guinea pigs for debugging it (a dev on Fedora forums admitted this).

I asked the following questions on another Linux distro forum (and did not receive one positive review of Pulseaudio from a single person), so I will ask here as well:

How has Pulseaudio enhanced your Linux audio experience?  Has it made your life easier than ALSA?  Is the sound quality better than with ALSA?  Do you have more options in pulseaudio than you did with ALSA mixer?  Do you like **not** being able to adjust bass/treble, etc. with Pulseaudio?

---

### Post by 3rdalbum on 2009-05-26
If you argue that Pulseaudio is unnecessary for 90% of users, then I'm going to argue that Pulseaudio is trouble-free for 90% of users. It's certainly trouble-free for me.

ALSA is notoriously difficult to program with directly. With ALSA there is no easy way to control the volume of an individual program; Pulseaudio makes this easy and it's a very useful feature that I use every week.

I was never able to control bass or treble with ALSA; I didn't know that anyone could. Pulseaudio is a userspace daemon that works on top of ALSA, so any controls that ALSA provides should still be able to be used.

One of the big aims of Pulseaudio was to stop the current situation with different sound systems locking the audio output device. I haven't observed this "locking" happening since Ubuntu 8.04, so I'm happy.

I just literally don't see any problems. It's safe to remove the "ubuntu-desktop" package, by the way; but it's also unnecessary to remove the pulseaudio package even in Fedora. You can just stop PA from loading in the first place.

---

### Post by mikewhatever on 2009-05-26
I think it is the matter of moving forward and being innovative. New technologies are cool, they draw attention, pulseaudio sound server, wow, awesome. A distro that doesn't include pulseaudio would probably be labeled conservative, old, stagnated. I really hope it does work for most users, however, it strikes me as odd that the GUI for utilizing all of its great features isn't installed by default. How exactly am I supposed to know that the pavucontrol package will let me control volume per application?
That said, I am not against PA. It's very simple to remove it, and right after, everything works as expected.

---

### Post by HappyFeet on 2009-05-26
I also  am experiencing no issues with pulse audio.

---

### Post by Kareeser on 2009-05-26
ubuntu-desktop is a meta package. You can remove it, mangle it, vandalize it to echo "rookcifer rulez!", and it will wouldn't do anything.

---

### Post by Seq on 2009-05-26
I also have no problems with Pulse Audio on a laptop with Intel HDA and a desktop with Asus Xonar DX. Furthermore, software like earcandy is rather cool, and not possible without a system like pulseaudio. Also note that newer versions of gnome (2.6.27 branch, for example) will have better volume control for pulse. Everything takes time.

As for feeling like a guinea pig -- welcome to Desktop Linux. The old mantra rings true: release early, release often. If you only wish to use things that have been previously stablized, there is always RHEL and Debian Stable.

Also note that removing ubuntu-desktop may cause upgrade problems in the future.

---

### Post by zenithdave on 2009-05-26
I would have agreed with you a year ago when i started tinkering with Ubuntu however it has improved lots since then.

I don't know if it's the same now but i just used to go to synaptic and uninstall the Pulseaudio server on every install i did until Jaunty.

It still prefers my on board realtek audio card to my Midiman delta [-(

---

### Post by urosg3 on 2009-05-26
Pulseaudio is huge step forward IMHO. Sound its just better with pulse...

Btw sorry for Fedora, its great distro.

---

### Post by cb951303 on 2009-05-26
8.10 and 9.04 are the only ubuntu releases I could listen to music while a flash movie was open in firefox. I have fewer problems with pulseaudio than I had with esound/alsa

---

### Post by Zaiden on 2009-05-26
Ever since I started using Ubuntu (Around 8.10), Pulseaudio has always caused a delay in sound for everything, and it still has this issue in 9.04(and still no fix/workaround). Making it an optional install would be great instead of making it default. Otherwise, this is the only issue that keeps me from switching to Ubuntu.

---

### Post by Sef on 2009-05-27
This is not a new opinion.   There have been others who have posted the same complaint, so recurring discussion it goes.

---

### Post by Swarms on 2009-05-27
> **Zaiden said:**
> Ever since I started using Ubuntu (Around 8.10), Pulseaudio has always caused a delay in sound for everything, and it still has this issue in 9.04(and still no fix/workaround). Making it an optional install would be great instead of making it default. Otherwise, this is the only issue that keeps me from switching to Ubuntu.

If the minority has problems with PA, why change the OS for the majority?
You have an option to uninstal it anyways.

---

### Post by gnomeuser on 2009-05-27
[Interview with the PA lead developer](http://jaboutboul.blogspot.com/2009/05/sound-of-fedora-11.html) which should shine some light on the subject.

---

### Post by mikewhatever on 2009-05-27
> **Swarms said:**
> If the minority has problems with PA, why change the OS for the majority?
You have an option to uninstal it anyways.

You don't know those having problems with PA are a minority. The number of people speaking in favour of PA in this thread is obviously irrelevant. 
On the same note, had PA not been installed, you would have had an option to install and use it. PA is not fully functional even in Jaunty, simply for the lack of pavucontrol package and various little glitches. It would be a great thing once stabilized and fully functional, but meanwhile, is a bad choice. Ubuntu is too popular a Linux disrto to serve as a testing ground. It should just work, for as many users as possible, especially for new users that may not know why and how to remove PA.

---

### Post by aysiu on 2009-05-27
> **Kareeser said:**
> ubuntu-desktop is a meta package. You can remove it, mangle it, vandalize it to echo "rookcifer rulez!", and it will wouldn't do anything.
I second the motion.

*ubuntu-desktop* is just a pointer to the default set of packages. If you remove one of the default packages, the pointer goes away. That's it. No harm done.

I've removed Pulse Audio from my Ubuntu installation, and I've had no problems removing it or seen any adverse effects from removing it.

---

### Post by Swarms on 2009-05-27
> **mikewhatever said:**
> You don't know those having problems with PA are a minority. The number of people speaking in favour of PA in this thread is obviously irrelevant. 
On the same note, had PA not been installed, you would have had an option to install and use it. PA is not fully functional even in Jaunty, simply for the lack of pavucontrol package and various little glitches. It would be a great thing once stabilized and fully functional, but meanwhile, is a bad choice. Ubuntu is too popular Linux disrto to serve as a testing ground. It should just work, for as many users as possible, especially for new users that may not know why and how to remove PA.

Sure it is a minority, yet a very vocal and noisy minority.

---

### Post by kerry_s on 2009-05-27
i prefer alsa.

---

### Post by Bios Element on 2009-05-27
> **mikewhatever said:**
> You don't know those having problems with PA are a minority. The number of people speaking in favour of PA in this thread is obviously irrelevant. 
On the same note, had PA not been installed, you would have had an option to install and use it. PA is not fully functional even in Jaunty, simply for the lack of pavucontrol package and various little glitches. It would be a great thing once stabilized and fully functional, but meanwhile, is a bad choice. Ubuntu is too popular Linux disrto to serve as a testing ground. It should just work, for as many users as possible, especially for new users that may not know why and how to remove PA.

Probably because pulseaudio saves you from the mess that having 3+ different sound servers cause. But by all means if you enjoy that just disable it and have fun...Can't say it's a good idea though.

---

### Post by mikewhatever on 2009-05-27
> **Bios Element said:**
> Probably because pulseaudio saves you from the mess that having 3+ different sound servers cause. But by all means if you enjoy that just disable it and have fun...Can't say it's a good idea though.

Personally, I have had no problem with removing PA from the last three releases I used to fix sound issues. It was a very, and I mean **very**, good idea, as the only thing PA saved me from was sound working by default.

---

### Post by rookcifer on 2009-05-28
> **3rdalbum said:**
> ALSA is notoriously difficult to program with directly. 

The PA developers say the same thing.  It might be true, I don't know, but this doesn't help the end user.

> With ALSA there is no easy way to control the volume of an individual program

I assume you mean control the volume of more than one program at a time.  No, it doesn't seem this is possible with ALSA, but really, who does this?  And why?  If I have music playing and I want to watch a youtube video, I turn my music down.  I really see no need for the "modular" sound approach unless one is trying to stream to other devices or something of that sort.  But those people are far from the majority.

> I was never able to control bass or treble with ALSA; I didn't know that anyone could. 

Hmm.  I am not a Linux sound expert, but I have always been able to control every possible mixer setting on my soundcard by using nothing other than ALSA and the kernel driver for my sound card (emu10k1).  This includes bass/treble.  I have the same complaint as you though -- I can't adjust *anything* but volume with pulseaudio enabled!

> Pulseaudio is a userspace daemon that works on top of ALSA, so any controls that ALSA provides should still be able to be used.

In theory, yes.  But, why add this extra layer to complicate things?  I have always noticed sound improvements once I disabled Pulseaudio.  Besides not being able to adjust bass/treble with PA enabled, I also notice that my sound is more likely to cut-out or to crackle when I am moving around windows in X.  Never happens after I disable PA.

> I just literally don't see any problems. It's safe to remove the "ubuntu-desktop" package, by the way; but it's also unnecessary to remove the pulseaudio package even in Fedora. You can just stop PA from loading in the first place.

That's what I thought, too.  In Fedora 10, this works (you can even remove all Pulseaudio packages, including the libraries without having to remove the desktop).  If I remove PA from F10, I have full control over my mixer settings again.  In Fedora 11 Preview, you can remove all PA packages *except* for the libraries.  If you try to remove them, you must remove the entire desktop (in my case, KDE).  And even if I remove all PA packages except for the libs, I still cannot adjust my mixer settings (even the volume cannot be adjusted).  So, something has changed from F10 to F11 -- they have sunk PA's tentacles even deeper.

(Let me just say I like Fedora and by no means am trying to bash the distro as a whole.  The devs over there do some very excellent work, especially on the security front.  I am in fact on a Fedora 10 box right now.  My complaint is against pulseaudio).

---

### Post by rookcifer on 2009-05-28
> **Seq said:**
> Also note that newer versions of gnome (2.6.27 branch, for example) will have better volume control for pulse. Everything takes time.

I hope so.  As someone else pointed out, it is strange that the PA controls (pavucontrol, etc.) are not installed by default (either on Ubuntu or Fedora).  Why?  All this does is confuse users who wonder why gnome-mixer or Kmix will not adjust the volume.  Moreover, I hate having to open the menu navigate over to pavucontrol and then take the time to adjust the volume.  I want it in my taskbar where I have immediate access to it.  Someone told me this can be done, but why isn't it done by default?

> As for feeling like a guinea pig -- welcome to Desktop Linux. The old mantra rings true: release early, release often. If you only wish to use things that have been previously stablized, there is always RHEL and Debian Stable.

Or Gentoo's stable tree.  I am a former Gentoo user and love it, but I decided I wanted to go with a binary distro so that things just work without configuration.  I got tired of all the compiling, etc.

---

### Post by cb951303 on 2009-05-28
> **rookcifer said:**
> 
In theory, yes.  But, why add this extra layer to complicate things?  I have always noticed sound improvements once I disabled Pulseaudio.  Besides not being able to adjust bass/treble with PA enabled, I also notice that my sound is more likely to cut-out or to crackle when I am moving around windows in X.  Never happens after I disable PA.


you always need the extra layer whether it's PA, esound or kde's old daemon arts if you want to be able to run audio applications simultaneously. ALSA, out of the box, doesn't provide audio mixing feature.

PA, contrary to other daemons such as esound provides consistent API to developers (along with software audio mixing) which IMHO is the single most important thing that should be done audio-wise in linux. We have literally 10s of libraries that do the same thing. PA will eventually reduce it to 1

Other features such as modular volume control are just perks...

---

### Post by Seq on 2009-05-28
> **rookcifer said:**
> Or Gentoo's stable tree.  I am a former Gentoo user and love it, but I decided I wanted to go with a binary distro so that things just work without configuration.  I got tired of all the compiling, etc.

I switched over from Gentoo as well. I fired up a Warty disc and realized it was extremely similar to the Gentoo system I took a week or so to build. Including all the "project utopia" stuff like Hal that everybody was having problems with...

---

### Post by Foster Grant on 2009-05-30
Add me to the list of Ubuntu users who can happily take a WFM attitude when one guy out of 500 complains about Pulseaudio. When I upgraded from 7.10 to 8.04, it actually fixed a couple of sound issues I had in 7.10.

---

### Post by Mr. Picklesworth on 2009-05-30
And it isn't just changing volumes for individual applications. It's abstraction to the point you can move a particular stream for a particular application to another output device (eg: a headset) without a hiccup and without the application needing to care.

---

### Post by WatchingThePain on 2009-05-30
Pulseaudio promises a lot and maybe one day it will deliver.
Until then Alsa is what I'm using.

---

