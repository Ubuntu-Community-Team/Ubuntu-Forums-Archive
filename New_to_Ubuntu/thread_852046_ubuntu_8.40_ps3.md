---
title: "ubuntu 8.40 ps3 ???"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by DirtyHammo on 2008-07-07
gday people  im writing this on my ps3  and was just wondering if i can instal ubuntu 8.40 on my ps3.  im fairly new to ubuntu aswell so any help would be appreciated.  the only experience ive had with ubuntu  is with wubi on my windows xp.


woooo 1st post :)

---

### Post by Bigtime_Scrub on 2008-07-07
I hope this link helps.

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

Personally, without a lot of Linux experience I would be too chicken to risk putting Linux on a $400 PS3 but you know what they say, no guts no glory.

---

### Post by t0p on 2008-07-07
**DirtyHammo:** Sorry, this isn't an answer to your query. I just wanted to point out to you (and anyone else who doesn't know this) - Hardy Heron is NOT Ubuntu 8.40 or 8.4.  **It's 8.04**  This is because it's version 8, and was released in April, the 4th month.

Thank you for your attention ;)

---

### Post by tjwoosta on 2008-07-07
well.. if your already running linux on your ps3 then installing hardy aint going to hurt anything


but if i were you i would not install linux on my ps3


i have heard from alot of upset nix useres who installed nix on there ps3 thinking that they would still be able to play games

**if you put linux on your ps3 the only games you will ever be able to play on it are simple snes emulators  (even OpenGL games dont work)**

**and you wont be able to play blue ray dvd's anymore**

not to mention that the resolution will never look right no matter how you set it

---

### Post by blazercist on 2008-07-07
Yea I tried installing both Ubuntu and Yellow Dog Linux on my PS3 and was severely dissappointed. 

Basically, flash doesn't work, there is no 3D, its very slow and is a big pain to setup. Also, there currently is no Hardy version for the PS3 only Gutsy.  AND if you plan on using wifi you can forget it with Ubuntu on the PS3 unless you are willing to do alot of kernel hacking.  YDL6.0 supports wifi but not OOB you need to tweak it a bit.  I had to disable almost all the services and eye candy just to get gnome to function reasonably.  Again, flash doesn't really work so surfing youtube is out of the question, I can't even play dvds on mine although I do think its possible.  This could be a really cool project but its not ready for use yet.  STill needs alot of work.

edit: oh yea you are gonna have to mess around hardcore and reboot several million times to get a normal(ish) resolution.

---

### Post by fatality_uk on 2008-07-07
You can, as mentioned YDL is designed for it. Sony actually has the option into install another OS which is quite nice.

---

### Post by damis648 on 2008-07-07
I have installed Gutsy on my PS3... it actually worked quite well, except I could not get wireless working. AND, because the OS is on the NAND, there is NO risk of bricking your PS3. Just try it... once you install it, just run
```
sudo boot-game-os
```
in terminal, and you will return to normal. If the install fails, just hold down the power button for five seconds after starting it up and it will reset the boot options and boot the game os.

---

### Post by mcduck on 2008-07-07
> **tjwoosta said:**
> well.. if your already running linux on your ps3 then installing hardy aint going to hurt anything


but if i were you i would not install linux on my ps3


i have heard from alot of upset nix useres who installed nix on there ps3 thinking that they would still be able to play games

**if you put linux on your ps3 the only games you will ever be able to play on it are simple snes emulators  (even OpenGL games dont work)**

**and you wont be able to play blue ray dvd's anymore**

not to mention that the resolution will never look right no matter how you set it

Yes you can. You can select which OS is booted, Linux or the normal PS3 system. When booted to normal PS3 OS all games and movies work just like they would without Linux on the system.

Linux is actually even *supported* on PS3, to the level that it has options for installing another OS and choosing which one to boot in it's own menus.

The only thing is that you can't play games _in_linux_, Apart from those available for PPC Linux or run by emulators. PS3 games of course will not work, and Windows games are even less likely as they are for both wrong hardware and wrong OS.

---

### Post by tjwoosta on 2008-07-07
> 
Yes you can. You can select which OS is booted, Linux or the normal PS3 system. When booted to normal PS3 OS all games and movies work just like they would without Linux on the system.


O, my bad

i had no idea you could switch Operating Systems 
(i figured the there would only be enough room for one)

i guess i was wrong, sry

---

### Post by damis648 on 2008-07-07
> **tjwoosta said:**
> O, my bad

i had no idea you could switch Operating Systems 
(i figured the there would only be enough room for one)

i guess i was wrong, sry

The game OS is not even on the hard drive... it is on a flash memory card in the system (NAND). This is how the unit can function without a hard drive. This is the same way a PSP functions.

---

### Post by mrsudo on 2008-07-07
i would highly suggest yellow dog linux as it is designed for ps3, and you will be able to get better support relating to the same hardware

---

### Post by damis648 on 2008-07-07
> **mrsudo said:**
> i would highly suggest yellow dog linux as it is designed for ps3, and you will be able to get better support relating to the same hardware

Not necessarily. I installed Ubuntu gutsy on my PS3 and it worked great. Wireless did not, but I hear some people have success with recompiling a newer kernel, specifically designed for the PS3. I definetely reccomend Ubuntu gutsy over yellow dog... I have tried yellow dog. It is not that great.

---

### Post by DirtyHammo on 2008-07-08
> **Bigtime_Scrub said:**
> I hope this link helps.

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

Personally, without a lot of Linux experience I would be too chicken to risk putting Linux on a $400 PS3 but you know what they say, no guts no glory.


yes i have read that link, looks  very confusing. from all the other posts ive read in this topic ive decided not to install ubuntu 8.04 (thanks 4 the correction) on my ps3 until i get some more experience  with ubuntu.
and one more thing about my ps3,the price of a ps3  in australia  is $688 (Australian dollars), wich is a big rip off if u ask me

---

### Post by damis648 on 2008-07-08
> **DirtyHammo said:**
> yes i have read that link, looks  very confusing. from all the other posts ive read in this topic ive decided not to install ubuntu 8.04 (thanks 4 the correction) on my ps3 until i get some more experience  with ubuntu.
and one more thing about my ps3,the price of a ps3  in australia  is $688 (Australian dollars), wich is a big rip off if u ask me

Here is the link for 8.04 if you are interested: [http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04.1-desktop-powerpc+ps3.iso](http://cdimage.ubuntu.com/ports/releases/8.04/release/ubuntu-8.04.1-desktop-powerpc+ps3.iso)
It gets easier.

---

### Post by blazercist on 2008-07-08
there is no risk to the ps3 unit itself, the install itself is relatively painless... ubuntu gets installed to the HDD, the playstation XMB is not on the harddrive and thus cannot be damaged, the XMB is actually on the flash memory built into the PS3.

---

### Post by MrWES on 2008-07-08
Yah, but with YD installed you can rip HD DVD's :)

Bill

---

### Post by damis648 on 2008-07-08
> **MrWES said:**
> Yah, but with YD installed you can rip HD DVD's :)

Bill

No... it is a blu-ray drive.

---

### Post by blazercist on 2008-07-08
YDL does not have the codecs to play DVD's at all AFAIK, I dont think their even in the YDL repos... you have to install them manually.  Ubuntu on the other hand has them in restricted and its an easy apt-get install.

---

### Post by Kevbert on 2008-07-08
If you want to install a Linux OS on anything there's a decent article in the August Edition of Linux Format magazine - uClinux on aPSP, Openwrt on a WRT54G router, Fedora core5 on PS3, Opie on an iPaq or Treo PDA, dslinux on a Nintendo DS and linux on aXbox360.

---

### Post by treggs on 2008-08-12
> **Bigtime_Scrub said:**
> I hope this link helps.

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

Personally, without a lot of Linux experience I would be too chicken to risk putting Linux on a $400 PS3 but you know what they say, no guts no glory.

There's no risk involved the PS3 will still work fine no matter how bad you do if you screw up you just hold the power button to reset and the PS3 os loads back up easy

---

### Post by treggs on 2008-08-12
> **tjwoosta said:**
> well.. if your already running linux on your ps3 then installing hardy aint going to hurt anything


but if i were you i would not install linux on my ps3


i have heard from alot of upset nix useres who installed nix on there ps3 thinking that they would still be able to play games

**if you put linux on your ps3 the only games you will ever be able to play on it are simple snes emulators  (even OpenGL games dont work)**

**and you wont be able to play blue ray dvd's anymore**

not to mention that the resolution will never look right no matter how you set it

YOU ARE WRONG, Blue Ray Movie's work fine u just have to add the player and codecs.

All the ps3 games still work fine, and if sony ever open up the rsx to use then it will play all game any other linux machine will play and in reality why would you install linux on a gaming machine to play games

---

### Post by billgoldberg on 2008-08-12
I thought about putting a linux distro on my ps3, but decided not to do it.

Why?

- there is a risk involved
- the desktop experience will suck. The ps3 has only around 256mb of ram memory
- no wireless!!! I can't even get a cable to where my ps3 sits.
- I don't have a lcd tv. I still use an old crt (?) tv. So you just know the resolution will suck and reading text will be impossible.

If you need another pc, buy a second hands one from ebay for 100 bucks and put fluxbuntu on it.

---

