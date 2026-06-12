---
title: "[SOLVED] Burning K9Copy ISO files"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-11-02
I have been using K9Copy with Ubuntu 7.10 without any issues until this week end. All of a sudden it quit working. I'm not sure if it has anything to do with the last Ubuntu File Update or not. The K9Copy looks to be running OK... But fails when I start to burn the ISO file on a blank DVD. It used to began a different burn program than the default program which is showing up now. It looks like it is not reading the ISO file. :confused:

---

### Post by diablo75 on 2008-11-02
Try burning the ISO with Gnomebaker or Brasero.  You'll find both of them available in Applications>Add/Remove.

---

### Post by fooman on 2008-11-02
k3b is tops with me!  :)

---

### Post by CoCoKnots on 2008-11-02
I tried all three suggestions... Still coming back with errors in burning. Also tried reloading libdvdcss2 & rebooting... that didn't work either.

---

### Post by CoCoKnots on 2008-11-02
It acts as thought some files have been dropped. I've tried reloading K9Copy - it's copying OK.  I don't know how to get Burning to work again...Please Help...

---

### Post by fooman on 2008-11-02
is it just with one particular iso file?  ...have you tried re-downloading the file?

don't know about the other apps,  but with k3b,  when you click on "burn cd image" or "burn dvd iso image" and point it at your iso file...the first thing it does is check the md5 checksum.  ....does it even get that far with your file?

what iso are you trying to burn? ...perhaps the file itself is bad,  try another iso.

---

### Post by CoCoKnots on 2008-11-02
I've tried to burn a couple of ISO files which I used K9Copy with the same results. I'm not familiar with K3B. Do I need to have it listed in the K9Copy setup prior to downloading the original file ?

---

### Post by CoCoKnots on 2008-11-02
Well... I can't seem to get anything to work. All I'm doing is waisting a lot of DVDs. I've tried K9copy to rip and for burning I've tried... Brasero, GnomeBaker, DeVeDe, and K3B. They are all coming back with an error in burning. I'm sure it has to be something simple & common to the burn side of the projects. I believe this all started with the last Ubuntu update... I was runing into issues during the download. Any Ideas ???

---

### Post by sdowney717 on 2008-11-02
use DVD shrink or DVDfab5 in wine for ripping.
both of these work well in wine.

For some reason, K9copy has failed to work for me for a while. It crashes while ripping.
Use brasero for cd burning, it is best.

---

### Post by CoCoKnots on 2008-11-02
This can't be that hard... Although I'm not married to it, K9Copy has been working fine. I've been trying other programs & I can't get any of them to work. Could I have two or more programs in the System> Admin> Syn/Pkg/Mgr
installed which could be conflicting with each other ?

---

### Post by CoCoKnots on 2008-11-02
Thanks for the suggestion. I tried using DVD Shrink in Wine... No luck there either. I've gone through about two dozed DVDs trying different routines and variations of each. Should I re-install Ubuntu & get rid of everything on the drive & start over ?

---

### Post by skunkTrader on 2008-11-02
Are you sure there is no hardware error with the drive?  Is it clean?  Are the cables attached OK?

---

### Post by CoCoKnots on 2008-11-02
Everything looks OK. The drive is internal & reads/plays CDs & DVDs without any problem. It looks like they read fine when in the copy mode... It's the writing of the disc when I get the error.

---

### Post by CoCoKnots on 2008-11-02
This is getting crazy. I've removed anything that looked like it could create a conflict with the copy/burn routines. The only two left were K9Copy & K3B to use for burShould I upgrade to Hardy & start over ?

---

### Post by CoCoKnots on 2008-11-02
This is getting crazy. I've removed anything that looked like it could create a conflict with the copy/burn routines. The only two left were K9Copy & K3B to use for burning. Should I upgrade to Hardy & start over ?

---

### Post by CoCoKnots on 2008-11-02
Please... If anyone has any ideas of what to do from here, Please help. I have no idea of what is wrong or how to fix it. Thanks

---

### Post by sdowney717 on 2008-11-02
if you wish to verify the iso file, try opening it with VLC.
VLC can play the iso file just like a dvd directory.

You should definitely consider upgrading from feisty to IBEX as it is end of life.

I dont have any issues burning with IBEX using Brassero. I do seem to remember having trouble with Brasero when running feisty. K3b was giving me some grief so I dont use it.

You can also burn the ISO with nautilus CD Creator program. Just go to places - CD-DVD creator.

---

### Post by alwayshere on 2008-11-02
I remember having a conflict of open gl cant remember much more sorry i had to edit a file and change a 0 to a one or something

---

### Post by larryn28 on 2008-11-03
i'm having a similar problem. k9copy always worked for me fine with 8.04, it would copy the disc & then automatically launch k3b to burn the dvd. now since i've updated to 8.10, k3b no longer launches & even though i tell k9copy to create & save an .iso image, it only creates separate video & audio vts folders so i can no longer even burn a dvd with k3b. if anyone knows a solution under 8.10, please post it.

---

### Post by 4Foot on 2008-11-03
> **CoCoKnots said:**
> I have been using K9Copy with Ubuntu 7.10 without any issues until this week end. All of a sudden it quit working. I'm not sure if it has anything to do with the last Ubuntu File Update or not. The K9Copy looks to be running OK... But fails when I start to burn the ISO file on a blank DVD. It used to began a different burn program than the default program which is showing up now. It looks like it is not reading the ISO file. :confused:

CoCoKnots:

The problem that you are facing is one which I ran into when I upgraded to Ubu 8.04. It also happened when I switched to Mint and upgraded to the Mint equivalent of 8.04. My system would just not write an ISO to a disc no matter what. Symptoms differed and I was not alone, but very few solutions were offered and none worked. 

I finally concluded that it was some kind of quirky kernel issue and downgraded to my old version which worked fine. Happily, while they never did get a fix that worked for me in either Ubu 8.04 or Mint 5  the newest version of Ubu, 8.10 works just fine.
 
If you did anything to update your ver 7.10 that brought the kernel up to date that may have been what buggered your burning.

Jump up a couple of versions if you can to the latest or if you cannot, just downgrade a couple of updates.

Hope this helps.

4Foot

---

### Post by indytim on 2008-11-03
Try running k9copy with direct output only to an iso file.   Then go to your burning app burn the iso image that k9copy outputted.  

IndyTim

---

### Post by CoCoKnots on 2008-11-03
Thanks Everyone, I am currently downloading the upgrade to 8.04... Then on to 8.10 from the sound of things. I will keep this post open until I have a chance to test the results. It's all a learning curve isn't it.

---

