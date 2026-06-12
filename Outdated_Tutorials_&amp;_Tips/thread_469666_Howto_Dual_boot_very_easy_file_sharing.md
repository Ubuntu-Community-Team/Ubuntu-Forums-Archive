---
title: "Howto: Dual boot very easy file sharing"
date: 2007-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2007-06-10
Hi,
    here is a very easy and quick way to share files between ubuntu and XP on a dual boot PC. The howto is for Feisty, but should work on other versions as well. This is a simplified method taken from many other more complex howto's with recognition to those publishers.

  	 	 	 	 	 	 	 	  [COLOR=#000000][SIZE=3]_**Howto Feisty Very easily share files on dual boot**_[/SIZE][/COLOR]
 

 Most Windows Partions nowadays are in NTFS format and Linux partions in EXT3. This means that natively they cannot read or write properly and safely to each other. On a dual boot PC the solution is easy and just requires a usefull application to be installed on each installation that will solve the problem. These applications are now fully stable and you do not need to use a seperate fat32 partition for sharing  any more as was prescribed in the past and which is not very efficient.
 

 [LIST=1]
[*][COLOR=#000000][SIZE=3]_**Ubuntu 	or Kubuntu to access files in Windows XP**_[/SIZE][/COLOR][COLOR=#000000][SIZE=3]
Ensure 	that universe repositories are enabled.[/SIZE][/COLOR]
[/LIST] [COLOR=#000000][SIZE=3]Use Adept or Synaptic to install ntfs-config, which will then also download and install all required dependancies.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]You will find a new menu entry that is called NTFS Configuration Tool. Just run it if you are using Ubuntu, but edit it first, before running it in Kubuntu, by right clicking on it and changing the line gksu ntfs-config to kdesu ntfs-config before running it.
This will then automatically configure the application and you will be asked for a name of the mountpoint in Ubuntu, give anything i.e. WinXP. 
Now you should be able to see this WinXP drive together with your Ubuntu drives and use it.

[/SIZE][/COLOR]

 [LIST=1]
[*][COLOR=#000000][SIZE=3]_**Win 	XP to access files in Ubuntu or Kubuntu**_[/SIZE][/COLOR][COLOR=#000000][SIZE=3]
Go 	to [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=3]http://www.fs-driver.org/[/SIZE]]("http://www.fs-driver.org/")_[/COLOR][COLOR=#000000][SIZE=3] 	
Download the application Ext2lFS_1_10c.exe or latest version and 	install on your XP.
You will be shown a graphic display of your 	hard drives partitions and be able to select a drive name for the 	linux drive to be mapped to. You can use any one but suggest you use 	L  (for Linux!) and only map to Ext3 and leave the swap 	unmapped.
You will now find a Drive L that is your Linux drive 	and you will be able to read and write to it in XP.

[/SIZE][/COLOR]
	
[/LIST] Obviously you need to be careful and only really access the files and folders that are used for document, data etc. that the user keeps and not access the system files or carefully do this in case of messing up your installation.

---

### Post by sambehera on 2007-07-04
thanks! this worked really well ... very easy to understand and useful howto!

thanks a lot matchless... and yes ... kubuntu is amazing...

---

### Post by tutua on 2007-07-04
cheers :)

---

### Post by Lucho77 on 2007-11-26
Hey Matchless, Does this replace the file sharing stuff like 'samba' or 'nfs' that some of us already have ??
Thank you for this usefull thread.
Lucho77

---

### Post by Matchless on 2007-11-28
This is only for dual boot PC, to allow linux to see windows and vice versa. Samba and NFS should still be used between separate machines.

---

### Post by treesurf on 2007-11-29
Has anyone verified that this will work with Gutsy and Vista?

---

### Post by chadeldridge on 2008-02-28
The mail sharing is working fine for me, but I am missing my custom configurations from my windows install that are located in the userchrome.css.  They still work in windows, but not in linux.

---

### Post by Jose Catre-Vandis on 2008-02-28
> **treesurf said:**
> Has anyone verified that this will work with Gutsy and Vista?


Yes it does. You have to fight a bit with Ext2lFS_1_10c.exe to get it to install under Vista (e.g. compatibility) but it does work. Been using it since gutsy came out. Seamless.

---

### Post by regbsn on 2008-02-28
Let me see if I understand...

Install these two programs. Have a NTFS partition with XP and an ext3 partition with Ubuntu.

1. Do I need a separate NTFS partition for shared files or will XP access files off Linux partition and Linux access files from XP partition? If not, do I make a third partition for shared files and what format should it be in (NTFS, ext2 or ext3)?

2. Can I share a swap partition? If so, what file format? How would I tell XP and Ubuntu to use it?

3. Would I put shared application, to be run with Wine on Ubuntu, on the third partition?

---

### Post by treesurf on 2008-02-29
To answer your first question, the whole point of this is so that you do not need to make a third partition for shared files.  The windows and linux partitions can access each other.

I got NTFS working very easily on my Linux partition and then decided not to bother with the Vista partition because I don't use it much anyways.

---

### Post by regbsn on 2008-03-03
What?

So I have a XP partition, download Ext2lFS_1_10c.exe and install it.
have a ext3 partition with Ubuntu 7.10 (comes with ntfs-3g already).
Have a swap partition and a "' home" partition.

Windows can read/write from both ext3 partitions and Ubuntu will read/write to XP partition.

If this is correct, then I could read data from all but swap partitions?..:confused:

---

### Post by regbsn on 2008-03-03
Bump...sort of.

Will this work:
XP Home with Ext2lFS_1_10c.exe installed
"/ home"
"/" with Ubuntu 7.10
Linux swap

Linux can read/write to XP home
 -and-
XP can read/write to "/ home" and "/"
is this correct?

Otherwise I am going to have to look into Primary and "extended-logical" partitions...which BTW I am still confused about.

---

### Post by regbsn on 2008-03-29
*Bump*
:)

---

### Post by Jerry41 on 2008-05-21
So after following all this, I give it a try & find out (by losing a few e-mails) that Thunderbird for LINUX will not accept a profile directory with blanks in the filename (like "Documents and settings/  .  .  ."

It downloads just fine (and deletes the files from the server as it should), it just can't find the files for later use. 

A fairly minor omission since that is only the default for the Windows installation.

I'll not let it bother me. I am, overall, very happy with UBUNTU, there are just a few items here & there that fail to give a heads up to those of us who have been with Billy Gates since he was skipping English classes.

---

### Post by naggis on 2008-05-26
It looks as though Hardy comes with this facility installed by default. Simple file sharing has been set up so that I can see files on my xp desktop from the ubuntu setup on the laptop. The laptop is dual booted with xp and its files are available to read and write from ubuntu.
Can I just add my agreement that ubuntu is just great - all tasks seem so much easier than the equivalent in xp. And as for Vista - well you have to almost start all over, it seems to be just change for the sake of it. Is the security better than xp? You still need to install antivirus etc.

---

### Post by Jerry41 on 2008-05-28
Very Interesting - maybe someone will correct me if I'm wrong, but it appears to me that since I upgraded rather than doing a clean install, support for NTFS was NOT installed. Once I realized that and corrected the omission, my dual boot Thunderbird installation began to work like a champ.

Thanks to all you folks who described what SHOULD happen and how it SHOULD work so I could see what was wrong.

---

### Post by joy12 on 2011-07-29
> **Matchless said:**
> Hi,
    here is a very easy and quick way to share files between ubuntu and XP on a dual boot PC. The howto is for Feisty, but should work on other versions as well. This is a simplified method taken from many other more complex howto's with recognition to those publishers.

                                           [COLOR=#000000][SIZE=3]_**Howto Feisty Very easily share files on dual boot**_[/SIZE][/COLOR]
 

 Most Windows Partions nowadays are in NTFS format and Linux partions in EXT3. This means that natively they cannot read or write properly and safely to each other. On a dual boot PC the solution is easy and just requires a usefull application to be installed on each installation that will solve the problem. These applications are now fully stable and you do not need to use a seperate fat32 partition for sharing  any more as was prescribed in the past and which is not very efficient.
 

[LIST=1]
[*][COLOR=#000000][SIZE=3]_**Ubuntu     or Kubuntu to access files in Windows XP**_[/SIZE][/COLOR][COLOR=#000000][SIZE=3]
Ensure     that universe repositories are enabled.[/SIZE][/COLOR]
[/LIST]
[COLOR=#000000][SIZE=3]Use Adept or Synaptic to install ntfs-config, which will then also download and install all required dependancies.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]You will find a new menu entry that is called NTFS Configuration Tool. Just run it if you are using Ubuntu, but edit it first, before running it in Kubuntu, by right clicking on it and changing the line gksu ntfs-config to kdesu ntfs-config before running it.
This will then automatically configure the application and you will be asked for a name of the mountpoint in Ubuntu, give anything i.e. WinXP. 
Now you should be able to see this WinXP drive together with your Ubuntu drives and use it.

[/SIZE][/COLOR]

[LIST=1]
[*][COLOR=#000000][SIZE=3]_**Win     XP to access files in Ubuntu or Kubuntu**_[/SIZE][/COLOR][COLOR=#000000][SIZE=3]
Go     to [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=3]http://www.fs-driver.org/[/SIZE]]("http://www.fs-driver.org/")_[/COLOR][COLOR=#000000][SIZE=3]     
Download the application Ext2lFS_1_10c.exe or latest version and     install on your XP.
You will be shown a graphic display of your     hard drives partitions and be able to select a drive name for the     linux drive to be mapped to. You can use any one but suggest you use     L  (for Linux!) and only map to Ext3 and leave the swap     unmapped.
You will now find a Drive L that is your Linux drive     and you will be able to read and write to it in XP.

[/SIZE][/COLOR]
[/LIST]
Obviously you need to be careful and only really access the files and folders that are used for document, data etc. that the user keeps and not access the system files or carefully do this in case of messing up your installation.

I am running Windows 7 and installed Ubuntu 11.04 on the same laptop and I am running it but I have tried installing the ntfs configuration tool, I try to open it but it asks for password and does nothing :(

I want to be able to use all the files that I use on Windows 7 please help me, I have been trying so hard nothing seems to work

---

