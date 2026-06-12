---
title: "The System Fan Has Failed"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by ocdkv on 2013-08-08
[COLOR=#000000][FONT=HPRegular]Hi There,

Second post and total noob to anything Linux.

I decided to repurpose my old desktop to a media server and learn a new OS while I was at it. It was an HP media center m8430f with a Core2Quad Core Q6600 and an IPIBL-LB motherboard running Windows Vista and the latest BIOS Update (v 5.43). I Purchased a new case for the server, a Bitfenix Ghost.  I've succesfully installed Ubuntu 12.04 LTS Desktop (so far so good).  Whenever I restart it i get the following message:

“Error: The System Fan Has Failed![/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Service PC to prevent damage to the system.[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]Press <F2> to Continue”

The fans are running fine. I've looked at many solutions online but none have worked so far.  I'm hoping someone here can help, Thank you.

Kevin [/FONT][/COLOR]

---

### Post by Boab1993 on 2013-08-08
Hi there Kevin, 

Is this on the ubuntu startup or system BIOS?

If its BIOS its most likely a loose connection within your case.

---

### Post by ocdkv on 2013-08-08
Thank you Boab1993, 

It seem to only be on ubuntu startup,  when I run a live cd of SeaTools for DOS I do not get this message.  Just tried switching fans to no avail.

---

### Post by Boab1993 on 2013-08-08
Since all fans are primarly controlled by BIOS systems, and you say it  works fine on windows, it sounds like a problem with drivers.
Sadly my knowledge of fans is purely from a hardware perspective.

There have also been a few reports within BIOS settings the 'smart-control' is enabled.

Sorry i cant help more, im sure someone else will.

---

### Post by Boab1993 on 2013-08-08
A potluck find, whilst looking at your other question.

An outdated BIOS system.

Windows download here :
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=uk&lc=en&dlc=en&softwareitem=pv-67215-1](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=uk&lc=en&dlc=en&softwareitem=pv-67215-1)

Run on windows, complete all prerequests i.e. reboot on windows etc, then boot ubuntu.

---

### Post by ocdkv on 2013-08-08
Thank you for trying Boab1993, I really appreciate any assistance.  I've read somewhere that the BIOS doesn't understand the lower rpm fans (ie. 120mm vs 90mm) and that the best fix is to get a high rpm fan.  Others have said to just ignore it if all the fans are working properly.  Hopefully someone has a better solution.

---

### Post by Dannyv2003 on 2013-08-08
Try looking up your computer model and download and install the Ubuntu drivers. It should work after that. If it does not, open up the pc, and unplug and plug back in the cords for the fans.

---

### Post by Mark Phelps on 2013-08-08
> **Dannyv2003 said:**
> Try looking up your computer model and download and install the Ubuntu drivers...

Did you even read the OP's make and model info in the first post? If you had, you would see their PC is an HP media center -- for which HP does NOT provide any Linux drivers.

---

