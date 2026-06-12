---
title: "second hard drive"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by geomcd1949 on 2013-08-06
Two computers, each with a primary SSD (on which Ubuntu 12.04 is installed) and a secondary HDD.

On the first computer, when I click the Home folder icon, I get a window that shows the second hard drive as a Device - it is shown as 1 TB File system.

On the second computer, when I click the Home folder icon, there is no category for Devices in the window that appears, and no sign of the second hard drive.

On each computer, when Ubuntu was installed, I didn't do anything that I think would have any effect on configuring hard drives - no gparting or anything like that - I just put it the bootable CD and followed the directions that came up.

My question is, how do I get the second hard drive on the second computer to show up in the list of things in the Home folder?

Thanks!

~George

---

### Post by Mk32 on 2013-08-06
Are they both formatted with the same filesystem?

Use gParted to find out if they are.

---

### Post by oldfred on 2013-08-06
Does BIOS see drive.
Is drive an internal drive or external?
What format are partition(s) on external drive.
Post this which may answer some of those questions automatically.

       sudo parted /dev/sda unit s print
      
 sudo blkid -c /dev/null -o list

Post above in code tags using # on advanced editor in reply. That preserves formatting.

---

### Post by deadflowr on 2013-08-06
Edit:<Deleted> I thought of something different than the point of this thread.

I'd follow oldfred's advice and make sure the drive is being read by BIOS.

---

### Post by geomcd1949 on 2013-08-07
Keeping in mind that this is the Absolute Beginners Section,

1. Don't know how to determine if the BIOS recognizes the drive,

2. Drive is internal,

3. Don't know how to determine the format petitions - drive is internal,

4. sudo parted /dev/sda unit s print
Model: ATA V4-CT128V4SSD2 (scsi)
Disk /dev/sda: 250069680s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       183670783s  183668736s  primary   ext4            boot
 2      183672830s  250068991s  66396162s   extended
 5      183672832s  250068991s  66396160s   logical   linux-swap(v1)

5. /dev/sda1  ext4             /              bbe886ab-4837-40f4-bf87-18375b775200
/dev/sda5  swap             <swap>         fac380ab-db75-4910-bf29-a506b84485ef

(sorry - don't understand posting instruction)

6. Don't know how to determine if they are formatted with the same filesystem, nor how to use gparted to determine this,

Sorry I don't know how to answer some of the questions.

~George

---

### Post by oldfred on 2013-08-07
Also should have asked for this:

sudo parted /dev/sdb unit s print

If it shows then BIOS has seen drive as no operating system can show a drive that BIOS has not seen. Command shows formatting or may give an error message if an issue.

---

### Post by geomcd1949 on 2013-08-07
sudo parted /dev/sdb unit s print gives:

Error: /dev/sdb: unrecognised disk label

---

### Post by oldfred on 2013-08-07
Disk label should not be an issue.


This command shows UUID, but also shows labels

sudo blkid -c /dev/null -o list

You can edit labels with Disks or Disk Utility or with gparted. I might make sure you only have text or number and no special characters.

---

### Post by geomcd1949 on 2013-08-07
speedbird@speedbird-desktop:~$ sudo blkid -c /dev/null -o list
[sudo] password for speedbird: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              bbe886ab-4837-40f4-bf87-18375b775200
/dev/sda5  swap             <swap>         fac380ab-db75-4910-bf29-a506b84485ef

---

### Post by oldfred on 2013-08-07
That is not showing any partitions or any part of sdb?

From Disks or Disk utility can you click on second drive? On the right it has Smart Status. It can run a lot of tests but all I really know is passed or failure.

---

### Post by geomcd1949 on 2013-08-07
Thanks OldFred,

In Disk Utility, I clicked on Format Volume, then Mount Volume, and the disk now appears in the Devices list. Exactly what I wanted. Appreciate the help!

~George

---

### Post by Jonathan Precise on 2013-08-07
If you're problem got fixed, then try the following:

First, on the top of the page you're on, go to Thread tools, as shown in the attachment.

Then click on "Mark thread as solved".

---

### Post by geomcd1949 on 2013-08-07
Jonathon,

I looked for the SOLVED mechanism before and couldn't find it.

I "tried" what you suggested. The **only two** options under THREAD TOOLS I get are SHOW PRINTABLE OPTIONS and UNSUBSCRIBE FROM THIS THREAD.

---

### Post by Jonathan Precise on 2013-08-26
Then go to your first post in this thread, click edit, then click go advanced. On the prefixes, change it to solved. Then click 'Save changes' or 'OK'. That should make this as solved.

Sorry I didn't respond in a while.:(

---

