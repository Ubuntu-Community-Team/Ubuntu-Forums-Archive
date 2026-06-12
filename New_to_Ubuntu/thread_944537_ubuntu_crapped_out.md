---
title: "ubuntu crapped out"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by brokenhachi on 2008-10-11
hey guys, while i was at work the other day, i got a phone call from my gf saying that my computer is broken.. so i asked whats wrong and she says while she was using limewire and firefox, and after opening yahoo japan`s website, firefox crashed and the gui froze. so i told her, just reset the computer and try it again. 

well she reset it and now when it starts up, only the desktop icons and background art show up, the rest of the desktop doesnt (including desklets and the menu bar) and when you try to open one of the icons on the desktop nothing happens. also if you press a key on the keyboard everything vanishes (any key). so i thought ok maybe i can boot into recovery mode and do something.. but when i do recovery mode at the login screen, it just makes the comp reset. so i tried recovery mode with terminal and that works, i can even use it to launch some programs like skype and amsn, but it wont work for launching firefox.

can someone help me fix this? i have important things on the comp that i really dont want to have to delete....




Thanks in advance.


edit: i`m using the newest lts version.. forget the version number.. sorry..

---

### Post by Commander_Keen on 2008-10-11
I'm no expert, but I would say use the Live Cd to back up your Data & Home Profile/folder and wipe the HD

---

### Post by ChildOfMana on 2008-10-11
I don't know how to fix your problem - but it might be wise to boot from a Live CD and back-up your important data before you try to implement any fix.

---

### Post by Keen101 on 2008-10-11
Yeah, first use a live-cd to back up your data.

Next try going to recovery mode or somehow get to a terminal and try this

```
sudo apt-get update
```

and/or

```
sudo apt-get upgrade
```

I don't know how things got messed up, but try to do updates. If that don't work. just do a new install... and maybe create a separate partition for your home folder to help prevent against future mishaps.

---

### Post by tgalati4 on 2008-10-11
After backing up your data, don't forget to clean the inside of the machine and reseat the memory and ribbon cables.  If it's a laptop, then reseating the memory is about all you can do.

Run it from the live disk for a few days to make sure that it's not a hardware/power supply problem.  If it freezes with the live disk, then you need to look at your log files (/var/log and dmesg) and see if you can find any obvious errors.

---

### Post by fdesign on 2008-10-11
By any chance is the hard drive full?

I think this problem can be solved without wiping the OS and starting over.

---

### Post by Orange_and_Green on 2008-10-11
Hi :) 
I'm sorry you are having these problems.

Just a few ideas... Have you tried:

1) Starting up from a previous kernel (maybe a kernel update broke something)?
2) Disabling compiz?
3) Creating a new account and see if that one acts up too?

I really hope you can get this fixed soon. Best wishes... gambatte!!:KS

---

### Post by brokenhachi on 2008-10-12
ok im backing up the hdd now with the live cd.. then i'll try the upgrade thing and see if that works.

@fdesign: no, the hdd isnt full, but it is half full (or half empty depending on how you look at it..:))

@Orange_and_Green: &#12362;&#36820;&#20107;&#26377;&#38627;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;:) how do i disable compiz in safe mode? and how do i create a new account in safe mode?


thanks for the replies everyone!

---

### Post by Orange_and_Green on 2008-10-12
&#12393;&#12358;&#12356;&#12383;&#12375;&#12414;&#12375;&#12390;&#12290;
> how do i disable compiz in safe mode? 
A radical way would be to uninstall compiz-core.:biggrin:

Or, you could go the "soft way" and try opening the following file:

/home/YOUR_USER/.gconf/desktop/gnome/applications/window_manager/%gconf.xml

and change the reference from "compiz" to "metacity".

(Originally found in  [this thread]("http://ubuntuforums.org/showthread.php?t=681048"))

> and how do i create a new account in safe mode?
System->Administration->Users and Groups->Add new user

Thumbs up!! &#12362;&#12497;&#12477;&#12467;&#12531;&#12398;&#20107;&#12358;&#12414;&#12367;&#34892;&#12365;&#12414;&#12377;&#12424;&#12358;&#12395;:KS

---

### Post by brokenhachi on 2008-10-14
> **Orange_and_Green said:**
> &#12393;&#12358;&#12356;&#12383;&#12375;&#12414;&#12375;&#12390;&#12290;

A radical way would be to uninstall compiz-core.:biggrin:

Or, you could go the "soft way" and try opening the following file:

/home/YOUR_USER/.gconf/desktop/gnome/applications/window_manager/%gconf.xml

and change the reference from "compiz" to "metacity".

(Originally found in  [this thread]("http://ubuntuforums.org/showthread.php?t=681048"))


System->Administration->Users and Groups->Add new user

Thumbs up!! &#12362;&#12497;&#12477;&#12467;&#12531;&#12398;&#20107;&#12358;&#12414;&#12367;&#34892;&#12365;&#12414;&#12377;&#12424;&#12358;&#12395;:KS



well i wasnt able to get anything with safe mode so i used the live CD and copied my home folder and then just reinstalled. thanks for the help everyone but it seems like this time the only way to fix it was to wipe it... i got my data, but i couldnt get my bookmarks from firefox.. which sucks really bad...

---

### Post by Orange_and_Green on 2008-10-15
> **brokenhachi said:**
>  i couldnt get my bookmarks from firefox.. which sucks really bad...

Try having a look in /home/yourname/.mozilla/firefox

(.mozilla is hidden, press CTRL+H to show it). If what I'm thinking is correct, there should be two directories here, with strange names.

One is the old one (should be bigger), the other one is the new, default one the "new" firefox created. If I were you, I'd compress both directories to a .tar.gz (so you have backups), then copy the contents of the bigger folder into the other one.

Good luck!!!!(K)&#27671;&#12434;&#33853;&#12392;&#12373;&#12394;&#12356;&#12391;&#12397;:KS

---

### Post by Orange_and_Green on 2008-10-17
Oh, and another thing that comes to mind... From the "Bookmarks" menu, select "Organise bookmarks", then "Import and Backup", then "Import HTML". Import from the bookmarks.html file in your ~/.mozilla/firefox/something/ directory. Are you still reading the forums brokenhachi san? How are you doing?

Keep us posted and good luck:KS

---

