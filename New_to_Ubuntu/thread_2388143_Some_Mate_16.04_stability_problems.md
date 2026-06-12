---
title: "Some Mate 16.04 stability problems"
date: 2018-03-29
forum: New to Ubuntu
---

### Post by bobsone on 2018-03-29
We have a Lenovo Ideapad 310-151K  8GB ram, 128GB SSD, a 1TB HDD and I5-7200U.  It is dual boot win10 and Mate 16.04.3 (kernel 4.13.0-32).  We have installed Mate and windows on the SSD with the windows storage and Mate home folder sharing the HDD.
   
  We have installed a number of (non Software Boutique) programs including Zotero (5.0.38) and Master PDF Editor (4.3.89 free version).  Unfortunately we are experiencing some stability issues with the most problematic being that Master PDF Editor occasionally crashes, Libre Writer often crashes when running Zotero and the Software Updater (i.e. System>Administrator>Software Updater) results in the following message &#8220;Failed To Download Repository Information&#8221; but it then updates successfully when I click OK (sudo apt-get update appears to work).
   
  Any tips to diagnose/resolve the issues are welcomed.  

Regards

---

### Post by oldrocker99 on 2018-03-29
Zotero is not in the Ubuntu repositories, except for a Unity scope, and I have no idea if that will work for MATE. Libre Office is darn stable, and Zotero may not play nicely with it. 

That is about all I can tell you.

---

### Post by cruzer001 on 2018-03-29
I use Zotero (5.0.35) as a webpage collector for offline reading so the Libre plugin is not necessary for me.

I do have it running on different computers using win10, ubuntu, mate and lubuntu without any issues, but again no libre plugin.  I would suggest posting in the zotero site forum, they have been very helpful in the pass with me.  If you don't find any answers there, I would be glad to add libre writer and pdf editor to mine and see what happens.  I have a copy in a VM that I can play with.  But I would try the zotero site first.

---

### Post by bobsone on 2018-04-03
Thanks for the replies 
  I have loaded a few things that are not in the Ubuntu repositories (including Zotero, Master PDF, Cherry Tree, Recoll) and most are working well.  The web searches I made indicated they work well (people are happy with them) in Ubuntu (and Mate).  Also, because this is my first attempt with all things Ubuntu and I have a number of small(ish) problems including the odd Software Updater behaviour I suspect the issues are self inflicted. 

   
  I think I might spend the next month(ish) attempting to identify any problems/errors and then reinstall (_again_ :() when the upgrade is released.  If anyone has some diagnostic suggestions I would like to try them.  I did find a Master-PDF-Editor error log, unfortunately I can&#8217;t make sense of it (and it is huge).

   
  I will also ask the Libre Office people for their ideas.  In my limited/short experience I have to agree with the statement &#8220;*[FONT=&quot]Libre Office is darn stable...[/FONT]*&#8221;.  I am impressed with what I have seen and I can vouch for their crash recovery, whenever it has fallen over it recovers all data up to the moment of the failure :).

   
  Regards

---

