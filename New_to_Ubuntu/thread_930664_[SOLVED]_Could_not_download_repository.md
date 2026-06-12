---
title: "[SOLVED] Could not download repository"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by swbrenton on 2008-09-26
I am a new beginner, having installed Ubuntu 6.10 1 week ago.
I'm having problems.
From the Gnome menu bar, I select 
System > Administration > Synaptic Package Manager
password > OK
Click Reload from menu bar
then this message box appears:

I have removed some of the comments from /etc/apt/sources.list but still get the same results.
P.S.  I also found out that System > Administration > Software Sources will modify the sources.list file.  Hmmmm.

What should I do?
Stephen.

---

### Post by perlluver on 2008-09-26
> **swbrenton said:**
> I am a new beginner, having installed Ubuntu 6.10 1 week ago.
I'm having problems.
From the Gnome menu bar, I select 
System > Administration > Synaptic Package Manager
password > OK
Click Reload from menu bar
then this message box appears:

I have removed some of the comments from /etc/apt/sources.list but still get the same results.
P.S.  I also found out that System > Administration > Software Sources will modify the sources.list file.  Hmmmm.

What should I do?
Stephen.

6.10 Edgy, is no longer receiving updates, that is one of the reasons, that those sources won't download.  Any reason why you didn't install 7.10 or later?

---

### Post by Elfy on 2008-09-26
I believe that support for 6.10ended a while ago - the newest version is 8.04.1 - 8.10 due in October.

Why did you install that particular version?

Edit - that'll be 'snap' then :)

You can get the newest version from [here]("http://www.ubuntu.com/getubuntu") if you wanted to use a torrent to download that can be got [here]("http://releases.ubuntu.com/8.04/")

---

### Post by swbrenton on 2008-09-26
> **perlluver said:**
>  Any reason why you didn't install 7.10 or later?

The 6.10 CD was included in the book Ubuntu Linux for Dummies that I bought about 2 weeks ago.  I used that CD to install Ubuntu onto a Dell laptop.  (And I read the book.)

After I installed it I got more confidence and downloaded the 8.04 ISO file to my desktop computer(HP), burned the CD and installed 8.04 to the desktop.  No problems.

I then took the 8.04 CD and tried to do a fresh install to the laptop but the CD just ran, and ran, and ran.  (It would bootup 'Live')

So I just reinstalled the 6.10 on the laptop.

I don't have 7.10 CD.  Nor a 6.10LTS CD.  :(

Now what?

---

### Post by Elfy on 2008-09-26
What specs on the laptop - memory particularly. If it booted up live then you needed to install it from there.

---

### Post by swbrenton on 2008-09-26
> **forestpixie said:**
> What specs on the laptop - memory particularly 

Specs:
Dell Latitude C610
1.2-GHz/733-MHz Pentium III-M CPU, 256MB of SDRAM, 512KB L2 cache, 14.1-inch active-matrix screen, ATI Radeon Mobility graphics with 16MB of DDR SDRAM, 20GB hard drive.


> **forestpixie said:**
> If it booted up live then you needed to install it from there.

Maybe I wasn't clear.  The 6.10 and the 8.04 CD both bootup live.  The 8.04 CD would not install, even after live bootup.

Is there anything I can do to allow downloading repositories?

---

### Post by Elfy on 2008-09-26
You could download the alternate installer - it should run with 256Mb RAM.

Alternatively install [xubuntu]("http://www.xubuntu.org/get")

---

### Post by semitone36 on 2008-09-26
Its also possible that the 8.04 didnt burn correctly.  That happened to me once.  Try burning another iso for Hardy and seeing if that will work

---

### Post by snowpine on 2008-09-26
384mb is the minimum to install Ubuntu 8.04 from the Live CD. The Alternate CD should work fine with 256mb as forestpixie mentioned. Another option is to try Xubuntu, which is a little bit lighter. Good luck!

---

### Post by swbrenton on 2008-09-26
> **forestpixie said:**
> You could download the alternate installer

What is the alternate installer?

Is there anyway I can download repositories for 6.10?

---

### Post by swbrenton on 2008-09-26
> **snowpine said:**
> The Alternate CD should work fine with 256mb

What is the Alternate CD?
Where do I get it?

> **snowpine said:**
> Another option is to try Xubuntu, which is a little bit lighter. Good luck!

I may go this route if I cannot download repositories to make updates/upgrades from 6.10.  Thanks.

---

### Post by snowpine on 2008-09-26
> **swbrenton said:**
> What is the Alternate CD?
Where do I get it?



I may go this route if I cannot download repositories to make updates/upgrades from 6.10.  Thanks.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

There's a check box " Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

---

### Post by Elfy on 2008-09-26
You can get the alternate installer from [here]("http://www.ubuntu.com/getubuntu/download") - you need to check the little box just below the green  Start Download button.

You might well be better of with xubuntu.

---

### Post by swbrenton on 2008-09-26
OK. I found the check box and downloaded the alternate copy of Ubuntu.  But I thought it would be better to see what Xubuntu has to offer so I installed it onto it's own partition.  After installation,it prompted me to make updates and that woked well also.   So now this laptop's running Xubuntu 8.04.

How was I ever supposed to know I needed 384mb of RAM?  Where should I have found that?

Thanks for the help, forestpixie and snowpine.
Stephen.

---

### Post by Elfy on 2008-09-27
[http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition) at the bottom system requirements

Glad you're sorted. Good luck

---

