---
title: "HOWTO: Share (samba) your NTFS directories from Ubuntu"
date: 2010-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by xenton on 2010-10-02
Right thanks everyone for your help though I'd throw together a HOWTO on this now I've got it working:

Firstly if you haven't already, you need to get your NTFS drives working  in Ubuntu. The method outlined below will mount all your drives  automatically on startup.

Click on*** Applications > Ubuntu Software Centre*** then  type NTFS in the search box, install NTFS-3g and the NTFS Configuration  Tool 

Now Click*** System > ****Administration> NTFS Configuration Tool*** and check the 'enable write support for internal devices' checkbox

Ubuntu can only share that which it owns, and at the moment your NTFS drives are owned by root, we need to change this;

Open a terminal and type

```
sudo gedit /etc/fstab

```You must add  
uid=1000
to any line that refers to an NTFS drive so my fstab was this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/mapper/nvidia_abjcfaad3    /    ext4    errors=remount-ro    0    1
/dev/mapper/nvidia_abjcfaad2    /media/Seven    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_jjeidcec1    /media/Storage    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad1    /media/XP    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad5    none    swap    sw    0    0
```and becomes this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/mapper/nvidia_abjcfaad3    /    ext4    errors=remount-ro    0    1
/dev/mapper/nvidia_abjcfaad2    /media/Seven    ntfs-3g    defaults,uid=1000,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_jjeidcec1    /media/Storage    ntfs-3g    defaults,uid=1000,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad1    /media/XP    ntfs-3g    defaults,uid=1000,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad5    none    swap    sw    0    0
```click ***File>Save ***then exit gedit.

Ubuntu won't share the files unless it has the correct permissions, and  at the time of writing, setting permissions for NTFS volumes wasn't  possible from within Ubuntu. So, restart your computer and boot into  windows XP. 

You must first disable simple file sharing:

Click ***Start>Control Panel ***if you are in classic view you will see the following screen and simply double click ***folder options***
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/folderoptionsclassicview.jpg?t=1286031444[/IMG]
If you are in the category view you will see this screen:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/folderoptionscatview1.jpg?t=1286031639[/IMG]

Click on ***Appearance and Themes***

Now click on ***Folder Options*** to open the following dialogue box:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/2folderoptionsdialogue.jpg?t=1286037532[/IMG]

Click on the ***view*** tab then scroll down to '***Use simple file sharing (Recommended)***' Click apply.

Now navigate to the folder you want to share from within Ubuntu, ***right click*** on the folder then click on ***properties*** you will see something similar to the image below, in this example I am sharing a folder called complete:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/1folderproperties1.jpg?t=1286037966[/IMG]

We are going to give full control to 'Everyone' [SIZE=1](please  note I have only tried giving full control to everyone and this is the  only tested working solution I have tried, other combinations of  read/write control may work, I have not tried)[/SIZE] in most cases we  must create the group 'Everyone'.  Click the Security tab then click  Add... you will get a dialogue box similar to this:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/2addeveryone.jpg?t=1286038628[/IMG]
Click in the large box at the bottom and type ***everyone*** then click on ***Check Names*** then click on ***OK ***this will return you to the previous dialogue:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/3giveeveryonefullaccess.jpg?t=1286040877[/IMG]
Click on ***Everone*** then click in the check box to allow ***full control*** then click on ***apply***.

You can then click OK and then reboot into Ubuntu

Now open the software centre again and search for samba, install the **'samba'** and '**GUI for managing samba shares and users'**.

Now click ***System>Administration>Samba*** then click ***Preferences>Server Settings...***

Change the Workgroup name to the correct name (as used by the rest of your network) then click*** OK.*** Back at the main Samba GUI as pictured below, click the green + to add a share:
Click ***browse*** and locate the folder we have just changed permissions for in XP then check visible, and optionally check writeable. 
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-CreateSambaShare.png?t=1286041960[/IMG]
Click on the access tab and grant access to 1 or more specific users or  allow access to everyone (In which case anyone connected to the network  will be able to view, and if you selected writeable, modify your files)
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-CreateSambaShare-1.png?t=1286042162[/IMG]
Click ***OK*** then exit the Samba GUI. Job done, you may need to restart Samba or reboot.

Working for me from within Lucid sharing to an XP laptop and an Xbox running XBMC.

Massive thanks to [[COLOR=#d40000]**dmizer_[B] [COLOR=Black]and[/COLOR] **_[/B][/COLOR]]("http://ubuntuforums.org/member.php?u=77219")[ Morbius1  ]("http://ubuntuforums.org/member.php?u=982144")

---

### Post by SuperFreak on 2010-10-15
Followed your instructions up to changes in Windows. I was unable to find "security" tab in NTFS folders only "General"," Sharing" and "Customize"

Also can you clarify what you mean by "Change the Workgroup name to the correct name" aree you changing this to the file name "complete" or what

---

### Post by xenton on 2010-10-15
> **SuperFreak said:**
> Followed your instructions up to changes in Windows. I was unable to find "security" tab in NTFS folders only "General"," Sharing" and "Customize"

It sounds like you still have simple file sharing enabled, please follow the steps to turn it off.

> **SuperFreak said:**
> Also can you clarify what you mean by "Change the Workgroup name to the correct name" aree you changing this to the file name "complete" or what

Yes, all computers on the network must have the same workgroup to be able to see each other correctly. The correct name, would be the workgroup name used by the other devices in your network.

It may be possible to get your NTFS shares working just by modifying fstab entries (not need to do anything on the windows side) I have not yet had time to test this and modify the guide accordingly but you can have a look here if your interested [http://ubuntuforums.org/showthread.php?t=1575426&page=3](http://ubuntuforums.org/showthread.php?t=1575426&page=3)

---

### Post by SuperFreak on 2010-10-15
Thanks for the clarification and I was able to follow your steps and had some success.
What I am trying to do is connect my network music player ( a "Squeezebox") to Ubuntu so I can play music files from my computer on my stereo. This may be beyond the scope of your tutorial but what seems to happen is when I shut down Ubuntu and then restart Ubuntu I have  problems and my "Squeezebox" does not always see my music files as it should. I  get an error message as Ubuntu boots saying "The disk drive for media/Music_ is not ready yet or not present". I if I do nothing the computer seems to spit out a few lines of code and stop. If I skip the problem by pressing S then my "Squeezebox" does not find any music files and even if I mount the drive by right clicking on it it still doesn't work. Sometimes the error message appears and I can't use my "Squeezebox" and sometimes it doesn't and I can use it.
Right now I am trying this dual boot setup with the aim of weaning off of M$ and going all Linux. The "Squeezebox" is essential if I do this and I realize it may work best if my FLAC and MP3 files are in a Linux friendly files system but until I am comfortable with Ubuntu I will maintain the NTFS file system

---

### Post by xenton on 2010-10-16
> **SuperFreak said:**
> Thanks for the clarification and I was able to follow your steps and had some success.
What I am trying to do is connect my network music player ( a "Squeezebox") to Ubuntu so I can play music files from my computer on my stereo. This may be beyond the scope of your tutorial but what seems to happen is when I shut down Ubuntu and then restart Ubuntu I have  problems and my "Squeezebox" does not always see my music files as it should. I  get an error message as Ubuntu boots saying "The disk drive for media/Music_ is not ready yet or not present". I if I do nothing the computer seems to spit out a few lines of code and stop. If I skip the problem by pressing S then my "Squeezebox" does not find any music files and even if I mount the drive by right clicking on it it still doesn't work. Sometimes the error message appears and I can't use my "Squeezebox" and sometimes it doesn't and I can use it.
Right now I am trying this dual boot setup with the aim of weaning off of M$ and going all Linux. The "Squeezebox" is essential if I do this and I realize it may work best if my FLAC and MP3 files are in a Linux friendly files system but until I am comfortable with Ubuntu I will maintain the NTFS file system

You welcome. I think you should make a separate post about the "The disk drive for media/Music_ is not ready yet or not present" include as much detail as possible. It sounds like if you solve this then you will solve your problem, I'm sorry i can't be of more help but I have no experience with this problem.

I too am running dual boot with the hope of giving up windows. My major problem is syncing my phone in Ubuntu. Good luck, hope someone has a solution for you.

---

### Post by xenton on 2010-10-16
Is the drive with your music on an internal drive?

Have a read of [this thread ]("http://ubuntuforums.org/showthread.php?t=1466555")
If your still having trouble make a new post and be sure to be clear about the fact that it is an intermittent problem. Good luck, and please let me know how you get on.

---

### Post by ubdead on 2011-03-23
BTW, the stage for applying Windows permissions should work except on XP Home. XP Home had some additional "features" that took away anything actually useful such as the ability to edit NTFS file permissions in the normal way. You can get round this by booting XP Home into safe mode (f8 immediately after Grub menu selection). 

**SuperFreak**  - this might be your problem where you got stuck on the Windows NTFS permissions stage.

---

### Post by Jose Catre-Vandis on 2011-03-24
I have not found the need to put my uid into fstab for XP or 7. My line to mount the entire  partition is:
```
UUID=05AAD3F55A0B9BDA                           /media/DATA     ntfs-3g defaults 0 0
```

and I have full read write permissions

---

### Post by Morbius1 on 2011-03-24
I'm not trying to make excuses but you need to understand the process that got him here: [http://ubuntuforums.org/showthread.php?t=1575426](http://ubuntuforums.org/showthread.php?t=1575426)

Although this HowTo shows you how to create a Samba Classic Share ( which is done by root and hence has access to everything ), he originally started out trying to make a Samba Usershare ( a.k.a. Nautilus-share). Usershare only allows you to create a samba share on something you own - that can be fixed but then it would allow all users to share anything. So he had to take possession of the partition.

Besides with a "uid=1000" he now is able to send something to the trash without getting a "cannot move file to trash" error :wink:

---

