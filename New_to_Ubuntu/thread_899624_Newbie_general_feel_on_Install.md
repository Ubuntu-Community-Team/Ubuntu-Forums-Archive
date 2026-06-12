---
title: "Newbie general feel on Install"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by squirrelpie on 2008-08-24
As an older amateur,semi pro tech from the pre dos days, through all the windows iterations I provide support to a lot of seniors and my level of disgust with MS finally reached the breaking point with Vista. Haven't had a lot of Mac experience as I simply don't run into a lot of them particularly at the price break range most consumers buy at- laptops in the 5-700 range.
A whole other bunch of issues are involved, but decided to investigate Linux as a Windows alternative- email, internet, some office apps, low level picture utility, and play music, photoshows.
I did all this on W2K and XP using Picasa, Gmail, Firefox, Works, Nero, and O Office and the various Media Players using AVG for security. It worked.
Have been installing and playing with Linux Mint and Ubuntu Desktop for last month and finding my way around. I have been using older boxes with pIII or PV processors and either integrated and/or PCI/Eisa sound and video. I like what I am experiencing. A few issues:
a) Command line: I don't yet have a grasp on the finer points but will master them. Most consumers will not
b) The install is quick and slick with the auto multi boot menu. Wish there was a GUI to edit it.
c) Video Card issues: with NVidia Vanta and ATI Rage XL AGP 2X128 video I can't beyod 800x600 resolution although the dual boot Windows XP and Y2K installations will go well beyond that. Have not yet been able to solve that issue with ENVY.
d] Could not make ntegrated Sound work on PIV machine with any OS so expect that was a hdwe prob rather than a driver. PIII box has both Int and Eisa Creative AWE 64 boards. XP w2k will pick the EISA board while Linux will only pick the Integrated BOard. Having Int Sound enabled/disable in the BIOS does not seem to make a difference
e) Accessing Windows shares for other drives on other computers on my network works better, easier, and seemingly quicker under Linux than the same actions under windows. Only prob seems to be with Picasa under Linux. It does not seem to be able to navigate to other drives either on this box or on the network.Am I missing something simple there.
Otherwise really like these distros although I have something amiss with the Linux Mint and will probably do a clean download, burn and reinstall.
Read a lot of opinions on Linux with a general tone or feeling it is not for the non tech public. Well neither is Vista. I'm not so sure about Linux.
Wouls welcome your opinions Linux community. Thank yo

---

### Post by cwsnyder on 2008-08-24
First, have you looked at the 'net-tops', like the ASUS EEE series of laptop computers, many of which come with Linux installed?  These are available in your price range, and many are even more rugged than normal laptops because their main storage is flash memory.

Second, from c) above. search for information on the /etc/X11/xorg.conf file.  I have had problems with my nVidia card on a desktop showing greater than 800x600 without a custom xorg.conf file.  What was strange was that the 'live' disk would allow me to use the maximum resolution of my LCD display.

Third, sound card issues: The sound card and other drivers are usually built in to the kernel, and if the sound card manufacturer does not make the information available to the kernel people, you are probably stuck.  I have found that using the ALSA sound drivers is more likely to work than the default Pulse Audio driver (default for Ubuntu 7.10 and later).

Fourth, Picasa:  Picasa under Linux runs under WINE, and because of that, does not find any path names which are on any other drives.  Maybe when Google completely re-writes the program under GNU/Linux instead of running under WINE.  Try F-Spot to organize photos on another drive.

cwsnyder

---

### Post by rossjman1 on 2008-08-24
b) sudo apt-get install startupmanager

Should go into the testimonials forum.

---

### Post by squirrelpie on 2008-08-24
Thankyou cwsyder and rossjman1. Appreciate the tips and direction

---

