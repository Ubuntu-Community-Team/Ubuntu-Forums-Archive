---
title: "Cannot uninstall software through Wine"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by sdim on 2008-05-20
Hi,everyone.
I can't seem to be able to uninstall software installed through Wine.It seems to start the process,but it ends a few seconds later,without having done anything.Any suggestions?
Thanks.

---

### Post by kestrel1 on 2008-05-20
If you go to the Wine configuration program you should be able to remove the installed apps from there.

---

### Post by KenBW2 on 2008-05-20
I'm with kestrel on this one. Many times I've tried to uninstall it. What about just deleting the folder from the C: drive?

---

### Post by sdim on 2008-05-20
Thanks for answering.
I've tried uninstalling the apps from the Wine sub-menu,but nothing happens.
Where are the apps that are installed through Wine,I mean in which folder?I've tried Wine folder but there are no apps there.

---

### Post by shifty_powers on 2008-05-20
look in ./wine in your home folder.

go places>home and press control h

---

### Post by kestrel1 on 2008-05-21
Alternitavly go to Applications> Wine> Browse c:\ Drive

---

### Post by Skeet on 2008-05-21
I've had similar problems. I find deleting them from the applications list, then deleting from Program Files in the Wine C:\ directory fixes it. It doesn't remove them from the Uninstall Programs list always though. Perhaps a bug to submit to the developers?

---

### Post by sdim on 2008-05-21
I did what Shifty_powers and kestrel1 suggested.
I erased all unnecessary programs,but still Wine Menu has them and cannot be erased.It must be a bug of some kind.
Thanks to all.

---

### Post by SunnyRabbiera on 2008-05-21
yes wine can be shaky arond the edges.
But what windows apps do you use? you know there are plenty of linux alternatives to most of them.
unless you are a gamer or something.

---

### Post by RiceMonster on 2008-05-21
> **sdim said:**
> I did what Shifty_powers and kestrel1 suggested.
I erased all unnecessary programs,but still Wine Menu has them and cannot be erased.It must be a bug of some kind.
Thanks to all.

Remove them from the main menu. System > Preferences > Main Menu

---

### Post by sdim on 2008-05-22
Thanks to both of you.
I tend to use apps that have to do with video editing,not games.There are some in WinXP that cannot be substituted by other ones in Linux,not at least with the same results.Apart from that,I had installed a program to erase dvd's,since K3b didn't include such a feature.
To Rice Monster:I did what you suggested and I no longer see them in the Wine Menu,but can't something else be done for almost all the unused apps to be removed? Do they influence the operation of the rest of the system?

---

### Post by mhedges48 on 2008-08-24
I have add to use the regedit command and do a search for programs to completely remove them before in wine (the add/remove wine function would not completely remove the program)...

---

### Post by six616 on 2009-12-17
Solution:
[http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8](http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8)

---

### Post by 7Lj3)(P38J on 2010-11-30
> **six616 said:**
> Solution:
[http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8](http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8)


Unfortunately this is no solution. I cannot uninstall Babylon Toolbar from the list of applications.

I ran "wine uninstaller" in terminal mode and here is the outcome, in case it helps:

fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:LookupAccountNameW (null) L"carlos" (nil) 0x33e910 (nil) 0x33e914 0x33e908 - stub
fixme:advapi:LookupAccountNameW (null) L"carlos" 0x13b490 0x33e910 0x13bbf8 0x33e914 0x33e908 - stub
err:ole:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err:ole:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {0002df01-0000-0000-c000-000000000046} could be created for context 0x17

Can someone help me?
thanks

---

