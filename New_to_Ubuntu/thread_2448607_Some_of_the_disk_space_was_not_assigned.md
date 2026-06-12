---
title: "Some of the disk space was not assigned"
date: 2020-08-10
forum: New to Ubuntu
---

### Post by fentonlui on 2020-08-10
Hello all, I am very new to Linux. I was trying to install ubuntu server 20 LTS to a VM for testing purpose. My VM had a 1TB datastore and attached is the LVM setup screen but actually I am not familiar with every settings and values.
After the Ubuntu server was installed, I found that the / mount point was only 200GB and I don' t know where is the other 800GB.
Can you tell me which setting I had made wrong, and is there any way to recover that 800GB to my current / mount point?
Thanks in advance.

---

### Post by TheFu on 2020-08-10
Please don't post images. For LVM, we need to see:
```
sudo pvs
sudo vgs
sudo lvs
```

Copy and past the text output, then wrap it inside "code tags" from the "Adv Reply" editor.  Please.  Chances are it is ready for making new LVs for specific storage/directories you need.  When using LVM, there are lots of smart things to do, like NEVER allocate all the storage for use.  Leave room for snapshots and to create other LVs and to add storage from the VG into the existing LVs, as needed in the future.  In short, only allocate the storage you need for the next 3-6 months.

---

### Post by fentonlui on 2020-08-10
```
freddy@server01:/local/notesdata$ sudo pvs

[sudo] password for freddy:
 
  PV         VG        Fmt  Attr PSize     PFree   
  
/dev/sda3  ubuntu-vg lvm2 a--  <1023.00g <823.00g


freddy@server01:/local/notesdata$ sudo vgs
  
VG        #PV #LV #SN Attr   VSize     VFree   
  
ubuntu-vg   1   1   0 wz--n- <1023.00g <823.00g


freddy@server01:/local/notesdata$ sudo lvs


  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert


  ubuntu-lv ubuntu-vg -wi-ao---- 200.00g      
```

Thanks TheFu. Here' s the output.

---

### Post by TheFu on 2020-08-10
So, the PV is 1023G in size with 823G free.  The VG  is the same.
There's 1 LV, sized at 200G, which is too freakin' HUGE for the OS.  I would shrink that to 25G-30G, then create a few LVs for /home (25G /userid) and perhaps some others for all the other data you want depending on use.  I'd definitely create a swap LV, then remove any swap file.

For example, virtual machines can use 1 LV for each specific virtual machine. This is much more efficient than having huge storage areas shared.  Each VM gets block storage provided which is faster.
Videos that aren't being edited go somewhere outside /home/, since they probably don't need daily, automatic, versioned, backups.
Same for Music.

So, I'd use **lvreduce** to make the current ubuntu-lv 25G in size - you'll need to resize from a "Try Ubuntu" boot flash drive.  This takes a little time.

But if you are really lazy and don't care about security or backup design or doing things following best practices, you can just use **lvextend** to make the ubuntu-lv larger by whatever amount you want.  Be certain to use the **-r** option so the file system gets resized correctly, at the same time. This is about a 5 second command.  Creating or increasing the amount of storage for an LV is under 5 seconds, while the system runs and the file system is mounted.

Each **lvcreate** command is about 5 seconds too, then just format with ext4 and mount the LV in the normal way inside the /etc/fstab.  I'd strongly recommend using the file system links in /dev/ubuntu-vg/....  for the mount devices. Use sudoedit to modify any system files. These don't change from boot to boot and are much more useful to humans.  

BTW, there isn't any GUI for doing this stuff.

Normally, only fairly experienced Linux admins would choose to deploy with LVM.  It is crazy flexible, but does add some complexity to storage management.  OTOH, there's no way to go back and add LVM to storage that's already used without it besides wipe and start over.  On a server, having LVM is highly recommended to ensure backups are clean by using snapshots to quiesce the backup areas. LVM-snapshots are NOT backups, but they enable 100% clean backups to be taken.

With LVM, moving to larger storage is really easy too.  I've moved from 1TB --> 2TB --> 4TB HDDs over the years. Thanks to LVM, that migration was 1 command that ran overnight while the system was up and running.

Crazy flexible. Anyways, those are your options.  There are lots of lvm tutorials on the internet. The good news is that LVM is the same on all Linux systems and any tutorial from 2005 or later will work.  LVM has been used in Linux enterprises well over 20 yrs. It is rock solid, provided the admin doesn't ask for something foolish like spanning a file system across multiple disks without any redundancy or backups.

Ask if you get stuck, but the tutorials online should cover more than you need today.

Tip:  Don't use lvresize.  Use lvextend and lvreduce instead. This prevents accidentally saying to reduce when you mean to increase or increase when you mean to reduce.  1 character diff and ouch.

---

### Post by fentonlui on 2020-08-11
Thanks TheFu, I shall take the tutorials first :)

---

