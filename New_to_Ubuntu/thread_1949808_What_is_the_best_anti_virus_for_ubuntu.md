---
title: "What is the best anti virus for ubuntu?"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by shotgun sam on 2012-03-31
Was also wondering about the security aspects of ubuntu 11.10 ....it will need some form of anti virus if so which is the best?

---

### Post by tehchibipanda on 2012-03-31
Here you go: 

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by zombifier25 on 2012-03-31
You don't really need an antivirus, but if you do, just use ClamAV. You don't need to download it manually from the website, and it works well.
Some Windows antivirus (like Bit Defender, avast!, AVG) has a Linux version, and they scan files using the same database as the Windows one. So, your mileage may vary. However, some of them appears outdated.
So, Clam all the way.

---

### Post by codemaniac on 2012-03-31
+1 for clamAv .Completely open source, ClamAV is probably the most famous Linux anti-virus. Using it requires some command line knowledge, but there is a basic GUI for running scans:

---

### Post by jerome1232 on 2012-03-31
Honestly antivirus won't do much to keep your linux OS safe and clean, there are currently zero known viruses out in the wild that can infect a linux computer, which is all these antivirus programs can protect against (known threats)

See this sticky in the security section for an idea about the linux approach to security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by codemaniac on 2012-03-31
Windows Viruses wont affect the linux system , but it can serve as carrier for windows viruses

---

### Post by whatthefunk on 2012-03-31
Smart user habits are the best anti-virus.  Tweak your internet browser to block unwanted content.  Think before you click on suspicious links.  Be careful when transfering files from other PCs.  Run a root kit hunter program every now and again. 

Ive been using Linux for a year and a half with no problem at all and I have no anti-virus program.

---

### Post by 1clue on 2012-03-31
> **whatthefunk said:**
> Smart user habits are the best anti-virus.  Tweak your internet browser to block unwanted content.  Think before you click on suspicious links.  Be careful when transfering files from other PCs.  Run a root kit hunter program every now and again. 

Ive been using Linux for a year and a half with no problem at all and I have no anti-virus program.

+1.

Also, start here:  wiki.ubuntu.com/BasicSecurity

No matter how many people insist you don't need to worry about viruses or security, you really do because not educating yourself about it will only get you owned.  It's amazingly easy to do something really stupid that compromises your system, and also not really hard at all to keep your system relatively safe just by being educated and using your head.

---

### Post by haqking on 2012-03-31
> **1clue said:**
> +1.

Also, start here:  **wiki.ubuntu.com/BasicSecurity**



[http://wiki.ubuntu.com/BasicSecurity](http://wiki.ubuntu.com/BasicSecurity)

fixed that for you ;-)

---

### Post by codemaniac on 2012-03-31
whatthefunk,completely agree with you .

---

### Post by 1clue on 2012-03-31
> **haqking said:**
> [http://wiki.ubuntu.com/BasicSecurity](http://wiki.ubuntu.com/BasicSecurity)

fixed that for you ;-)

Thanks!  :)

> **whatthefunk said:**
> Smart user habits are the best anti-virus.

BTW, this applies to absolutely any computing platform.

---

### Post by shotgun sam on 2012-03-31
So how do I go about installing clam and the clam gui?

And how can I make sure the firewall is running ? I take it that there is no one place where you can go and see to all is in the settings.

---

### Post by haqking on 2012-03-31
> **shotgun sam said:**
> So how do I go about installing clam and the clam gui?

And how can I make sure the firewall is running ? I take it that there is no one place where you can go and see to all is in the settings.

clam should be in the software centre

and read here about firewall and setup 

[Dangertux 3 methods for installing firewall]("http://ubuntuforums.org/showthread.php?t=1876124")

---

### Post by aysiu on 2012-03-31
[Security](http://ubuntuforums.org/showthread.php?t=510812) is great, but so-called "antivirus" doesn't really provide any security.

---

### Post by Hirobian on 2012-03-31
Is that ClamAV or KlamAV? (View attached image for screen-shot)

---

### Post by haqking on 2012-03-31
> **Hirobian said:**
> Is that ClamAV or KlamAV? (View attached image for screen-shot)

klamav still uses the clamav engine it is just a KDE front end [http://sourceforge.net/projects/klamav/](http://sourceforge.net/projects/klamav/)

Peace

---

### Post by lisati on 2012-03-31
> **aysiu said:**
> [Security](http://ubuntuforums.org/showthread.php?t=510812) is great, but so-called "antivirus" doesn't really provide any security.

This is something that's easily missed. AV tools are just that, tools, and are a poor substitute for sensible habits.

---

### Post by Hirobian on 2012-03-31
> **haqking said:**
> klamav still uses the clamav engine it is just a KDE front end [http://sourceforge.net/projects/klamav/](http://sourceforge.net/projects/klamav/)

Peace

Thanks for the clarification.

---

### Post by Krytarik on 2012-03-31
> **Hirobian said:**
> Is that ClamAV or KlamAV? (View attached image for screen-shot)
> **haqking said:**
> klamav still uses the clamav engine it is just a KDE front end
For Gnome, choose its GTK+ front-end, "ClamTk", the first item in your search results list, with that colorful icon. :P

Regards.

---

### Post by shotgun sam on 2012-03-31
I think I installed it properly from the website of clam av although it says the antivirus engine is outdated....I haven't been able to scan the whole system with it yet as it is a bit difficult to use...  I have enabled my firewall and downloaded a GUI for it however I notice I have no rules for the firewall yet I have to add these manually myself I am assuming?  I am gonna add the NOSCRIPT  add on to the firefoz browser ....so on a scale of one to ten how secure would you say I am right now?

---

### Post by 1clue on 2012-03-31
> **shotgun sam said:**
> So how do I go about installing clam and the clam gui?

And how can I make sure the firewall is running ? I take it that there is no one place where you can go and see to all is in the settings.

Your questions have been answered so far so my post is not quite related, but I would START by making sure you have Internet appliances for your ISP connection and router, with sensible settings on those.  Meaning your cable modem and whatever router you use.

Having an external appliance that handles a firewall doesn't obviate the need for security, it just adds one surprisingly good layer of security, assuming you have sensible settings.  It just makes it that much harder for someone to get into where you keep the good stuff.

---

### Post by HiImTye on 2012-04-01
generally speaking, you should only scan your folders you share with windows machines (or just your home folder) as ClamAV (and other viri scanners) have been known to cause problems doing full system scans. I use a bash script to scan the folders I want scanned
```

#!/bin/bash
clamscan -r -l scan.log /storage/Videos /storage/Music /storage/Pictures /storage/Windows
exit $?
```

---

### Post by Hirobian on 2012-04-01
> **Krytarik said:**
> For Gnome, choose its GTK+ front-end, "ClamTk", the first item in your search results list, with that colorful icon. :P

Regards.
Thank you as well Krytarik.

---

