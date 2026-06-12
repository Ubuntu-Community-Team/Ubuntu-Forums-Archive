---
title: "Recover hard disk data"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by ranggaahdiat on 2013-03-23
Help me . im very newbie in using ubuntu 12.10
This morning I installed ubuntu from usb, usb and I borrowed from my brother. 
I posted back up all the files from its usb drive and move it to drive e (in windows 8). I installed ubuntu with replacing of windows 8 to ubuntu. I did not press the buttons to format the data. 
but fitting I saw on the home folder (ubuntu) I can not see all the partitions like in windows 8, and saw the number of its size to be 500GB (total of all capacity hard drive).
 I tried all the way there on the forums but still , i cant recovery my brother data . help me master ubuntu . im really need help 
sorry my grammar is bad

---

### Post by AlecJ on 2013-03-23
If you selected "installed ubuntu with replacing of windows 8" then you have formatted the hard drive, no data left.
If you selected to install alongside and to daul boot, then at boot select to boot into windows, where all the data is.

---

### Post by ranggaahdiat on 2013-03-23
> **AlecJ said:**
> If you selected "installed ubuntu with replacing of windows 8" then you have formatted the hard drive, no data left.
If you selected to install alongside and to daul boot, then at boot select to boot into windows, where all the data is.

then what must i do ? is there a way to recover it

---

### Post by AlecJ on 2013-03-23
did you select Replace Windows 8?

---

### Post by ranggaahdiat on 2013-03-23
> **AlecJ said:**
> did you select Replace Windows 8?

yes replace ,
i think thats is only format drive c

---

### Post by AlecJ on 2013-03-23
Easy way to find out

look in Dash for "Gparted"

This will show the whole drive and the partitions on it, 
here is mine showing the windows partition

---

### Post by ranggaahdiat on 2013-03-23
[ATTACH=CONFIG]240449[/ATTACH]

 this is . look like it can not be recovered  . thanks anyway

---

### Post by Isamu715 on 2013-03-23
The original partition layout may be unrecoverable but you can probably recover your data with an utility like Photorec.

---

### Post by Mark Phelps on 2013-03-23
If you're willing to spend a little money to get the files back, and photorec doesn't work, then read on: 

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

### Post by Bashing-om on 2013-03-23
ranggaahdiat; Hi !

In addition to the above, the situation may not be hopeless. How much time and effort are you able to expend ?
Here is an linux tutorial to recover data that will prove of value. However it requires a deep understanding of what you are doing. There are no guarantees any data is recoverable, particularly so if the data has been over wrote.

[http://linux.sys-con.com/node/117909?page=0,0](http://linux.sys-con.com/node/117909?page=0,0)
[INDENT=2]
worth a shot

[/INDENT]

---

### Post by ranggaahdiat on 2013-03-24
its been two days 
now im trying use photorec , thanks for advice im looking for your guide .

---

