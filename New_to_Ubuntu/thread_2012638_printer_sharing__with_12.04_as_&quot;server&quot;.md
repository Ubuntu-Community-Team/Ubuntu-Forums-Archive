---
title: "printer sharing  with 12.04 as &quot;server&quot;"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by lkjjr on 2012-06-29
Still relatively new to Linux/Ubuntu, but really glad I finally found an alternative like this.  I&#8217;m embracing this to the extent I now run a dual boot desktop (12.04 64 & XP pro64) and laptop (12.04 64 & Win7 pro64) with goal of getting rid of MS entirely.  I&#8217;ve had great success with integrating almost all of my needs with Linux apps and being able to share files and printer .  There&#8217;s one major hurdle I can&#8217;t seem to get over though&#8230;

 My 12.04 OSes can &#8220;see each other&#8221; and &#8220;see Windows&#8221; just fine across our home network.  But I can&#8217;t make the connection getting Windows to &#8220;see&#8221; Ubuntu to either share files or printer.  Because the printer is hardwired to the desktop this causes a significant problem.  My family has two other Windows machines on the network as well, and right now the only way we can share the printer is to have the desktop booted to XP.  So I want to get the desktop integrated running Ubuntu and serve the other machines for printing.

 After a good bit of research I'm thinking this probably a Samba related issue.  I've even installed Gadmin for Samba, but still can't seem to find the solution.  Any ideas/guidance would be greatly appreciated
 


 Thanks...

---

### Post by Gone fishing on 2012-06-29
Sorry if Im a little rusty but to share a printer, install the printer, in printer properties make sure its shared. On the Windows boxes will be able to use the printer. In windows "Add Printer" add a new network printer, select "Connect to a printer on the Internet..." and enter the URL for your printer for example [http://192.168.0.1:631/printers/PDF](http://192.168.0.1:631/printers/PDF). You can administer the printer by going to [http://localhost:631/](http://localhost:631/) in your browser. port 631 is the cups printer port.

For file sharing you will need samba - there is a graphical tool for configuring this in the software centre.

---

