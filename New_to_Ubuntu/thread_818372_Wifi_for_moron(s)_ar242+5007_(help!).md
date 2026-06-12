---
title: "Wifi for moron(s) ar242+/5007 (help!?)"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by ennika on 2008-06-04
Hi!

I spend the last two days trying to get my wifi to work, and I've gotten to the point where I'm considering giving up and buying xp (there, that should show you I'm desperate ;) ). I have an acer aspire that came with linpus pre-installed, but switched to ubuntu last night. Wifi worked fine on Linpus (about the only thing that did), but I've been unable to get it to work on Ubuntu (8.04). It's an Atheros 242+ (afaik actually a 5007?). I realize a lot of people have problems with it and have found about thirty different ways to deal with it, but so far everything I've seen either requires you to have net access on the computer in question (I don't, only on my old notebook currently sitting next to it), are way too confusing for a clueless newbie or (as far as I understood) want me to install the driver from my install cd which apparently does not include the driver in question. Is there a dummy-safe how-to somewhere? any tips/tricks/ideas?

---

### Post by wwusnobrdr on 2008-06-04
There is a good tutorial in the tutorial and tips forum here [http://ubuntuforums.org/showthread.php?t=789824](http://ubuntuforums.org/showthread.php?t=789824)

My wireless broke with the latest kernel update but it could just be me.  You will need to download a driver using this however.  Another thing you can do is use ndiswrapper to install the windows drivers.  Here is another forum post.  [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

---

### Post by ennika on 2008-06-04
The trouble with that one is that as far as I can tell it takes the driver directly from the net (*wget [http://.](http://.)..*). I don't have trouble downloading the driver on my old notebook and then putting it on the notebook I need it on, but I have no idea how to access/install it. One how-to made me extract it in Home, which I did, but once I get to the point of *cd madwifi-nr-r3366... * I keep on getting the message that there is no such file/directory. I managed to install the wrong madwifi driver I downloaded first that way, but it won't work with the one for 5007.

---

### Post by avtolle on 2008-06-04
When you transferred the driver from the old notebook to the "new" notebook, where did you save it, e.g., the desktop; your home folder; somewhere else? If saved to the desktop, as an example, in the Terminal ```
cd Desktop
``` to get to the driver. Then extract from there. HTH.

---

### Post by ennika on 2008-06-04
It's in my home folder, extracted it there as well, but have no ides what to do next...

---

### Post by avtolle on 2008-06-04
OK, taking the obvious first, is there a typo in your directory/file name? I did this a lot until I started using the autocomplete (via Tab) in the terminal.

---

### Post by prshah on 2008-06-04
> **ennika said:**
> Hi!

I spend the last two days trying to get my wifi to work, and I've gotten  Is there a dummy-safe how-to somewhere? any tips/tricks/ideas?

Why not try my step-by-step guide (_with expected outputs_) ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up your wireless network card? If you run into any problems, post back which step you are stuck at.

But you _need_ the windows drivers if your card is not natively supported. The howto above will tell you how to check if your card's driver is already installed.

---

### Post by ennika on 2008-06-04
Turns out that that too, yes. Apparently I'd disabled the wrong restricted driver, and on top of that didn't realize that the nr in the file name automatically changes to ng once it's extracted. Got it up and running now, hope it stays that way. Thanks :)

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by prshah on 2008-06-10
> **braveerudite said:**
>  super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper 

I think that compiling a whole new atheros module will be much harder than using ndiswrapper. And you will have to recompile that module with every kernel update (There have been 3 for hardy so far). And also the suggestion is _only_ for 64 bit.

So I'd suggest you stick with ndiswrapper for now.

---

