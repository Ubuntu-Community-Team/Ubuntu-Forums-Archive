---
title: "storage device manager problem"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by gusteman on 2008-08-20
Hi there, I wanted to mount a second HD as slave. Connections are OK but when I want to mount it through Storage device manager (pysmd) I get the following problem:
when I click on the Assistant I find that the box [COLOR="Red"]"Mount file system in read-only mode"[/COLOR] is checked. I un-check it and click OK. When I re-open the Assistant the boxed is [COLOR="Red"]automatically checked again[/COLOR]. Even when I change the [COLOR="Red"]"Owner user of the file system uid="[/COLOR] from [COLOR="Blue"]root[/COLOR] to [COLOR="Blue"]gusteman[/COLOR] (my own username) the result is the same.
When entering the secondary HD I find that I can only read but not write. So I presume that my un-checking the box did not have any effect at all. Anyone has any suggestions on how to resolve this problem? I'd like to use this second HD as slave in order to update my storage capacity. Thanks in advance.

---

### Post by hermes0710 on 2008-08-20
I don't know if this will fix the problem but uid should refer to a code (normally 1000) instead of the user name (gusteman).

---

### Post by 4Orbs on 2008-08-20
I also use pysdm. In the Assistant, you can change the umask value for file and directory permissions in octal to 000. This gives read and write permissions to all user accounts on your computer. You may also need to change the mount point folder permissions (as root or owner) to allow "other" read and write permissions. Of course, these settings leave the hdd wide open which may not be your desired results.

---

### Post by falcon61102 on 2008-08-20
Your problem may also be that since you do not have write permissions to access that drive, you cannot change it's permissions values.  To do this you can use:
```
sudo chmod /device from to
```

For /device you will need that particular drive and then for from/to use the appropriate number codes.  I believe its 744 for root and 1000 or 000 for all access, but don't quote me on that one, it's been a while.

---

### Post by gusteman on 2008-08-20
Thanks for the hints but neither of them seems to do the job (unless I'm missing something here). Anyway, I opened pysdm from the commander line using sudo pysdm (instead of entering through System/Management) and tried to make the necessary changes there. The result was the following (whereas /dev/hdb1 is the second HD according to sudo fdisk -l):


[COLOR="Blue"]/dev/hdb1   *           1        9963    80027766    7  HPFS/NTFS
gusteman@gusteman-desktop:~$ sudo pysdm
Warning: Unknown option: rw
Warning: nouser is not suitable for user
Warning: Unknown option: async
Warning: nls=iso8859-1 can be not suitable for nls
Warning: umask=000 can be not suitable for umask
Warning: nls=iso8859-1 can be not suitable for nls
Warning: umask=000 can be not suitable for umask
Warning: Unknown option: rw
Warning: nouser is not suitable for user
Warning: Unknown option: async
Warning: nls=iso8859-1 can be not suitable for nls
Warning: umask=000 can be not suitable for umask
Warning: nls=iso8859-1 can be not suitable for nls
Warning: umask=000 can be not suitable for umask
Warning: Unknown option: rw
Warning: nouser is not suitable for user
Warning: Unknown option: async
Warning: nls=iso8859-1 can be not suitable for nls
Warning: umask=000 can be not suitable for umask
Warning: nls=iso8859-1 can be not suitable for nls
Warning: umask=000 can be not suitable for umask
gusteman@gusteman-desktop:~$ [/COLOR]

I'm trying real hard to try and understand what I am doing wrong but as you will have noticed I'm a complete rookie in the usage of the command line. To be quite honest most of the commands are some kind of abbreviations and look a bit like Chinese characters to me.
Anyway I am trying again to find a solution. If in the mean time someone could explane me how to solve my problems I'd be quite thankfull. Regards, Gusteman

---

### Post by 4Orbs on 2008-08-20
These are the steps I take to mount my second HDD and give read write permissions to all users on my computer. First, I would change owner back to root (using pysdm gui rather than command line).

1. Create a new folder in /media by using the command gksudo nautilus, which opens the file manager as root user, then navigate via Nautilus file manager to the /media folder and create a new folder inside named whatever you wish. Then right click on the new folder and select Properties and then Permissions tab and change permissions for "Others" to read and write via the drop down menu. Close nautilus.

2. Open pysdm gui and select the slave hdd from the left column (sdb). Now specify its mount point as the new folder you created inside the  /media folder. You can do this by using the button on pysdm to navigate to the new folder. The mount point will then be automatically assigned.

3. Configure the folder (mount point) using pysdm Assistant. I have only two boxes checked, Mount at Bootup, and umask file and directory permissions 000. Click the Apply button but not the mount button as the mounting will occur upon boot-up.

There is no need to use the command line except to open Nautilus as root user for the first step.

Reboot. You should now be able to open your new folder (/media/newfolder) and do your normal folder and file creations inside.

---

### Post by gusteman on 2008-08-20
@ 4Orbs
[COLOR="Black"][COLOR="Blue"]Thanks for the hints you gave me. Finally someone who explains in plain English the steps to take to solve a problem. Quite a relief.
Nevertheless I'm sorry to have to inform you that the results are not quite what you and I hoped for.
Before anything else I must say that I received this HD from my brother-in-law who used it in his PC before mounting a 180Gb HD. He had Win XP on it alongside Ubuntu. These programs and folders are still on the drive but leave 43 Gb free space which is more than I need, so I haven't yet formatted it. Maybe one of the files or folders on that drive is causing the problem so that I should format it before continuing. Anyway, here is what I did untill now:[/COLOR]
[COLOR="Black"]I worked out every step according to your instructions, including the re-boot and even found the new folder on the desktop.
When I opened it and tried to move a file from one folder to another one this is what happened:
I could copy the file but wasn't able to paste it.
So I opened the file-tab where I noticed what I can or cannot:[/COLOR]

[COLOR="Blue"]CAN:
open new window
connect to server
disconnect volume
close all windows
close folder[/COLOR]
[/COLOR][COLOR="Red"]CANNOT:
make new folder
make new file
open new window
enter properties
empty waste-bin[/COLOR]

So I am still stuck with the same problem. If you have any idea on how to solve this I would be much obliged. If not, it was quite pleasant to encounter a helpfull human being. Thank you very much :)

---

### Post by 4Orbs on 2008-08-20
Thanks for the nice words, gusteman. The whole Linux thing seems to foster a spirit of sharing and helpfulness that I have not seen anywhere else to such an extent.

Just a guess, but I suspect the existing files on your 2nd HDD are imposing old permissions from the Wimdows install, and probably there is also the remaining Windows master boot record on that drive. I believe those could certainly interfere in creating new folders and files. If it were mine, I would reformat the drive. Then open pysdm and click apply again for the drive. It might be a good idea to wait for some other opinions before reformatting, though. My advice may not be correct in this case.:)

---

### Post by 4Orbs on 2008-08-20
I just realized that you said your bro-in-law had a dual boot setup with Win and Ubu. If you are mounting the sdb partition of the drive, then you're possibly mounting the Windows System Recovery portion. I doubt that since you are able to copy files. You may have partitions labeled sdb1 and maybe sdb2. If you mount either of those, rather than the big kahuna, possibly the permissions can be affected by pysdm. Another possibility is that you could boot directly into the second HDD's grub list by changing your BIOS setting to boot from second disc first. In which case, if you know the password you could go into Windows (bro) and Ubuntu (bro) and change permissions from within. I haven't done this sort of thing myself, maybe one of the guru's will drop by with a definitive answer.

Since there are 43GB of empty space, you could easily use the partition tool in your Ubuntu install to shrink the existing partitions of the second HDD and create a new partition from the new unallocated space. Then mount that new partition for storage. It will show up as sdb3, most likely, and your assigned permissions should reign. Unmount the sdb partition before resizing.

---

### Post by gusteman on 2008-08-21
@ 4Orbs
Hi there,
after a good night sleep (here in good ol' Europe we have another time-zone as you know) I read your posts. Indeed the Linux principle creates bonds allover the world. A world that becomes smaller day after day. Now people only have to get to the point where they stop fighting with each other and this world will be a better place. But this is a matter that really ought to be discussed in another forum, so lets just stick to business right now.
Your proposal to simply format the new HD seems also to me the best way to get rid of the problem. Nevertheless I'm willing to try the repartitioning first just to see how it works out. Whatever the outcome I will post in this thread whether any of those actions was successful or not. Thanks again for spending your time helping out. Greetings from Belgium, Gusteman :guitar:

---

### Post by gusteman on 2008-12-07
Approaching the year 2009 maybe it is time give the final (temporary) answer to the above mentioned problem: well, as a matter of fact, there still hasn't been found a solution, except this one: I installed the new HD, Formatted it, started up Feisty Fawn from the install-CD and then updated to Gutsy, which is quite satisfying untill now. I hope to make the jump to Hardy once I am confident enough that most of the bugs have been eliminated. Greetings to all you community members, a Merry Christmass and a Happy 2009

---

### Post by ben2talk on 2009-01-01
Storage Device Manager appears to be rather unintuitive and has problems not apparent when using it - the first problem is one which I usually expect to get with Windows...

It lacks clarity - running as root, it needs clear controls (radio buttons perhaps) to select 'user mount/root mount/owner mount' etc - because I often find that if I used this software, I am not priviledged to unmount or do other things with partitions which previously behaved perfectly (albeit without automounting themselves).

Automounting should be an option selectable from Nautilus when right-clicking on a drive in 'Computer' view!

---

### Post by gusteman on 2009-01-02
@ ben2talk:
You said:
[B]Automounting should be an option selectable from Nautilus when right-clicking on a drive in 'Computer' view!
[/B]I totally agree with that. Maybe you should launch this idea on another forum. It might be hard to convince some of the "die-hards" but I get the feeling that the community is experiencing that little by little the number of users that are interested in "using" OS's rather than "developing" them is increasing day by day. Therefore it might be wise to adapt some features, not to make them more "Windows"-like but to make them more accessible to a world of users who are in fact quite afraid to alter basic parts of an OS.
I wish you the best of luck and a very happy 2009.
Greetings, Gusteman

---

### Post by PlainShane on 2009-01-25
I would love to see an answer to this also. Storage Device Manager (psydm) lets me auto-mount a secondary slave as well but when I uncheck "Read-Only Mode" in the assistant it checks it self back on. I need to write to the disk! Is there another way to auto-mount a drive and give everyone or atleast myself full permission?

---

