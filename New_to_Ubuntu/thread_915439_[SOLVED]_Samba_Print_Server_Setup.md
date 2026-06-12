---
title: "[SOLVED] Samba Print Server Setup"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by 44tr on 2008-09-09
Hi.  I have an HP color laser printer connected locally by USB to my computer now running Ubuntu (dual boot with XP).  In XP I share the printer on my home network so the other computers in the house can print to it.

How do I configure samba to make that happen when I am running Ubuntu?  This is key to my getting to spend more time in Ubuntu since my kids constantly need to print school work.

Thanks in advance.

P.S.  I am not COMPLETE newbie, but almost as far as GNU/Linux is concerned :)

---

### Post by ayenack on 2008-09-09
1, System>Administration>Printing
2, Server Settings
3, Click Share Published printers connected to this System
4, Apply
6, Click on Local Printers then highlight your printer
7. Click on Policies tab
8, Make sure that it's Enabled, Accepting Jobs, Shared

That should do it. You might need to reboot. It's also a good idea to enable letting anyone cancel any job.

---

### Post by 44tr on 2008-09-10
Unfortunately, that doesn't do it.  An Ubuntu computer on my network seems to see the printer but can't verify or use it.  A Windows XP computer on my network doesn't detect it at all (though when I boot the computer with the printer to Windows, the other Windows computer sees it and installs it no problem).  I'm stumped.

---

### Post by ayenack on 2008-09-11
OK with the Ubuntu comps you may need to set them so they see other shared computers on the network so you would go into the printer settings and select Server Setting and highlight Show Printers Shared by Other Systems. Reboot and see if that bring it up.

With the windows comps take a look at this it should guide you through and let you print to whatever you want.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by 44tr on 2008-09-13
> **ayenack said:**
> OK with the Ubuntu comps you may need to set them so they see other shared computers on the network so you would go into the printer settings and select Server Setting and highlight Show Printers Shared by Other Systems. Reboot and see if that bring it up.

With the windows comps take a look at this it should guide you through and let you print to whatever you want.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

Thanks for the link.  I finally got the Ubuntu computer in my son's room to print to my office printer.  Yeah! :biggrin:

I still can't get the Windows XP computer to print, but it may be a problem with the computer.  I can't get it to upgrade to Service Pack 3 either; something about registry keys that have access denied.  How does that happen?  Oh well, this may take a while.

---

### Post by 44tr on 2008-09-13
My Windows XP computers are printing!  :guitar:

The problem was with the driver.  I picked a more generic driver and it is working fine.  I don't know if that means I will lose some printer specific features, but for the time being, it is doing what I need.  Thanks.

---

