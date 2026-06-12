---
title: "Missing Windows Partition after ubuntu installation"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by bob80 on 2014-05-06
Hi ubuntu users! I am new to ubuntu, I have just intalled ubuntu on my system. Previously I have Windows 8 OS with two partition C:/ and D:/. Now, I could no more find D:/ drive. I taught I only reformat C: drive but it seems that D drive is also reformated. Is there any way to bring my D drive partition back?.  thank you

---

### Post by oldfred on 2014-05-06
If you said install to entire drive, that overwrites the entire physical hard drive. 

Post this, but stop using installed system immediately. Use live installer.
sudo parted -l

If you have data on d: that was not backed up and is worth several days of effort to recover you can use tools to scan drive and find files. Anything already overwritten will be gone. AND STOP using drive as all activity is overwriting more data. Linux is not large so some data will be recoverable, but it is not easy.

You can use free Linux tools like photorec or Windows tools that are not free and many say work better.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

      
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

