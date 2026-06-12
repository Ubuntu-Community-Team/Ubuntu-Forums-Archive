---
title: "Add My Ubuntu PC to Windows Domain"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by kolisikepu on 2008-07-02
Hi Community,

It has probably been asked before, but I can't find anything on it.

Can someone please tell me how to add my Ubuntu laptop to our work environment/domain.

In Windows, we do it by going to System Properties window > Computer Name Tab > Computer Name Changes > Workgroup/Domain.
Once I put in a domain name, it will ask to authenticate and then reboots when it is successful.

How do I do what I explained in Ubuntu so that my pc is part of the domain.  I'm also about to build my Ubuntu server and that too needs to be on my work domain.

Any help will be appreciated.

Regards,

Kepz

---

### Post by bab1 on 2008-07-02
Look up information on Samba and smbfs.  Linux does not natively support CIFS (windows file system).

Start here:[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by lazyart on 2008-07-02
Use [sadms]("http://sadms.sourceforge.net/").  I used it for my system and works like a champ.  After I joined it, I logged into my Gusty box using my wife's credentials (who has never used this machine) and it worked perfectly.  It sure makes file sharing easier.  In AD there is clearly an entry for my machine, with an "unknown" OS.

---

