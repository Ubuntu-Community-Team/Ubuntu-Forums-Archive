---
title: "Trying to recover a HD in a coma using Parted Magic"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by suppaduppa on 2013-08-31
So I have this NTFS HD, 200GB. It's an old Seagate. I have so much **** there.. valuable one. 
This morning I booted in Windows XP as usual but this hard disk was missing. I thought "well, this again". This happened to me a couple times before, I just would turn off the computer, connect and disconnect the SATA cable and power cable and then it would show up again. I managed to make it show up again but the computer was extremely unstable. I tried to copy the files from the disk into a safe 2TB one I have and I got a BSOD. I realized the disk works for like a couple minutes then it goes full retard..

I tried with Parted Magic and same happens, I can see it in health disk utility, then it starts getting really bad, like it freezes and stuff. I tried stuff like, fdisk, TestDisk... I always get some kind of error and it's not working. I tried the backup thing, an I couldn't do it, it said something about 0 size partition.. I cant remember the error.

I do remember what happened in the gui when I tried to access files on the, when trying to mount it said
"can't read superblock"

I took some screenshots and saved them on my 2TB drive but something went wrong and I can't see them.

I will boot again in Parted Magic and use my laptop to be here at the same time trying all the stuff you want to suggest. Let's hope I can recover the date, since the disk is not death yet but pretty close.

Thanks

---

### Post by whitesmith on 2013-08-31
Try SpinRite if you're dead in the water and the data is valuable. Gibson charges around $60 for his software. It's been around since the early 90s and saved many an ass, including mine. It works on pretty much anything--Windows, Linux, even OS/2!

---

### Post by coldraven on 2013-09-01
TestDisc is super powerful but use it carefully or you can be in worse trouble.
It comes with Photorec which will recover many file types but  you could end up with a folder with thousands of files and file fragments.
Create a folder on your 2TB drive for each file type that you want to recover in order to avoid confusion
[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Some good advice and links here:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by suppaduppa on 2013-09-01
Photorec is not an option, it seems like it recovers the files but doesnt name the files as they originally where. I have mostly samples and I need them to be with the same name otherwise my DAW will not recognize the samples and it will be a total mess.

Can you guys just tell me what cvars or stuff to type? Im honestly not very good with computers.

---

### Post by Mark Phelps on 2013-09-01
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

