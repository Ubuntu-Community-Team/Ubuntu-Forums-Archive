---
title: "[SOLVED] Fix Screen Resolution"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by brucenduane on 2008-10-18
I have a Toshiba Satellite A205-S5805 laptop with 2 Gig of Memory

The laptop specs are at this website:
[http://74.125.45.104/search?q=cache:8Ztu0ULRrycJ:www.electronicsme.com/pdfs/product/pdf_2779.PDF+toshiba+satellite+A205-S5805+LCD&hl=en&ct=clnk&cd=18&gl=us&lr=lang_en](http://74.125.45.104/search?q=cache:8Ztu0ULRrycJ:www.electronicsme.com/pdfs/product/pdf_2779.PDF+toshiba+satellite+A205-S5805+LCD&hl=en&ct=clnk&cd=18&gl=us&lr=lang_en)

The LCD screen is 1280x800

I have just installed Ubuntu 8.04 on the hard drive in a 35 GB partition
/dev/sda3 with a 2 GB swap as /dev/sda4

The screen resolution is 1280x800 in this new install.  The xorg.conf
only has the default screen of 1280x800.

I have a 160GB Western Digital USB Drive with Ubuntu 8.04 installed
in /dev/sdb2 which I installed on 9/15/2008.  I had a screen resolution
of 1280x800 until I did the package update yesterday with included a new
version of gdm, dbus, dbus-X11 and libraries.  A total of 74 packages
got updated.

When I rebooted the screen resolution switched to 800x640 and after several reboots it increased to 1024x768 max at 61 hz

The selections are 1024x768 at 61Hz or 800x600 or 640x480.

Question:
How do I get back to 1280x800 without reinstalling Ubuntu from scratch?
Why did the fonts and screen resolution change?

I have 4 Ubuntu 8.04.1 including one Ubuntu Studio version running on 
the hard disk and 2 USB drives.  The newly installed Ubuntu two hours ago are at 1280x800 plus the two copies that I have not updated since 9/27/2008.  Only the USB Drive copy I updated yesterday has had the screen resolution of 1024x768.

What do I do to add the detailed line to xorg.conf to add the screen resolution of 1280x800.  The other three lines have a bunch of numbers in it.

Thanks for your help.

---

### Post by Ryadt on 2008-10-18
First try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by brucenduane on 2008-10-18
Thanks Ryadt, that fixed it.

What caused it to change???????

And How do I add to your "Thank-you count" and mark this "Solved"?

---

