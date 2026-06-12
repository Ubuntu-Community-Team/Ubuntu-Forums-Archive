---
title: "WDTV Live + HD problems"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by swab148 on 2012-11-28
Hey guys, yeah kinda new at this :)

I've shared my music folder via Samba, and the WD box sees my laptop (two versions of it, actually), but it keeps telling me there's no media in the folder. 

Now here's the tricky part: The network is Windows-based (run by my dad, lol), and he's using a program called "Network Magic" to basically do his job for him. 

Basically, my question is either a) how do I get the WD box to see my files or b) is there an Ubuntu version of Network Magic that will make my music happen.

Any help, even just a redirect to the thread where this has been solved, would be greatly appreciated by this obvious newbie.

Thanks,
~swab148

---

### Post by colin.p on 2012-11-28
I have the original WDTV Live since 2009, and was never able to get it to work properly to see my USB NTSF drive connected to my Dell laptop running ubuntu 9.04 up to 10.04. However, I could sometimes see the drive from a couple win computers, but not the actual media files.

I futzed around with all the ideas that others used, and even though it may have worked for them, not me. So I had to use another USB drive attached to the Live, for media access, and used the network to move files to and from it.

Then when 12.04 came out, I moved my living room around and had to start using a wireless dongle on my WDTV Live. I also flashed to B-Rads WLXTV firmware. Then my USB drive that I had connected to the Live tanked. Then I, just by luck, tried to access my USB drive connected to my laptop and lo-and-behold, all files were visible and useable, from all other computers on my network as well as the Live.

So was it the update to 12.04, moving furniture around, using wireless instead of RJ45, WLXTV or just blind luck?

Seriously, if your Live+ will run B-Rads FW, you should look into it. Will save you alot of pain and suffering.

---

### Post by coffeecat on 2012-11-28
I can confirm that my WD TV Live can stream media just fine from a samba share on my Ubuntu system. I wonder if your problem is an issue with Windows' homegroup. Homegroup was introduced with Windows 7 and doesn't work with other operating systems, or Windows XP for that matter I believe. What version of Windows is your father running? If Windows 7 (or 8 ) and homegroup is involved, this might be something you could look into.

---

### Post by audiomick on 2012-11-28
> **coffeecat said:**
> ... introduced with Windows 7 and doesn't work with...Windows XP 
<rant about microsoft...> ;)


That last sentence was supposed to look like this
```
If Windows 7 (or 8) and homegroup is involved, this might be something you could look into.
```

rather than having a smiley in it.

---

### Post by docshawnc on 2012-11-28
I have the WD media box hooked up to my lan and it works well.  If yours can see the ubuntu box, but can access it (ie. see folders or files within directories) it sounds like a permission issue with the ubuntu box.  As someone above mentioned, make sure that both the media box and ubuntu box are in the same workgroup.

Oh and one more thing - and I know this sounds stupid, but I've done it myself a number of times - on your ubuntu box - make sure the smb deamon is running

---

