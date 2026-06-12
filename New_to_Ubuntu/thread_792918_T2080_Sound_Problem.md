---
title: "T2080 Sound Problem"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by doineedlinux on 2008-05-13
In vista the sound is high def
but in ubuntu the sound is very very low
very very low on youtube

please help
because all my hardware works but this one sound problem:(:(

---

### Post by NR1224 on 2008-05-13
I assume that the T2080 referenced is an emachines, try going into preferences->sound and making sure you are using the right drivers. Also try searching for high def drivers in synaptic

---

### Post by doineedlinux on 2008-05-13
Toshiba Laptop

---

### Post by Inxsible on 2008-05-13
> **doineedlinux said:**
> i have a t2080 toshiba laptop and i get very low sound
when in windows my sound is like HD loud

please someone help because i really like ubuntu but i can't really even hear youtube videos that good with ubuntu so i might go wiped the drive and reinstall vista in a few hours if i can't get this fixedType in ```
alsamixer
``` into a terminal and max out all the volumes there.

If such a small problem can make you go back to Windows, then I guess you should. Linux needs much more commitment than that. And in any case, if you are stumped, you can always ask on the forums.

---

### Post by philinux on 2008-05-13
> **doineedlinux said:**
> i have a t2080 toshiba laptop and i get very low sound
when in windows my sound is like HD loud

please someone help because i really like ubuntu but i can't really even hear youtube videos that good with ubuntu so i might go wiped the drive and reinstall vista in a few hours if i can't get this fixed

Which version of ubuntu are you using?

also post the output of 
lspci

---

### Post by SunnyRabbiera on 2008-05-13
and you tried all the volume maximizers out there right?
the volume control applet has a lot of hidden things in it, did you open up volume control and go into preferences and see if you can get all the audio adjusters checked?
you may want to play around with it.

---

### Post by doineedlinux on 2008-05-13
> **philinux said:**
> Which version of ubuntu are you using?

also post the output of 
lspci

latest
x86

---

### Post by doineedlinux on 2008-05-13
> **SunnyRabbiera said:**
> and you tried all the volume maximizers out there right?
the volume control applet has a lot of hidden things in it, did you open up volume control and go into preferences and see if you can get all the audio adjusters checked?
you may want to play around with it.

yeap

---

### Post by Het Irv on 2008-05-13
> **doineedlinux said:**
> latest
x86

Thats all you got when you typed lspci in the terminal?  That doesn't seem right.

---

### Post by doineedlinux on 2008-05-13
> **Het Irv said:**
> Thats all you got when you typed lspci in the terminal?  That doesn't seem right.

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

---

### Post by NoviceNotesdotNet on 2008-05-13
i realize my too sense two follows basically an issue of "convenience, and preference (the illusion of a broken box, notwithstanding)" vs. "let's rig this thing so i can hear something already!"...

but...
have you tried your ipod earbuds, inserted into the 'phones' jack of the hardware itself [uh... earbuds, headset, or whatever it is y'all use these days... we used to call 'em "headphones"]

PS. i was going to allude to "Signal to Noise Ratio", but i'm afriad such a pun, though i revel in its ironic quality, t'would be borderline crass. uh oh... ! hee hee
:-)

---

### Post by doineedlinux on 2008-05-13
> **NoviceNotesdotNet said:**
> i realize my too sense two follows basically an issue of "convenience, and preference (the illusion of a broken box, notwithstanding)" vs. "let's rig this thing so i can hear something already!"...

but...
have you tried your ipod earbuds, inserted into the 'phones' jack of the hardware itself [uh... earbuds, headset, or whatever it is y'all use these days... we used to call 'em "headphones"]

don't have any
but why use a headset when i have 2 high def speakers on my laptop

---

### Post by Ender305 on 2008-05-13
check to see what sound drivers you are using, of if there are proprietary ones available

---

### Post by Het Irv on 2008-05-13
Its weird, I can't find anyone with the same problem as you, in any disto. Have you checked your speakers to make sure that nothing got changed by mistake on them?

---

### Post by Ender305 on 2008-05-13
before wiping your whole hd, make a windows live cd and try to see if the sound works in windows, if it doesn't, you have a pair of broken speakers

---

### Post by doineedlinux on 2008-05-13
> **Ender305 said:**
> before wiping your whole hd, make a windows live cd and try to see if the sound works in windows, if it doesn't, you have a pair of broken speakers

it does and in HD

---

### Post by Ripfox on 2008-05-13
> **Ender305 said:**
> before wiping your whole hd, make a windows live cd and try to see if the sound works in windows, if it doesn't, you have a pair of broken speakers

How do you make a windows live cd? Link?

---

### Post by Ender305 on 2008-05-13
try _[this](http://www.nu2.nu/pebuilder/)_, my friend told me he used one, but I can't remember if it was this, I just looked this up on google

---

### Post by Gordon Bennett on 2008-05-13
Open and edit

**/etc/modprobe.d/alsa-base**

And add this:

**options snd-hda-intel model=auto**


That may solve your problem - keep us posted.

Regards.

---

### Post by gatorbrit on 2008-05-13
Failing that, try this - it worked for me on my toshiba satellite.


Open Applications> Accessories> Terminal
Then type the following:
sudo gedit /etc/modprobe.d/alsa-base
Then type your password if it asks for it
Once gedit opens up with this document scroll down to the end of the page
the last three line will look like this:

options snd-usb-caiaq index=-2
options snd-hda-intel model=3stack (Add this line here, so its third last)
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

Save and restart the computer it should work...

---

### Post by gatorbrit on 2008-05-13
TRy this - worked for me on my toshiba laptop

Open Applications> Accessories> Terminal
Then type the following:
sudo gedit /etc/modprobe.d/alsa-base
Then type your password if it asks for it
Once gedit opens up with this document scroll down to the end of the page
the last three line will look like this:

options snd-usb-caiaq index=-2
options snd-hda-intel model=3stack (Add this line here, so its third last)
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

Save and restart the computer it should work...

---

