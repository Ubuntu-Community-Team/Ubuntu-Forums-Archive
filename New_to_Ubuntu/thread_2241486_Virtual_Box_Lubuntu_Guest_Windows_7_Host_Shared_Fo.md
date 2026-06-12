---
title: "Virtual Box Lubuntu Guest Windows 7 Host Shared Folders"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by Jim_Brown on 2014-08-26
I have successfully installed Lubuntu as a guest on two systems, including Guest Additions, and I've set up two shared folders using the Devices, Shared Folders Settings dialog. One system is WinXP Pro Host, the other is Win 7 64-bit host. I've checked the boxes for Auto Mount and Make Permanent. My problem is that I can't find these shared folders in the GUI. What do I need to do to see these folders?  They are My Documents and Downloads on the Windows Host. VBox is 4.3.12

I'm a retired EE and have been using computers actively since 1982, beginning with CP/M, but am completely new to Linux. I would appreciate suggestions for a book applicable to Lubuntu.

Thanks

Jim K9YC

---

### Post by yancek on 2014-08-26
If you want to access folders/files on the windows host from the Lubuntu guest, you need to create a mount point for it and either manually mount it or put an entry in /etc/fstab.  The standard place is under the /mnt directory in Lubuntu.  If you open Devices while booted to Lubuntu in VBox and click on Shared Folders you can see the command for Linux or windows if you move the mouse in to the main window on the right.

---

### Post by ajgreeny on 2014-08-26
In your Lubuntu guest the shared folders will normally be in /media/sf_*username*

In the guest you must be  member of the vboxsf group in order to share the folders, so check that with terminal command **groups** and if you are not a member add yourself to that group.

---

### Post by Jim_Brown on 2014-08-26
Thanks. I added myself to vboxsf, then looked in /media  There is /media/username, but no /media/sf_username.

---

### Post by Jim_Brown on 2014-08-26
> **yancek said:**
> If you want to access folders/files on the windows host from the Lubuntu guest, you need to create a mount point for it and either manually mount it or put an entry in /etc/fstab.  

>>You're assuming I know more than I do. :)  What entry do I put in /etc/fstab?  _How_ do I put it there?

The standard place is under the /mnt directory in Lubuntu.  If you open Devices while booted to Lubuntu in VBox and click on Shared Folders you can see the command for Linux or windows if you move the mouse in to the main window on the right.

>> I tried this and didn't see any commands. I clicked on the VBox Devices Menu for the Lubuntu Guest, then selected Shared Folder Settings. Right? 

Thanks

---

### Post by yancek on 2014-08-26
I have an older version of VBox, don't use it often.  Boot the system in VBox, click on Devices, Shared Folders and a new window opens.  Moving my mouse to the right into the main window, it show an example windows and an example Linux command.  Might not be on your version?

Did you check in the /media/username directory to see if the shared folders were there?  I thing that is what was meant by sf_username??  I usually create my mount points manually so can't help with this.

---

### Post by Jim_Brown on 2014-08-26
> **yancek said:**
> I have an older version of VBox, don't use it often.  Boot the system in VBox, click on Devices, Shared Folders and a new window opens.  Moving my mouse to the right into the main window, it show an example windows and an example Linux command.  Might not be on your version? 

Did you check in the /media/username directory to see if the shared folders were there? 

Yes, I did look, and the only thing there is an empty folder /username.

> **yancek said:**
>  I thing that is what was meant by sf_username??  I usually create my mount points manually so can't help with this.

Can you tell me how you do it manually (I assume you mean from the command line). The /mnt and /etc directories are there. I don't have any sort of reference that would tell me how to do it. 

Thanks

---

### Post by yancek on 2014-08-27
My examples from an entry in the Linux /etc/fstab file won't help because they are both Linux guest and Linux host using nfs (network file system)

If you want the windows shared folders mounted on boot in Lubuntu you will need an entry in fstab or you can manually mount them each time you boot.  VirtualBox has extensive documentation and the mount commands I referred to are on the VBox documentation link below:

[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

The general documentation page with the User Manual link is below:

[https://www.virtualbox.org/wiki/Documentation](https://www.virtualbox.org/wiki/Documentation)

---

### Post by steeldriver on 2014-08-27
Hmm this is odd

I have a number of unices in VirtualBox VMs on my Win7 desktop - on the older (crunchbang) one, Shared Folders "Just Works" - I did not need to add anything to the fstab, I just clicked the radio buttons for 'Permanent' and 'Auto'. The mtab entry looks like

```

none on /media/sf_steeldriver type vboxsf (rw,nodev,relatime)

```

I just tried the same on a vanilla 13.04 Ubuntu VM and it doesn't even mount - let alone automount. The folder is listed in the VirtualBox dialog but I can't find it anywhere...


EDIT: so it looks like you need to manually create the mountpoint and mount the folder one time to get things started, e.g.

```

sudo mkdir /media/sf_Documents

sudo mount -t vboxsf **Documents  **/media/sf_Documents

```

where **Documents**  is the 'Name' of the shared folder under the VirtualBox 'Shared Folder Settings' dialog. After that I rebooted and the folder was automounted

```

Documents on /media/sf_Documents type vboxsf (gid=999,rw)

```

---

### Post by Jim_Brown on 2014-08-27
> **steeldriver said:**
> 

EDIT: so it looks like you need to manually create the mountpoint and mount the folder one time to get things started, e.g.

```

sudo mkdir /media/sf_Documents

sudo mount -t vboxsf **Documents  **/media/sf_Documents

```

where **Documents**  is the 'Name' of the shared folder under the VirtualBox 'Shared Folder Settings' dialog. After that I rebooted and the folder was automounted

```

Documents on /media/sf_Documents type vboxsf (gid=999,rw)

```'

That worked!  Exactly what I was looking for. The shared folders show up in /media in the GUI. Many thanks. 

Another oddity for you mental collection. When installing Guest Additions on Lubuntu in the XP Pro Host machine, I executed "sudo ./VBoxLinuxAdditions.run from the /media/username directory, which is what VBox doc says. On the Win7 machine, I had to execute from the /media/username/imagename directory. I found that suggestion online, perhaps here. 

Jim

---

### Post by Jim_Brown on 2014-08-27
> **Jim_Brown said:**
> '

That worked!  Exactly what I was looking for. The shared folders show up in /media in the GUI. Many thanks. 

Another oddity for you mental collection. When installing Guest Additions on Lubuntu in the XP Pro Host machine, I executed "sudo ./VBoxLinuxAdditions.run from the /media/username directory, which is what VBox doc says. On the Win7 machine, I had to execute from the /media/username/imagename directory. I found that suggestion online, perhaps here. 

Jim

More in the "curious" department.  After using your suggested instructions to mount the shared drives in the Lubuntu VBox on the Win7 Host, I started to do the same thing on the machine with the XP Pro Host (but did not) and noticed that the shared drives were now shown in the /media directory. I think I had looked there before, so what happened in the meantime was one or more openings and closings of the Lubuntu box. 

So the "takeaway" is the VBox sets up a bit differently on a Win 7 Host as compared to an XP Pro Host.

---

### Post by yancek on 2014-08-27
Changes in /etc/fstab on Linux are usually not made until a reboot, as I understand as the file is read on reboot.  I would guess that the option you used in VBox to make your setting permanent did just that.  Not really familiar enough with it so it's just a guess.

---

### Post by ajgreeny on 2014-08-27
> **yancek said:**
> Changes in /etc/fstab on Linux are usually not made until a reboot, as I understand as the file is read on reboot.  I would guess that the option you used in VBox to make your setting permanent did just that.  Not really familiar enough with it so it's just a guess.
The command ```
sudo mount -a
``` will also execute fstab without a reboot, and is a great way to check that there are no problems or syntax errors after an fstab edit; no error message on running the command means all is OK.

---

