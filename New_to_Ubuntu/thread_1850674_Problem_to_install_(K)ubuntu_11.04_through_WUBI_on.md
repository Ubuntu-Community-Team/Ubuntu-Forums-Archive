---
title: "Problem to install (K)ubuntu 11.04 through WUBI on Windows 7"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by srimadhann on 2011-09-27
When I tried to install Kbuntu 11.04 (WUBI.EXE) in drive-D on Windows 7  platform - Windows 7 installed in drive-C, I received some problem at  that time to install the software. I have used 1.0 TB hard disk and  partitioned as 6 drivers. I have interested to use Kubuntu software in  my system. Please give your suggestions to solve the problem. The  problem is as follows (as per the log  file):-

>>stdout=
09-21 18:43 DEBUG  TaskList: # Cancelling tasklist
09-21 18:43 DEBUG  TaskList: New task modify_bcd
09-21 18:43 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {c5a8f7af-e225-11e0-9e71-a71a88c27c0b} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 651, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {c5a8f7af-e225-11e0-9e71-a71a88c27c0b} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-21 18:43 DEBUG  TaskList: New task modify_bcd
09-21 18:43 DEBUG  TaskList: New task modify_bcd
09-21 18:43 DEBUG  TaskList: New task modify_bcd
09-21 18:43 DEBUG  TaskList: New task modify_bcd
09-21 18:43 DEBUG  TaskList: ## Finished modify_bootloader
09-21 18:43 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2011-09-27
Do you have dynamic drives setup on Windows? You shouldn't install Ubuntu over dynamic drives as it doesn't recognize them and could therefore lead to data loss.

That particular error is Windows refusing to let you boot something from that drive and that's usually because it doesn't physically exist in the partition table.

---

### Post by srimadhann on 2011-09-27
Thank you for your reply.I have partitioned my hard disk as 6 drivers in NTFS file system. Please explain me as brief, i.e., possible to install (K)ubuntu in my system or not.

---

### Post by Elfy on 2011-09-27
Please answer as to whether you are using dynamic disk or not.

Check in Windows.

---

### Post by Mark Phelps on 2011-09-27
> **srimadhann said:**
> Thank you for your reply.I have partitioned my hard disk as 6 drivers in NTFS file system. Please explain me as brief, i.e., possible to install (K)ubuntu in my system or not.

And, you did this using the Win7 Disk Management utility, right?

You should have paid attention to the warning popup that told you it was going to convert your partitions to Dynamic Disks.

---

### Post by srimadhann on 2011-09-27
I do not know this is dynamic disk or not.  How do I know about my disk dynamic or not? Please give me guidelines. In which partition, can I install (K)ubuntu ? i.e. dynamic or basic disk.

---

### Post by bcbc on 2011-09-28
Boot windows, hit the start button, type 'disk manage' and right at the top you'll see 'Create and format hard disk partitions'. click on that and you'll see the Disk Management console. That'll tell you whether the partitions are dynamic or not.

---

### Post by srimadhann on 2011-09-28
Dynamic type.

---

### Post by bcbc on 2011-09-28
I know that some people have installed ubuntu over dynamic disks. But it appears that Ubuntu only sees the partitions as shown in the partition table and ignores the dynamic drive info. So this could lead to corruption/data loss.

The only solution I am aware of is to switch back to 'Basic disks'. Unfortunately this is not supported by Windows.

In my opinion, Windows doesn't warn strongly enough when offering to switch to dynamic disks - that this is not a reversible process and also that it could be incompatible with other operating systems.

Microsoft offers [this unhelpful advice]("http://technet.microsoft.com/en-us/library/cc755238.aspx") on converting back to basic from dynamic:
> The decision to convert a dynamic disk to a basic disk has implications that should be considered carefully. For more information about basic and dynamic disks and how to choose which type to use, see [http://go.microsoft.com/fwlink/?LinkId=64133](http://go.microsoft.com/fwlink/?LinkId=64133).
To change a dynamic disk back to a basic disk using the Windows interface
1. Back up all volumes on the disk you want to convert from dynamic to basic.

2. In Disk Management, right-click each volume on the dynamic disk you want to convert to a basic disk, and then click Delete Volume for each volume on the disk.

3. When all volumes on the disk have been deleted, right-click the disk, and then click Convert to Basic Disk.

This link [http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html) has an option (option four) that show how to convert back to basic without losing everything - but it warns that a full backup is required. In principle, if you delete only the volumes that aren't in the MBR partition table, it should be okay to convert it, but obviously there is a strong chance of losing everything.

---

### Post by jackparsana on 2012-02-09
Hello guys,

Please reply here this is work or not..

i face same problem. so solve this.


Jack parsana

---

