---
title: "Can't play media after copying from external usb-drive"
date: 2014-08-16
forum: New to Ubuntu
---

### Post by Joel_de_Bruijn on 2014-08-16
My daughter has a PC with Lubuntu 14.04 on it. I have a USB drive with media (dvd, mp4, mkv, mp3 etc). It's a copy I made before switching from WinXP to Lubuntu. Now I want to copy this media to the PC so she can use her media. Tried the following:
[LIST]
[*]I logged in, created a folder for general storage and copied a DVD wit PCManFM. I can play it with VLC and Gnome MPlayer. She can't. I gave everybody all rights, she still can't play them. ("Permissons denied") 
[*]I logged in, created a folder for storage in her Home folder and copied a DVD. I can play it with VLC and Gnome MPlayer. She can't. I gave everybody all rights, she still can't play them. ("Permissons denied") 
[*]She logs in, Lubuntu mounts the drive for her, she copies the media to her home folder, open MPlayer ... error: "Permissons denied" 
[/LIST]

So I ended up logging in myself, just to get her to watch a Disney video. I know, not a very well work around ...

Thanks for the help!

Discalimer: 
[LIST]
[*]This is my very first post here. I grew up with windows, but switched from XP to Lubuntu. My use-case: My wife and kids use PC's, I support and do maintenance. So as a Windows admin I used to do upgrades/updates/anti-virus/backup/restore en provide local network storage. I want to do the same with Linux/Ubuntu. I don't want to throw out old hardware just because it's old, so after some browsing around I choose Lubuntu. I'm eager to learn, but GUI is in my DNA I guess .... 
[*]I don't know this belongs in a Lubuntu forum, a newbie forum, a PCManFM forum etc. So please switch if it is the wrong place here. 
[/LIST]

---

### Post by mikewhatever on 2014-08-16
You should probably show us one or two files' permissions, also, expand a bit on "I gave everybody all rights". It obviously didn't quite work, so what exactly did you do?

---

### Post by Sanctimonious_Ape on 2014-08-16
Relatively new to Linux myself, come from a similar background, and had a  few years of SCO UNIX experience that ended about ten years ago.  See  if I can at least point you in the right direction.

It's pretty  obviously an ownership and permissions thing.  You need to look at the  owner, group, and permissions of the files and probably the directories  they are in as well.  You should be able to configure PCmanFM to show  that info or you can go to that directory in a terminal and enter "ls  -l" to see the details.  By default, files and directories are owned and  usable only by those that created them. You need to modify the  properties to allow others read access.  The directories themselves may  need execute access (been such a long time since I had to deal with this  stuff I don't recall what's Windows vs. Linux/UNIX).  You can change  them in PCmanFM by viewing their properties, or you can use the commands  'chown', 'chgrp', and 'chmod' - you should read up on their man pages  (issue the command 'man chmod' in the terminal, for example) to ensure you've got a full understanding of what you're doing.

EDIT: I see you've got someone else who probably has more recent experience with permissions issues than I, so I'll butt out now and just watch.  Take it away, mikewhatever.

---

### Post by bizhat on 2014-08-16
Can other user can see the file ?

If yes, run 

```

sudo chmod 777 FILE_NAME

```

FILE_NAME can be relative or absolute path.

If you have multiple files, put it in a folder, then set permission for that folder like

```

sudo chmod -R 777 /path/to/folder

```

I only have one user, so i never faced the need to share files with other users. Even if i have, with my current setup have some NTFS disks, that won't have any permissions. So any user can access these disks. May be adding all users to same group will help.

---

### Post by ajgreeny on 2014-08-16
Just a thought; depending on where the files came from, could this be a DRM problem?

---

### Post by Rob Sayer on 2014-08-16
> **ajgreeny said:**
> Just a thought; depending on where the files came from, could this be a DRM problem?

That's what I was thinking ... even in ubuntu, if you install vlc the first time you run it it asks you if you want DRM enabled.  The default is yes, and it'd be pretty easy to just click through that without changing it.  Don't know if gnome mplayer does that though.

---

### Post by Joel_de_Bruijn on 2014-08-16
OK! Made some screenshots. 

[ATTACH=CONFIG]255526[/ATTACH]
So the folder "Video" shows my daughter has permissions.

[ATTACH=CONFIG]255525[/ATTACH]

The folder "Nanny McPhee", which she copied herself, shows my name as owner (grayed out).
[ATTACH=CONFIG]255524[/ATTACH]
The errors in VLC.

---

### Post by Joel_de_Bruijn on 2014-08-16
> **bizhat said:**
> Can other user can see the file ?

If yes, run 

```

sudo chmod 777 FILE_NAME

```

FILE_NAME can be relative or absolute path.

If you have multiple files, put it in a folder, then set permission for that folder like

```

sudo chmod -R 777 /path/to/folder

```

I only have one user, so i never faced the need to share files with other users. Even if i have, with my current setup have some NTFS disks, that won't have any permissions. So any user can access these disks. May be adding all users to same group will help.

Yes, she sees them all. Do I have to do this every time she copies something, or just now to solve this. I 'just' want a folder in which we (we both) can dump all media, play it and delete it eventually.

---

### Post by Joel_de_Bruijn on 2014-08-16
I also read this thread: 
[http://askubuntu.com/questions/52584/shared-folders-for-all-users](http://askubuntu.com/questions/52584/shared-folders-for-all-users)
but it is very intimidating for me. It looks the same problem,but very different solutions.

---

### Post by Joel_de_Bruijn on 2014-08-16
So ... if I create a folder somewhere in her home folder, see can't use them?
And if she creates a new folder I can't delete them?

---

### Post by Joel_de_Bruijn on 2014-08-16
Find this one also:
[http://ubuntuforums.org/showthread.php?t=2209347](http://ubuntuforums.org/showthread.php?t=2209347)

I used to do "gksudo pcmanfm" to allow myself to change ownership to another group, with pcmanfm.
A group "users" with me in it.

---

### Post by JeQhdMD on 2014-08-16
Joel:

Yes, you can delete files created by another user (quite easily) if you are the sudo'er.

Why don't you show her how to:

>  create the mp3's (or better yet, the ogg-vorbis music files)

>  create a folder, and have her do the copy/paste (from your USB-Flash stick)

If you use basic terminal commands as shown earlier in this thread (or "rm" command . . but read about it first), you can delete anything, even if created by Saint Nickolaus . . . . 

>  Also, be sure SHE is the first one to login to the PC so IF the files are in a usb-flash stick that's inserted before start-up, she will be the device owner.  (edit-note:  this last info is how Ubuntu manages usb-flash devices.   Perhaps Lubuntu does it different.   And lastly - another option is to install the "Thunar" file manager, and then google the method to add "open as root" to it (so you don't need to use the Terminal).

---

### Post by Joel_de_Bruijn on 2014-08-16
> **JeQhdMD said:**
> Joel:

Yes, you can delete files created by another user (quite easily) if you are the sudo'er.

Why don't you show her how to:

>  create the mp3's (or better yet, the ogg-vorbis music files)

>  create a folder, and have her do the copy/paste (from your USB-Flash stick)

If you use basic terminal commands as shown earlier in this thread (or "rm" command . . but read about it first), you can delete anything, even if created by Saint Nickolaus . . . . 

>  Also, be sure SHE is the first one to login to the PC so IF the files are in a usb-flash stick that's inserted before start-up, she will be the device owner.  (edit-note:  this last info is how Ubuntu manages usb-flash devices.   Perhaps Lubuntu does it different.   And lastly - another option is to install the "Thunar" file manager, and then google the method to add "open as root" to it (so you don't need to use the Terminal).

Yes! Yes! Yes! 
- Now I know how to change group permissions on a folder, I can create every folder structure I want with appropiate rights. I'm still hesitating to do it with CLI, but with PCManFM as root it can be done. 
- Just showed my daughter how to copy/paste and to navigate between folders. She picked it up right away.
- I don't remember when exactly but switching users after mounting definitely happend, so I'll remember your last remark!

Thanks to you all, for making this first experience a good one.

---

