---
title: "White Screen on GENOME Session"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by flutti-tutti on 2008-05-18
Hi
When i switch a session from Kubuntu to GENOME through Logout->Options->Change Session->GENOME, my screen goes white, and never be able to get into GENOME any more.

My graphics card is ATI Radeon Xpress 1250, but its driver is "generic Vesa" provided by Ubuntu.  After Ubuntu is installed, KDE-package is implemented and set as a default.

What should I do?  Plz help.
Thanks.
tutti

---

### Post by Patb on 2008-05-18
Flutti, I assume you mean Gnome, not Genome.  It seems the first thing you should do is use Adept to check is that the relevant Gnome components are installed.  

Cheers, Pat.

---

### Post by flutti-tutti on 2008-05-19
Pat,
u r right - gnome.  I must have been thinking of DNA -- what kind of DNA you Ubuntu guys commonly share.

Before I installed the KDE-Desktop package, Ubuntu-64bits had worked perfectly on the ASUS M2A-VM mobo with AMD Athlon 64 X2 and 2 GB memory.  (I did not have the white screen syndrome when the system come back from "Hibernation".)

How can I check the GNOME components?
tutti

---

### Post by Patb on 2008-05-19
> **flutti-tutti said:**
> How can I check the GNOME components?
Tutti, this is a bit of a stretch for me because I don't have 64 bit, I don't use KDE, I don't use Adept and I only use a few parts of Gnome. Do you still have any confidence in me or my DNA? :)

Pressing on regardless... Using Adept's sister program, Synaptic, I would simply look down the list of available packages to the ones starting with "gnome..." and install (or perhaps reinstall), first the basic gnome package, and then any of the listed gnome packages likely to be useful to me.  Examples from my list for instance would include gnome, gnomebaker, gnome-cups-manager etc etc.  
> Ubuntu-64bits had worked perfectly
If you mean using the hardware and the base installation you presently have (Ubuntu rather than Kubuntu), I'm not so sure the above advice will be any use.  I was assuming you had not run Gnome before.  But it's probably worth a try anyway, and should certainly do no harm.  

I hope this helps.  Good luck, Pat.

---

### Post by flutti-tutti on 2008-05-20
Pat, 
Thanks for your reply.  I have confidence in your DNA, because you do not use KDE, keeping things simple -- very smart!

My Ubuntu-64bits system worked perfectly, and then I installed the KDE package to make it (K)Ubuntu.  (I am no programmer, and wanted to use GUI.)  After that, things started going down and down....

The cause of the problem must have been related to bugs of Compiz with Motherboard's ATI video.

Before your response, I removed all the Compiz related components using Synaptic.  Then, things got better all of sudden.

Now, I am able to use GNOME without whiting the screen.  Occasionally, the system complains of missing some Compiz components, but has not caused any problem for me so far.
 
I will go through gnome components according to your suggestion. 

Thanks for your help.
tutti

---

