---
title: "Is there a recommended anti-virus for Ubuntu"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by camino3701 on 2008-07-28
I would like to know if there is a recommended anti-virus program for Ubuntu.
Thank you,
RLB

---

### Post by falcon61102 on 2008-07-28
While there really isn't a large need for an anti-virus in linux, you can use ClamAV.  It's simple, yet powerful and updated often.

---

### Post by ajmorris on 2008-07-28
> **camino3701 said:**
> I would like to know if there is a recommended anti-virus program for Ubuntu.
Thank you,
RLB
 
Hi there,
you do not particularly need an antivirus in linux. There is about one known virus out there, and virus scanning in linux will more often than not just produce false positives. If you would like an antivirus, it is probably best to go with avg:
[https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)
 
Also, more info on linux antivirus here:
[https://help.ubuntu.com/community/Antivirus/](https://help.ubuntu.com/community/Antivirus/)
 
AJ

---

### Post by ramjet_1953 on 2008-07-28
It depends upon what files you want to scan.

As far as I know, there is no Linux native virus scanner.

The anti-virus software available for Linux is for scanning Windows files, searching for Windows viruses.

Unless you are forwarding-on emails, with Windows executables, and attachments to Windows users, relax and enjoy the world of Linux.

Regards,
Roger :cool:

---

### Post by BLTicklemonster on 2008-07-28
While it's true that you probably won't need to worry about viruses in Linux, if you get an email with a virus in it, and accidentally forward it to someone, then it would have been a good idea to have some antivirus protection running that could catch a virus in an email and alert you so you don't unwittingly spread stuff.

Otherwise, just sit back and enjoy the view. 

Oh, and only use trusted repositories.

---

### Post by BGFG on 2008-07-28
I've heard that AVG is not really that great. You could try avast, or the linux native ClamAV.
For avast you'll have to visit their website:

[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

I'd say your best be would be between these two.

---

### Post by crjackson on 2008-07-28
> **camino3701 said:**
> I would like to know if there is a recommended anti-virus program for Ubuntu.
Thank you,
RLB

```
sudo apt-get install clamtk
```

Clam does scan for the approx. 50 dead Linux virus' that are no onger alive in the wild.  It's a fair scanner for scanning hpfs drives that are shared with a windows system.

Clamtk won't really help much if you run a Linux only system and don't share any windows junk. Linux IS your best anti-virus in it's self.

---

### Post by dietkinnie on 2008-07-28
> **crjackson said:**
> ```
sudo apt-get install clamtk
```

Clam does scan for the approx. 50 dead Linux virus' that are no onger alive in the wild.  It's a fair scanner for scanning hpfs drives that are shared with a windows system.

Clamtk won't really help much if you run a Linux only system and don't share any windows junk. Linux IS your best anti-virus in it's self.

I agree "Linux IS your best anti-virus in it's self."

---

### Post by oldsoundguy on 2008-07-28
F-Prot .. it is free for Linux. .. really not needed though unless you install your own virus .. it's all about permissions!

---

### Post by camino3701 on 2008-07-28
Thank You everyone for your help I am just installing Ubuntu on my extra computer and have been using Windows so long that I assumed I needed an anti-virus both avg and avast don't list an anti-virus for Limux

Thanks Again,
RLB

---

### Post by BGFG on 2008-07-28
Well for those who use torrents and file sharing, i know that windows viruses don't affect Linux systems but for me it's not even about passing viruses on to windows users. I just don't like the idea of any virus at all in my system. So i keep clamAV and avast at hand.

---

