---
title: "sound problem"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by De-code on 2008-07-02
Hello everybody, this is my first time using ubuntu. After my install the only thing that isn't working is the audio. I tried looking for the drivers but could not find them. When I type "lspci -v" I get this for my audio card.

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company d330 uT
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1000 [size=256]
	I/O ports at 1400 [size=64]
	Memory at fc480400 (32-bit, non-prefetchable) [size=512]
	Memory at fc480600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

your help is much appreciated.
thanks

---

### Post by hakko on 2008-07-03
Try this?

> **CanadaHeat said:**
> Ok, after installing ubuntu, I was having trouble getting my sound card to work.  After looking at several solutions on the forums here, it seemed hopeless.  Then I happened upon "Volume Control".  I had my earphones on and happened to unmute "everything" in the control panel.  Well, I just hope my eardrums are still inside my head.   :-& 

Turns out that on first install ubuntu assumes your sound card is controlled by "volume", but that wasn't the case here.  After I had sound enabled, I was almost ready to uninstall again as my sound was tinny/very crappy!  Can't watch movies/live like that...  ;)  So I decided to go back into the volume control panel once again.

Ok, now this is interesting, you know how in windows volume control, you have everything selected that you could "possibly" use, right?  Well, in ubuntu if you have checked things off that you aren't using/don't exist, then it opens all of those channels, and the sound (almost like a mic), get channelled through, so it sounds really bad.  I had to play a sound while selecting/deselecting items in here to know which one's were on my sound card, but it did work, and sounds beautifully now...

The other thing I had to do was right click on the desktop volume control, select preferences, and select the "PCM" option to control my volume from there, but over all, everything works great.

On a side note, I don't recommend using Totem for ANYTHING.  I was using that to troubleshoot most of my problems, since it was the default install.  I should have remembered from Gentoo that Xine was the be all/end all when it came to video/audio playback.  I recommend installing Xine to play media, atleast you know it works...  ;)
[http://ubuntuforums.org/showthread.php?t=15318](http://ubuntuforums.org/showthread.php?t=15318)


---

### Post by De-code on 2008-07-05
Thanks, I got it working

---

### Post by ZabiGG on 2008-07-05
Great, thanks for letting us know. To help us help people solve issues more efficiently, please mark your post Solved:

Click Thread tools 

above your first post

Then select Mark thread solved.

Thanks in advance, and welcome to Ubuntu

Z.

P.S. For getting started info, click on the "Look here" link in my signature below.

---

