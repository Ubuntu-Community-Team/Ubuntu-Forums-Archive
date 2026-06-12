---
title: "NVidia GeForce MX400"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by rbmoler on 2013-12-02
"Well, that was interesting," I said to myself as I uninstalled ubuntu.

I was hoping to get around upgrading my XP OS to W-7.  I've used versions of Linux in the past, it was such a chore to learn all the command line requirements that I abandoned the effort.  I hoped that Ubuntu would be the answer.  I did a test run of the 32bit version on my old Acer laptop which has a comparatively tiny HD and ubuntu loaded in test mode and I could use it so I had some hope.  They were dashed.  My old computer (at least 10 years) was home brew.  It is an AMD AThlon XP-M Processor 2800+ at 1.6 GHz, 2 GB RAM running XP Pro Ver 2002 Service Pack 3.

It definitely wants the 32 bit version of Ubuntu.  I made a DVD (Same one I used on my laptop) and proceeded to use the windows installer WUBI to do a side by side installation.  The installation finished.  I rebooted, selected Ubuntu from the screen and waited, and waited.  A few lines of diagnostics appeared and disappeared before I could copy anything.  There were a few brief flashes on a part of the screen, but nothing showed up after 20 minutes.  I decided I could do no harm by trying a hard reboot, but the results were identical although I did get a B+W screen telling me it was in recovery mode.

I'm not optimistic that there is any remedy other than to download all the data from the machine onto my external HD, and buy a new machine that will run after installing ubuntu.  I was hoping to avoid spending another three or four hundred bucks to get from here to there.

---

### Post by daslinkard on 2013-12-02
Question for you...you stated that you were looking at installing Ubuntu and dumping Windows.  If that be the case, why not back up your data from the XP machine such as your documents, pictures, music, etc. and then go ahead and install Ubuntu on the entire HD instead of dual booting?

---

### Post by Impavidus on 2013-12-03
1: WUBI installs Ubuntu inside Windows, on a virtual partition, which is really a file on the Windows partition. It's not a dual boot, it's being phased out and it's not a good idea if you ultimately want to get rid of Windows. Make a proper dual boot or wipe Windows completely.
2: You indeed need the 32 bit version on that processor. Currently supported releases of Ubuntu are 12.04 LTS and 13.10 (and 12.10 and 13.04, but I don't see any reason to install one of those). On your hardware it may be better to install one of the lighter flavours, Xubuntu or Lubuntu. Lubuntu 12.04 is no LTS release, so don't use it. Stick to supported releases.
3: Your black screen may be the result of a graphics driver issue. Try the nomodeset option: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132). The instructions are a bit older, but should still apply. Maybe you can tell us which graphics card you use.

---

### Post by rbmoler on 2013-12-03
OK.  The video adapter that I added early on is the Microsoft NVidia GeForce MX MX400.

I understand that it wasn't a true duel boot system, but the instructions seemed to be making a big thing of it.  On the other hand I had earlier tried to see if Ubuntu would load and play by installing it in the tryout mode.  That resulted in the same issue of not getting a screen.  It also resulted in a few lines of diagnostics that lasted too briefly for me to catch anything but the word crash.

The reason for keeping the old XP system is that it is the last place that I can run an 80's DOS database program which has some 3000 entries for my entire collection of LP, CD and DVD/BluRay discs.  I converted all my old VHS (and Beta) tapes to DVD.  That program was first installed and used on a Sanyo PC with two single sided floppies which I acquired in 1986 when my collection had already exceeded my willingness to keep it cataloged on file cards.  Converting it to a modern database program and saving the data (there are six different ways to search with six separate data files) is beyond my skills.

An alternative would be for me to buy and install a newer motherboard which would be compatible with ubuntu.  I've done that in the past on several occasions when I upgraded from the 8088 processor to the 386 processor and then the 486(?) processor.  Of the 5 computers in our household only the laptop was purchased as a new original computer.  All the others I assembled and upgraded over time.

I do have an external HD which operates once a day at 10pm to back up all the data that I keep stored on a separate internal HD (E:)  S I'm not worried about that issue.  Unless it is possible to run that old DOS program in ubuntu (It won't run in Win7) then I'm going to keep XP alive indefinitely, but off line.

---

### Post by arubislander on 2013-12-03
> **rbmoler said:**
> Unless it is possible to run that old DOS program in ubuntu (It won't run in Win7) then I'm going to keep XP alive indefinitely, but off line.

FreeDOS might be able to run your program. It can be installed on a USB stick, or run in a virtual machine (QEMU comes to mind) in Ubuntu. Not sure if it would run on your hardware setup though...

---

### Post by Impavidus on 2013-12-03
NVidias often need the nomodeset option. However, I can't tell whether the bits and pieces forming your computer are fully compatible with Ubuntu. The thing is that hardware manufacturers often only provide drivers for Windows, so sometimes things are a bit complicated on Linux.

---

### Post by mörgæs on 2013-12-03
[COLOR=#000000]The graphics card is slow, in fact it was also low performing at the release date ten years ago. I would go for a more powerful card. [/COLOR]More advice in the link in my signature.[COLOR=#000000]

If the only thing XP is used for is an old database I would recommend that you try to copy your data into Libreoffice (Base or Calc). 
[/COLOR]

---

