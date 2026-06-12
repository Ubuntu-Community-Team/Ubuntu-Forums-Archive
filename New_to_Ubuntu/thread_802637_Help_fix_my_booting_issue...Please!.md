---
title: "Help fix my booting issue...Please!"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by marcmywords on 2008-05-21
Hi,
So heres my situation. i installed ubuntu on my external hdd, thinking that i would be able to boot into ubuntu whenever i wanted while still using vista as my primary OS (you see linux is more of a new thing-sorta side project experiment for me and i have no idea what the hell i'm doin). but what happened after the install is where my problem is, everytime i boot up my computer it brings up a menu to boot into linux or windows, now thats great and all but that only pops up IF i HAVE my hdd plugged in, so now i have no way of a portable laptop it must have the hdd plugged in in order to turn on the computer, in NOT i get an error 21 i think, it says GRUB... then ERROR. so my question is this... Can i simply have just windows boot if the hdd is not plugged in? if not where do i begin an uninstall? Thanks in advance for any help you can provide.

---

### Post by kansasnoob on 2008-05-21
GRUB rewrote the MBR (master boot record).

I think what you'll want to do is (with your external harddrive unplugged):

Boot from Windows Vista installation disc, select language and keyboard or input method, click Next and choose to Repair your computer. Then you will need to select the operating system that you want to repair. In the System Recovery Options dialog box click Command Prompt and type the following:

    Bootrec.exe /FixMbr
    Bootrec.exe /FixBoot 

This should restore the Vista mbr. Vista will then boot normally without your external hard drive plugged in, yet GRUB should still show up when the external drive is plugged in as long as settings in the BIOS are correct.

But, wait and run this by a few others before proceeding. I'm still a bit new at this.

---

### Post by nicedude on 2008-05-21
That will restore your Vista MBR and bootrecord but Grub will no longer show up when external is connected since the main disks MBR will have been rewritten for Vista again. This is probably the best fix for you though unless you have an advanced knowledge of Grub to allow you to reconfigure it. You just used a bad install method to try and get a dual boot senario and I would suggest before attempting this again you just read some of the many good online guides for dual booting Vista and Ubuntu to get an idea of what you will be doing before you attempt it.

Hope this helps you out,

nicedude

---

### Post by marcmywords on 2008-05-22
k thanks for the help, i would still like to have ubuntu though so if i do this method will i be able to boot into unbuntu again? or will i have to reinstall that aswell?

---

### Post by kansasnoob on 2008-05-22
Sorry, I didn't see this earlier.

I assume you've already restored the windows mbr, so look here:

[http://ubuntuforums.org/showthread.php?p=3995006#post3995006](http://ubuntuforums.org/showthread.php?p=3995006#post3995006)

---

### Post by marcmywords on 2008-05-24
well i still haven't restored my windows boot yet. i wanted to make sure there wasn't another way to switch booting order frst. and nice find on the guide. i'm printing it out now to follow it along. thnx. hopefully problem solved very soon.

---

