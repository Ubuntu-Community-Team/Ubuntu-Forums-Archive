---
title: "ubuntu with xp safe?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-06-23
i just downloaded a couple things over torrent last night on ubuntu thinking it would be safe, cuz its ubuntu and not windows! i have 3 partitions, windows, ubuntu, and a shared partition. i notice though, on ubuntu, i can mount the other 2 partitions and access files from them. i dont think the files i downloaded were dangerous. i try not to download things im not too sure about and read other peoples comments before downloading. so i left the computer on overnight to download last night. today there was some weird error message i got before ubuntu started up after i reset the computer. it was in red and i didn't get a chance to read it. and now kaspersky on my xp is messed up. first time i opened windows, it tells me that my antivirus program isn't on, but after 30 seconds or so it turned on, so i thought "oh maybe it just took a little longer this time". but i decided to run a virus scan just incase. when i did this kaspersky ran into some errors and so did the rest of the computer. i tried right clicking on desktop>properties, when i went to the screen resolution tab, the thing scrolled from 1280x1024 to 800x600 by itself, and i had to click the "x" so many times to close that window and all the other windows id opened. nothing i tried to change worked on anthing. after i restarted once more, my kaspersky wont even start up anymore. the thing is though, i never touched the 2 files i downloaded(never executed them) and i didn't move it to the other 2 partitions either. is it possible to get a virus through ubuntu just like that? i thought viruses had to be ran manually....

---

### Post by angryfirelord on 2008-06-23
You got me. It certainly sounds like a virus or something got corrupted on your Windows install. If you use system restore, then I'd roll back to your previous restore point. If you really think you have a virus, disconnect your computer from the internet, boot into safe mode, and run your AV utility. If Kaspersky is still corrupted, re-install it and connect to the internet to only get updates for it, then disconnect. 

Could also be back luck too. You just happened to get a virus while downloading a torrent. Where did you get the torrent and what program were you using to get Ubuntu?

---

### Post by ubromtoo on 2008-06-24
waggingwabbit :

     what torrent / program were you using?

---

### Post by waggingwabbit on 2008-06-24
how do i get to safe mode on the grub boot loader?

the 2 torrents i downloaded were from mininova. there was 100+ comments and some thanks on 1 of them. i check these before downloading.

i was using deluge

---

### Post by gtdaqua on 2008-06-24
> **waggingwabbit said:**
> how do i get to safe mode on the grub boot loader?


1. Hope you are shown your boot option screen where you can select which OS to load. 

a. Select XP, press enter and press F8 immediately. You should then see the XP boot options screen. Select safe mode.

2. If you are not automatically shown the OS the load when your computer starts up, you should still see a message 'GRUB Loading....Press 'Esc' for menu' - and a short countdown for 2 seconds. Press 'Esc'and go to point 1a above.

---

### Post by bodhi.zazen on 2008-06-24
From your description it is hard to know. I have seen similar malware on Windows XP.

IMO, assuming the problem came through Ubuntu, it then essentially boils down to circumventing your antivirus by transferring files from Ubuntu to Windows without scanning them first.

Before you draw conclusions though you should start with forensics. It is a hardware problem or malware? If malware, what ? Is it a "new" problem not yet in your antivirus data base or is an old one ? Scan *All* the files in your shared partition and downloaded applications.

torrents / shareware are a perfect vehicle for "social engineering".

---

### Post by waggingwabbit on 2008-06-24
i never but transfered the files from ubuntu to windows. they are still in this partition, but ubuntu does by default have access to the other 2 partitions. im pretty sure they were unmounted last night ( dont know if that makes a difference). im unable to do a scan with kaspersky anymore, and i dont want to connect to the internet with xp at the moment either just incase of whatever. 

ill try tomorrow to get into safe mode and run kaspersky or some free one if that doesnt work, im pretty sure it wont. ill come and give an update then.

---

### Post by bodhi.zazen on 2008-06-24
Well if you did not transfer files from Ubuntu to windows then it is hard to see how they affected windows then.

From what you described you downloaded files. Where did you put them ? Somewhere accessible to windows, then yes that may affect windows.

But if they are on your Ubuntu partition, and you do not access your Ubuntu partition from windows, I do not see how the downloads would affect windows. You would have to have opened a file or run a program that then deployed malware to Ubuntu and then to windows, very, very unlikely. Not impossible mind you, but unlikely.

---

### Post by waggingwabbit on 2008-06-24
i just remembered something. when hardy first came out and i was installing it, i tried the memtest thing for fun. after 1 pass i got about 700+ errors. when i went to windows today, everything was fine. i wasn't there long though, i just needed to get into windows and log out properly so i can access the partitions again from ubuntu. i dont think my windows can get into the ubuntu partition. could this be a problem with my ram? maybe when things are too intensive now they start to give up on me. I've just figured out how to get avast's gui to appear for my ubuntu and updated the database for it. it crashes here too while scanning...

edit:
could it be that i was getting errors because i left the computer on overnight and it caused the rams to stress out or something like that?

---

### Post by Tea4all on 2008-06-24
It is probably a RAM problem. Try the tests from a cleanly burned ubuntu disk, and if the same errors pop up, try replacing the RAM. You can always use more RAM anyway!:lolflag:

---

### Post by bodhi.zazen on 2008-06-24
To be honest you should do some forensics, you need to identify the problem.

Start with the OS you are most comfortable with and test your hardware, look a logs.

No, leaving your hardware on overnight will not hurt it. do a gogole. search on uptimes (uptime = how long a computer, usually server, has been running without rebooting).

It just wastes power, produces heat, and leaves you vulnerable to cracking (hard to crack a computer which is off).

---

### Post by sydbat on 2008-06-24
I dunno...with the exception of rebooting for certain updates or to get into XP, or to replace hardware, my box (both of them actually) have been running for years.

As suggested above, it most likely has to do with your RAM. I would do the hard diagnostic first...turn off the computer, unplug it, open the box, make sure nothing has come loose, then put it back together, plug it in and do the memtest from the Ubuntu CD.

After that, if the problem still persists, do what these guys say.

---

### Post by waggingwabbit on 2008-06-26
i have 3 pieces of rams. 2 i bought from ebay some months ago (215 x 2 dual channel) and one i had for about 5 years or so (512). i ran memtest on my ram and then on the other 2(both pluggdin in at the same time). my ram got over 20,000 errors, but it kept going. i decided to just press esc and stop it. after 900 errors on the pair i bought, the system just froze; instead of showing the errors rolling in at the red bottom half of the screen, the texts disappeared and so did the esc to restart computer option and the other options i dunno what they are. im guessing these rams are causing my system to freeze up now. is it safe to just assume its my rams now? =/ also, what about my 512 ram that got 20,000+ errors? what does that mean? my system doesn't seem to be choking up (yet) using only this ram.

---

