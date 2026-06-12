---
title: "Ubuntu doesnt load up after installation !"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by cheeky_lankan on 2008-09-08
hello i am new user to ubuntu and was trying to get ubuntu all set up. i have been up from 7 this morning and its my 4 th installation of the live cd on my computer and still doesnt seem to load ubuntu! btw iam using the latest version of ubuntu live cd and not the alternative one .

i have 2 HDD one a 70 gig and the second a 40 Gig .. i removed the partitions and the ext3 in the 40 gig where i want to install ubuntu using gparted. I installed it ubuntu from the desktop via the live cd followedit all the way though selected the whole disk to be used (40 gig one ) and then restarted it removed the cd out went into my bios and changed the boot sequence to HDD

Once that was done .. the computer started and then went to an option where i can choose windows or ubuntu; chose ubuntu ... then came the ubuntu splash screen and then went blank and i ended up with a screen like this 

busy box v1.1.1(debian ......


and prompt of 

(initramfs): 

.... 
so iam stuck at this part and i dunno how to jump around this 
any help would be really appreciated

here is a print screen of wat iam looking @ through the live Cd (Gparted) :

[http://img413.imageshack.us/img413/9796/screenshotec5.png](http://img413.imageshack.us/img413/9796/screenshotec5.png)

thank you for your time 
cheeky_lankan

---

### Post by cheeky_lankan on 2008-09-08
I hope this would help i have a gigabyte motherboard which has raid drivers and maybe thats why iam getting this error and its not loading up properly. i think my motherboard model is a 8195p duo mobo which has raid capabilty. i really would like some suggestions or help 
( ps how wouldi know wat motherboardi have through ubuntu ?) 
thank you 

cheeky_lankan

---

### Post by cheeky_lankan on 2008-09-08
i removed the primary HDD where windows was installed and tried to  boot up but this time grub showed up .. and let me choose my kernal ..once i did that still it just gave me the splash screen this time in a better resolution than before .. but nothing came up except the busy box v1.1.1again... so then i went back nad then deleted the partition and re-installed the ubuntu ... and it still didnt work ..so again .. thishas taken me over 9 hours and STILL nothing .. so please could some one in this community HELP me !

---

### Post by kansasnoob on 2008-09-08
I'm sure sooner or later someone will jump in. I just know nothing at all about RAID!

I am curious if you were able to run the live CD though? I mean by choosing "Try Ubuntu without any changes to your Computer"?

---

### Post by technotitclan on 2008-09-08
how old are these hdd's?

---

### Post by cheeky_lankan on 2008-09-08
> **kansasnoob said:**
> I'm sure sooner or later someone will jump in. I just know nothing at all about RAID!

I am curious if you were able to run the live CD though? I mean by choosing "Try Ubuntu without any changes to your Computer"?

Yes i was able to run and i am actually typing this using the live cd .. soit worrks

---

### Post by cheeky_lankan on 2008-09-08
> **technotitclan said:**
> how old are these hdd's?

one of them is like maybe 4 years the other like year and a half

---

### Post by kansasnoob on 2008-09-08
> **cheeky_lankan said:**
> Yes i was able to run and i am actually typing this using the live cd .. soit worrks

Good! That at least shows that things are hardware compatible.

Was the machine fully functional with Windows? I noticed that you said you have Windows on the other drive.

Also, is this 64 bit Ubuntu or i386?

I can at least help you google:(

---

### Post by cheeky_lankan on 2008-09-08
> **kansasnoob said:**
> Good! That at least shows that things are hardware compatible.

Was the machine fully functional with Windows? I noticed that you said you have Windows on the other drive.

Also, is this 64 bit Ubuntu or i386?

I can at least help you google:(

YUP it ran fine ..everything was cool on windows.. and i downloaded the i386 pretty sure ..if iam wrong how can i check ?

---

### Post by kansasnoob on 2008-09-08
> **cheeky_lankan said:**
> YUP it ran fine ..everything was cool on windows.. and i downloaded the i386 pretty sure ..if iam wrong how can i check ?

Go to terminal and:

```
uname -a
```

I have Ubuntu i386 and I get:

> Linux lance-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux


Would you please post the output of:

```
sudo fdisk -l
```

---

### Post by technotitclan on 2008-09-08
may want to try testing the drive your trying to install to. could be a physical problem w/ the drive

[http://support.gateway.com/support/drivers/getFile.asp?id=21280&dscr=GWSCAN%205.12&uid=1810909](http://support.gateway.com/support/drivers/getFile.asp?id=21280&dscr=GWSCAN%205.12&uid=1810909)

burn that to a cd as an image and boot to it. run the quick test then the extended test-see if it comes back w/ errors. the extended test will try to repair as much as it can and/or mark bad sectors if it needs to.

---

### Post by cheeky_lankan on 2008-09-09
> **technotitclan said:**
> may want to try testing the drive your trying to install to. could be a physical problem w/ the drive

[http://support.gateway.com/support/drivers/getFile.asp?id=21280&dscr=GWSCAN%205.12&uid=1810909](http://support.gateway.com/support/drivers/getFile.asp?id=21280&dscr=GWSCAN%205.12&uid=1810909)

burn that to a cd as an image and boot to it. run the quick test then the extended test-see if it comes back w/ errors. the extended test will try to repair as much as it can and/or mark bad sectors if it needs to.

hey man once i read your post; i didnt download that program to fix that HDD instead i wiped out windows and installed ubuntu on the other HDD and it worked smoothly like how it was  supposed to have. I was wondering is there a tool similar to the one one you poseted; but for linux cox i would like and try to use the HDD that wasnt installing ubuntu b4 to install windows if i ever feel like it. Since Ubuntu is installed on my main HDD .. would installing windows on the other HDD and dual booting be possible (coz i thought you have to have windows firs and then install ubuntu.. so there is no complication?)

thank you again ..i should have just stopped trying to install ubuntu on a bad HDD ..too bad i only figured this out after 12hrs or something !!!


thank you again 

cheeky_lankan

---

