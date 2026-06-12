---
title: "Do I need PAE for Ubuntu 10.04?"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by caraj on 2013-06-25
My Dell Latitude D600 gives me the message "this kernel requires the following features not present on the CPU: pae".
A possible solution I found was installing 10.04 and upgrading it to 12.04 once I did.
I would just install it over the internet now, but my HD is blank.

---

### Post by Cheesemill on 2013-06-25
You can use the 12.04 non-PAE mini CD to do the installation if this machine has an internet connection.

[32-bit non-PAE 12.04 Mini CD]("http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-i386/current/images/netboot/non-pae/mini.iso")

---

### Post by caraj on 2013-06-25
If it can't boot I don't think I could use internet on it.

---

### Post by Cheesemill on 2013-06-25
You boot from the mini CD and then this connects to the internet to download the rest of the packages needed for installation.

When I said 'if the machine has an internet connection' I meant 'if the machine is capable of an internet connection'.

---

### Post by kurt18947 on 2013-06-25
You could check on Xubuntu or Lubuntu 12.04.  The 32 bit version of Xubuntu does not require PAE and neither does Lubuntu.  If you wanted gnome-shell or Unity, you could install those after installing X or L ubuntu.  It sounds like Xubuntu  will not offer a non-PAE version after 12.04.  Lubuntu is continuing to offer a non PAE 32 bit 13.04 so there are ways to work around the non-PAE issue.  Looking at the specs for the D600, it looks like it might be happier with Xubuntu or Lubuntu anyway.  Those distros often have better support for older machines than Ubuntu/Unity or Gnome-Shell and they're less demanding of resources.

---

### Post by newb85 on 2013-06-25
Really good instructions for Cheesemill's suggestion are here:
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

---

### Post by caraj on 2013-06-25
> **kurt18947 said:**
> You could check on Xubuntu or Lubuntu 12.04.  The 32 bit version of Xubuntu does not require PAE and neither does Lubuntu.  If you wanted gnome-shell or Unity, you could install those after installing X or L ubuntu.  It sounds like Xubuntu  will not offer a non-PAE version after 12.04.  Lubuntu is continuing to offer a non PAE 32 bit 13.04 so there are ways to work around the non-PAE issue.Could I upgrade to Ubuntu 12.04 while running Xubuntu or Lubuntu without an install CD?

---

### Post by Cheesemill on 2013-06-25
You could, but it would take a very long time and there is always the possibility that it won't work.

It would be much easier and quicker to install Ubuntu 12.04 from the beginning using the method I outlined above.

---

### Post by Cheesemill on 2013-06-25
You could, but it would take a very long time and there is always the possibility that it won't work.

It would be much easier and quicker to install Ubuntu 12.04 from the beginning using the method I outlined above.

---

### Post by sanderj on 2013-06-26
> **caraj said:**
> My Dell Latitude D600 gives me the message "this kernel requires the following features not present on the CPU: pae".
A possible solution I found was installing 10.04 and upgrading it to 12.04 once I did.
I would just install it over the internet now, but my HD is blank.

How much RAM does your Dell Latitude D600 have? If it's low (512MB, 1GB), it is useless to install Ubuntu 12.04: Ubuntu 12.04 is resource hungry, both in RAM and CPU.

---

### Post by newb85 on 2013-06-26
I wouldn't call it resource hungry, but compared to the stock specs of the D600 (1.6GHz single-core, 128MB RAM), it's a raging beast.  Unless someone did some major hardware upgrading, or unless you're an extremely patient person, you need to switch to something lighter, like Lubuntu.  Actually, Ubuntu 12.04 won't run on less than 512MB.

---

### Post by mörgæs on 2013-06-26
> **kurt18947 said:**
> Lubuntu is continuing to offer a non PAE 32 bit 13.04

No, 12.04 was the last.

> **kurt18947 said:**
>  so there are ways to work around the non-PAE issue. 

Yes, here's a guide:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by Rob Sayer on 2013-06-26
> **sanderj said:**
> How much RAM does your Dell Latitude D600 have? If it's low (512MB, 1GB), it is useless to install Ubuntu 12.04: Ubuntu 12.04 is resource hungry, both in RAM and CPU.

That's what I was thinking too.  I checked and some early versions had 128Mb.

I run kubuntu (KDE desktop) on a 1Gb netbook.  I'd never install ubuntu with the unity desktop on it.  I have an i3 based 4Gb netbook and I consider ubuntu (unity) too slow on that.

If xubuntu and lubuntu have a 32 bit non pae kernel version install I'd definitely install one of them.  Probably lubuntu if it's a 512Gb RAM computer.

Please note: you will have to install version 12.04.  According to what I just looked up, both xubuntu and lubuntu have dropped non-pae kernel support in 12.10 and later versions.  12.04 is the long term service version - it's supported until 2017 so that shouldn't be a problem.

This is from [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) ...

"We have done many tests and we've found out that  Lubuntu can be installed on a Pentium II or Celeron system with 128 MB  of RAM, but such a system would not perform well enough for daily use.

With 256MB - 384MB of RAM, the performance will be better and the system will be more usable. 


With 512MB of RAM, you don't need to worry much. 


The  default "Desktop" installer requires 384-800 MB of RAM (depending on  selected options.)  If you have problems, please use the "Alternate"  installer."

---

### Post by mörgæs on 2013-06-26
> **Rob Sayer said:**
> 
Please note: you will have to install version 12.04.  According to what I just looked up, both xubuntu and lubuntu have dropped non-pae kernel support in 12.10 and later versions.  12.04 is the long term service version - it's supported until 2017 so that shouldn't be a problem.



Everybody, please post only information that you are absolutely sure about.

Lubuntu has no long time support and for Xubuntu long time support means three years, that is until april 2015 for 12.04. A spin-off from Lubuntu 12.04 called LXLE is approaching long-time support, but it is not official. 

My recommendation is Lubuntu 13.04 using the workaround I posted above.

---

### Post by OrangeCrate on 2013-06-26
> **mörgæs said:**
> **Everybody, please post only information that you are absolutely sure about.**

Lubuntu has no long time support and for Xubuntu long time support means three years, that is until april 2015 for 12.04. A spin-off from Lubuntu 12.04 called LXLE is approaching long-time support, but it is not official. 

My recommendation is Lubuntu 13.04 using the workaround I posted above.


A big part of moderating a technical forum, is to correct a post or thread, when opinions are potentially being posted as fact. It seems a lot of this type of monitoring has been missing in recent times here on the forums, and misinformation has been left to stand as gospel, so to speak. It's refreshing to see posts such as yours here. Good job!

---

### Post by mörgæs on 2013-06-26
Thanks, but everyone is free to post and correct mistakes. Sometimes even mods go offline :-)

---

### Post by OrangeCrate on 2013-06-26
> **mörgæs said:**
> Thanks, but everyone is free to post and correct mistakes. **Sometimes even mods go offline** :-)

That certainly wasn't my experience.

After I woke up one morning, and found myself indentured to a set of forums, I was doomed to a life of Mountain Dew, Hot Pockets, an ankle tether, and an always on connection. It took me several years to plan and execute my escape...

:)

---

