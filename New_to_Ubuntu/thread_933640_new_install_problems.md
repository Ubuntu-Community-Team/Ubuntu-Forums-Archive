---
title: "new install problems"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by sanchezero on 2008-09-29
hi all, totally new to linux, but my wife's computer has taken a massive dump and am trying to get it up and running again. she's got xp and a buncha viruses/trojans/spyware that we just can't kill. 

we don't have an xp disc (cheap azz dell, thx) so i've followed the n00b instructions to get linux ([https://help.ubuntu.com/8.04/switching/installing.html]("https://help.ubuntu.com/8.04/switching/installing.html")) and burn a CD. 

however, when i tried to burn it using Infra Recorder i couldn't find an ISO image per the instructions and had to burn it using the 'burn the compilation to a physical disc' option. this disc doesn't seem to be giving me any of the prompts i'm looking for from the previous listed tutorials. when i enter setup/bios and boot from CD i just go straight to XP. i can install ubuntu as a regular app, but it doesn't seem like it will overwrite XP or offer partitions. i cancelled it before completion, awaiting some knowledgable advice.

my goal is to use the disc at boot to reformat (and destroy XP) with ubuntu.

sorry for the huge 1st post. hopefully someone can give me some tips here...

thanks alot!

---

### Post by shoot2kill on 2008-09-29
did you download a 'live CD' ???
did you change the first boot device to CD-ROM Drive ???
when you look at the CD through windows, do you see lots of files or one file ending in '.iso' ???

---

### Post by rodriguez24 on 2008-09-29
I don't own a Dell. However, some laptops require that you press (for example F2 or Del) to enter a boot option screen. Then from there you would select to boot from CD. That is definitely the easiest way to eliminate your xp from the laptop because you will have the option to tell Ubuntu Installation to use the whole disk instead of Dual Booting (thereby eliminating your xp install). I hope this helps. If not, feel free to post your computer model, maybe I could explain in more detail.

---

### Post by WhyCantEveryOSBePerfect on 2008-09-29
Huge post?  You ain't seen nothin yet ;)

Anyway!  Sounds like maybe you didn't burn the ISO to your disc correctly to me.  When I tried to make a disc with Infra it didn't work either.  I think I ended up getting "ISO Recorder" online and used that to properly burn my ubuntu .ISO to the disc.  If it did burn properly... I don't know I'm still a linux-n00b too!  But with my disc when I do boot from CD from the bios menu it brings up a screen that says "Ubuntu" and 

Try Ubuntu without any change to your computer 
Install Ubuntu
Check Disk for defects
Test Memory

If you didn't see that maybe the disc wasn't burned right?

---

### Post by Jeroenix on 2008-09-29
I have no experience with 'Infra Recorder', but I can point you to an excellent light-weight ISO burner for Windows, which you can use to burn an Ubuntu ISO to CD.

1. Download an Ubuntu install disk from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
2. Install ISO Recorder from [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)
3. After installation, right-click on the ISO file and burn.
4. Boot from this CD, using the correct boot order options in your BIOS.

5. Good luck! :)

---

### Post by Flare183 on 2008-09-29
What brand/name is your BIOS? Does it have any boot options?

---

### Post by sanchezero on 2008-09-29
wow! this forum is busy and helpful.

ok, my download gave me a winRAR with a wide selection of folders and a coupla apps to include an exe. it was supposed to be an ISO but i guess i somehow picked a bad mirror or something. i'm trying a 2nd download from a different mirror. this one is also named an ISO so with any luck...

as for setup/bios stuff, that should've been fine. i went into the boot order and setup to ONLY boot from CD, but i got a message that there were no boot resources available.

hope the new d'load fixes things. i'll update if all is well or, if not, i'll cry like a little girl some more...

thanks all.

:guitar:

---

### Post by markbuntu on 2008-09-29
If you got viruses on that machine, you might want to burn the iso on a different one because some viruses will get into everything that moves, including an iso.

---

### Post by oilchangeguy on 2008-09-29
> **sanchezero said:**
> hi all, totally new to linux, but my wife's computer has taken a massive dump and am trying to get it up and running again. she's got xp and a buncha viruses/trojans/spyware that we just can't kill. 

we don't have an xp disc (cheap azz dell, thx) so i've followed the n00b instructions to get linux ([https://help.ubuntu.com/8.04/switching/installing.html]("https://help.ubuntu.com/8.04/switching/installing.html")) and burn a CD. 

however, when i tried to burn it using Infra Recorder i couldn't find an ISO image per the instructions and had to burn it using the 'burn the compilation to a physical disc' option. this disc doesn't seem to be giving me any of the prompts i'm looking for from the previous listed tutorials. when i enter setup/bios and boot from CD i just go straight to XP. i can install ubuntu as a regular app, but it doesn't seem like it will overwrite XP or offer partitions. i cancelled it before completion, awaiting some knowledgable advice.

my goal is to use the disc at boot to reformat (and destroy XP) with ubuntu.

sorry for the huge 1st post. hopefully someone can give me some tips here...

thanks alot!

if you didn't get a recovery cd with your new computer, it most likely has a restore partition. read the owners manual. when it boots it should say something like press f11 for recovery (example).

---

### Post by sanchezero on 2008-09-29
ya, i'm doing all the work on my gateway.

the 2nd download was the same as the 1st. there's a folder in the mix called isolinux but nothing shows up using infrarecorder. guess it's time to try a new burner.

---

### Post by sanchezero on 2008-09-29
k, i'm following instructions here ([https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)) on burning this thing and i've tried 2 different burners as well as 2 different downloads. neither burner recognize an ISO file from either download.

i attached a shot of the contents of the ubuntu i've downloaded (twice). does this look familiar to anyone?

---

### Post by oilchangeguy on 2008-09-29
> **sanchezero said:**
> k, i'm following instructions here ([https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)) on burning this thing and i've tried 2 different burners as well as 2 different downloads. neither burner recognize an ISO file from either download.

i attached a shot of the contents of the ubuntu i've downloaded (twice). does this look familiar to anyone?

ok, you download the iso file from the download site, save it to my documents. using your burning software (i use nero) burn the file as an image, not a data disc.

---

### Post by sanchezero on 2008-09-29
well that's just it. i've gone to the site linked as the ISO d'load but i keep getting a data format. below is a screen of where i'm grabbing it. am i totally retarded?

i'm choosing 8.04 desktop and std computer. i've tried 2 diff locations. i'm NOT checking the text installer option. this is the link from this ([https://help.ubuntu.com/8.04/switching/installing-get.html#installing-get-iso]("https://help.ubuntu.com/8.04/switching/installing-get.html#installing-get-iso")) page.

---

### Post by oilchangeguy on 2008-09-29
> **sanchezero said:**
> well that's just it. i've gone to the site linked as the ISO d'load but i keep getting a data format. below is a screen of where i'm grabbing it. am i totally retarded?

i'm choosing 8.04 desktop and std computer. i've tried 2 diff locations. i'm NOT checking the text installer option. this is the link from this ([https://help.ubuntu.com/8.04/switching/installing-get.html#installing-get-iso]("https://help.ubuntu.com/8.04/switching/installing-get.html#installing-get-iso")) page.

you're burning it wrong. there is no data download. burn it as an image, not as data. for example, in nero look under the backup tab for image burning.

---

### Post by sanchezero on 2008-09-29
ok, i'm totally confused. the data download is what i unpack from the winRAR that i get from that site.

i don't have nero, but when i use infrarecorder (their recommendation) and follow the tutorial, i click 'burn an image' and am taken to a screen where i select that image. i open the ubuntu folder and there's no ISO on top. i sort thru all of the folders, looking for images in each...nothing.

i know i'm missing something obvious, but i can't figure it out. again, on the offchance that i got a corrupted download, i grabbed it again from another mirror and it matched. very frustrating.

---

### Post by oilchangeguy on 2008-09-29
> **sanchezero said:**
> ok, i'm totally confused. the data download is what i unpack from the winRAR that i get from that site.

i don't have nero, but when i use infrarecorder (their recommendation) and follow the tutorial, i click 'burn an image' and am taken to a screen where i select that image. i open the ubuntu folder and there's no ISO on top. i sort thru all of the folders, looking for images in each...nothing.

i know i'm missing something obvious, but i can't figure it out. again, on the offchance that i got a corrupted download, i grabbed it again from another mirror and it matched. very frustrating.

you don't unpack the download. like i said earlier, save it to my documents. and burn it as an image.

---

### Post by sanchezero on 2008-09-29
ok, it's true...i'm an idiot!

the file was coming to my desktop as a zipped/RARed icon, so what did i do? i opened it...i'm so brainy.

it works just like you guys said, but now i need more CDs, har har.

---

### Post by oilchangeguy on 2008-09-29
> **sanchezero said:**
> ok, it's true...i'm an idiot!

the file was coming to my desktop as a zipped/RARed icon, so what did i do? i opened it...i'm so brainy.

it works just like you guys said, but now i need more CDs, har har.

glad you finally got it to work.

---

### Post by JC Cheloven on 2008-09-29
> **sanchezero said:**
> ok, it's true...i'm an idiot!

the file was coming to my desktop as a zipped/RARed icon, so what did i do? i opened it...i'm so brainy.

it works just like you guys said, but now i need more CDs, har har.

This is the kind of "help" resulting from the over-guidance that some operating systems impose to their users. The icon told you that it was a rar archive, and your reaction is to unpack it. Not entirely your fault ;-)

Hope you'll find linux much more stimulating :-)

---

