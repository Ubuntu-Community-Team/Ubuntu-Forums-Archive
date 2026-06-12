---
title: "administrator rights on VirtualBox WinXP"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by UbunGax on 2011-09-30
Afternoon,

I'm pretty new to Ubuntu (11.04) and need to have XP installed so I can connect to work.
So, I installed Virtual Box and have Win XP client installed - all seems good.

However, when I try to load the Terminal service download through the XP client, I get an error:

RDP Client is not installed on your machine.  To install the RDP client you have to have administrator rights on your machine.

I am the only user in the XP environment, and am set up as an administrator.

Can anyone assist?

Cheers in advance

---

### Post by seawolf167 on 2011-09-30
> **UbunGax said:**
> RDP Client is not installed on your machine.  To install the RDP client you have to have administrator rights on your machine.

You need it to install, try going to Start -> Control Panel -> Add/Remove Programs -> Then click Add/Remove Windows Components -> Look for the RDP Service (Terminal Services)

Edit: [MS Knowledge Base link]("http://support.microsoft.com/kb/307894")
[Remote Desktop Download link]("http://www.microsoft.com/download/en/details.aspx?id=21075")

---

### Post by UbunGax on 2011-09-30
Cheers SeaWolf,

I hadn't thought to do that, so thanks.  However, in all the options but there was no option to install this.  I'm using XP - might it be something else?

Cheers

---

### Post by seawolf167 on 2011-09-30
Since you mentioned RDP Client, the applicable Windows XP links are here.

If you still cannot get it to work after following the below links I'd suggest taking it to a Windows forum to get Windows-specific help.

[http://www.microsoft.com/windowsxp/downloads/tools/rdclientdl.mspx](http://www.microsoft.com/windowsxp/downloads/tools/rdclientdl.mspx)

[http://support.microsoft.com/kb/969084](http://support.microsoft.com/kb/969084)

[http://support.microsoft.com/kb/925876](http://support.microsoft.com/kb/925876)

[http://www.microsoft.com/download/en/details.aspx?id=856](http://www.microsoft.com/download/en/details.aspx?id=856)

[http://support.microsoft.com/kb/284931](http://support.microsoft.com/kb/284931)

---

