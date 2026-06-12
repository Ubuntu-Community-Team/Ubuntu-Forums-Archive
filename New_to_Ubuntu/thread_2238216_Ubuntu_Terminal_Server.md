---
title: "Ubuntu Terminal Server"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by CoolnessInc on 2014-08-06
Hello everyone,

I am very new to Ubuntu and have a project at work that I could use some help with. I have a server with Ubuntu Server 14.04 installed. I am wanting to set it up as a terminal server for users to log in (using RDP from their windows machines) to a desktop environment with a web browser (they need to have access to an oracle system from a different network). I have found some guides online, but nothing that is really clear enough for a newbie like me. Could someone point me in the right direction?

Thanks!

---

### Post by TheFu on 2014-08-06
In the Linux/UNIX world, "terminal server" means something completely different than you intend. A terminal server usually means a peice of hardware on the head of a rack row that provide remote consoles into the 20-100 servers on that rack - no GUI involved.  At least that's what it means to old guys.  It could also mean a server that accepts CLI requests (usually via telnet or ssh), but definitely without a GUI - sorta like a "terminal session."

What you really want is a **remote desktop server** - there are many ways to accomplish this with different protocols, but I don't have experience doing it the way you probably want (via RDP) - we need security and RDP just isn't sufficient to use over the internet.

So ... if your users will connect over the LAN, then just load a LAN-friendly desktop (NOT Unity!) and I suspect either **xrdp** or **x11rdp** is the server-side software you want. Don't know which, sorry.  I've used FreeNX and x2go for the last 5 yrs which have great security - safe from anywhere in the world, if ssh-keys are used.

Being new to Ubuntu, probably means a guide could be used: [http://ubuntuguide.org/](http://ubuntuguide.org/) 
Hope this sends you in the right direction.

---

### Post by CoolnessInc on 2014-08-07
> **TheFu said:**
> In the Linux/UNIX world, "terminal server" means something completely different than you intend. A terminal server usually means a peice of hardware on the head of a rack row that provide remote consoles into the 20-100 servers on that rack - no GUI involved.  At least that's what it means to old guys.  It could also mean a server that accepts CLI requests (usually via telnet or ssh), but definitely without a GUI - sorta like a "terminal session."

What you really want is a **remote desktop server** - there are many ways to accomplish this with different protocols, but I don't have experience doing it the way you probably want (via RDP) - we need security and RDP just isn't sufficient to use over the internet.

So ... if your users will connect over the LAN, then just load a LAN-friendly desktop (NOT Unity!) and I suspect either **xrdp** or **x11rdp** is the server-side software you want. Don't know which, sorry.  I've used FreeNX and x2go for the last 5 yrs which have great security - safe from anywhere in the world, if ssh-keys are used.

Being new to Ubuntu, probably means a guide could be used: [http://ubuntuguide.org/](http://ubuntuguide.org/) 
Hope this sends you in the right direction.

I am looking into xrdp now and it looks like I may be able to use it for our needs. I appreciate your reply. I still have a lot to learn!

Thanks!

---

### Post by TheFu on 2014-08-07
> **CoolnessInc said:**
> I am looking into xrdp now and it looks like I may be able to use it for our needs. I appreciate your reply. I still have a lot to learn!

Thanks!

Me too!  I've only been doing UNIX/Linux stuff since 1993 and there is just too much more to know!

If you have more than a few users, you'll probably want to connect their Linux userids to the AD server via LDAP. From my little bit of reading on this, it is easiest if you are the domain admin in Windows.  Wish I knew more, but we are Microsoft-free at my job.

---

