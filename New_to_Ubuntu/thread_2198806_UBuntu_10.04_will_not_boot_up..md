---
title: "UBuntu 10.04 will not boot up."
date: 2014-01-10
forum: New to Ubuntu
---

### Post by gordon33 on 2014-01-10
Hello All

Presently the HP G60t-200 will not Boot up.  When I turn the computer on things start as normal and quit at the second or third screen.  The last screen says:

boot from (hd0.0) ext3    8498c-46a4-a825-721b308656b3        
Starting up...

I have been running Ubuntu 10.04 with out problems unti 2 weeks ago.  First, Firefox would crash. then the computer would frezze, now the computer will not boot up.

Any sugestions on how to get this thing to boot up.

I have been trying to up grade to Ubuntu 13.10.  I gett to the end of the install and I get error mesages. I am wondering if the problem is with the Flash stick, down load or computer.  I am going to down load to a flash stick aganin and will report back when done.

Gordon

---

### Post by egeezer on 2014-01-10
Check the MD5SUM or SHA256SUM of each of your downloads to make sure it is correct.

Don't bother with 10.04 any more - it has been unsupported for some time now.

---

### Post by fantab on 2014-01-10
> **gordon33 said:**
> 

I have been running Ubuntu 10.04 with out problems unti 2 weeks ago.  First, Firefox would crash. then the computer would frezze, now the computer will not boot up.

Any sugestions on how to get this thing to boot up.

I have been trying to up grade to Ubuntu 13.10.  I gett to the end of the install and I get error mesages. I am wondering if the problem is with the Flash stick, down load or computer.  I am going to down load to a flash stick aganin and will report back when done.

First of all Ubuntu 10.04 has reached its 'end of life'. You should not use it anymore... (recommendation).

Reinstalling 13.10 is indeed an excellent idea...

>  I gett to the end of the install and I get error mesages

What error messages do you get?

---

### Post by gordon33 on 2014-01-10
Hello egeezer

How would i check the  MD5SUM or SHA256SUM of each of the downloads to make sure it is correct?  Is there some thing I can search for onthe web?

gordon33

---

### Post by fantab on 2014-01-10
For MD5Sum Check: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
For SHA256Sum check: [https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)

---

### Post by gordon33 on 2014-01-10
Hello fantab
How would I change the following commnds.  The old system is Ubuntu 10.04 and the new system is 13.10 on a USB flash stick?

I get no such command when typing in  the following commands:

[ ubuntu@ubuntu-desktop:~$ cd Downloads ]


[ md5sum ubuntu-11.10-dvd-i386.iso ]


[ 8044d756b7f00b695ab8dce07dce43e5 ubuntu-11.10-dvd-i386.iso ]



And, for the SHA256SUM:

[ cd download_directory ]


[ sha256sum ubuntu-9.10-dvd-i386.iso ]


[ c01b39c7a35ccc3b081a3e83d2c71fa9a767ebfeb45c69f08e17dfe3ef375a7b *ubuntu-9.10-dvd-i386.iso ]



gordon33

---

### Post by verymadpip on 2014-01-11
Hi there.
First, you need to download the correct iso file.  Try from here:
[http://www.releases.ubuntu.com/13.10/](http://www.releases.ubuntu.com/13.10/)

You will then need to change directory (cd command) to the directory (AKA folder) that contains the downloaded iso.
```
cd Downloads 
```
Ubuntu is case sensitive, so downloads & Downloads are two different places.

Then run the md5 or sha256 command, for example:
```
md5sum ubuntu-13.10-desktop-i386.iso 
```
Or whichever version you have downloaded.

The result will be a string of characters that should match the string for your downloaded version from this page:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
If the bunch of characters don't match download the iso again.

This all assumes you have a working Ubuntu installation to do this from.

Good luck.

---

### Post by tgalati4 on 2014-01-11
Regardless of how you install 13.10, you didn't address the original problem.  What caused your 10.04 system to fail?  To me it looks like a disk failure or a power supply failure:

System running fine for several years (10.04)
Then Firefox crashes (typically a bad profile or cache is messed up due to disk errors).
Then Computer freezes (could be disk access problem--not technically frozen, but waiting for data--IOWaits in *top* go up.)
Then Computer won't boot--again, trouble reading the drive during boot.
Prolems installing new distro--if the drive is bad then installing  new distros will be a frustrating experience.

What is the SMART status of the drive?

---

### Post by mörgæs on 2014-01-11
The easy approach is to try a fresh install of 13.10 first. Only if that also fails we should consider the hardware, which is difficult for most users to deal with.

---

### Post by gordon33 on 2014-01-11
Hello verymadpip, tgalati4, and morgaes

verymadpip I am downloading "ubuntu-13.10-desktop-i386.iso" from "http://www.releases.ubuntu.com/13.10/"  I will see what happens.

tgalati4, and morgaes  I will be looing into checking the SMART status of the drive on the hp lap top.  

Gordon33

---

### Post by gordon33 on 2014-01-11
I can not get the HP lap top to boot up that meens no terminal unless it can be accessed from BIOS?

---

### Post by mörgæs on 2014-01-11
Did you try both USB and DVD/CD for booting?

---

### Post by gordon33 on 2014-01-11
Morgaes the machine that work has a RO for the DVD disk drive.

---

### Post by gordon33 on 2014-01-11
gordon@gordon-desktop:~$ cd Downloads
gordon@gordon-desktop:~/Downloads$ md5sum ubuntu-13.10-desktop-i386.iso
d0508f909c2c71d96aeac5efb0329b33  ubuntu-13.10-desktop-i386.iso
gordon@gordon-desktop:~/Downloads$ 


Does this meen the dowload was okay?  

The HP lap top would not accept the install.  The computer when through a few screens and stalled at a ubuntu rust colored screen.  The only thing  of value was 2 arrows when clicked on listed web connections both wireed and non wired.

gordon33

---

### Post by gordon33 on 2014-01-11
Hello All

tgalati4 suggested checking the SMART status of the drive on the HP lab top.  Can this be done on a machine that will not boot up?

---

### Post by gordon33 on 2014-01-11
So the 3rd of 4 th down load was used to create a start up flash stick in hopes of getting the HP lap top to install Ubuntu 13.10.  After some time a box came up w3ith the following information.




Sorry Ubuntu 13.10 has experienced an internal error.

If you notice further problems, try restarting the computer.

Send a report to help fix the problem

show details                           			continue



click on show details

ExecutablePath
/usr/lib/gnome-settings-daemon/gnome-settings-daemon



click on continue

Invalid program report
This problem report is damaged and cannot be processed
error ('Error -3 while decompressing data Invalid Block type')

Close

---

### Post by pst007x on 2014-01-11
Fresh install, but only after you back everything up.

Boot into you system using a live CD, connect an external drive, and move the entire contents of you Home folder (and all hidden files) to you external drive. I would also back up the etc and usr folders too. 

After the fresh install of 10.04, you should be able to restore most of your settings and all of your files. However, i would recommend using the latest version of Ubuntu or a light weight derivative if you are using an old PC.

:guitar:

---

### Post by mörgæs on 2014-01-12
> **gordon33 said:**
> Morgaes the machine that work has a RO for the DVD disk drive.

I'm not sure what you mean. What is RO? Readonly? 
In general we would appreciate longer and more detailed posts.

Does the USB stick work when booting other computers? 
If you create a CD (not DVD) with Lubuntu 13.10 how does that work?

---

### Post by verymadpip on 2014-01-12
Hi gordon33.
Your download is fine :)

As a side note, I get the gnome settings daemon error fairly regularly on one of my machines.  However, it doesn't seem to cause me any problems.
Was that in a Live Session? (Running from USB stick after choosing the "Try Ubuntu" option)?  If so that could *possibly* be the reason for the faulty error report, but I'm not at all certain of that.

I think it would be a good idea to try the USB stick in a different machine as morgaes has suggested.

---

### Post by gordon33 on 2014-01-12
Hello morgaes and verymadpip

Yes I am sorry I ment the disk drive is readonly for DVD's.  I did not think CD had enough space for Ubuntu.  i will look for a CD with a bout 900 MB's of space.

I have been reluctent to mess with the only other computer that works.  But I will try the USB key on the Dell that works.

What has happend about 40% of the download tries, has been the machine does not show the usual question boxes.  No questions to try or download, no langue question, no time zone question.  The Lap top just booted up in the newer version of Ubuntu.  Still none of my folders were seen, and Firefox would not connect to the wired internet.  This makes me wonder would the folders be seen owith a live version?

I remeber one or 2 tries where the machine asked thoes questions.  When I thought the download was verry close to compleat I got a error message the same as the one In thread # 16.

I am going to see what happens when this computer is restarted with the USB Startup Ubuntu.

Hope this does not kill this computer.

Gordon33

---

### Post by gordon33 on 2014-01-12
The Dell desktop is an older computer and I did not find a BOOT from USB option.  I did select "other" as a boot option but the mache did not recognize the USB Startup key.  I will take the usb key to a public computer and see what happens.

gordon33

---

### Post by gordon33 on 2014-01-12
I Went to BIOS on th HP lap top ( the one I am having install problems with) and did the 3 test:

Statr-up Test      PASSED
Primary Hard Disk Self Test  PASSED

Run-In Test
The "memory Test" portion PASSED
The "Primary Hard Disk Self Test"  portion  PASSED  (But it kept repeaing its self 0%-100%)

gordon33

---

### Post by verymadpip on 2014-01-12
Hi gordon33.
Sometimes USB sticks appear in the options section for hard drives & not removable devices/USB drives.
It may be worth looking in that area of the BIOS.

---

### Post by gordon33 on 2014-01-12
I checked the BIOS on the Dell some of the list was as follows:

"Removable Device Priority [Press Enter]"  (pressed enter and the following was selected)
"USB-ZIPO : hp USB Flash Drive"

First Boot [Removabl]
Second boot [Hard Drive]

so it looked good.   Started the machine with the USB key to get a Boot Error mesage.

---

### Post by verymadpip on 2014-01-13
Hi gordon33
Can you please check in the hard disk boot priorities & see what's there.
Just to keep me quiet if nothing else.

---

### Post by gordon33 on 2014-01-13
Hello verymadpip

The first priority in the hard disk boot priorities was:  "USB-ZIPO : hp USB Flash Drive"  on the Dell desk top (that has been working) that I tried to use the startup USB flash stick on.

Presently  I have the Hard drive out of the HP G60t-200.  I will be learnihng how to test it out the lap top.

Gordon33

---

### Post by ppjdee on 2014-01-13
I cant comment on the usb installation method as i havent used that method yet. But i think a normal CD is only 700-800mb and Ubuntu 13.10 i think is larger than that now. So you may have to slow burn the iso to a DVD via your dvd drive.

---

### Post by verymadpip on 2014-01-14
Higordon33.
Thanks for checking that for me.  At least we know you're trying to boot from the right drive (I assume).

I think the easiest way to test the HDD is to connect it to a working machine & use disk utility (or "disks" I think it's called) to check the SMART data, if the HDD supports it.
I think you can do that from a working installation or a Live Session.
How comfortable are you with opening up a machine?

I think I am nearing the end of my usefulness to you by the way...

Maybe it would be worth checking that your USB stick is ok too.  Just an idea.

---

