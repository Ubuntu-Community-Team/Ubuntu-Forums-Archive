---
title: "Linux sa Negosyo"
date: 2008-09-16
forum: Philippine Team
---

### Post by mitchi on 2008-09-16
Hi Ubuntu enthusiasts!

I really need support/help on implementing Ubuntu on a Small Business setup. Some of our guys here in the forums has already implemented this by putting up Internet Cafes. The forum is a great support for all of us, from installation, design, usage, etc.,

I also am planning to put up a Small Business and thinking on how to fully maximize the system. I am pleading to all of guys here in the forums if you could share, even a bit of knowledge on how to setup a simple Ubuntu computer network to compete with our M$ counterpart.

Several topics that needs attention would be the following:

    * File Sharing
    * Printer Sharing
    * Remote Desktop Access
    * Setting up an Intranet


I am willing to compile a manual basing on the contents that you would share on this thread. Other topics suggested would be greatly appreciated. I am digging into the forum archives for other topics.

---

### Post by loell on 2008-09-16
file/print shares is all about **samba** :)

heres one of the less cryptic howtos i've found

[http://www.jonathanmoeller.com/screed/?p=181]("http://www.jonathanmoeller.com/screed/?p=181")

for remote access

[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop]("http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop")

---

### Post by Nhatz on 2008-09-16
Yup tama so loell...hehehe :)
File/Print Sharing = Samba (madali lang i-configure)
Remote Desktop Sharing = VNC

ASTIG! :guitar:

---

### Post by kikoman on 2008-09-17
File Sharing
Printer Sharing

[http://ubuntuforums.org/showthread.php?t=804379&highlight=samba](http://ubuntuforums.org/showthread.php?t=804379&highlight=samba)

What business are you planning? Internet cafe?

I would also suggest you to go to Software Freedom Day in Makati, they will tackle opensource in business over there including foss for internet cafe.

---

### Post by wilper on 2008-09-17
File print sharing = Samba punta kalang sa Add-remove meron na dun application. be sure na naka check yung list sa source-package para mag download sya sa ubuntu repository.
Internet sharing = MAg install ka ng Squid mag lagay ka ng isang server. madali lang configure
[www.squid-cache.org](www.squid-cache.org)
kung sa mga games naman try mo yung WINE. meron na din ito sa add-remove sa ubuntu

---

