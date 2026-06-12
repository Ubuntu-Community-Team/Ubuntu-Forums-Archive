---
title: "Unmounting Devices and using storage partition for media files instead of home"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by Staarlite on 2013-04-14
I am running Ubuntu 12.04.2 64bit dual boot with Win 7 on my Asus N56VM in EFI mode.
Apologies for long post but please bear with me...
After running NTFS Configuration tool I am unable to eject the 3 devices in my home folder.  The error message that comes up for each device is "Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=245440B15440878E from /media/DEVICE."  The OS (Location /media, Volume OS) & Recovery Devices (Location /media, Volume OS) should definitely NOT be mounted as they relate to the C Drive and Recovery partition in Windows.  The Storage device is my data partition that I want to use instead of Home for my media files so that I can share them between Windows & Ubuntu (Location /media, Volume Storage).  Currently I have media folders in both home and the storage device.  Folders in home only relate to home but folders in storage device can be seen by windows and ubuntu.
Firstly, how do I unmount these 3 devices so that I can eject them (as I could when I first installed Ubuntu)?
Secondly, once unmounted I want to redirect Ubuntu to use the storage partition as the location for my media files (docs, pictures, videos, music, downloads).  Will the procedure I've entered below work (please amend if I've made errors) and for this to work is it ok to keep the media folders in storage device and delete from home (only put 60gb to home but have 500gb in storage)?
PROCEDURE
Terminal: sudo cp /etc/fstab /etc/fstab.backup
Terminal: sudo blkid
Copy UUID
Terminal: gksudo gedit /etc/fstab
Add the following to the bottom of fstab and Save:
# storage mount
UUID=245440B15440878E /media/storage/    ntfs-3g        auto,user,rw 0 0
Reboot Ubuntu
Terminal: gedit .config/user-dirs.dirs
Change all items except desktop and templates from $HOME/ to /media/Storage/
Click Save & Reboot

---

### Post by fantab on 2013-04-14
So, you want to share a NTFS partition between Windows and Ubuntu? You don't want to use /home for your Media Files and want to use NTFS partition to store your Media? Correct me otherwise.

First of all, we don't EJECT partitions on the HDD. They are only UNMOUNTED. 'Eject' is for CD, DVD, USB drive, etc...

Secondly, if you unmount any partition Ubuntu cannot access it. The partition HAS to be mounted to be able to read from or write to it.

Now, if you have in fact followed the "PROCEDURE" you have posted, then I suggest you UNDO it. DELETE the /etc/fstab that you have created and then RESTORE the 'backed up' /etc/fstab.backup. You can do this by just removing the .backup after fstab.

Once this is done, we have to add 'NEW' fstab entry for the partition IF you want to 'automount'. If you don't want to automount then, IMO, you don't need a new fstab entry.

I use a shared NTFS partition between Windows and Ubuntu. I don't automount it. I mount it manually from 'Nautilus' whenever I need to.

For **[MORE INFO]("http://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions")**.

---

### Post by grahammechanical on 2013-04-14
When you speak of ejecting devices and you referring to removing their icons from the Launcher? If so then right click the icon and select Unlock from Launcher. Are you aware that the settings for Storage device mean that it will not be checked at boot up to see if it is about to fail? Do you really want to risk that storage device failing without much of a warning?

> [COLOR=#000000]UUID=245440B15440878E /media/storage/ ntfs-3g auto,user,rw 0 0[/COLOR]

The last zero disables file checking. You could change it to 2. 

> [COLOR=#333333][FONT=Ubuntu]You may also "tune" or set the frequency of file checks (default is every 30 mounts) but in general these checks are designed to maintain the integrity of your file system and thus you should strongly consider keeping the default settings.[/FONT][/COLOR]

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Regards.

---

### Post by Staarlite on 2013-04-14
> **fantab said:**
> So, you want to share a NTFS partition between Windows and Ubuntu? You don't want to use /home for your Media Files and want to use NTFS partition to store your Media? Correct me otherwise.

First of all, we don't EJECT partitions on the HDD. They are only UNMOUNTED. 'Eject' is for CD, DVD, USB drive, etc...

Secondly, if you unmount any partition Ubuntu cannot access it. The partition HAS to be mounted to be able to read from or write to it.

Now, if you have in fact followed the "PROCEDURE" you have posted, then I suggest you UNDO it. DELETE the /etc/fstab that you have created and then RESTORE the 'backed up' /etc/fstab.backup. You can do this by just removing the .backup after fstab.

Once this is done, we have to add 'NEW' fstab entry for the partition IF you want to 'automount'. If you don't want to automount then, IMO, you don't need a new fstab entry.

I use a shared NTFS partition between Windows and Ubuntu. I don't automount it. I mount it manually from 'Nautilus' whenever I need to.

For **[MORE INFO]("http://askubuntu.com/questions/46588/how-to-automount-ntfs-partitions")**.

Yes, that's exactly what I want to do.  
Apologies - I used the word eject because the unmount buttons look like eject buttons next to each of these devices in the home folder.  
I thought the solution would be to unmount all 3 devices and then remount the storage device as the default location for my media folders.  Put everything back the way it was when I first installed (I had ownership of all 3 devices and could use the unmount button next to each, whereas now root has ownership and thus I can't unmount them using the buttons and get the error message I posted).  I don't understand why ownership has transferred from me to root and why the OS & Recovery devices are now mounted - surely I need to unmount these 2 since they belong to windows? 
What are the pros and cons of manual versus automount - to help me decide which road I should go down?
If I don't automount this storage partition, does this mean it won't be checked for errors at startup and as you've said above - I won't be able to read/write to it?  If so, I don't understand why you would have a shared partition that you manually mount as it would mean that each time I want to access/change files I'd have to manually mount my storage partition?
Can you explain what you mean by mounting it manually from Nautilus when you need to?  I've looked this up in the software center & it says it's the file mgr and graphical shell for gnome which is installed already.  
Apologies if this is all very obvious to you but this is all very new to me right now and am grateful for your help and clarification.
Thanks for your help.

---

### Post by fantab on 2013-04-14
Okay. There are no pros and cons, per se when you use automount or manual mount. My thing is why mount it when you don't need to. I am not accessing my Shared partiton all the time, I only access it when I play my media or want to save something on it. So, I mount it when I need it. Automount will mount the partition when Ubuntu boots and it stays mounted, until you manually unmount it. That is all.

[QUOTE=Staarlite]If I don't automount this storage partition, does this mean it won't be  checked for errors at startup and as you've said above - I won't be able  to read/write to it?  If so, I don't understand why you would have a  shared partition that you manually mount as it would mean that each time  I want to access/change files I'd have to manually mount my storage  partition?[/QUOTE]

Yes. But since its a NTFS partition, Windows will 'automount' it and check for and fix file system errors, if any. When a partition is NOT mounted, lets say, its NOT active, its NOT available to the system. Windows automounts all its partitions, we have no choice, whether we use it or not. My point why make it available when we are not using it. I am not reading or writing to my Shared partition all the time. So I like the idea of mounting it when I need it. That is all.

In windows you have 'windows explorer' which is a file manager, meaning a graphical interface where you see all your files and folders. In Ubuntu we have NAUTILUS as default file manager or file browser. There are many more in Linux.

In the file manager, Nautilus, on the left pane you have 'Devices' which are your HDD partitions (It will also show pluged in USB drives, CD/DVD drives when in use). You have to click the partition and it gets mounted, and it stays mounted until you unmount it. It is not mounted automatically when Ubuntu boots. That is what I mean by manual mounting.

See the Nautilus Screenshot below:
[ATTACH=CONFIG]241324[/ATTACH]

---

### Post by Staarlite on 2013-04-14
Accidental duplicate posting - see next post.

---

### Post by Staarlite on 2013-04-14
> **fantab said:**
> 
In the file manager, Nautilus, on the left pane you have 'Devices' which are your HDD partitions (It will also show pluged in USB drives, CD/DVD drives when in use). You have to click the partition and it gets mounted, and it stays mounted until you unmount it. It is not mounted automatically when Ubuntu boots. That is what I mean by manual mounting.

See the Nautilus Screenshot below:
[ATTACH=CONFIG]241324[/ATTACH]

Ok, from what you're telling me I should be able to unmount any of these devices by clicking on the unmount button next to them,but that's part of my current problem - I CAN'T unmount ANY of the devices because I don't have ownership of them anymore - root does.  When I click on the unmount button it says "Error unmounting: umount exited with exit code 1: helper failed with:umount: only root can unmount UUID=245440B15440878E from /media/Storage".
So firstly, do I need to fix this so that I have the choice whether I want to have these 3 devices mounted or not - because right now it appears they're ALL mounted and I can't choose whether they stay mounted or not.
Secondly, if I understand you correctly, if I choose the storage partition to be unmounted, then when I want to access files/folders in the partition, I simply click on the mount button (as per your screen shot)  and off I go.  Is that right?
Finally, I absolutely want ubuntu to automatically save all my media including downloads in my storage partition not my home folder.  E.g right now if I download something it goes to the downloads folder in my home folder not my storage partition.  What do I need to do to ensure that everything gets directed to my storage partition?
Thanks

---

### Post by fantab on 2013-04-14
Firstly, fix your problem as suggested in the post #2. Get your original /etc/fstab back. Then you can figure out how, what and when to mount your partitions. And the forum will help you.

---

### Post by Staarlite on 2013-04-14
Ok - must have run the command wrong - re-ran the f/stab back up and can now mount/unmount all 3 devices - phew!. So now I'd like to know how to enable ubuntu to point to my storage partition instead of home for all media files including downloads.  Can I do this as per part of my original procedure I outlined above:
Terminal: gedit .config/user-dirs.dirs
Change all items except desktop and templates from $HOME/ to /media/Storage/
Click Save & Reboot 				
Or is there another way that I change the location from home to storage?

---

