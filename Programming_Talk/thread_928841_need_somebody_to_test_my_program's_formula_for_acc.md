---
title: "need somebody to test my program's formula for accuracy"
date: 2008-09-24
forum: Programming Talk
---

### Post by gotenks05 on 2008-09-24
Hi there.  I have just started to make my own programs (less than ten), so I can gain experience as well as save money on software, in the event a new program is needed.  Yes, I do know that there are good free apps to use, but this is not what this thread is about.  I created a program that is supposed to tell me how much storage I really have on a secondary storage device, not what I have left.  How it works is the user enters the amount of gigabytes (does not work with TB or MB or KB since the constants are are either too high or too low) mentioned on the box and then that number is inputted into a formula (after clicking a button).  I've seen a video of somebody talking about this on youtube, as a response to a user who did not understand or seem to understand that you do not get the amount of space mentioned on the packaging of a hard drive or other secondary storage medium.  True, not everything on youtube is correct, just like wikipedia is incorrect many times.  However, since I forgot how to do it, I opened up an openoffice spreadsheet and did a bit of testing, using my computer's hard drive for comparison.  Well, after I got the program coded and compiled, I created a jar and tried to test it out in my VMs.  This is where the problem lies though in needing to determine the accuracy of the program, as I either don't know what VMware setup the for hard drive storage capacities or did not write them down (I only got Vmware to tell me the max sizes).  Is somebody willing to test the program's formula and tell me how accurate it is?

the formula used is: a=(GB*10^9)/1024^3

in the formula, a=actual and GB is what the user inputted.

When I tested it with my computer's hard drive, it was only a 0.26 difference from what the computer's OS reported for total capacity, but I'd still like to know how accurate it is on your end and if it it is not accurate, is there a better formula? I know that GB*1024^3 will report more than what the computer reports.

---

### Post by Quikee on 2008-09-24
> **gotenks05 said:**
> Hi there.  I have just started to make my own programs (less than ten), so I can gain experience as well as save money on software, in the event a new program is needed.  Yes, I do know that there are good free apps to use, but this is not what this thread is about.  I created a program that is supposed to tell me how much storage I really have on a secondary storage device, not what I have left.  How it works is the user enters the amount of gigabytes (does not work with TB or MB or KB since the constants are are either too high or too low) mentioned on the box and then that number is inputted into a formula (after clicking a button).  I've seen a video of somebody talking about this on youtube, as a response to a user who did not understand or seem to understand that you do not get the amount of space mentioned on the packaging of a hard drive or other secondary storage medium.  True, not everything on youtube is correct, just like wikipedia is incorrect many times.  However, since I forgot how to do it, I opened up an openoffice spreadsheet and did a bit of testing, using my computer's hard drive for comparison.  Well, after I got the program coded and compiled, I created a jar and tried to test it out in my VMs.  This is where the problem lies though in needing to determine the accuracy of the program, as I either don't know what VMware setup the for hard drive storage capacities or did not write them down (I only got Vmware to tell me the max sizes).  Is somebody willing to test the program's formula and tell me how accurate it is?

the formula used is: a=(GB*10^9)/1024^3

in the formula, a=actual and GB is what the user inputted.

When I tested it with my computer's hard drive, it was only a 0.26 difference from what the computer's OS reported for total capacity, but I'd still like to know how accurate it is on your end and if it it is not accurate, is there a better formula? I know that GB*1024^3 will report more than what the computer reports.

Yeah.. the formula is exact for conversion from GB to GiB. For MB to MiB it would be (MB*10^6)/1024^2 and kB to kiB (kB*10^3)/1024. 

Note that you will always get a little less if you look at total available size because the file system takes some space also (how much - it depends on the FS) and also capacity of the disk isn't a round number.

---

### Post by gotenks05 on 2008-09-24
thanks for the help.

---

