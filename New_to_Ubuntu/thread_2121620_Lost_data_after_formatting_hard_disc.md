---
title: "Lost data after formatting hard disc"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by jrbrooks on 2013-03-02
I have a dual boot Ubuntu/Windows system. I added a 1TB hard disk to my system, formatted it with the NTFS file system and partitioned it into 2 nominal 500 GB drives. I have been using it for months with no problems.
Then, yesterday, I thought I was formatting a removable hard disc with the FAT file system but found to my horror I had formatted one of the partritions. This partition contains/ed all my photos AND it is my backup location. So my backups have gone too.

Is there any hope?

---

### Post by matt_symes on 2013-03-02
Hi

Your best bet may be test disk but very best of luck to you !
```

matthew-S206:/home/matthew/dlink_dir_615/tp-link % apt-cache search testdisk
testdisk - Partition scanner and disk recovery tool
testdisk-dbg - Partition scanner and disk recovery tool
matthew-S206:/home/matthew/dlink_dir_615/tp-link % 
```

Boot into a Ubuntu liveCD/USB, install testdisk and run it.

```
sudo apt-get install testdisk
```

There are load of tutorials on the net.

Here is one

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Kind regards

---

### Post by arpanaut on 2013-03-02
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Should give you some options.

---

### Post by ezcomputersolutions on 2013-03-02
The only thing that I can think of that you can try is this.

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

If that doesn't work, I don't know what will.

---

### Post by Mark Phelps on 2013-03-02
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

### Post by presence1960 on 2013-03-02
Testdisk has a windows version. Recuva is a decent windows recovery software as well. Whatever you do, do not mount those volumes, if any writes occur you may lose any chance you have of recovering your files. I would do what Mark says based on your filesystem. If it was windows filesystem then try windows recovery software. I would try free software first.

For future reference: Always have at least one working backup of your files because stuff happens.

---

### Post by jrbrooks on 2013-03-04
Thanks for all the help. Unfortunately I am still in the xxx. The  biggest advance I have made is to discover that I could install Classic  Menus and forget the ghastly thing I have been using since moving to  Ubuntu 12.04. Now I can find and control things again.
I simply could  not follow the instructions for downloading the image file for CDRom  for Ubuntu 9.01 "Karmic Koala". I booted normally and installed and ran  Testdisk. The sparse black screen worried me. Testdisk took at least 7  hours to scan the 1 TB drive. The next morning it told me that the disk  size was wrong (implying a hardware fault?) and appeared to say that  nothing could be recovered (or did it?). I selected Quit and not  Continue. I booted from my GParted disc and it showed me in a nice  pretty picture exactlly what the story was on the the drive. The 500 GB  NTFS partition that I had messed up was broken into 3 or 4 blocks - 420+  GB, 50 GB and a couple of smaller ones with non-NTFS file structure.   There is an option "Attempt Data Recovery" - before pressing the button I  checked with the GParted Forum. They were helpful but recommended  "Photorec". Photorec is also written by "Testdisk man".  I have booted  into Windows once (to do something else on other partitions) and noticed  that it had no "knowledge" of the re-formatted partition (not  surprising).
I am thinking to go with Mark and presence1960 and use a Windows utility as all the files were written under NTFS. 

btw  I had a fully up-to-date Ubuntu back-up - stored nicely on guess which  partition. Just to prove Sod's law is alive and well, the Windows  Back-up feature does not work so no Windows back-up. I have been on the  Microsoft forum with error messages - they have not solved it yet.

---

### Post by montgomeryj on 2013-03-05
Another option that you have depending on your technical abilities is to recover the data and information on your own.  There is a tool called Autopsy which utilizes sleuthkit to explore crashed, erased hard drives as well as recover information from them.  You can find information on how to download and install Autopsy (sleuthkit should install automatically) for windows and linux at [http://www.sleuthkit.org/autopsy/](http://www.sleuthkit.org/autopsy/).  I hope that this helps you out.  Post here if you have any more questions in relation to those tools.

---

### Post by jrbrooks on 2013-03-25
I tried three different Windows-based file recovery options. Recuva, RecoverMyFiles and Stillar Phoenix; the latter 2 give you a free analysis and if you are happy with the analysis then you pay to actually carry out the fix. No success. Then I used Testdisk again (I actually made the Ultimate Boot Disk which contains various utilities). Again I could not recover the original file structure on the partition that I had formatted. I received a lot of help from the forum on cgsecurity.org but I could not get my partition back. However as the only files that I was desperate to recover were my photos etc. PhotoRec recovered the files excellently. All file names are lost but you have the file size and the date that the file was modified to help you sort everything. Hours of work of course. Remarkable number of jpeg files etc. are downloaded from the internet without ones knowledge.
Anyway I think I have recovered at least 90% of my photos. Fortunately I found I had backed up my photos onto my laptop a few months ago which helped.
I have made a note of the reference to "Autopsy" (montgomeryj) in the unlikely event that I do something this stupid again.

Thanks to all who offered help and advice.

I should close the thread but I do not know how to do that!

---

