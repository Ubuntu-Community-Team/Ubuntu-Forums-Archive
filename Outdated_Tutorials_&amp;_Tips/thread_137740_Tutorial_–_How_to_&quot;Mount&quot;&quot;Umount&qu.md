---
title: "Tutorial – How to &quot;Mount&quot;/&quot;Umount&quot; Partitions"
date: 2006-02-28
forum: Outdated Tutorials &amp; Tips
---

### Post by dvarsam on 2006-02-28
Hello all !!!

This is just New Tutorial Stuff coming up from ME !!!


_Tutorial – How to "Mount"/"Umount" Partitions in Ubuntu_:

_Story_:
Every now & then, we see people asking questions in this Forum, on how to access other Partitions, regardless of whether they are Windows Partitions or Linux Partitions or Other.

This Tutorial's main target is to teach you HOW to mount/unmount (create access/remove access), to any (Hard Drive) Partition you connect to your Ubuntu.

_Note_:
It is Required that you connect your (Hard Drive) Partition, before you Boot your Ubuntu, unless your (Hard Drive) Partition is connected to your Ubuntu through USB. 

So, here it goes:


_Part 1 – Mounting Partitions (auto mount mode)_:
The file named "fstab", is a file where ALL your Ubuntu's "mount" options are listed.
The "fstab" file is the automatic way to "mount" File Systems.
They are "mounted" at Log on & "unmounted" at Log off.
By default, the basic options (including the Ubuntu File System), will be found there.

To view the basic (default) contents of your  "fstab" file, launch a Terminal (from the Menu, select "Applications\Accesories\Terminal"), & type:

	sudo -i
	Type your <password>    ( < - To get Administration/root Privileges)
	cd /				       ( < - To move to the root directory)
	cd /etc			 ( < - To move to a subdirectory where the file "fstab" is)
	cat fstab		( < - To only view the basic default options of "fstab" file)

You should get this output:

# /etc/fstab: static file system information.

# <file system>	<mount point>	<type>	<options>		<dump>	<pass>
proc			/proc			proc	  defaults			          0	  0
/dev/sda1	   /			       ext3	defaults,errors=remount-ro  0	    1
/dev/hdd	    /media/cdrom0	 	  udf,iso9660 user,noauto	0	0
/dev/fd0	     /media/floppy0		    auto    rw,user,noauto	    0	    0


The last three lines in the above are ALL the basic (default) devices found on your Computer:

1. sda1: "s" = SATA Hard Drive, "a" = 1rst SATA Bus, "1" = 1rst Partition

2. hdd = the CD Rom (to access it, you must move to the "/media" subdirectory)

3. fd0 = the Floppy Drive (to access it, you must move to the "/media" subdirectory)


_As we said before_:
The "fstab" file is the auto way to "mount" FileSystems.
They are "mounted" at Log on & "unmounted" at Log off.

No other (Hard Drive) Partitions are "mounted" automatically when you Boot your Ubuntu PC.

So, if you want to add (or "mount") more (Hard Drive) Partitions in your Ubuntu PC, you MUST:

    1. Edit your "fstab" file & manually add a command that will result in an 
        automatic mounting of your added (Hard Drive) Partition every time you 
        startup your Ubuntu PC.

    OR:

    2. Select the Temporary method.
        That means, EVERY time you would like to mount added (Hard Drive) 
        Partitions, you will have to launch the Terminal (from the Menu, select 
        "Applications\Accesories\Terminal") & EVERY time manually type-in the correct 
        command that "mounts" your Partition.

       _Note_:
       To learn how you can manually mount added (Hard Drive) Partitions by using 
       the Terminal, move to Part 3 (section) of this Tutorial.


To Edit your "fstab" file & manually add a command that will result in an automatic mounting of your added (Hard Drive) Partition every time you startup your Ubuntu PC, do the following:

Launch a Terminal (from the Menu, select "Applications\Accesories\Terminal") & type:

1. sudo -i

2. Your Password

3. fdisk -l

    _Note_:
    In this stage, you MUST examine the output of the above command.
    Depending on the output you get, the command line that you are supposed to 
    type/insert inside your "fstab" file MUST relate to what you see (as output), in 
    this step (with the "fdisk -l").

    _Output Example_:

	root@house:/# fdisk -l

	Disk /dev/hdc: 40.0 GB, 40020664320 bytes
	255 heads, 63 sectors/track, 4865 cylinders
	Units = cylinders of 16065 * 512 = 8225280 bytes

	   Device Boot      Start         End      Blocks   Id  System
	/dev/hdc1   *           1        4865    39078081    7  HPFS/NTFS

	Disk /dev/sda: 82.3 GB, 82348277760 bytes
	255 heads, 63 sectors/track, 10011 cylinders
	Units = cylinders of 16065 * 512 = 8225280 bytes

	   Device Boot      Start         End      Blocks   Id  System
	/dev/sda1               1        2432    19535008+  83  Linux
	/dev/sda2            2433        6079    29294527+  83  Linux
	/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)
	/dev/sda5            6080       10011    31583758+   b  W95 FAT32

	Disk /dev/sdb: 120.0 GB, 120034123776 bytes
	255 heads, 63 sectors/track, 14593 cylinders
	Units = cylinders of 16065 * 512 = 8225280 bytes

	   Device Boot      Start         End      Blocks   Id  System
	/dev/sdb1               1       10416    83666488+   7  HPFS/NTFS
	/dev/sdb2           10417       14593    33551752+   f  W95 Ext'd (LBA)
	/dev/sdb5           10417       14593    33551721    b  W95 FAT32

	Disk /dev/sdd: 32 MB, 32768000 bytes
	5 heads, 63 sectors/track, 203 cylinders
	Units = cylinders of 315 * 512 = 161280 bytes

	   Device Boot      Start         End      Blocks   Id  System
	/dev/sdd1   *           1         202       31783+   4  FAT16 <32M
	

    In the above output example, notice that there are 4 Devices found:

    a. Disk /dev/hdc: 40.0 GB		( < - "h" = IDE Hard Drive, "c" = 3rd IDE Bus)

    b.  Disk /dev/sda: 82.3 GB		( < - "s" = SATA Hard Drive, "a" = 1rst SATA Bus)

    c.  Disk /dev/sdb: 120.0 GB	( < - "s" = SATA Hard Drive, "b" = 2nd SATA Bus)

    d.  Disk /dev/sdd: 32 MB		( < - This is too small to be a Hard Drive, it is a USB stick)


    Let us now take a closer look on the first, Disk "a" above:

	   Device Boot      Start         End      Blocks   Id  System
	/dev/hdc1   *           1        4865    39078081    7  HPFS/NTFS
 
    hdc1: "h" = IDE Hard Drive, "c" = 3rd IDE Bus, "1" = 1rst Partition

    Notice the "*" under the Boot title.
    This (Hard Drive) Partition is Bootable (i.e. it contains an Operating System) .
    And if you look at the NTFS under the System title, you can assume that there is 
    a Windows OS installed in that (Hard Drive) Partition.

    Let us now take a closer look on the second, Disk "b" above:

	   Device Boot      Start         End      Blocks   Id  System
	/dev/sda1               1        2432    19535008+  83  Linux
	/dev/sda2            2433        6079    29294527+  83  Linux
	/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)
	/dev/sda5            6080       10011    31583758+   b  W95 FAT32

    sda1: "s" = SATA Hard Drive, "a" = 1rst SATA Bus, "1" = 1rst Partition (a Linux EXT3 one)
    sda2: "s" = SATA Hard Drive, "a" = 1rst SATA Bus, "2" = 2nd Partition (a Linux EXT3 one)
    sda5: "s" = SATA Hard Drive, "a" = 1rst SATA Bus, "5" = 3rd Partition (a Windows FAT32 one)

    You will probably wonder why did I omit talking about "sda3"...
    If you notice "sda3" & "sda5" they have a common (title) Start & End Blocks.
    That basically tells you that the 2 rows are ONE & the SAME Partition.
    Do NOT ask me why Ubuntu does that, I do NOT know...
    But the (Hard Drive's) FAT32 Partition is the "sda5" (W95 FAT32) .
    Remember this (in case you run into again), in the near future.

    _Note_:
    You might also notice that under the Boot title, there is NO "*" on the "sda2" 
    line.
    Well, there should be, cause I have Booted (& am typing this right now), from 
    my Ubuntu PC.
    Why there is NO "*" on that line, I do NOT know either...

    I am NOT going to describe (in thorough) the third, Disk "c" above. But in a few 
    words it contains ONLY 2 Partitions ("sdb1" & "sdb5"). One of them is a 
    Windows NTFS & the other a Windows FAT32. Both of them contain NO 
    Operating System (just files – since there is NO "*" under the Boot title).

4. Now that we explained the above (Hard Drive) Partitions, in detail, we can now 
    go & edit our "fstab" file & manually add a command that will result in an 
    automatic mounting of our added (Hard Drive) Partitions every time you startup 
    your Ubuntu PC.

    To do this, perform the following:

    a. If your "Terminal" is still open (I never told you to close the window, did I?), 
        type:

	cd /			  ( < - To move to the root directory)
	cd /etc			( < - To move to a subdirectory where the file "fstab" is)
	cp fstab fstab_backup	( < - Backup your "fstab" file to "fstab_backup" in 
                                                      case you mess up with the Editing procedure 
                                                      which is coming  up shortly...) 
	nano fstab		( < - To only view the basic default options of "fstab" file)

	_Note_:
	If your "Terminal" were still open, you should NOT need to type the first two 
        commands, but I just put them, in case you have (mistakenly) changed 
        directory.

    b. Now you are inside the "nano" Editor.
        _Warning_:
        Be careful with what you type (or change), because typing the wrong stuff 
        could result in NOT being able to boot your Ubuntu PC...

    c. Use the arrow keys on your keyboard & go down to the last line of your 
        "fstab" file.

    d. Type the "Enter" key of your keyboard twice to create 2 new lines.

    e. This is the tricky part.
        You MUST type inside, the correct info (and I mean the info that applies to 
        YOUR Partition & NOT mine or this Tutorial's one).
        In OUR example, we would go & type the following:

	# 1. To see my NTFS Partition (on the SATA "Backup" Hard Drive), type:
	#    Note: You can ONLY Read Files in this Partition.

	/dev/sdb1       /mnt/ntfs_files  ntfs   nls=utf8,umask=0222  0  0


	# 2. To see my FAT32 Partition (on the SATA "Backup" Hard Drive), type:

	/dev/sdb5       /mnt/fat32_files vfat   iocharset=utf8,umask=000  0  0


	# 3. To see my NTFS Partition (on the IDE "WinOS" Hard Drive), type:
	#    Note: You can ONLY Read Files in this Partition.

	/dev/hdc1       /mnt/ntfs_os     ntfs   nls=utf8,umask=0222  0  0


       _Description_:
       Any line that starts with the "#" is a comment line & you can type-in any 
       comment you want.
       All the other lines are command lines.
       These command lines are the lines required to finally be able to auto "mount" 
       the Partitions you want every time you Boot your Ubuntu.

       Notice that the lines on mounting an NTFS (Hard Drive) Partition are different 
       than the lines on mounting a FAT32 (Hard Drive) Partition.

       Lets take a closer look on the first command line:

       /dev/sdb1       /mnt/ntfs_files  ntfs   nls=utf8,umask=0222  0  0

       "/dev/sdb1": "/dev" = will always be the same,
		            "/sdb1" = This comes from the "fdisk -l" output.

       _Note_:
       When I asked you previously to type "fdisk -l" in the Terminal & to take a look 
       at your output, I did it for a reason. That output, will tell you what you have to 
       type inside your "fstab" file (e.g. "/sdb1" in the above command line).

       "/mnt/ntfs_files": "/mnt" = will always be the same,
			        "/ntfs_files" = give any name you would like & it is going to be the name of the 
				folder you must visit, to access your Partition's contents.

       "ntfs" = represents the Format Type of your Partition you are trying to access. 
                    Again, the "fdisk -l" output will tell you what you have to type inside 
                    your "fstab" file (e.g. "ntfs" in the above command line).
	        _Note_:
	            If it was a FAT32 Format Type we were trying to access, we would type "vfat".
	            If it was an EXT3 Format Type we were trying to access we would type "ext3"

       "nls=utf8,umask=0222" = This part is ALWAYS used when you are 
                                                 dealing/mounting NTFS (Hard Drive) Partitions. And 
                                                  it is ALWAYS the same.
				                  The "umask=0222" is THE most important part. 
                                                  Basically it says that you can ONLY Read the 
                                                  contents NTFS Partition. You can NOT Write
                                                  anything or Execute anything from the NTFS 
                                                  Partition. Ubuntu will restrict ANY of your attempts 
                                                  to write into that Partition. That is restricted by the 
                                                  "222" number part.
				                  Unfortunately this is a Windows problem, NOT an 
                                                  Ubuntu one.
				                  Windows NTFS Format is "sealed" only for 
                                                  Windows OS use...
				                  There are ways to make it possible, to write to a 
                                                  Windows NTFS Partition, but they are NOT 100% 
                                                  safe & they might result in damaging your NTFS 
                                                  Partition. ... and you do NOT want to do that... do 
                                                  you?
				                  _Note_:
				                  This Tutorial's goal is NOT to teach you how to do 
                                                  that...
				                  In Ubuntu, when somebody wants to pass files 
                                                  from an EXT3 (Ubuntu) Partition, to an NTFS 
                                                  (Windows) Partition, his files have to (first) pass 
				                  from an intermediary FAT32 Partition. Ubuntu has 
                                                  NO problem in dealing with FAT32 Partitions. So, 
                                                  people save their files in a FAT32 Partition (from 
                                                  Ubuntu) & they (then) use Windows to access & 
                                                  get their files from the FAT32 Partition to their NTFS 
                                                  one.

       "  0  0" = will always be the same.


       Now, lets take a closer look on the second command line:

       /dev/sdb5       /mnt/fat32_files vfat   iocharset=utf8,umask=000  0  0

       "/dev/sdb5": "/dev" = will always be the same,
		    "/sdb5" = This comes from the "fdisk -l" output.

       _Note_:
       As I said before, when I asked you previously to type "fdisk -l" in the Terminal 
       & to take a look at your output, I did it for a reason. That output, will tell you 
       what you have to type inside your "fstab" file (e.g. "/sdb5" in the above 
       command line).

       "/mnt/fat32_files": "/mnt" = will always be the same,
			  "/fat32_files" = give any name you would like & it is going to be 
                                                   the name of the folder you must visit, to access 
                                                   your Partition's contents.

       "vfat" = represents the Format Type of your Partition you are trying to access. 
                     Again, the "fdisk -l" output will tell you what you have to type inside 
                     your "fstab" file (e.g. "vfat" in the above command line).
	         _Note_:
	             If it was an NTFS Format Type we were trying to access, we would 
                     type "ntfs".
	             If it was an EXT3 Format Type we were trying to access we would 
                      type "ext3"

       "iocharset=utf8,umask=000" = This part is ALWAYS used when you are 
                                                         dealing/mounting FAT32 (Hard Drive) 
                                                         Partitions. And it is ALWAYS the same.
				                         The "umask=000" is THE most important part. 
                                                         Basically it says that you can 
                                                         Read&Write&Execute the contents of your 
                                                         FAT32 Partition. You are given ALL available 
                                                         Permissions on the FAT32 Partition. That is 
                                                         permitted by the "000" number part.

       "  0  0" = will always be the same.


       I am NOT going to describe (in thorough) the third command line. But in a few 
       words it is an IDE (Hard Drive) Partition ("/hdc1") & the "/ntfs_os" is the folder 
       name I gave under which I can access the (Hard Drive's) NTFS Partition 
       contents (give it any name you would like). The rest should remain the same ( 
       that SAME part is ALWAYS used when you are dealing/mounting NTFS 
       Partitions). 
  
       Now that you can understand what we typed in our "fstab" file, to mount MY 
       (Hard Drive) Partitions, you MUST add/type inside YOUR "fstab" file, the 
       appropriate command lines, depending on what the output was printed in 
       YOUR  output file (the output you get by using the "fdisk -l" command in YOUR 
       Terminal).

       So, go & type-in the info that applies to YOUR Partition & NOT mine or this 
       Tutorial's one.

      When you're done Editing the "/etc/fstab" File, Save (Ctrl-X), Confirm (y) & Exit 
      (Enter). 

       Congratulations, you just finished Editing your "fstab" file (the tough part). 
       The rest is easy.

5. In the above example, we Edited our "fstab" file & typed-in 3 command lines 
    with 3 Partitions that we wanted to auto mount every time we boot our Ubuntu 
    PC.
    We have also indicated the folder names under which we would access the 
    contents of the Partitions we would like to have auto mounted (during every 
    boot):

    a. "/mnt/ntfs_files" = Folder name "ntfs_files" under the "/mnt" directory

    b. "/mnt/fat32_files" = Folder name "fat32_files" under the "/mnt" directory

    c. "/mnt/ntfs_os" = Folder name "ntfs_os" under the "/mnt" directory

    But the above Folder names do NOT exist !!!
    Therefore, we MUST create them.

    To do that, from your open Terminal (I hope you did NOT close it – I never told 
    you to do so...), type the following:

    cd /				( < - To move to the root directory)
    cd mnt		 	( < - To move to the subdirectory named "/mnt")
    (Alternatively you could type: "cd /mnt" – but sometimes this does NOT work) 
    mkdir ntfs_files		( < - To create a folder/directory named "ntfs_files")
    mkdir fat32_files		( < - To create a folder/directory named "fat32_files")
    mkdir ntfs_os		( < - To create a folder/directory named "ntfs_os")

6. In the beginning we mentioned the following:
     The "fstab" file is the automatic way to "mount" File Systems.
     They are "mounted" at Log on & "unmounted" at Log off.

     Since we have already Logged on our Ubuntu, we can NOT expect our (Hard 
     Drive) Partitions to have auto mounted.

     We MUST either:

    a. "mount" them manually, or

    b. Restart our Ubuntu computer.

    Since nobody likes restarting, inside your open Terminal, type:

    cd /				( < - To move to the root directory)
    mount -a			( < - To mount ALL the Partitions - "-a" = all) 

Congratulations, you have now Mounted your (Hard Drive) Partitions successfully.

_Remember_:
The next time you will reboot your Ubuntu Computer, all those typed-in (Hard Drives) Partitions stated inside your "fstab" file will me mounted automatically.
If, in any case, you decide to Remove one (Hard Drive) Partition & do NOT want it to automatically mount when you are Booting your Ubuntu, edit your "fstab" file & add a "#" right in front of your command line. That will turn that command line into a comment & that line will NOT be run while booting...


_Part 2 - Unmounting Partitions (auto mount mode)_: 
Now, if you want to Unmount a (Hard Drive) Partition:

Edit the "/etc/fstab" File, & either:

a.  Remove the command line that mounts your (Hard Drive) Partition.

OR:

b. Add a "#" right in front of the command line that mounts your (Hard Drive) 
    Partition.
    That will turn that command line into a comment & the line will NOT be run while 
    booting...

However, by Editing the "/etc/fstab" File, you do NOT really unmount your (Hard Drive) Partition, until you actually shutdown your Ubuntu PC.

If you would like to immediately unmount your (Hard Drive) Partition & do NOT want to wait until you shutdown your Ubuntu for this to be applied, you MUST do it through the Terminal window.
In the Terminal window, type the following: 
 
	sudo umount /mnt/ntfs_files		( < - To unmount the Partition named "ntfs_files")

_Note_:
Notice that the unmount command that you MUST type is: "umount" & NOT "unmount".
To immediately unmount a different Partition, in our example, replace the "ntfs_files" with "fat32_files" or  "ntfs_os"


_Part 3 – Mounting Partitions (manual/temporary mount mode)_:

Launch a Terminal & type:

1. sudo -i

2. Your Password

3. fdisk -l

    _Note_:
    In this stage, you MUST examine the output of the above command.
    Depending on the output you get, the command line that you are supposed to 
    type/insert inside your "Terminal" window MUST relate to what you see (as 
    output), in this step (with the "fdisk -l").

    If you do NOT know (or remember) how to do this, go back & read Part 1 (of this 
    Tutorial).

4. To temporary mount a Partition, type:

    a. In the case of an  NTFS (Hard Drive) Partition:

	cd /					( < - To move to the root directory)
	cd mnt				 	( < - To move to the subdirectory named "/mnt")
	(Alternatively you could type: "cd /mnt" – but sometimes this does NOT work) 
	mkdir ntfs_files		( < - To create a folder/directory named "ntfs_files")
	
	_Note_:
	If you have already created a folder/directory named "ntfs_files" in the past, 
        omit the above 3 steps.

	mount -t ntfs -o ro,umask=0222 /dev/sdb1 /mnt/ntfs_files

	_Note 1_:
	The additional options "-o ro" & "umask=0222" will leave it locked in Read 
        Only ("ro") mode & still grant everyone rights to it (for reading).
	This way, there is NO chance of accidentally writing to the NTFS drive (a bad 
        idea in Linux).
	So, basically ANY user can ONLY Read the NTFS Partition.
	As I explained earlier, you can NOT Write anything or Execute anything from 
        the NTFS 
	Partition. Ubuntu will restrict ANY of your attempts to write into that Partition. 
        That is restricted by the "222" number part.
	Unfortunately this is a Windows problem, NOT an Ubuntu one.
	Windows NTFS Format is "sealed" only for Windows OS use...
	There are ways, to make it possible, to write to a Windows NTFS Partition, 
        but they are NOT 100% safe & they might result in damaging your NTFS 
        Partition. ... and you do NOT want to do that... do you?
	_Note 2_:
	This Tutorial's goal is NOT to teach you how to do that...
	Again, in Ubuntu, when somebody wants to pass files from an EXT3 (Ubuntu) 
        Partition, to an NTFS (Windows) Partition, his files have to (first) pass from an 
        intermediary FAT32 Partition. 
	Ubuntu has NO problem in dealing with FAT32 Partitions. So, people save their 
        files in a FAT32 Partition & they (then) use Windows to access & get their files 
        from the FAT32 Partition to their NTFS one.

    b. In the case of an  FAT32 (Hard Drive) Partition:

	cd /					( < - To move to the root directory)
	cd mnt				 	( < - To move to the subdirectory named "/mnt")
	(Alternatively you could type: "cd /mnt" – but sometimes this does NOT work) 
	mkdir fat32_files	( < - To create a folder/directory named "fat32_files")

	_Note_:
	If you have already created a folder/directory named "fat32_files" in the past, 
        omit the above 3 steps.

	mount -t vfat /dev/sdb5 /mnt/fat32_files

    c. In the case of a CD Rom:

	mount -t iso9660 /dev/hdd /media/cdrom0

	_Note_:
	You do NOT need to create a folder/directory for accessing a CD-Rom drive.
	Ubuntu's default directory for accessing such devices, is the "/media" 
        directory.

    d. In the case of a (Windows Formatted) Floppy Disk:

	mount -t vfat /dev/fd0 /media/floppy0

	_Note 1_:
	To access a Linux Floppy, you would ONLY change "vfat" to "ext2".

	_Note 2_:
	You do NOT need to create a folder/directory for accessing a CD-Rom drive.
	Ubuntu's default directory for accessing such devices, is the "/media" 
        directory.

    e. In the case of a (Windows Formatted) USB Stick:

	mount -t vfat /dev/sdh1 /media/usbdisk

	_Note_:
	To access a Linux USB Stick, you would ONLY change "vfat" to "ext2".
	Ubuntu's default directory for accessing such devices, is the "/media" 
        directory.

_Note_:
According to the Ubuntu OS "rules":

a. All Hard Drive Partitions should be mounted under the "/mnt" directory.
b. All Media Drives (e.g. CD-ROM, Floppy Disk, USB Stick, etc.), should be mounted 
    under the "/media" directory.

Following the above "rule" is NOT obligatory, but it is the common approach.


_Part 4 – Unnounting Partitions (manual/temporary mount mode)_:

Launch a Terminal & type:

1. sudo -i

2. Your Password

3. To temporary unmount a Partition, type:

    a. In the case of an  NTFS (Hard Drive) Partition:

	umount /mnt/ntfs_files	( < - To unmount the Partition accessed from "ntfs_files" folder)

	or:
	
	umount /mnt/ntfs_os		( < - To unmount the Partition accessed from "ntfs_os" folder)

    b. In the case of an  FAT32 (Hard Drive) Partition:

	umount /mnt/fat32_files	( < - To unmount the Partition accessed from "fat32_files" folder)

    c.  In the case of a CD Rom:

	umount /media/cdrom0

    d. In the case of a Floppy Disk:

	umount /media/floppy0

    e. In the case of a USB Stick:

	umount /media/usbdisk

_Note_:
Notice that the unmount command that you MUST type is: "umount" & NOT "unmount".


That is all Folks !


P.S.1> I hope I have not made many bad grammar syntax (& repetitions), but I 
           have spent more than 6 hours (this time) to create this...


P.S.2> I would appreciate if somebody has something to Add that corrects me if I 
 	   have performed a mistake.

           PLEASE do NOT add comments like "thanks dude", or "that's how you do it" 
           because people that want to read a Tutorial, end up reading comments of 
           NO Learning value.	  
	   
           Thanks !!!

---

### Post by bayvista on 2009-01-28
HI,

Great Tutorial.

I believe that CIFS has replaced NTFS as the preferred filesystem for NTFS partitions. Also, I THINK that CIFS is quite safe for writing to NTFS partitions. Perhaps someone with more knowledge would like to comment.

---

