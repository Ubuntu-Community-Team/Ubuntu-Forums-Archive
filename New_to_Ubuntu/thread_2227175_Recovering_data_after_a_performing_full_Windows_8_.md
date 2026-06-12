---
title: "Recovering data after a performing full Windows 8 recovery"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by Flesh_Hammer on 2014-05-31
Hello, my friend's computer recently crashed and he decided to do a full system recovery. The computer is an HP desktop that came with Windows 8 pre-installed. He used the HP recovery option to reload his OS. He attempted to backup his data during the recovery process but ran out of space on his external hard drive and the backup failed. Obviously he lost all of his personal data after the recovery and I am wondering if there is any way to recover this data? I know that it is possible to recover data after a format but since he did a full recovery on this drive which also installed Windows 8 I'm worried that any old data was overwritten and may now be impossible to recover. 

I'm running Ubuntu 14.04 on my laptop and I have his hard drive setup as an external USB. I can view his hard drive and see all of the current partitions and files. I can see the hard drive in Gparted and I've run testdisk to scan for lost partitions but have not been able to see any old partions or data. 

Is there any way to recover his lost data from before the recovery process?

---

### Post by LastDino on 2014-05-31
Since you've ran the recovery and overwritten any possible existing file fragments, it is not likely. However, you can still try to consult some professional data recovery service to see if they can offer any help. Mind you, they do not come cheap.

---

### Post by Flesh_Hammer on 2014-06-01
Thanks LastDino. I feared as much. I guess he'll just have to suck it up and re-download all of his porn. ;)

---

### Post by oldfred on 2014-06-01
You can try photorec, but a long process.
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

When I used photorec on a smaller drive it took over 8 hours. And you only get extensions not full file names.

And with a Windows reinstall, it is larger and overwrites from the start of drive. Or less likely to have left over data, but depends on where on drive it was.

Others:

 gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Some suggest this is better for NTFS but is not free.

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

One more reason I suggest separate system & data partitions. A smaller system partition is very slightly more efficent and having separate data partition may allow better recovery. But you then do have to manage partition sizes and houseclean system regularly.

---

