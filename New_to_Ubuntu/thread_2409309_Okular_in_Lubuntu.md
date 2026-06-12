---
title: "Okular in Lubuntu"
date: 2018-12-31
forum: New to Ubuntu
---

### Post by kesetyan on 2018-12-31
I have just set up a dual boot arrangement for Lubuntu on my Windows 7 desktop computer as part of my preparation for Microsoft ceasing support for Windows 7 in about 12 months time (I will then disable the internet on Windows 7).  The installation of Lubuntu went very well and was much more straightforward than I anticipated.  The next stage involved installing the applications I required, setting up my multi-function printer, enabling the UFW firewLL and and installing ClamTK.  

I wanted a PDF reader to replace Evince and opted for Okular which serves my purposes well.  However there is one puzzling thing I have noticed: when I look in /usr/share/applications, I find that there are multiple occurrences of the Okular icon.  I cannot delete the surplus icons and have tried uninstalling and reinstalling Okular with the same result. Okular works well without problems so this is not a problem for me but I am somewhat mystified so wondered if forum members with greater experience might enlighten me.

One other point, I would like to put an icon for the UFW firewall on the panel but, as yet, have not located the firewall's location.

Thanks and a very happy new year to all forum members.

---

### Post by CatKiller on 2018-12-31
> **kesetyan said:**
>  when I look in /usr/share/applications, I find that there are multiple occurrences of the Okular icon.  

Those are .desktop files: launchers for different functions. Nothing to worry about, and nothing to fiddle with.

---

### Post by kesetyan on 2018-12-31
Hi CatKiller,

Thanks for your helpful response - I promise I won't fiddle.

---

### Post by CatKiller on 2018-12-31
If you're into that sort of thing, the .desktop files are quite interesting. You can drag-and-drop them onto a text editor to see how they work.

If you *aren't* into that sort of thing, they are soooo dull :)

---

### Post by kesetyan on 2019-01-01
Hi CatKiller,

Thanks for your reply.  I was aware of .desktop files through years of using Puppy Linux live dvds and having a dual boot Windows XP/Puppy Precise 5.7 desktop computer for a few years.  

My experience with Ubuntu and variations of it were limited to live dvds until recently when I tried live usb memory sticks with persistence.  In Puppy Linux, I did edit .desktop files on occasions, usually to change associated icons.  With my present Lubuntu/Windows 7 dual boot, I'm getting to grips with things and working out how to do the things I did with my Windows 7 setup.  I'm getting there and feeling more confident that, once I disable the internet on Windows 7, I will still be able to still be able to replicate all the internet related activities, I did in Windows, in Lubuntu.

Regarding Okular, there are fourteen .desktop files for it all labelled just 'Okular' whereas generally any other application in the applications folder, if it has more than one entry, then the label for each contains extra individual text. Exceptions include two 'Files' and and two 'Notifications' although the latter are distinguished by different icons.  It's all very interesting and adding to the learning experience of this 77 year old geek.

Cheers and all the best for 2019.

---

