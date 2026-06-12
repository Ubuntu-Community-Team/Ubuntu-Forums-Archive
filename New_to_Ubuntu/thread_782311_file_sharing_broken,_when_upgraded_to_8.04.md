---
title: "file sharing broken, when upgraded to 8.04"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by vodka_tonic on 2008-05-04
i had file sharing working through samba and nautilus in my older version, i.e. i saw the shares that i had on my windows computer.  this is all within my home intranet.
i upgraded to hardy heron and it does not work anymore.  it sees the computer, but does not see the shares.  i checked through another windows computer and it sees the shares.
i went into synaptic and samba and all related clients/services are installed.
i shared a folder in nautilus and windows was able to see it.

any help on what next to do to diagnose / solve this problem.  many thanks.

---

### Post by SiN_AmoR on 2008-05-05
I'm having the same problem !!

waiting for a solution..

---

### Post by quirks on 2008-05-05
Nautilus and network shares have always been a hassle ... I don't know if I can help you fix this, but I'll try.

Have you checked if you can list the shares using the smbclient?
If you do not use passwords:
```
smbclient -N -L *ip_of_windows_machine*
```
If you use passwords:
```
smbclient -L *ip_of_windows_machine* -U *user_of_windows_machine*
```
If this works, then Nautilus has a problem. If this doesn't work, maybe it gives us valuable hints in the form of error messages.

---

### Post by frodon on 2008-05-05
Don't forget to read th stickies ;) :
[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by Dani Filth on 2008-05-05
frodon : I think you didn't get what the topic starter meant here. Those solutions in the sticky topic is to solve sharing matters from your Ubuntu PC to others, whilst the problem here is to gain access to other remote PCs (XP and/or Ubuntu, perhaps). At least, that's what I think after reading the topic.

I'm having the same problem [here](http://ubuntuforums.org/showthread.php?p=4885013) and so far, it hasn't been solved yet, kinda like a bug, I presume.

---

### Post by vodka_tonic on 2008-05-05
i will try that later today, i am at work right now. thanks.

---

### Post by vodka_tonic on 2008-05-05
here's the smbclient output for the machine that doesn't work windows xp 2002, sp2:

cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.0.100.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.0.100 failed (Called name not present)
session request to 192 failed (Called name not present)

here's the smbclient output for the machine that DOES work windows xp 2002, sp2:
immortal@immortall:~$ smbclient -N -L 192.168.0.103
Domain=[NIKE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	E$              Disk      Default share
	IPC$            IPC       Remote IPC
	D$              Disk      Default share
	I$              Disk      Default share
	G$              Disk      Default share
	F$              Disk      Default share
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	sort            Disk      
	J$              Disk      Default share
session request to 192.168.0.103 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[NIKE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------


i have a feeling some setting's for this computer are cached somewhere and need to be refreshed. i will investigate some more.

---

### Post by vodka_tonic on 2008-05-05
okay, i was mistaken, both my machines are Windows XP 2002, SP2...but it sees the shares in one, but not the other.  u can see the smbclient debug info. above.  guest account works on one to list shares, but not on the other. i tried the method below and it works for admin. but not for guest.

<<<<<<< ADMIN >>>>>>>>>>>>>>>>
immortal@immortall:~$ smbclient //foxtrot/literature -U guest
Password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_ACCESS_DENIED


immortal@immortall:~$ smbclient //foxtrot/literature -U administrator
Password: 
Domain=[FOXTROT] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> ls
  .                                   D        0  Mon Apr 14 01:00:49 2008
  ..                                  D        0  Mon Apr 14 01:00:49 2008
  BOHEMIANS OF THE LATIN QUARTER.htm      A     3592  Mon Jun 14 14:22:38 2004
  book_THE STORY OF THE MALAKAND FIELD FORCE (An Episode of Frontier War)_Sir Winston S. Churchill.txt      A   542193  Sat Nov  8 17:29:52 2003
  Charles Bukowski - 661 Scanned Manuscripts and Letters - By Cassady      D        0  Mon Apr 14 01:01:07 2008
  Clive Barker                        D        0  Mon Apr 14 01:00:48 2008
  ebook_actions and reactions_rudyard kipling_1909.txt      A   387998  Wed Dec 22 16:06:28 2004
  home.swbell.net                     D        0  Mon Apr 14 01:00:46 2008
  play_The Doll's House_Henrik Ibsen.html      A   219164  Mon Feb 23 19:36:06 2004
  play_The Doll's House_Henrik Ibsen.txt      A   219164  Mon Feb 23 19:36:06 2004

		45747 blocks of size 4194304. 2661 blocks available
smb: \> 


some problem with SMB program, hopefully they will resolve it one day.  my windows machine sees my ubuntu shares so i just use that to transfer files.

---

### Post by vodka_tonic on 2008-05-05
**IT WORKS THIS WAY !!!**
okay more info...when i look before i do not see any shared folders for that machine...in the location bar in nautilus, type the full path, i.e. add the name of the share you want to see and voila it will ask for password and then connect.  it mounts it as a volume and if you unmount it, it's gone again :)

---

### Post by BartInTN on 2008-05-07
Same problem here.  This is repeatable when accessing shares on a windows machine in which the guest account is disabled.  Nautilus insists on using the guest account, as I've posted before.  Typing in the full path like vodka suggested above works... but add that to the list of annoyances, when one can't browse a simple smb host.

---

### Post by swells5 on 2008-05-21
I have been using ubuntu for years now. I have had an interesting experience with Hardy and file sharing. My home network if fairly complicated - I have a seanix pentium 4 1.5gb ram dual harddrive which dual boots xp / ubuntu. My new desktop = dell amd dual core 2gb ram dual boot vista/ubuntu. I have an old sony vaio laptop with ext cdrom, running ubuntu. My wife has a lenovo laptop running xp and a dell desktop running vista home premium. Needless to say I have spent days, weeks, maybe months keeping everything working over the last several years with each upgrade - I am a ubuntu junky. The old desktop(Seanix) has been my file server for the rest of the house actually running xp with ubuntu in a vmware virtual machine as the actual file server - lastest version all working well was gutsy. By working well, I mean every computer had access to our photos and music and movie collection with no password and my wife and I both had home folders available on all the machines with password protection. The only reason my server ran xp with virtual ubuntu was my old printer wouldn't work with ubuntu, nor would my scanner.
My printer broke so I got a new one, I got a new scanner -carefully choosen to work with linux.
So now is the time to get rid of the last of windows.
I downloaded hardy heron i386 desktop and burned one cd.
I installed it on my newer Dell desktop to try it out. Printer, scanner work and share. File sharing works out of the box. All looks great.
So I use the same install cd on the Seanix, Install hardy heron on its own partition with a separate partition for the home folder. AND file sharing is broken. Non of the folders  are shared properly, even the ubuntu machines don't share well any more. I got all of the error messages about net usershare = permission denied etc. I learned about net usershare.I edited my smb.conf(repeatedly) I did the logout/login and even reboot suggestions and still NO proper sharing. I tried all combinations of sharing options after R clicking nautilus folders. There seemed no rhyme or reason to what happened. Allow guest = still need password, no guest - everyone had access to my home folder.

It is interesting that some users install hardy and everything works out of the box. Other install hardy and have a nightmare with sharing. I have had both - the only difference being the machine that I installed hardy on.

I am not a computer expert, but I hope that this information gets into the hands of someone who can make some sense of it. 
I have now reinstalled Gutsy on the Seanix - file server and my home network is back to HAPPY with all working well.

I would be pleased to send any specific information about the machines, installation, or anything else if someone with the knowhow can help sort out this problem. 
I am now windows free but would like to have hardy running on all my machines.
Thanks for your patience with this long post - I hope that it helps ubuntu and hardy improve.

---

