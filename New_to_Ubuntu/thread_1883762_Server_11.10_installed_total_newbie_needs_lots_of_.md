---
title: "Server 11.10 installed total newbie needs lots of help now please"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by Nolanuk on 2011-11-19
I've just installed Ubuntu server 11.10 for the first time, but more importantly I'm totally new to Ubuntu and I need help to understand how to do what I want to do and get the server setup properly as at the moment I'm fumbling around.
I'll be as detailed as I can be as I'm not sure on the relevance.
Hardware:-
Hp proliant micro server with 250gb hdd (pre installed)
2 x 2tb Samsung drives (added)
Software:-
Ubuntu server 11.10 (installed on the 250gb drive from USB)
LAMP
Desktop GUI gnome (installed after first install)

And now I am stuck.

This is what I want to use the server for:-
Local and remote access of files including streaming for media files and saving of documents.
Install of Transmission
Installations for testing Joomla and vbulletin (that's where lamp comes in which I installed in the original installation setup)
Web GUI would be perfect too

The questions:-
Now I've installed a GUI how do I get to use the command prompt?
How do I use the 2tb drives in raid? I did this in freenas previously but can't find the options in the desktop of Ubuntu. The drives are seen but the system is just looking at the 250gb drive that the OS is installed on.
Where can I find info on installing Joomla and vbulletin on Ubuntu to be accessed locally and remotely?
How should I installed program's like transmission? Through the GUI app or through the command prompt? I want this to be remote also.

Sorry for the potential poor questions but I've looked around and found only snippets of what I think I'm looking for, but that maybe because I may not be asking the right questions.

Any help would be hugely appreciated.

---

### Post by collisionystm on 2011-11-19
Is this a personal server or some kind of business tool?
Just wondering because Zentyal is freakin awesome.

---

### Post by Nolanuk on 2011-11-20
It's a personal server, but I'm open to ideas.

---

### Post by The Cog on 2011-11-20
> Now I've installed a GUI how do I get to use the command prompt?
Ctrl-Alt-F1 through Ctrl-Alt-F6 will get you six convention console logins, with Ctrl-Alt-F7 taking you back to the GUI. But assuming the GUI is working, menu Accesories->Terminal will get you a terminal that is rather more user friendly, with scroll bars, copy/paste support.
> How do I use the 2tb drives in raid? I did this in freenas previously but can't find the options in the desktop of Ubuntu. The drives are seen but the system is just looking at the 250gb drive that the OS is installed on.I'm not up on configuring RAID. I beleve that LVM (logical volume manager) is the conventional way to go, of you care to google for that. 

An interesting new file system is BTRFS which can be specified to do its own raid arrangement. It also allows taking of snapshots of the filesystem which can be useful for rollbacks etc. It's officially experimental, but seems quite solid. You need to install btrfs-tools, and read up on mkfs.btrfs for formatting the drives.
> How should I installed program's like transmission? Through the GUI app or through the command prompt? I want this to be remote also.
I would suggest that you install synaptic, which hs a GUI package manager. **sudo apt-get install synaptic**. After install, it's in the menus under System->Synaptic. This is probably the easiest way to search and learn about packages. It can be driven remotely by tunneling X over SSH, for instance like this (your typing in bold):
> me@laptop$ **ssh -X administrator@server**
Enter password:
administrator@server$ **gksu synaptic**
but the nice thing is that synaptic still uses apt-get behind the scenes so there's no conflict if you sometiomes use a command-line **sudo apt-get install xsnow** type install instead.

---

### Post by Gone fishing on 2011-11-20
I've always set up the raid in Linux on the initial install rather than after, however, this looks about right [http://linuxconfig.org/Linux_Software_Raid_1_Setup](http://linuxconfig.org/Linux_Software_Raid_1_Setup)

Might as well plug webmin as a handy server admin tool [http://www.webmin.com/](http://www.webmin.com/)

---

