---
title: "Please Help ME!!! GRUB error 22! :("
date: 2008-04-23
forum: New to Ubuntu
---

### Post by ALex! on 2008-04-23
I'm a Linux newbie! I have used Windows all my life... 

Well all this started when looking to a friend's blog... he said ubuntu was my best bet... i installed it in my desktop computer and the first issue i had: Ubuntu vanished my windows vista os!!! :( ok ok no big deal... it was my fault! (I accidentally chose that option :???: )

2 days ago, while experimenting, i installed Ubuntu in the same computer BUT in another partition... (NO Reinstallation!) so... i had my two OSes (both were ubuntu) and one was of 73 gb and the other was of 55...

I installed gparted in one of the ubuntu OSes and deleted the partions of the other Ubuntu OS so that i could only have ONE OS... When i rebooted my computer, a Grub error 22 appears and the booting fails!!!! Now I just can't boot my computer, it's useless!!! :(

I've even tried to reinstall Ubuntu via Live CD but it doesn't boot at all... again the same error..... (does it have anything to do that i have another iso file in the same Live CD??)

PLEASE HELP!!!!! :cry:

---

### Post by spiderbatdad on 2008-04-23
Maybe some ramfs stuck. Disconnect all power and remove internal battery for a short while. You may need to move a jumper pin for a few seconds to clear cmos...check motherboard info in owners manual.
Simply removing the battery for a few minutes should do it...

---

### Post by ALex! on 2008-04-23
> **spiderbatdad said:**
> Maybe some ramfs stuck. Disconnect all power and remove internal battery for a short while. You may need to move a jumper pin for a few seconds to clear cmos...check motherboard info in owners manual.

excuse me... but could you please simplify this for me? I'm sorry but i don't understand very well :( i'm new to this!

---

### Post by nicedude on 2008-04-23
Something tells me the Ubuntu partition you deleted was the one you installed first and now you still have the one you installed second. Well hate to tell you this one is your fault too since Grub ( the boot loader ) keeps files in the /boot/grub/ folder of the partition you first installed linux on with it. so you wiped that out more than likely. It is fixable by reinstalling Grub and while I am not the best to tell you how, someone will chime in and answer that for you I am sure. 

Just be careful in the future, but I do the same kind of stuff allot :-)

---

### Post by Can+~ on 2008-04-23
To force boot from the LiveCD, usually, most PCs have a certain key to access a boot menu, it's usually F8.

After the logo of your computer (or check, or whatever it does when turning on), try hitting F8.

---

### Post by ALex! on 2008-04-23
> **nicedude said:**
> Something tells me the Ubuntu partition you deleted was the one you installed first and now you still have the one you installed second. Well hate to tell you this one is your fault too since Grub ( the boot loader ) keeps files in the /boot/grub/ folder of the partition you first installed linux on with it. so you wiped that out more than likely. It is fixable by reinstalling Grub and while I am not the best to tell you how, someone will chime in and answer that for you I am sure. 

Just be careful in the future, but I do the same kind of stuff allot :-)

ooh! thanks! :) but one thing i'm sure of is that i deleted my 2nd ubuntu os because i remember the fist one had the 55 gb! And with the gparted i deleted the 73 gb partition :???:
what can i do now?! :cry:

---

### Post by sam_delta on 2008-04-23
restore your grub loader, just follow these steps
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

sam

---

### Post by ALex! on 2008-04-24
there is still the message of:

GRUB Loading stage1.5.

GRUB loading...

Error 22
_

---

### Post by sam_delta on 2008-04-24
> **ALex! said:**
> there is still the message of:

GRUB Loading stage1.5.

GRUB loading...

Error 22
_

even after restoring grub by following the above link instructions?

---

### Post by OmahaVike on 2008-04-24
hi alex.

take a deep breath.  this has happened to me numerous times, and i've recovered through a little bit of work.

sam_delta pointed you to a great review of how to get back on track.

---

### Post by ALex! on 2008-04-24
> **sam_delta said:**
> even after restoring grub by following the above link instructions?

I can't even boot on the Live CD! even with the F8 option! :(

---

### Post by ALex! on 2008-04-24
> **sam_delta said:**
> even after restoring grub by following the above link instructions?

I can't even boot on the Live CD! even using the F8 option.... :(

---

### Post by ALex! on 2008-04-24
My Live CD has another iso file, not only Ubuntu.iso .... Does this have anything to do?

---

### Post by sam_delta on 2008-04-24
have you booted before from a live cd?? if not, it might be possible that your boot order tries to boot from the hard drive before trying to boot from the cd, try to get into the computer bios and change the boot order and put the CD as first

if you already booted from the CD before, and havnt changed anything under the computer  then the bios should be set to boot from the cd.

the live cd has nothing to do with Grub boot loader, it should be able to boot even without GRUB, 

if you still cant boot to a live cd
mayb try what spiderbatdad sayd on post # 2?

---

### Post by sam_delta on 2008-04-24
double post sry

---

### Post by sam_delta on 2008-04-24
> **ALex! said:**
> My Live CD has another iso file, not only Ubuntu.iso .... Does this have anything to do?

yeah of course, try re-burning the iso, just ubuntu one!!

---

### Post by Can+~ on 2008-04-24
> **ALex! said:**
> I can't even boot on the Live CD! even using the F8 option.... :(

Try other keys, my brother's laptop uses F9 I think.

You're on a desktop, who is the MoBo Manufacturer?

---

### Post by ALex! on 2008-04-24
I installed my Ubuntu OS via a Live CD.... But now, it just doesn't boot! :???: so... could the other iso file be the cause of boot fail? thank yo saaaam!!! :)

---

### Post by ALex! on 2008-04-24
> **Can+~ said:**
> Try other keys, my brother's laptop uses F9 I think.

You're on a desktop, who is the MoBo Manufacturer?

Mine is a Desktop HP Pavilion... it uses the F10 key! :???: but i don't know how to use this config option... I think that if i change boot ---> first boot----> DVD it will work... but i don't know! What if i screw it all again?! :(

---

### Post by sam_delta on 2008-04-24
yeah, iso images are ment to be burned 1 per disk, specially on booteable CDS such as the live cds

for instructions on how to burn a iso image 
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

sam

---

### Post by ALex! on 2008-04-24
OMG! GUYS! thank you very much for your support!! (specialy you sam!!!! :)) I'll try this again as soon as i get a virgin cd!! :???: haha!!! thank yo sooo much! I hope this works.. :(

---

### Post by Can+~ on 2008-04-24
> **ALex! said:**
> Mine is a Desktop HP Pavilion... it uses the F10 key! :???: but i don't know how to use this config option... I think that if i change boot ---> first boot----> DVD it will work... but i don't know! What if i screw it all again?! :(

Run it, you can't screw it up more ;D.

*edited out: it was for bios, damn*

---

### Post by sam_delta on 2008-04-24
no problem , let us know how it goes

well be here to help if something goes wrong


sam

---

### Post by ALex! on 2008-04-24
> **Can+~ said:**
> Run it, you can't screw it up more ;D.

*edited out: it was for bios, damn*

hahahaha :mrgreen: thanks!!! uh!!! :)

---

### Post by Can+~ on 2008-04-24
> **ALex! said:**
> hahahaha :mrgreen: thanks!!! uh!!! :)

I once reinstalled grub and overwrote the first sector of my windows partition, screwed some other partitions too in the process.

But to make an omelet, you have to break some eggs. Although, I should've backed-up those eggs.. damn.

---

### Post by ALex! on 2008-04-24
> **sam_delta said:**
> no problem , let us know how it goes

well be here to help if something goes wrong


sam

oh!!! thanks to your last link (and of course to you!) I've realized Ubuntu mis-burned (does that exist? :???: ) my iso file because there are no folders, but the iso! I've also realized, ubuntu doesn't support DVD-RW :mad:!!

---

### Post by ALex! on 2008-04-24
> **Can+~ said:**
> But to make an omelet, you have to break some eggs. Although, I should've baked-up those eggs.. damn.

Nice quote! :wink: haha!!! I have only a doubt.... What would be the easiest process for uninstalling Gutsy in a partition, for then upgrading it to hardy?! That's because I have a dual boot in my lap! (nothing went wrong on this one) and i would like to screw vista in this one too... :???:

---

### Post by sam_delta on 2008-04-24
burn ubuntu hardy cd, insert it, boot into live, click install and when prompt about partitions, choose, "use entire disk", or something similar

---

### Post by ALex! on 2008-04-24
> **sam_delta said:**
> burn ubuntu hardy cd, insert it, boot into live, click install and when prompt about partitions, choose, "use entire disk", or something similar

but... isn't this option going to overwrite my WHOLE HDD?? or just a desired partition?

---

### Post by sam_delta on 2008-04-24
> **ALex! said:**
> but... isn't this option going to overwrite my WHOLE HDD?? or just a desired partition?


oo sry about that, i thought you wanted to get rid of vista since you sayd
"and i would like to screw vista in this one too... "
, if you do not want to get rid of vista, you can simply boot into gutsy and click update once hardy is released, and ull get hardy

---

### Post by ALex! on 2008-04-24
> **sam_delta said:**
> oo sry about that, i thought you wanted to get rid of vista since you sayd
"and i would like to screw vista in this one too... "
, if you do not want to get rid of vista, you can simply boot into gutsy and click update once hardy is released, and ull get hardy

ah! haha sorry, my fault... so that means i won't have to wait 3 hours for my OS to download?! :) or worse... wait 4 weeks 'til it arrives home :???:

---

### Post by sam_delta on 2008-04-24
once hardy is released, you can type Alt+f2 and type the following command

update-manager --devel-release

and ull get a window telling you that theres a new version available bla bla bal, just follow the steps and there you go, ur gutsy will not be hardy

heres the official link   [https://help.ubuntu.com/community/HardyUpgrades#head-378718bf27e85b8e05c7a5966125eb194b5f26bb](https://help.ubuntu.com/community/HardyUpgrades#head-378718bf27e85b8e05c7a5966125eb194b5f26bb)

you can actually update now into the release candidate, but id recomend to wait until the final release

---

### Post by starcannon on 2008-04-24
take a little extra time and learn to do manual partitioning so that you can create /home on its own partition, makes experimenting much less painful.

Just my 2bits on the subject.
Have fun,
Starcannon

---

### Post by sam_delta on 2008-04-24
> **ALex! said:**
> ah! haha sorry, my fault... so that means i won't have to wait 3 hours for my OS to download?! :) or worse... wait 4 weeks 'til it arrives home :???:

updates may take a while, not as much as downloading the whole OS,, but itll take a while, specially just after the release since everyone will be updating, so you may want to wait few days to update.

sam

---

