---
title: "[SOLVED] Use Ubuntu to connect to XP/Vista Remotely?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-30
Can I use Ubuntu to connect to my Windows machine remotely?

Is it possible to connect to Ubuntu with Windows?  I am behind hardware firewall(s) so I don't think I will need encryption or anything like that.

How would I go about doing this?

Thanks!

---

### Post by JoneYee on 2008-07-30
> **pi.boy.travis said:**
> Can I use Ubuntu to connect to my Windows machine remotely?

Is it possible to connect to Ubuntu with Windows?  I am behind hardware firewall(s) so I don't think I will need encryption or anything like that.

How would I go about doing this?

Thanks!

If your XP/Vista Machine is a professional version (Xp/Vista Pro) you can use the Terminal Services Client in Ubuntu.  XP/Vista Home versions don't even support RDP from other Windows Machines.  

Otherwise, look into VNC.

---

### Post by SunnyRabbiera on 2008-07-30
yes its possible, there is a remote desktop application for it though I forget what its called as I dont use that sort of thing

---

### Post by pi.boy.travis on 2008-07-30
Is there a version of Vinagre or another client with a GUI for Windows?

---

### Post by JoneYee on 2008-07-30
> **pi.boy.travis said:**
> Is there a version of Vinagre or another client with a GUI for Windows?

I think the easiest thing to do is to have a VNC server run on the Windows machine and connect to it with the TSC client in Ubuntu.

I've done that in the past in order to help my wife (Xp/Vista Home) when I've been on the road.

---

### Post by BDNiner on 2008-07-30
You can use VNC, ubuntu supports it by default, you would just have to install a VNC client on the windows machine.

---

### Post by bodhi.zazen on 2008-07-30
> **BDNiner said:**
> You can use VNC, ubuntu supports it by default, you would just have to install a VNC client on the windows machine.

If you want to connect to Windows XP with VNC you need to install a VNC Server on Windows.

You can connect from Ubuntu "out of the box" with RDP. You do not need to install anything on either windows or ubuntu.

Windows config :

[http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx](http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx)

Ubuntu side :

[http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46](http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46)

[http://www.cyberciti.biz/tips/linux-remote-desktop-for-controlling-windows-xp-desktop.html](http://www.cyberciti.biz/tips/linux-remote-desktop-for-controlling-windows-xp-desktop.html)

---

### Post by JoneYee on 2008-07-30
> **bodhi.zazen said:**
> If you want to connect to Windows XP with VNC you need to install a VNC Server on Windows.

You can connect from Ubuntu "out of the box" with RDP. You do not need to install anything on either windows or ubuntu.

Windows config :

[http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx](http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx)

Ubuntu side :

[http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46](http://mixeduperic.com/index.php?option=com_content&task=view&id=70&Itemid=46)

[http://www.cyberciti.biz/tips/linux-remote-desktop-for-controlling-windows-xp-desktop.html](http://www.cyberciti.biz/tips/linux-remote-desktop-for-controlling-windows-xp-desktop.html)

RDP is not native to XP Home or Vista Home Premium.  Must be a Professional or higher series Windows Install.

---

### Post by tashmooclam on 2008-07-30
There is a web-based "logmeinfree". It's free. If you install that on the *target* pc, you should be able to use the Ubuntu on Firefox to see the pc desktop. Logmein is similar to "gotomypc". 
You can also try using the built-in VNC in Ubuntu. Applications->Internet->Remote desktop viewer.

---

### Post by bodhi.zazen on 2008-07-30
> **JoneYee said:**
> RDP is not native to XP Home or Vista Home Premium.  Must be a Professional or higher series Windows Install.

OIC, what a *pain*

I knew there as a reason I don't use Windows, lol

Nice avatar by the way.

---

### Post by JoneYee on 2008-07-30
> **bodhi.zazen said:**
> OIC, what a *pain*

I knew there as a reason I don't use Windows, lol

Well I am a Complex Systems Senior Analyst for one of the big three Server makers, and we deal with Windows all day for the most part.  So, I'm pretty familiar with most of the microsoft stuff to an advanced level (and I chose Linux).

> **bodhi.zazen said:**
> Nice avatar by the way.

Been working on him for a few days, trying to make a tux that sums up what JoneYee is, so thanks =)


Anyway, based on the non-confirmation of Pro, I would assume Home (as noone installs Pro for a home user at the store), so VNC is the best way to go.

---

### Post by pi.boy.travis on 2008-07-30
This is all excellent stuff.  I will have to check out logmeinfree.  Will a VNC client on my Windows box work, because isn't Ubuntu running VNC server and client?

YAY!  100th post!  \\:D/

---

### Post by tashmooclam on 2008-07-31
I will try to answer, but I am not an expert. XP Professional has remote desktop. Ubuntu has remote desktop. If your windows is XP pro, you can use the Ubuntu probably to get onto it. 

[http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx](http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx)

I have not checked Vista's capabilities. 

If you download that small piece of software at logmein.com ONTO the Windows/Mac, then you can see that remotely using another computer through a browser (Safari or Firefox). To me, this seems like an easier way, but I don't know how it behaves, I have not used it yet. 

The way I conceptualize it is, imagine you go to meebo for instant chat. This is web-based, you use Firefox to go to meebo. But, you can chat with people who have installed a chat client (MSN, AIM, ICQ) onto their computers. Their computers chat with yours, but only theirs has a chat client installed. 

I am answering a post, but I am by no means expert at this stuff. 

I would install the client logmeinfree on the XP/Vista computers and give it a try.

---

### Post by robertsaron on 2008-09-21
To connect to my linux box from work I use nomachine.com its software that installs on linux, and the client is installed on the machine you want to connect from.

When I want to connect to my windows box from Work I use dyndns, or logmein. 

As for RDP capabilities for Vista, Vista ultimate and home premium have it built in. Not sure about Vista business. I would not use anything other than Vista Ultimate. As far as windows is concerned it has better security and networking. 

I have never messed with VNC, getting logmein to work with linux, it does not at this time, I have tried Firefox and even intalled IE6 into linux. VNC or some form of RDP from linux to windows will work better.

---

