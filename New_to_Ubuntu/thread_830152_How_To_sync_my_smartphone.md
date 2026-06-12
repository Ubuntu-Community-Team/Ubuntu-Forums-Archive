---
title: "How To sync my smartphone?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by XTR0RDiNAiRE on 2008-06-15
with the help of some helpful members i now have photoshop workin
thx

now im tryin to sync my t mobile shadow 
i downloaded this program called multisync already
but my pc is not recognizing the usb ports

---

### Post by Stefanie on 2008-06-15
this site has all the information you need : [http://www.synce.org/moin/FrontPage](http://www.synce.org/moin/FrontPage) . let us know if you have a problem.

---

### Post by XTR0RDiNAiRE on 2008-06-15
wow

all this stuff is sooo complicated for  me

i have no idea what im doing 
just going from link to link to link
:confused:

---

### Post by Stefanie on 2008-06-16
Well, you can begin here [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)  . Follow all the instructions. After adding the repositories you have to paste the commands in the blue boxes into a terminal and hit enter after every line. it's not more difficult than that. 
when you have done that you follow the link to synce-setup. [http://www.synce.org/moin/SynceSetup/SyncEngine](http://www.synce.org/moin/SynceSetup/SyncEngine) 
you will have to open a terminal and run synce-sync-engine. it will hang on "installing signal handlers". this is normal, don't touch it and open a second terminal. in this second terminal you have to create a partnership with your phone. 
I tried to enable contact syncing, but it didn't work, so I only sync my calendar. i typed synce-create-partnership "Mypartnership" "Calendar" instead of synce-create-partnership "Linux desktop" "Contacts,Calendar". 

Then you follow the link to Opensync setup, [http://www.synce.org/moin/SynceSetup/OpenSync](http://www.synce.org/moin/SynceSetup/OpenSync) . Make sure synce-sync-engine is still running in the first terminal and enter the commands in the second terminal.

---

### Post by svet-am on 2009-01-07
does SynCE now work with the T-Mobile Shadow/HTC Juno?  I've search and there are lots of threads about this, but no one seems to have ever reported back a result/solution of their experiments.

---

