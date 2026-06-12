---
title: "Antivirus scanner for windows which runs on ubuntu"
date: 2008-12-02
forum: Recurring Discussions
---

### Post by Modnar1 on 2008-12-02
Hi i dual-boot my pc with windows xp and ubuntu, however i think windows has got a virus as windows now no longer gets past the menu where you can select it to start in safe mode before reseting itself. I was wondering if there is an anitivirus program which i can use to scan my windows partition from linux

---

### Post by lukjad on 2008-12-02
There are a few things. I hear that there's Avast, and ClamAV that are the most popular. Also, Spybot can be run with WINE too.

---

### Post by Elfy on 2008-12-02
> There are a few things. I hear that there's Avast, and ClamAV that are the most popular.+1

Assuming that you have the windows partition mounted I think you should be able to run it on that win partition from linux.

But are you sure that it's a virus, will it not start from safe mode?

---

### Post by binbash on 2008-12-02
also there is f-prot

---

### Post by Twitch6000 on 2008-12-02
There is an older version of AVG that works aswell.

---

### Post by overdrank on 2008-12-02
Just to add to the others 
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by oilchangeguy on 2008-12-02
> **Modnar1 said:**
> Hi i dual-boot my pc with windows xp and ubuntu, however i think windows has got a virus as windows now no longer gets past the menu where you can select it to start in safe mode before reseting itself. I was wondering if there is an anitivirus program which i can use to scan my windows partition from linux

most likely not a virus. since you spoke of safe mode, i'm guessing you're pressing F8 at start up. try selecting use last known good config. and see what happens. also try using your windows cd, boot from it, when prompted press r to enter the recovery console. and type chkdsk/ r and press enter. this will check the hard drive for errors. and fix them, if any are found. then press exit to restart the computer.

---

### Post by Modnar1 on 2008-12-03
i have tried pushing both f8 at startup and trying all the options there as well as when this screen appears automatically when windows fails to start correctly

---

### Post by gandaran on 2008-12-03
of all antivirus mentioned here I only recommend avg and bitdefender, all other antivirus linux versions have a small data base of virus, with bitdefender you get full virus, antispyware and adware data.
just out of curiosity, do you run avg antivirus in your windows?
avg has been damaging some windows computers in the past weeks, if this was your case the repair is easy.

---

### Post by Paqman on 2008-12-03
+1 on checking the Windows partition for errors. Viruses don't usually stop you from booting. If they did, they wouldn't be able to spread.

---

### Post by Modnar1 on 2008-12-04
i'll try running a scan disc from windows repair console as the scan i just did with clam av unsurprisingly didn't come up with any viruses

---

### Post by Modnar1 on 2008-12-04
just done a scan disc on windows, told me immediately that there were one or more irrecoverable errors, so i guess i'll just have to get all of my data off through linux then reinstalled it all... again
Thanks for the help though

---

### Post by madsc89 on 2008-12-04
pity.

I run dual boot with XP, as well. I only use XP for games, Ubuntu is good enough for everything else.

You should consider Avira antivir FREE, SuperAntiSpyware, and Comodo Personal Firewall on your fresh XP install, those are widely accepted programs which runs smoothly and protects well. Earlier, I had AVG 7.5, and when I got a spyware, I installed SAS, which removed it well, then uninstalled it. Now I run the mentioned programs, and the only possible thing to say, is that Comodo is not for newcomers, but considering you're using Linux, that should not be a problem.

---

### Post by FreewheelinFrank on 2008-12-04
You can run the Kaspersky online scanner in Firefox on Ubuntu and it will scan the Windows partition. 

Kaspersky has just about the best malware detection rate of all the AV's.

---

### Post by ysNoi on 2009-07-25
Avast is a good one... I'm using it with my Jaunty box..!

---

### Post by koleoptero on 2009-07-25
If I'm not mistaken, ClamAV has a native linux client for scanning folders. It would probably be the best solution IMHO.

---

### Post by ibuclaw on 2009-07-25
Closing as this is an old thread, and all discussions ceased over 6 months ago.

For more information on AntiVirus software in Ubuntu, please read here: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

For any queries, please start a new thread. :)

Regards
Iain

---

### Post by ibuclaw on 2009-07-25
As advised/discussed. Thread opened and moved to recurring discussions.

Have a good day!

Regards
Iain

---

