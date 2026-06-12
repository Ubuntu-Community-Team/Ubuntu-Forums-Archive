---
title: "Help in suggesting OSS to employer...."
date: 2008-05-12
forum: Other OS Talk
---

### Post by linuxaz on 2008-05-12
Hello,
I work at an architectural millwork company in the US with a small IT budget.  In the near future, we will be facing severe upgrade costs for our server (server 2000) and software.  I have suggested to the *sudo* IT guy here that OSS could very easily replace our Exchange, and File Server needs.  Other OS functions would not be easily replaced by OSS such as MAS 90, Microvellum, and Autocad 2008.  Therefore, any implementation would have to support MS networking, and domain authentication as well.

I'm an avid user of Ubuntu and SuSe, and could talk till I'm blue in the face about why I think OSS could save the company money, but I'm not always the best at getting the point across.  If anyone could point me to some comparison, review, or other data to assist in this cause, I would greatly appreciate it.

regards,

linuxaz

---

### Post by darrelljon on 2008-05-12
I'm in the same situation. Have a look at [this article]("http://www.desktoplinux.com/articles/AT7506682379.html").

---

### Post by dca on 2008-05-12
Good luck on the Exchange part...  Sometimes people get spoiled because in all honesty (EXPENSIVE AS HELL) it is a good solution.  If you have your clients on cached exchange mode, the emails stay on the secure server where as any other solution you would have to create some kind of email storage repository that can be accessed from possibly anywhere (a'la Exchange's web app).  
 
In those terms if you (yourself) don't have the capability to support/manage/troubleshoot/install FOSS than it may be easier for them to bite the bullet and go w/ MS...  Be sure to find out what OS the current property management system, billing/invoice system, etc runs on...

---

### Post by Midwest-Linux on 2008-05-12
Show them the savings in money in a chart. Money always causes management and IT to take another look. Cost of the program, associated license fees surrounding it like client access licenses, enterprise license fees. 

Service costs, service contracts,uptime/downtime costs, percentage of savings in one year, three years, five years. You have to speak money in "their" terms, then they will listen.

---

### Post by linuxaz on 2008-05-13
DCA,
The accounting solutions run on the Redmond OS only I'm afraid.  It's MAS 90 from Sage software.....and a real piece of work.  I understand from the support tech for it, that it's actually based on old Unix code, but has been ported to DOS years ago.  It's very clunky and patched software.


The interesting thing about Exchange here is that we do not use it for much except email delivery locally and WAN.  The global address book is almost useless, all emails are stored on the local machines.  the web interface is nice on the rare occasion that people need to access their mail via web browser.

I have looked at OpenXchange and Zimbra.  Both seem to actually offer more features.

Right now the server runs Windows Server 2K SBA, and it comes with Exchange.  There are compatibility issues with that version and vista.  and, unfortunately, eventually we will run some type of vista on the office client machines.
I really think they could save money and move file sharing and email off to an OSS powered server.

linuxaz

Thanks for the information.

---

### Post by dca on 2008-05-13
Well then it looks like you can get it all done w/ two new servers, plus a back-up possibly tape solution.  One primary server, the second for back-up/failover (hardware versus HDD issues) in case of primary failure, and the tape archive.  The key points when it comes to business is not necessarily FOSS vs Windows (obviously it's too small to consider mainframe HP-UX, AIX, etc), it's more availability.  Which total platform will give them total availability and up-time.  Buying new gear can help as far as virtualizing.  One host will run the ol' timey OS, the other will run Linux for email/MTA, etc, etc.  The nice thing about VM is only the 'Virtual Machines' directory from each will need to be archived...  I dunno', matter of preference I guess...

---

