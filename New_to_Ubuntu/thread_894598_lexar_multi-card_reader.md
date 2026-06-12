---
title: "lexar multi-card reader"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Veggiet on 2008-08-19
Hi, I am running Ubuntu 8.04 and I want to use my Lexar 2.0 multi-card reader, but It will not recognize. I've tried connecting it and restarting the pc, but no it's just sitting there with its lights blinking,  Is there a driver I can use?

Edit: Ok, I did some testing and found that it's reading my card reader fine, it pull up four usb drives in the computer folder, but now I have a new problem, It's not reading my 2GB or 4GB SD card, now I realize that the 4gb is an SDHC and won't be recognized by all devices, but I don't know why It's not reading the 2gb, any help?

---

### Post by vikramaditya on 2008-08-19
It should "just work". :-k  Does anything at all happen when you put a card in?  Have you looked under "Places" in the top panel to see if it's listed as a drive?

---

### Post by Veggiet on 2008-08-28
Well, it did get listed as a drive at least once, but ever since it just sits there with lights blinking rapidly, but no drives, and no recognition. Its aggrivating because I need to move some files to a windows pc, and my CD burner isn't functioning at all.

---

### Post by bubwitmaingay on 2009-02-20
I have the same problem with my memory card too. It is a Kingston 8 gigabyte SDHC and only newer card-readers can detect the removable device.

My Asus eeePC 2g Surf runs on eeePCLinuxOS and its built-in card-reader can detect and open the 8gig SDHC Card. So I figured that if I install PCLinuxOS 2009 to my PC with the same packed codecs, plugins and drivers of the eeePCLinuxOS, I can also detect and read my SDHC Card using my Built-in Card-Reader there (China-made Lian Li brand). To my chagrin, it did not read the card still (thus I also removed the PCLinuxOS installation and reverted to Ubuntu).

I went back to the store where I bought the SDHC Card to return it and I was amazed that it was detected and opened there through their card-reader. I asked how recent their card-reader is and they said its the latest hardware version. I went home scratching my head. :(

MY CONCLUSION IS THAT **THIS IS A HARDWARE ISSUE, NOT A DRIVER ISSUE**. **SDHC MEMORY CARDS CAN ONLY BE DETECTED BY CARD-READERS WITH SDHC DETECTION CAPABILITY. OLDER CARD-READERS WITHOUT THE SAID SPECS CANNOT DETECT SDHC CARDS NO MATTER HOW YOU LOOK FOR APPROPRIATE DRIVERS FOR THEM.**

*MY ADVICE IS THAT WE BUY A NEWER CARD-READER WITH SDHC DETECTION CAPABILITY. I THINK THESE CARD-READERS HAS THE SAME DRIVERS FOUND IN UBUNTU.* ;)

---

### Post by bubwitmaingay on 2009-02-20
I think your 2gig memory card is also SDHC. If the PC can detect the lexar multi-card reader, it's those cards that the reader could not.

---

### Post by bubwitmaingay on 2009-02-21
One thing I found out too is that you should not insert your SDHC memory card into the card-reader because it will cause some bad things. That's what ahppened to my card-reader when I inserted the SDHC card, it will not read the other non-SDHC cards afterwards.

---

### Post by Veggiet on 2009-07-30
Ok not that I want to bump an old post but I ran into a couple of new challenges, first off I'm still using the lexar, I got my main cards to work with it, but now I've bought a 16GB SDHC. I was not too surprisedwhen it didn't work, but I looked up the media card reader on the makers website here:[http://www.lexar.com/readers/multi.html]("http://www.lexar.com/readers/multi.html") and there they list "SDHC" compatible. So now I'm thinking it must have something to do with ubuntu, and now my camera, previously usable by connecting directly to the computer now registers a "connection error" with the 16GB card inserted! (I am also now using ubuntu 9.04)

---

### Post by egalvan on 2009-07-30
> **Veggiet said:**
> ...first off I'm still using the lexar, I got my main cards to work with it,

What size SDHC cards are working?


> ... I've bought a 16GB SDHC... it didn't work,
I looked up the media card reader on the makers website 
:[http://www.lexar.com/readers/multi.html]("http://www.lexar.com/readers/multi.html")

and there they list "SDHC" compatible...now I'm thinking it must have something to do with ubuntu,


Does the card reader and 16GB-SDHC work under XP?
It may not be capable of seeing such a large memory size.

>  and now my camera, previously usable by connecting directly to the computer now registers a "connection error" with the 16GB card inserted! (I am also now using Ubuntu 9.04)

Did it ever work under Linux with the 16GB-SDHC card installed?
If not, it may not have the hardware capable of seeing such a lsrge card...
 or maybe it needs a software upgrade.
Check the maker's web site.

I have a Palm Pilot TX (Palm Garnet OS), and it maxes out at 2GB cards.
My Palm Treo 650P (Palm Garnet OS) also maxes out at 2G GB cards.

Neither sees any SDHC cards.
But my buddy's Palm Treo 650W (Windows Mobile OS) sees a 4GB-SDHC.

None of my six different card readers (external or internal) see anything bigger than 2GB, no SDHC at all.

Picked up an external card reader at Radio Shack last week, and it sees 4GB-SDHC fine.
XP and Hardy and Jaunty, oh my.

---

