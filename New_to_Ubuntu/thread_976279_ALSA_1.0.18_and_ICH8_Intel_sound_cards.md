---
title: "ALSA 1.0.18 and ICH8 Intel sound cards"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Xobel on 2008-11-09
Hey kids!

I've just installed the ubuntu studio audio packages
```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-devices linux-rt
```

I understand this sets up ALSA as the sound device and looking in synaptic package manager I can see that I have the latest version 1.0.18

I'm on a Dell Vostro 1510 notebook with an Intel ICH8 soundcard... Looking at the ALSA site, it says there is support for everything up to ICH7 cards from Intel, but the page says it hasn't been modified for a year. 

I've also noticed quite a few pages suggesting that support for ICH8 could be achieved by updating to ALSA 1.0.17 (they were fairly old pages).

Ubuntu seems to be recognising the soundcard (when I type ```
lspci -v | less
``` it is listed, but when testing it in system>preferences>sound (i.e. the GUI) it says

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.
```

Anyone know if the current ALSA is up-to-date with the most recent soundcards from Intel?

Hopefully this is enough info!

Xobel:popcorn:

---

### Post by Dermot Doyle on 2008-11-09
Hi, I think I have a similar problem which I haven't been able to sort out yet with help from the forum. I have a Dell Inspiron 1525 with the Intel ICH8 card and couldn't get the sound to work when I upgraded from the 19 to the 21 kernel in Ubuntu 8.04. The point is the sound worked perfectly before the upgrade and Synaptic Package Manager tells me I  have the older ASLA 1.0.16. Like you I couldn't find the ICH8 supported on the ASLA website, but the fact that my sound works perfectly on the 19 kernel (which I still use as a default) implies that your problem may not be with ASLA. Just a thought from an admittedly barely computerate newbie to Linux.

---

### Post by Dermot Doyle on 2008-11-09
Just realised I spelt 'ALSA' as 'ASLA'. Only 4 letters and I get it 50% wrong!!!

---

### Post by Xobel on 2008-11-10
Hmmmm..... what's the relationship of kernel numbers to ubuntu version numbers? I understand ubuntu is the clothes that go on the skeleton that is the linux kernel....

As far as I can make out, the problem is not with ubuntu, but with ALSA, but if I understand my linuxing right, driver software like ALSA is built into the kernel?

I really am rather confused, and probably don't have the lingo down yet. But I live in hope that someone knows what I'm talking about!

---

### Post by tikki3hill on 2008-11-10
Hi, i have the same problem as Dermot...inspiron1525...no sound after upgrading... does anyone know how to make the sound work?
im really new to this...
thanks

---

### Post by Dermot Doyle on 2008-11-10
I still haven't managed to get the sound working on mine despite following many threads on these forums. You may already know this, but if you keep pressing escape as the computer is turning on yopu will get into the boot menu and by scrolling down you can chose the earlier 19 kernel. It won't solve the problem, but at least everything will work as it did until someone comes up with a fix for us. I was also advised to download the Start-up Manager so I could set the 19 kernel as a default.
Good luck

---

### Post by bntjah on 2008-11-11
Got the same problem here with the ALSA I'm trying the realtek package but it doesn't recognise my audio card while lspci -v finds it straight away.

Googled alot of things and read through alot of threads(tryed them to) but stil nothing.

I hope someone finds a solution for this.

---

### Post by sven_wien on 2008-11-11
Hi all,

i have the same problem with my Acer Aspire 6920G and my ALC889.
Anything sorted yet?

---

### Post by bntjah on 2008-11-11
> **sven_wien said:**
> Hi all,

i have the same problem with my Acer Aspire 6920G and my ALC889.
Anything sorted yet?

was playing around with linux mint just a few minutes ago and the sound well works right out of the box at a very low level even tho every slider is put to the max :(:confused:

Edit:

Playing around with ubuntu to see what it gives.

---

### Post by 3layn on 2009-03-02
> **bntjah said:**
> was playing around with linux mint just a few minutes ago and the sound well works right out of the box at a very low level even tho every slider is put to the max :(:confused:

Edit:

Playing around with ubuntu to see what it gives.

I have the same problem, i followed some step mentioned at this forum and got the sound to work - altough it is very low even if i have the volume bar at max. :(

If anyone have some ideas how to correct this irretating issue, it whould be appriciated and very welcome.

Thanks in advance

---

### Post by aresthedog on 2009-03-02
I have the same problem with my Acer Aspire 6935G.

---

### Post by 3layn on 2009-03-02
> **aresthedog said:**
> I have the same problem with my Acer Aspire 6935G.

Yes unfortually it seems that many suffer from this problem :(
I am forced to keep my vista with a dual boot just because of this sound problem - And the only thing i want to do is to release my computer from the microsoft claws :P

---

### Post by 3layn on 2009-03-02
I might found a solution for this problem, i haven´t tested it yet tough but will do this afternoon..

[>> Here is the thread <<]("http://ubuntuforums.org/showthread.php?t=820774&highlight=low+sound")

---

### Post by 3layn on 2009-03-03
I can now say that the information in the above sent link is working like a charm ! :guitar:

---

### Post by ecrivain5 on 2009-03-18
I know this is just ubuntu forums but I have tried many different systems and found most do not recognise my ich8 card. the differences vary from no sound to very low sound...some have accepted my usb card and work well while others just produce a garbled sound effect. as the other ich cards appear to work Ok. (according to the forums) then it can only be assumed that the ich8 card came out during the version upgrades of the newer distros. I guess ALSA now needs to fix the problem asap as the internet is full of folk with the same problem. I am a newbie to LINUX and find it so frustrating that there are so many drivers, codecs etc are missing from the distros. I know it is not windows and I am happy it is not...but surely the basics should be in place .
Best wishes to all.
Brian

---

