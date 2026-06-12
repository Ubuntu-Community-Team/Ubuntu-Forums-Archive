---
title: "Unable to access Windows files running Ubuntu from a USB drive"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by alkin2 on 2014-05-18
My 8.1 stuffed up! It doesn't load Windows and instead keeps  saying Windows is repairing the problem and will restart. It keeps on  restarting time and time again.
  So I've mounted the latest version of Ubuntu onto a USB drive.  Changed my computers settings to disable fast boot and made the USB  drive a priority when booting. I did this in the menu by pressing F2  when I start the computer. I cannot change it in the power options in  Windows because I can't open it.
  I press try Ubuntu and when I go into the computer I can't open the hard drives it shows there because of the following message.
  I tried following instructions given here but still cannot access the drives. [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
  [http://imageshack.com/a/img841/9659/dqhgu.jpg](http://imageshack.com/a/img841/9659/dqhgu.jpg)
  Please help as I wish to save some of my files onto an external USB  before sending the computer back to the manufacturer where it will most  likely be formatted.
  Regards

---

### Post by sudodus on 2014-05-18
The message in the screenshot is clear. The NTFS file system needs repair, before it can be read by linux. And I think you need a Windows tool to repair it. If it was damaged but not [semi-]hibernated, it can be repaired from a Windows live repair system, for example
[URL="http://technet.microsoft.com/en-us/library/hh825110.aspx"]
WinPE for *Windows 8*: Windows *PE* 5.0 - TechNet - Microsoft[/URL]

I don't know what can be done with a semi-hibernated or hibernated system. Data concerning the file system is sitting in the virtual memory (corresponding to the swap of linux), and I don't know if it can be identified and written to disk by some other system than that which was hibernated.

---

### Post by Mark Phelps on 2014-05-18
The other problem is that, by default, when you exit Windows 8, it goes into a new form of Hibernation -- which actually keeps the partitions Mounted.  This prevents you from accessing them from outside Windows 8.  

To fix this, you have to get back into Windows 8 and disable FastStartup.  Then, when you exit Windows 8, it won't be hibernating anymore and you can then access the files.

If you have a file problem preventing you from accessing Windows 8, then consider doing the following:
1) Using another PC, download the ISO file of the Minitool Partition Wizard Boot CD
2) Burn a CD from that
3) Boot your PC using that CD
4) Use the option to Check the drive -- that will run CHKDSK and is likely to repair the filesystem.

---

### Post by Kingsrookie on 2014-05-18
Windows 8 will eventually boot to advanced startup if it can not boot into the partition correctly. In advanced startup you can use boot to USB and it will load Ubuntu. On a side note, if the file is hibernated, you can boot to command line and disable it so that Ubuntu will see the partition.

---

