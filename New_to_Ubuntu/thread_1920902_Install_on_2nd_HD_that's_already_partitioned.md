---
title: "Install on 2nd HD that's already partitioned"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by sillystring on 2012-02-05
Hey guys, brand new to Linux and a little overwhelmed.  Have a new Dell with Win7 on a 500GB SATA hard drive.  I installed a second HD 1TB SATA where I want to install Ubuntu 11.10. I'm working from a bootable USB. On the "Installation Type" screen I pick "Something Else" since I don't want to run Ubuntu alongside Win nor do I want to replace Win. Then I get the scary screen with my two drives and all the partitions listed and I'm stuck.   

I think I made a very big mistake and I don't know if it can be fixed or worked around... I partitioned my new hard drive from Windows Disk Manager and it now has three NTFS partitions and one Logical Drive. Now I understand that Ubuntu will partition the drive for me and now I know I cannot have more partitions than I already have.  So, is there a solution for this mess I created?

Thanks for any advise you can give me!

---

### Post by mikewhatever on 2012-02-05
You'll have to delete at least one partition and then let the installer use the unallocated space.

---

### Post by larrypg on 2012-02-05
Hello,

Does your new drive have anything on it?  Windows might have partitioned it but not installed anything.  If a partition is empty you can make it unallocated from windows disk utility and then have ubuntu install there.  I would make it an extended partition so that you can have logical partitions inside of it to make a seperate / and /home and swap.  First you need to check out your drive to see what is on it though.

---

### Post by sillystring on 2012-02-05
Hi, thanks!

There is nothing on the new drive. I deleted a couple partitions using Windows Disk Manager and now have 927GB of unallocated space. Will I be asked during the install what kind of partition I want... is this how I can make it an "extended partition"?

On the "Installation Type" screen where my drives and partitions are listed, if I highlight the Unallocated Space does that designate it as the  target space for the installation?  Want to be sure before I hit the "Install Now" button. 

Also, would it be correct to select my new hard drive as the "device boot loader installation?  Seems so but just want to be sure.

Thanks!

---

### Post by Bodsda on 2012-02-05
> **sillystring said:**
> Hi, thanks!

There is nothing on the new drive. I deleted a couple partitions using Windows Disk Manager and now have 927GB of unallocated space. Will I be asked during the install what kind of partition I want... is this how I can make it an "extended partition"?

On the "Installation Type" screen where my drives and partitions are listed, if I highlight the Unallocated Space does that designate it as the  target space for the installation?  Want to be sure before I hit the "Install Now" button. 

Also, would it be correct to select my new hard drive as the "device boot loader installation?  Seems so but just want to be sure.

Thanks!

If your not doing an advanced installation (where you manually assign every partition (/, /home, /boot)) then you should be fine just selecting the unallocated space.

The bootloader needs to go on whatever drive is first in the bios boot order. The default selected is usually the correct one.

Bodsda

---

### Post by sillystring on 2012-02-05
So, by selecting the unallocated space you mean that I simply highlight it? (orange bar)  Leave my first drive in the bootloader and I'm ready to hit install?

The free space will automatically be partitioned for the OS and SWAP without me doing it?

Thank you for your quick responses and patience with so many questions :)

---

### Post by oldfred on 2012-02-06
I would put the boot loader on the new drive's MBR and change BIOS to boot the new drive. Then if you ever have issues, you can still boot the Windows drive as it has the Windows boot loader still in it.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by sillystring on 2012-02-06
Success!  Deleted the extra partitions from my new hard drive during the installation process then manually set up the new ones. Had someone talk me through it but it was just like the link above from OldFred. I have Ubuntu up and running but since it's new to me I haven't used it enough yet to know if it's all stable.  Appears good so far.  

Thanks!

---

