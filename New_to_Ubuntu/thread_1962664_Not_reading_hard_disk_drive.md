---
title: "Not reading hard disk drive"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Keithshoshin on 2012-04-21
I am new to Linux and have just installed Ubuntu on a 40GB IDE hard disk. The pc also has an 80GB SATA hard disk, 3/4 full of data important data, inherited from when the pc ran Windows XP. I had hoped to copy this material to an external hard disk, but Ubuntu cannot read it. What can I do to resolve this? Any help will be appreciated.

---

### Post by ajgreeny on 2012-04-21
Does the system see the disk at all, or is it invisible to ubuntu?

It should appear in the left hand pane of nautilus, the file manager.  If it doesn't and is not listed in the places list in that left pane, please use the command ```
sudo fdisk -l 
```in terminal and report back here with the output.

---

### Post by Keithshoshin on 2012-04-22
Thanks. I have now found the correct menu and Ubuntu is recognising the 80gb drive. I now want to be able to copy the files from that drive to an external drive. Obviously I do not want to reformat the disk at this stage, but would like reassurance that if I click on 'Mount', it will enable me to read the files on the drive, and that there will be no risk of losing data on the drive. 

Am I right in thinking that the next steps would be 
mounting the 80gb drive
connecting and mounting the external drive

followed by a straightforward copy from one to the other?

---

### Post by souravc83 on 2012-04-22
Yes, those steps are correct.
mounting will not cause any data loss.

---

### Post by Keithshoshin on 2012-04-23
Thank you very much. Everything went smoothly. It is interesting that Windows wouldn't recognise the hard disk but Ubuntu had no problem with it.

---

