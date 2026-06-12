---
title: "Speakers + Headphones"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Oreo Killa 225 on 2008-07-13
Well. When I plug in my headphones, to the jack, the sound comes out of both the internal speakers, and headphones. I am dual-booting Vista and Ubuntu 8.04.1, and don't have this problem with Vista.

Any help would be appreciated.

---

### Post by Giacecco on 2008-07-14
Same problem here with 7.10. I guess it is a feature rather than an issue, but I need to understand how to make it behave in the good traditional way.

---

### Post by Xerp on 2008-07-14
Sorry, dont have a fix, but thought I'd just let you know that it doesn't work that way for me. I pop in my headphones into the headphone jack and sound only comes out through the headphones...

---

### Post by LowSky on 2008-07-14
desktop or laptop?

---

### Post by jtuchscherer on 2008-07-14
Hi there, 
I have the same problem on a Lenovo laptop (3000 N100). I found my way around it by unchecking the 'External amplifier' checkbox in Switches tab of the Volume Control applet, when I need to mute the speakers but not the headphones. 
On two other laptops I own this is not an issue at all and it works as expected (muting speakers when headphones plugged in).

I hope that helps a bit.

---

### Post by hovzio on 2008-07-14
> **jtuchscherer said:**
> Hi there, 
I have the same problem on a Lenovo laptop (3000 N100). I found my way around it by unchecking the 'External amplifier' checkbox in Switches tab of the Volume Control applet, when I need to mute the speakers but not the headphones. 


I too am having this problem with sound :confused:    

I've checked out the Vol. control applet and I don't have the 'External amplifier' option, there is only an option for headphones. (Which does disable the headphones...) I have enabled everything under preferences and tried out all available sound mixers. 

I'm using a Toshiba A200 laptop and I've had the problem with gutsy and hardy. Any ideas?

---

### Post by Metallic_Silence on 2008-07-14
Im having the exact same problem you are, with the same laptop. But I'm dual booting with XP, not vista.

---

### Post by Oreo Killa 225 on 2008-07-20
jtuchscherer, I do not see the "external speaker" option, also, I am using a desktop.

---

### Post by billgoldberg on 2008-07-20
Just mute your speakers.

Anyway, I use a use headset, so I don't have that problem anymore.

---

### Post by Oreo Killa 225 on 2008-07-20
I do not know how to mute my speakers.

---

### Post by hovzio on 2008-07-20
> **billgoldberg said:**
> Just mute your speakers.

Anyway, I use a use headset, so I don't have that problem anymore.

How do I mute my external speakers when any device (headphones/set..) are plugged into the headphone jack? Sorry if this is far fetched but is there anyway to temporarily disable them by somehow disabling a driver/module. (or somehow disable them, from a hardware type level??) I have messed around with the various gnome settings and have tested virtually any combination of settings in the sound applet. Although I can disable the headphones :(

I have tried out k/x/ubuntu hardy as well as gutsy with no difference. I must add, this is the only "problem" I have encountered in ubuntu and that all else has been absolutely mind blowing:razz:

---

### Post by Juhla Mokka on 2008-08-14
I have the same problem, and it is quite annoying as I cannot listen music privately.

I have an Advent laptop. Dual booting Vista/Hardy. I had the same problem with with Gutsy. In Vista it works fine.

If I mute the speakers, headphones mute as well.
I only have the following options in 'Switches' tab: IEC958, Caller ID and Off-hook. Selecting them does not change anything.

Ideas anyone? :confused:

---

### Post by Oreo Killa 225 on 2008-08-16
Really need help, as I have tried countless solutions to no avail. This is the only thing with Ubuntu that bugs me. =\

---

### Post by beagle1 on 2008-08-17
I too have sound problem.
The laptop (Asus M6B006 centrino) is installed with Ubuntu (8.04; Linux-generic).  I get no audio sound or beep from the computer.  Every thing else is working fine.  When I checked system for audio cards, it displayed Intel 82801DB ... I went to System > Preferences > Sound, and changed settings; didn't help.  
The compuer's audio worked fine with Windows.  Thanks in advance for any help.

Beagle

---

### Post by Juhla Mokka on 2008-08-18
> **beagle1 said:**
> I too have sound problem.
The laptop (Asus M6B006 centrino) is installed with Ubuntu (8.04; Linux-generic).  I get no audio sound or beep from the computer.  Every thing else is working fine.  When I checked system for audio cards, it displayed Intel 82801DB ... I went to System > Preferences > Sound, and changed settings; didn't help.  
The compuer's audio worked fine with Windows.  Thanks in advance for any help.

Beagle
Hi, To get help I would post to another thread - this thread is about sound coming out from speakers when headphones are plugged in. Your problem sounds very different (use search for a similar problem). :)

---

### Post by beagle1 on 2008-08-18
Sorry for posting in a wrong thread.  I will re-address my question in a suitable thread.

Beagle

---

### Post by jtuchscherer on 2008-08-20
Hi there,

Sorry for not answering earlier, I didn't see that there was a follow question.

I got the 'External Amplifier' setting in the Volume Control after I enabled it in the 'Preferences'. You fin the 'Preferences' in the 'Edit' menu. 
I hope that helps.

---

### Post by Mon Jiller on 2008-08-23
I too have a Toshiba A215 series laptop and was having the same issue with sounds coming from the internal speakers as well as, in my case, the speakers plugged into the headphone jack. I was fiddling around with the settings, since I do not have the option of "External Amplifier" and found that the "Front" volume control seems to control the internal speakers. I muted it on my laptop and now only get sound from my external speakers. 

Hope this helps. 

PS If you don't see "Front" you can enable it by going to Edit --> Preferences and checking the box.

---

### Post by Juhla Mokka on 2008-09-30
I got mine (sort-of) working after changing my ALSA configuration (following this how to: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) the bit that says Choosing your model). 

However... no sound from video clips on the internet! I can hear music via Rhythmbox. Annoying. One problem solved, a new one appeared. ](*,)

---

