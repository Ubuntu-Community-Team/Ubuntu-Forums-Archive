---
title: "WIFI Help"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by BamaBob on 2008-09-12
Hello All,

I apologize for posting in this request in the beginner forum; however, I am a beginner and the issues I'm having may be typical for a beginner.

I have Kubuntu loaded on a 2 GHz, 1 Gig memory laptop.  The laptop is dedicated to Kubuntu.  (Yes, I know this is a Ubuntu forum; I think the quality of help in this forum is more consistent).

I'm having problems getting my WIFI card to work.  I've used all the ideas in the Kubuntu forums and Ubuntu forums without success.  The WIFI is a Linksys WPC11 version 3.  Is that a loud groan I hear?

I've recently discovered and downloaded the Linux driver from Linksys for this card hoping to make it work.  However, I don't know how to 'install' the driver!!  I have a driver sitting on the desktop and unable/don't know how to use it.  ARGG!

Yes, I've tried using the ndiswrapper without success.

So, I'm at a standstill.  I'd appreciate assistance.  I tried loading Ubuntu on the laptop, but it kept hanging; Kubuntu installed without a problem.  Go figure.

Thanks!

Bob

---

### Post by dhtseany on 2008-09-12
Hi there,
Please post the results from the following:
```
user@localhost:~$ lspci | grep Network
```

Peace
Sean

---

### Post by BamaBob on 2008-09-12
Thanks for taking a look at this!  Results of the command entered:
 
bash: ~$: command not found

I know this isn't good!  I think I have the drivers, but don't know how to install.  I'm guessing something else has to be done before installing the drivers . . . .?

Thanks!

---

### Post by SuperSonic4 on 2008-09-12
What filetype did it download as? .tar.gz? If so what does the readme or install text files say (after extraction)?

Have you looked in Restricted Hardware, it looks like a chip in the system tray.

---

### Post by BamaBob on 2008-09-12
Yep, the file is a tar.gz file.  It is sitting in a folder on the desktop.  

When I open it with Ark?, a listing of the contents show up.  I did open the readme file.  It is too technical for me to understand, but I did see the drivers are for RedHat and Mandrake variations of Linux.  Would it be safe to say Kubuntu will not support it?

There is no install file in the folder.

Restricted Hardware: I don't see an icon for it in the tray.

I've been poking around and found the Network Connections section and found out that the built in NIC is operating.  I also see wifi0 and wlan0 with a green check mark with text: Enabled Wireless Network Device.  This has got to be good!

Thanks SS4!

---

