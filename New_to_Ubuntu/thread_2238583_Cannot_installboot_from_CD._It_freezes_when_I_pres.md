---
title: "Cannot install/boot from CD. It freezes when I press a key."
date: 2014-08-08
forum: New to Ubuntu
---

### Post by mithras2 on 2014-08-08
Hello everyone,

I'm fairly new to Linux. Today I decided to revive my old laptop (Presario 2104EA) by giving Lubuntu a try. The laptop still works (has XP running on it) but it's annoyingly slow ;) A perfect reason to try Lubuntu I thought. After I downloaded the 32bit installer disc, I burnt it onto a cd (4x) and booted up my laptop.

The laptop boots normally, the cd spins, and I see a flash of the boot menu before the language select screen pops up with a timer. Unfortunately this is as far as I can get.
As soon as I press a key, the timer stops, and the cd stops spinning after a while, the laptop shows no signs of activity (numlock doesnt work anymore). So I reboot. I tried again a couple of times, but the same thing keeps happening. Then I decided to let the timer run out: The language select screen disappears, and I get a black screen with a blinking cursor. After a couple of seconds the CD stops spinning again, and the laptop shows no further signs of activity.

I tried some other stuff (increased and decreased video memory in the bios, turned off USB legacy support, tried an external keyboard, used a different CD - the alternate install, and an older version of Lubuntu (12.xx) -, pressing shift while booting (which causes a freeze too, it doesnt even show the language select screen then), etc.

XP still boots normally, and XP's boot menu doesnt freeze after I press a key. I even gave Puppy Linux (non pae) a shot, but it freezes too as soon as I press a key (or when the auto-installer starts). 

Does anyone know whats wrong? I couldn't find anything solid on Google or this forum. The presario 2104EA is even listed as supported device for Ubuntu. So it should work.. 


Here are the specs of my laptop:
Presario 2104 EA DM428A
Celeron Mobile 2Ghz.
512 mb RAM
20 GB HD

Thanks,

Mithras

---

### Post by Rex Bouwense on 2014-08-08
A couple of items.
First, did you do an md5sum on the downloaded ISO?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Theoretically you have enough RAM and hard disk size to install and run Lubuntu.  If you compare the hash and they are the same, I would re-burn the ISO.  Make sure you are burning it and not merely coping it.
Second, if you have done that and you still cannot get it to boot, try Force PAE which is an option under 6. Other (I believe).

---

### Post by Jesse_Campton on 2014-08-08
Sometimes old laptop disc drives act funny, you may also try to create a live usb to boot your Lubuntu...Just a thought of course..Keep us posted!

---

### Post by Rex Bouwense on 2014-08-08
+1 Jesse.

---

### Post by mithras2 on 2014-08-09
Thanks for your replies!

I didnt do a md5 checksum. I'm downloading another iso right now.
I burned the CD's with Imgburn at 4 speed. And verified it afterwards. 
I also tried a bootable USB (with Universal USB Installer 1.9.5.5). Unfortunately my laptop doesn't recognize the USB stick when I boot it. (The led on the USB-stick doesnt power up during boot). I guess USB booting is not supported on my laptop?

---

### Post by mithras2 on 2014-08-09
> **Rex Bouwense said:**
> 
Second, if you have done that and you still cannot get it to boot, try Force PAE which is an option under 6. Other (I believe).

How exactly does that work? Press f6 during boot? It probably wont work either ;) I'm not allowed to press any keys, since it will freeze then.
But I'll try.

---

### Post by dave131 on 2014-08-09
I had a similar problem when I tried to install lubuntu 14.04.  It did have problems with PAE - but I found a download I had no problems with - perhaps you should try it if you haven't already.  Select the 32-bit i386 option on this link:

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by mithras2 on 2014-08-09
> **dave131 said:**
> I had a similar problem when I tried to install lubuntu 14.04.  It did have problems with PAE - but I found a download I had no problems with - perhaps you should try it if you haven't already.  Select the 32-bit i386 option on this link:

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Thanks for your reply. Still no luck.. I downloaded this file: lubuntu-14.04.1-desktop-i386.iso .
MD5 checksums match (281fc36d625f7ca0704297b3b811fa66). Burned with ImgBurn at 4 speed, verified ok. 

Then when booting the CD I get the same problem; it freezes on the language select screen when I press a key.

---

### Post by Jesse_Campton on 2014-08-09
Try this: When you boot up and you get to the install menu, you should have an option there to ( Try Ubuntu ). Try ubuntu and when you get to the desktop, try to install from there.

---

### Post by Addk on 2014-08-10
> **Rex Bouwense said:**
> A couple of items.
First, did you do an md5sum on the downloaded ISO?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Theoretically you have enough RAM and hard disk size to install and run Lubuntu.  If you compare the hash and they are the same, I would re-burn the ISO.  Make sure you are burning it and not merely coping it.
Second, if you have done that and you still cannot get it to boot, try Force PAE which is an option under 6. Other (I believe).

Cannot find the MD5 chechsum of lubuntu-14.04.1-desktop-i386.iso on the link of Rex : [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes). There are only hashes of 14.04 (and lower) and not of 14.01.

---

### Post by Jonathan Precise on 2014-08-10
> **Addk said:**
> Cannot find the MD5 chechsum of lubuntu-14.04.1-desktop-i386.iso on the link of Rex : [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes). There are only hashes of 14.04 (and lower) and not of 14.01.

Same problem here. See the text file [here]("http://releases.ubuntu.com/trusty/MD5SUMS") which provides all the md5sums (14.04 and 14.04.1)

---

### Post by mörgæs on 2014-08-10
Does this help?
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by mithras2 on 2014-08-11
Sorry for my late reply. I was away from home for a while.

About the PAE suggestion and the suggestion to select the 'Try Lubuntu' option in the menu:

I'm afraid it is impossible for me to select any options at all in the boot-menu ;) Before the boot menu shows, you will see a language select screen (right?). This language select screen is where my laptops decides to freeze, as soon as I try to make a selection.
This means that I cant even get into the boot-menu :( 
I think that my laptop freezes as soon as I press a key on the keyboard. Maybe the drivers being loaded while booting are not compatible with my laptops' hardware? Although I doubt that, since other people with the same model (Presario 2104 EA) didn't report any problems..

I did try another possible solution:
I booted into windows XP to test my Live-USB. It did show up in the explorer, then when I selected it, it prompted me with an option to install Lubuntu :)
However, when it was done installing something went wrong. It complained about 'not enough permission' to do something.. I'll try to figure out how to handle that problem, I might be able to succeed in installing Lubuntu on my laptop after all :)

---

### Post by Jonathan Precise on 2014-08-11
Oops! Looks like you are installing WUBI! I don't recommend this, as it's not supported anymore due to a lot of unfixed bugs.

---

### Post by mithras2 on 2014-08-12
> **Jonathan Precise said:**
> Oops! Looks like you are installing WUBI! I don't recommend this, as it's not supported anymore due to a lot of unfixed bugs.

You are right. That might explain the error ;)

Any other suggestions on how to install Lubuntu? Is it impossible to install it from win XP? Or could I use DOS or something?

---

### Post by mörgæs on 2014-08-12
I think it's time for some hardware experiments. 

How does it work with an external keyboard? 
Do you have another computer where you could install onto the hard disk and after that move the disk back into the Presario?

---

### Post by mithras2 on 2014-08-12
> **mörgæs said:**
> I think it's time for some hardware experiments. 

How does it work with an external keyboard? 
Do you have another computer where you could install onto the hard disk and after that move the disk back into the Presario?

I have the same problems with an external (ps2) keyboard. I could try a USB keyboard though.
HD swapping sounds like a good option, thanks! I should have an old compatible computer around.

Let's hope my Presario's HD is easy to remove ;)

---

### Post by mithras2 on 2014-08-12
Update:

Turns out the HD is easy to remove. However, it needs an IDE connector to connect it to the computer, which I dont have :(
I'm gonna ask around if there's anyone with an IDE connector. In the mean time I'll try some other solutions. I didnt update the BIOS yet. Maybe that helps?

I also tried the USB keyboard, but it didnt help :(

---

### Post by mithras2 on 2014-08-12
Finally, Lubuntu is installing!

The BIOS update did the trick :)

Thanks for all your help!

---

### Post by mörgæs on 2014-08-12
Good, please mark the thread 'solved'.

---

