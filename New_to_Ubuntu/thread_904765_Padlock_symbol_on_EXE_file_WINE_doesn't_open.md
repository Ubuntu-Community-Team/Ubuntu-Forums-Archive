---
title: "Padlock symbol on EXE file: WINE doesn't open"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by RobHK on 2008-08-29
I downloaded Irfan View but it won't run. 

I have set permission to run as an executable, and the icon changed accordingly, but it has a padlock sign on it, and will not run. (WINE is installed.)

I know this program will run under WINE as I have done it succesfully before.

---

### Post by spiderbatdad on 2008-08-29
the padlock usually indicates the file is not writable. Perhaps the problem is one of ownership; that is, is the file executable only by root?
Maybe you should chown the file. Not a user of wine, myself, so I don't know if wine runs programs owned by root. Or you might try sudo chmod a+x to ensure that all groups can execute the file.

---

### Post by RobHK on 2008-09-02
> **spiderbatdad said:**
> the padlock usually indicates the file is not writable. Perhaps the problem is one of ownership; that is, is the file executable only by root?
Maybe you should chown the file. Not a user of wine, myself, so I don't know if wine runs programs owned by root. Or you might try sudo chmod a+x to ensure that all groups can execute the file.

I gave up on it. WineDoors has Irfanview, but they are between versions at the moment. I'll wait till the new one is out ant go that way.

---

### Post by keith.eckstein on 2008-09-02
Rob - not the technically most elegant way but it certainly suits an idiot like me...  under terminal run SUDO nautilus and then set read/write and execute permissions (highlight file, right click - go to properties) - don't think Wine needs to run as root but the few MS files that I have downloaded have needed the above.  

I have found that virtualisation (under VirtualBox) a better long term solution for myself - am not knocking the brilliant efforts of the Wine team but if you have an MS OS licence (and have paid for it) - why not use it?  

Don't get me wrong, if there is a Linux solution - I'll always use that but... what about .Lit ebooks (being an expat, I've spent a lot of money on these - am not going to junk a great OS that works fine for me 99% of the time just to read books that I've already paid for - thus... virtualisation - using a licence that came with my machine - thus, already paid for.)

All the best

Keith

---

### Post by RobHK on 2008-09-02
> **keith.eckstein said:**
> Rob - not the technically most elegant way but it certainly suits an idiot like me...  under terminal run SUDO nautilus and then set read/write and execute permissions (highlight file, right click - go to properties) - don't think Wine needs to run as root but the few MS files that I have downloaded have needed the above.  

I have found that virtualisation (under VirtualBox) a better long term solution for myself - am not knocking the brilliant efforts of the Wine team but if you have an MS OS licence (and have paid for it) - why not use it?  

Don't get me wrong, if there is a Linux solution - I'll always use that but... what about .Lit ebooks (being an expat, I've spent a lot of money on these - am not going to junk a great OS that works fine for me 99% of the time just to read books that I've already paid for - thus... virtualisation - using a licence that came with my machine - thus, already paid for.)

All the best

Keith

I'll look into this, Keith. It's mainly an interest thing, not a necessity, as I have a Windows XP licence. I have a VirtualBox but Windows wouldn't activate for me. I tried to activate by phone but I don't think they understood what I was talking about. Told me to contact Technical Services. TS of course kept me waiting so I thought Sod it. Ve have vays of making it actifate ;)

I since read that MS doesn't allow XP OEM on a virtual box even on the same machine!

Glad you are enjoying France. I married a French woman and have dual nationality now. Not that it gives me any advantages now we are in the EU, except when I was working in Algeria I didn't need an exit visa to get out.

---

### Post by Mizfit51 on 2009-01-02
I have a somewhat similar problem. No matter what the file is, or how many times I re-install WINE... Nothing opens when I tell WINE to open it. If I go to configure WINE it will open up fine, but nothing when I right click and say to open with WINE will open. I've tried to make a new "Open With" tab and all that stuff recommended on other forums, but nothing works...

If you reply and help me out, try and put it into simple terms. I'm not the brightest when it comes to computers, let alone Linux.

---

