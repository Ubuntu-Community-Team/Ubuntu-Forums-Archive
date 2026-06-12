---
title: "Anti-Virus"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by OuT.Law on 2008-08-12
Hi,i wonder if it possible to turn an old PC to an ANTI-VIRUS that i can connect it to my network to monitor other PC's !?

---

### Post by WRDN on 2008-08-12
It's possible to use another PC to scan a computers files.

You could setup samba shares for the drives, and connect them to the 'Anti-Virus PC'. Then, you could scan the shares with the PC that has the antivirus software installed upon it.

---

### Post by OuT.Law on 2008-08-12
> **WRDN said:**
> It's possible to use another PC to scan a computers files.

You could setup samba shares for the drives, and connect them to the 'Anti-Virus PC'. Then, you could scan the shares with the PC that has the antivirus software installed upon it.

Thanx for your reply.
I want real time monitor, something based on linux that scan my other computers (Windows XP)automatically IS THIS POSSIBLE ? AND HOW ?

---

### Post by bodhi.zazen on 2008-08-12
IMO, if you are running windows, it is best to use antivirus scanners running on windows on Windows. The linux antiviurs scanners do not work the way you envision. You would need to mount C:\ via samba and then scan it.

---

### Post by WRDN on 2008-08-12
If you want real-time protection, you may be able to use [AVG Free for Linux]("http://www.brothersoft.com/avg-anti-virus-free-for-linux-freebsd-download-60623.html"), which (I believe) includes the Resident Shield that provides the real-time protection you desire.

---

### Post by OuT.Law on 2008-08-12
Thank you all for your help :)

---

### Post by freak42 on 2008-08-13
I don't think this works in the way you intend it to.
Installing a scanning engine on a computer cannot effectively protect another computer from getting viruses.

Virsus scanners hook into the OS to intercept opening calls by the os and scan the accessed files beforehand (real-time protection). This is afaik not possible with a scanner on another computer (how should this computer know what you just downloaded and are trying to open?). 
You can of course try to scan continuously the harddisk of the remote computer, however this is not a very effective method (you still can get infected in between scans as well) and your network is probably constantly at it's limits.

I therefore strongly suggest simply installing av software on any windows (and maybe mac?) computer.

---

### Post by Dill on 2008-08-13
+1 to the comments on running anti-virus/malware programs natively in Windows. AVG is a good, free anti-virus program. You might have already researched this, but some others you should check out are:

SUPERAntiSpyware: [http://www.superantispyware.com/download.html](http://www.superantispyware.com/download.html)
Autoruns: [http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx](http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx)
Spybot: [http://www.safer-networking.org/index2.html](http://www.safer-networking.org/index2.html)
Ad-Aware: [http://lavasoft.com/products/ad_aware_free.php](http://lavasoft.com/products/ad_aware_free.php)

These are all free and work pretty well.

Cheers,
Dylan

---

### Post by lisati on 2008-08-13
> **WRDN said:**
> If you want real-time protection, you may be able to use [AVG Free for Linux]("http://www.brothersoft.com/avg-anti-virus-free-for-linux-freebsd-download-60623.html"), which (I believe) includes the Resident Shield that provides the real-time protection you desire.

And don't forget to add your user name to the avg user group. Caught me out, and when I visited the AVG forums I found the equivalent of "RTFM" given to others who had asked why updates didn't work.

---

