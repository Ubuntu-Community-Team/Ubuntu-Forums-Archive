---
title: "Ubuntu 12.04 installation constantly ends in errors. Is my HDD bad?"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by kramer65 on 2012-05-03
Hello,

I've been running Ubuntu 12.04 since Alpha 2 and it has been wonderful for me all that time. But since it was officially released last week I started having trouble with it. Firefox started crashing on me, Apport didn't work anymore, and I started getting all these obscure System errors and segmentation faults. Around the time that Ubuntu started going bad I did install some new stuff (all from the Software center or Synaptic) so I first though that these programs were the problem. I uninstalled all those things, but this didn't help.

So today I decided I would start fresh again and reinstall Ubuntu alltogether. So I downloaded the latest Ubuntu image, and booted it from a usb-stick. When installing however, I got these errors saying that some file did not match its source copy on the CD/DVD (see attachement for an example; the errors always refered to different files though).
So after retrying a couple times I simply downloaded the image file on my laptop and created a CD and tried with that. This has the same effect though; constant errors refering to various files.

The error message contains two suggested problems:
[LIST]
[*]faulty CD/DVD disk or drive
[*]faulty hard disk
[/LIST]
Since I've tried with both a CD and a USB stick I guess the first one is not the case. This leaves the second one, which would make sense in a way. The hard disk is about 5 years old and has been used intensively (often running for months without ever be turned off). It would totally explain the randomness of the files that do not match, and I guess it would also explain the random system errors I was getting with my last install.

So My question: How do I check wether my "*hard disk is old and in need of replacement*" (as the error message suggests)? Is there maybe a tool that checks how warm the hard disk gets (I tried psensor, but I can't find the HDD temp)? Or is there anything else I can do to check the hard disk?

All tips are welcome!

---

### Post by Peter09 on 2012-05-03
Can you boot the LiveCD and then run a disk check on your hard drive?

---

### Post by kramer65 on 2012-05-03
I'm booted into the live cd right now (the disc is already formatted). How would I run a "disk check"? I've never done anything like that..

---

### Post by Peter09 on 2012-05-03
Here is an asnswer of the net - its a bit old but most probably still valid..
 
>  
 
you could run the fsck tool manually from a terminal prompt (type man fsck for more info) or if you are like me and prefer using a gui, go to System->Administration->Partition Editor sometimes its listed as gparted. If its not installed on your system you can install gparted from synaptic or using the terminal:

sudo apt-get install gparted

it comes installed by default on the Ubuntu LiveCD but it may not be on your installation.

anyway once you have gparted running choose the disk from the dropdown menu you want to check. make sure its unmounted, then right click and choose "check' from the menu.

If that doesnt resolve your problem you should look into the program testdisk:

[[COLOR=#006699]http://www.cgsecurity.org/wiki/TestDisk[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk")


---

### Post by kramer65 on 2012-05-03
Alright. I found a program called "disk utility", in which I clicked "SMART data". In there I found some numbers. Below I typed some of those numbers:

Read Error Rate: Value = 0
Spinup Time: Value 3.5 Seconds
Start/Stop Count: Value = 503
Reallocated Secotr Count: Value = 0 sectors
Power-On Hours: Value = 2.4 years
Spinup Retry Count: Value = 1
Cailbration Retry Count: Value = 1
Power Cycle Count: Value = 503
Airflow Temperature: Value = 24 C / 75 F
Temperature: Value = 24 C / 75 F
Hardware ECC recovererd: Value = 2493

Would this mean my disk is alright, or "*old and in need of replacement*"?


[EDIT]
I just see your answer right now. I went into Gparted and did the tests. It doesn't find any bad blocks, which I guess is obvious since I already formatted the whole drive. Does this say anything about how good the hardware still is?

---

### Post by kuvanito on 2012-05-03
just had your problem 2 days ago and sure enough,it was the hard drive.
i replaced it with an old one and had no problems doing a fresh install
my hard drive was abused........

---

### Post by Peter09 on 2012-05-03
There is a program 'Disk Utility' which should also be already installed. That will do some read / write checks. Try that and see if you get any problems.
 
Other than that your HD looks O.K.

---

### Post by kramer65 on 2012-05-03
> **kuvanito said:**
> just had your problem 2 days ago and sure enough,it was the hard drive.

What exactly do you mean with "your problems"? Random system errors and segmentation faults? Or something else?

---

### Post by kramer65 on 2012-05-03
Alright!!

After doing some more tests I got a tip on another forum that it could be the memory as well. So I did a memtest, and it turned out that one of my three memory cards was broken. So I took it out, and now things are working smoothly again.

Thanks for all the tips!

---

### Post by Peter09 on 2012-05-03
Glad its been resolved.

---

