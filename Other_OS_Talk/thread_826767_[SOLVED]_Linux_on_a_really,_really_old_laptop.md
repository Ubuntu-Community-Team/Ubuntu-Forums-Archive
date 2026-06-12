---
title: "[SOLVED] Linux on a really, really old laptop"
date: 2008-06-12
forum: Other OS Talk
---

### Post by durand on 2008-06-12
My friend was going to throw away an old laptop but I thought that it might be useful as a bittorrent client or something really lightweight. Anyway, the laptop is an [AcerNote Light 370]("http://www.acersupport.com/notebook/html/an373plus_specs.html") which is really, really, really old with a 133Mhz processor and 16 megs of ram. It also has a 1gb hard disk and a floppy and cd drive.

Now I've read the sticky at the top of this forum which was very helpful but I'm not really sure what the best OS would be. Any of ubuntu's variants are obviously out of the question and according to my friend, DSL takes an hour to boot. I found [this]("http://www-ra.phys.utas.edu.au/~sellings/acer.html") website which is exactly the same laptop as me but it's from a while ago and a lot has changed...

Oh and does anyone know of a 16 bit type II pcmcia  ethernet card that I can use with this laptop? This is also a high priority.

So, what would you recommend me trying?


I don't really know much about old hardware so any replies would be useful. Thanks!

---

### Post by Midwest-Linux on 2008-06-12
> **durand said:**
> My friend was going to throw away an old laptop but I thought that it might be useful as a bittorrent client or something really lightweight. Anyway, the laptop is an [AcerNote Light 370]("http://www.acersupport.com/notebook/html/an373plus_specs.html") which is really, really, really old with a 133Mhz processor and 16 megs of ram. It also has a 1gb hard disk and a floppy and cd drive.

Now I've read the sticky at the top of this forum which was very helpful but I'm not really sure what the best OS would be. Any of ubuntu's variants are obviously out of the question and according to my friend, DSL takes an hour to boot. I found [this]("http://www-ra.phys.utas.edu.au/~sellings/acer.html") website which is exactly the same laptop as me but it's from a while ago and a lot has changed...

Oh and does anyone know of a 16 bit type II pcmcia  ethernet card that I can use with this laptop? This is also a high priority.

So, what would you recommend me trying?


I don't really know much about old hardware so any replies would be useful. Thanks!

 I see your maximum ram for that machine is 64 MB. So if you added RAM, that is your limit. I would just give a check on E-bay on how much ram would cost for your laptop. If the ram is inexpensive, I would suggest starting there.

 Try to go into the bios and see if you can change the boot sequence to boot from the CD Rom, if you can't set it up that way. Then you know you are limited from booting from floppies. (See side note below)

 So once you know those two things, you might be able to plot your course better and someone here can assist you further.


Side Note

 I almost have a similar problem. I have a very dated laptop, HP 5700 with 48 MB RAM. I can only boot from floppies. Not bad right? Except the blessed Linux programs that could run on floppies are 147 MB and floppies have a 144 MB limit. Go figure...

 I need a program that will take Damn Small Linux and split it into 144 MB bits to fit on floppies so I can install it on the laptop.

---

### Post by jariku on 2008-06-12
Here's something I wrote on a different thread:

> **jariku said:**
> I recently installed DeLi Linux 0.7.2 on a Pentium 133 with 1,6 gigabyte HDD and 16 megabyte RAM using boot floppies and a CD. It runs IceWM quite all right, but I made a 150 megabyte swap partition just to be sure. Also, I turned the swap on before I started the install process. The newest version of DeLi Linux (0.8.0) needs 32 megabytes of RAM, so it was out of the question.

What comes to your problem with the floppy or cd situation, you could try installing via null modem connection from another computer. I haven't tried it myself but I think you should be able to install DeLi with it. Another possibility might be having the CD ISO image on the HDD and booting to it with boot floppies (DeLi Linux boot floppy images are included in the 0.7.2 CD).

Here are links to the DeLi Linux website and a mirror where I downloaded the 0.7.2-big ISO image, which contains IceWM and Fluxbox (I couldn't find a download link for it from the official website). The smaller ISO is for a command line system only. I hope this helps.

[http://www.delilinux.org/](http://www.delilinux.org/)
[http://darksnow.radiolivre.org/deli/](http://darksnow.radiolivre.org/deli/)

EDIT: I forgot to mention that I used the boot floppies because I couldn't boot from the CD even with a sbootmgr floppy.

---

### Post by Tom Mann on 2008-06-12
As for your ethernet card problem - going onto ebay and buying a PCMCIA network card for the Amiga 1200 should reap you some benefits - I have one attached to my A1200 which I have had working on a Windows laptop too.
(Look for the 3Com stuff!)

---

### Post by durand on 2008-06-12
Oh, I can boot from cdrom. Infact, the laptop is trying to boot DSL. Its been on a blank X screen for about 40 minutes now [IMG]http://www.durand.zephyrhosting.net/dump/smileys/smile-big.png[/IMG] and no changes though it definitely sounds like its doing something. Oh and my friend's looked around for more EDO ram. It's hard to find and expensive but I'll give it another shot.

I will give DeLi Linux a go, it looks interesting.

EDIT: Do I have to use floppies or can I boot straight from the CD? I'd have to recompile my old pc's gentoo kernel to add floppy support and it would be a bit annoying.. I guess I might need to for some of these distros. Hmm, maybe I could use a live cd for floppy support.

---

### Post by durand on 2008-06-12
I'm looking at the ebay cards right now though not many of them actually say type II. Is there any other keyword I should look for?

EDIT: Ok, I found this one via google products: [http://www.kikatek.com/product_info.php?products_id=8799&source=froogle](http://www.kikatek.com/product_info.php?products_id=8799&source=froogle) It sounds like the right one but will it work in linux?

I also found this one: [http://cgi.ebay.co.uk/16-Bit-Ethernet-PCMCIA-Card_W0QQitemZ120269993261QQihZ002QQcategoryZ45000QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122](http://cgi.ebay.co.uk/16-Bit-Ethernet-PCMCIA-Card_W0QQitemZ120269993261QQihZ002QQcategoryZ45000QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122)

---

### Post by durand on 2008-06-12
> **Midwest-Linux said:**
> I see your maximum ram for that machine is 64 MB. So if you added RAM, that is your limit. I would just give a check on E-bay on how much ram would cost for your laptop. If the ram is inexpensive, I would suggest starting there.

 Try to go into the bios and see if you can change the boot sequence to boot from the CD Rom, if you can't set it up that way. Then you know you are limited from booting from floppies. (See side note below)

 So once you know those two things, you might be able to plot your course better and someone here can assist you further.


Side Note

 I almost have a similar problem. I have a very dated laptop, HP 5700 with 48 MB RAM. I can only boot from floppies. Not bad right? Except the blessed Linux programs that could run on floppies are 147 MB and floppies have a 144 MB limit. Go figure...

 I need a program that will take Damn Small Linux and split it into 144 MB bits to fit on floppies so I can install it on the laptop.

I think you missed the decimal point there. Btw, this won't work if you wanted to boot from the floppies but you can use [HJSplit]("http://www.freebyte.com/hjsplit/#linux") to separate the programs then join them back together when your on the system.

---

### Post by durand on 2008-06-12
the second deli site is really slow :S

---

### Post by wolfen69 on 2008-06-12
i believe DSL requires at least 24MB of ram.

---

### Post by durand on 2008-06-12
Oh right, makes sense..I never knew DSL could be that resourceful :D I got DeLi linux installed. Its working perfectly so far! With icewm. Just installing fluxbox.

---

### Post by volkswagner on 2008-06-12
I have on order the order the following card.

Lucent Orinoco Classic GOLD.  This card is rebranded under several names, including Dell.

It appears to be supported in linux, mac, and windows.  This causes prices to reach over $20 sometimes (many avail in ebay).  From what I have read, stick with the silver and gold models.  They have better support for wep.  I don't think the do wpa.

---

### Post by Tom Mann on 2008-06-12
> **durand said:**
> I'm looking at the ebay cards right now though not many of them actually say type II. Is there any other keyword I should look for?

EDIT: Ok, I found this one via google products: [http://www.kikatek.com/product_info.php?products_id=8799&source=froogle](http://www.kikatek.com/product_info.php?products_id=8799&source=froogle) It sounds like the right one but will it work in linux?

I also found this one: [http://cgi.ebay.co.uk/16-Bit-Ethernet-PCMCIA-Card_W0QQitemZ120269993261QQihZ002QQcategoryZ45000QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122](http://cgi.ebay.co.uk/16-Bit-Ethernet-PCMCIA-Card_W0QQitemZ120269993261QQihZ002QQcategoryZ45000QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122)

Why it's good to look for Amiga 1200 - it had and only ever had a PCMCIA Type II slot - PCMCIA is a universal spec so you can quite safely assume it'll work on a PC. Failing that you could always buy mine :)

---

### Post by zmjjmz on 2008-06-13
You could also try BasicLinux.
It has the 2.2 kernel and JWM. On the site ([www.basiclinux.com.ru](www.basiclinux.com.ru)) there are a bunch of links to some old Slackware 4 software that you could use.
It fits on two floppies.
And for all your floppy booting woes, try SmartBootManager.

---

### Post by durand on 2008-06-13
> **Tom Mann said:**
> Why it's good to look for Amiga 1200 - it had and only ever had a PCMCIA Type II slot - PCMCIA is a universal spec so you can quite safely assume it'll work on a PC. Failing that you could always buy mine :)

I don't really want to buy from ebay unless I have to...and it's looking to be that way now.

I found these on ebay and they look like the right price range for me. If wifi cards work on DeLi, then I'll buy one because I just need networking in whatever way is possible:

[http://search.ebay.co.uk/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&satitle=pcmcia+16+bit&sacat=-1%26catref%3DC6&sadis=200&fpos=Postcode&sabfmts=1&saobfmts=insif&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&seller=1&sass=wifi-planet&fsop=32%26fsoo%3D2&fgtp=](http://search.ebay.co.uk/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&satitle=pcmcia+16+bit&sacat=-1%26catref%3DC6&sadis=200&fpos=Postcode&sabfmts=1&saobfmts=insif&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&seller=1&sass=wifi-planet&fsop=32%26fsoo%3D2&fgtp=)

zmjjmz: I think I'll stick with DeLi for now because it appears to be a really good distro. This laptop can boot directly off a cd and I'm really suprised about that.. My friend might have done somethine, I'm not really sure.

---

### Post by durand on 2008-06-13
> **volkswagner said:**
> I have on order the order the following card.

Lucent Orinoco Classic GOLD.  This card is rebranded under several names, including Dell.

It appears to be supported in linux, mac, and windows.  This causes prices to reach over $20 sometimes (many avail in ebay).  From what I have read, stick with the silver and gold models.  They have better support for wep.  I don't think the do wpa.

Oops! Didn't see this post before...I've searched for those cards but they are quite expensive in the UK, I could order it from the US but its still pretty expensive.

---

### Post by zmjjmz on 2008-06-13
Cool, just gonna say though, the next DeLi (.8 ) needs 32MB RAM.

---

### Post by raul_ on 2008-06-13
Have you considered a Linux installation with no X? you can set-up a bittorrent client based on ncurses apps

---

### Post by zmjjmz on 2008-06-13
> **raul_ said:**
> Have you considered a Linux installation with no X? you can set-up a bittorrent client based on ncurses apps

And use twin for an X like WM.

---

### Post by durand on 2008-06-14
> **zmjjmz said:**
> Cool, just gonna say though, the next DeLi (.8 ) needs 32MB RAM.

Yeah, jariku said that so I just tried 0.72 and I think deli is going to stop supporting older computers like this one within a year but I don't think it will really matter to me.

> Have you considered a Linux installation with no X? you can set-up a bittorrent client based on ncurses apps

Well, that was my original plan because I didn't actually think that this laptop would run X but its actually really smooth. I will be using an ncurses bittorrent client anyway because there would be little point in running X unless I was doing something else on the laptop.

Are there any lightweight bittorrent clients that people recommend?

> And use twin for an X like WM.

I've looked at that before but I don't really see the need for a WM without X. I can just run the bittorrent client in one tty and do other stuff in another, or more likely, just ssh into the laptop.


I've still got the problem of finding a network card that would work :S.

---

### Post by zmjjmz on 2008-06-14
rtorrent is a good ncurses torrent client.

---

### Post by durand on 2008-06-14
> **zmjjmz said:**
> rtorrent is a good ncurses torrent client.

Haha, I was just looking at that one. Is it good on low end hardware and do you know if it works on linux 2.4?

---

### Post by raul_ on 2008-06-14
> **durand said:**
> Haha, I was just looking at that one. Is it good on low end hardware and do you know if it works on linux 2.4?

Of course

---

### Post by durand on 2008-06-14
> **raul_ said:**
> Of course

Great! Thank you both!

---

### Post by durand on 2008-06-21
I've now got networking working on it. Would anyone recommend me a good lightweight browser? Dillo doesn't render the pages well and it doesn't have many features either. I don't really want to use a commandline browser and opera doesn't wanna run for some reason. I keep getting:
```

opera: No such file or directory

```

---

### Post by raul_ on 2008-06-21
> **durand said:**
> I've now got networking working on it. Would anyone recommend me a good lightweight browser? Dillo doesn't render the pages well and it doesn't have many features either. I don't really want to use a commandline browser and opera doesn't wanna run for some reason. I keep getting:
```

opera: No such file or directory

```

kazehakase is pretty lightweight as well as arora (under heavy development and has qt-dependencies)

maybe opera isn't the name of the executable, or isn't in the normal path (/usr/bin)

---

### Post by durand on 2008-06-21
> **raul_ said:**
> kazehakase is pretty lightweight as well as arora (under heavy development and has qt-dependencies)

maybe opera isn't the name of the executable, or isn't in the normal path (/usr/bin)

Ill look into arora. kazehakase uses the gecko engine which would be too slow..

---

### Post by zmjjmz on 2008-06-21
If you're up to it, you can compile Epiphany with webkit (has gtk dependencies though :/) or get Skipstone with webkit (Skipstone will be included in the next DeLi)
EDIT: Netsurf is good too, but it doesn't support js

---

### Post by durand on 2008-06-21
> **zmjjmz said:**
> If you're up to it, you can compile Epiphany with webkit (has gtk dependencies though :/) or get Skipstone with webkit (Skipstone will be included in the next DeLi)
EDIT: Netsurf is good too, but it doesn't support js

Well, this laptop won't work with 0.8+ cos I've only got 16megs of ram. I'll look at the others though Epiphany also feels too big. I've been compiling a lot of programs so it shouldnt be a problem except that a program that takes 1 minute on my desktop pc takes 1 hour on the laptop :D

---

### Post by durand on 2008-06-24
I've been working on some documentation for this laptop over the past few days:

[http://durand.zephyrhosting.net/dump/acer370.htm](http://durand.zephyrhosting.net/dump/acer370.htm)

Comments and Criticism please :)

I've converted most of the images to base64 so that the document is portable. Please tell me if this is a bad thing.

---

### Post by zmjjmz on 2008-06-24
Wow, although that was just a guide for that laptop, it had a lot of great stuff for DeLi in general. Thanks, I'll make use of it.

---

### Post by volkswagner on 2008-06-24
> **durand said:**
> I've now got networking working on it. Would anyone recommend me a good lightweight browser? Dillo doesn't render the pages well and it doesn't have many features either. I don't really want to use a commandline browser and opera doesn't wanna run for some reason. I keep getting:
```

opera: No such file or directory

```

I am not sure if Firefox 1.06 would be too demanding.  It does use more ram than dillo.  It does render pages better though.  These forums look great on it.  Obviously no flash so many sites are a no go with these relics.

One would think if Opera mini could do a great job on my free nokia 6126, surely these laptops should have a viable solution.  

Here is my official plea, someone port opera mini to deli or DSL.  ;)

I would like to try deli.  Does it load all drivers on boot, or is it customized during install?  My laptop can't boot to CD rom.  I installed DSL by swapping the HD to a laptop that could boot via CD.  Do you think this would work in Deli?

---

### Post by zmjjmz on 2008-06-24
I doubt there's an x86 port of Opera mini in the first place.

---

### Post by durand on 2008-06-25
Opera Mini's great. volkswagner, I think you can use a floppy to load the drivers required to boot off a cd. Try sbm: [http://btmgr.sourceforge.net/about.html](http://btmgr.sourceforge.net/about.html) I've used it before and found it to be pretty good.

zmjjmz, I might add more deli stuff to it if I can get my laptop to work again... It just died randomly - screen doesn't come on, hard drive makes clicking noises and then just stops and starts again...I guess that's the problem with old computers >_>. I really need to open it up at the weekend and see if there's a loose connection somewhere...

---

### Post by zmjjmz on 2008-06-25
Y'know, everyone's been saying that old computers are unreliable and such, yet I have had no problems with any of mine.

---

### Post by volkswagner on 2008-06-25
> **durand said:**
> Opera Mini's great. volkswagner, I think you can use a floppy to load the drivers required to boot off a cd. Try sbm: [http://btmgr.sourceforge.net/about.html](http://btmgr.sourceforge.net/about.html) I've used it before and found it to be pretty good.

Thanks.  I tried SMB.  The issue with my machine is the floppy drive and CD rom share the same slot.  There should be an additional housing to use either as an external drive, with a propriatory connector.  I don't have this additional hardware and I already spent too much money on this setup.  

I did not want to hijack this tread but I think this is still on topic. So either I need to swap the hard disk to another machine, or use the DSL as a host OS.  The 1gig hard drive does not leave much room for multiboot.  I am still learning a lot.  :)

---

### Post by zmjjmz on 2008-06-25
I believe SBM gets loaded to RAM, so you should be able to do a quick switch (then rescan the drives in SBM)

---

### Post by volkswagner on 2008-06-25
> **zmjjmz said:**
> I believe SBM gets loaded to RAM, so you should be able to do a quick switch (then rescan the drives in SBM)

I believe when I did the rescan, the CDrom still showed as a floppy.  I may give it a second try to give the exact results.

---

### Post by Dr.Ninethousand on 2008-06-26
for a really light distro, try searching for one called "mean puppy"..  the whole OS is something like 50mb, and it has a desktop and everything..


as for wifi cards, I just ordered this one for an old Toshiba:

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&Item=250262337612&Category=74954&_trksid=p3907.m29](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&Item=250262337612&Category=74954&_trksid=p3907.m29)

hopefully it works for me..


and I have some others that will likely work for you listed here:

[http://ubuntuforums.org/showthread.php?t=840938](http://ubuntuforums.org/showthread.php?t=840938)


also I don't think you have to use Type II; I believe TypeII slots are backward-compatible..  so you should be ok as long as you get one that can work in 16-bit mode..

---

### Post by durand on 2008-06-26
> **volkswagner said:**
> I believe when I did the rescan, the CDrom still showed as a floppy.  I may give it a second try to give the exact results.

I think you can install SBM to the master boot record...though don't quote me on that.

---

### Post by zmjjmz on 2008-06-26
> **durand said:**
> I think you can install SBM to the master boot record...though don't quote me on that.

Sounds like a great idea actually, so it can act in place of LILO or GRUB too?

---

### Post by durand on 2008-06-26
Yes, I remember installing it over grub by accident. It did a pretty good job though.

---

### Post by volkswagner on 2008-06-26
Sorry, misread earlier post.

Removed comment

---

### Post by volkswagner on 2008-06-26
> **durand said:**
> I think you can install SBM to the master boot record...though don't quote me on that.


I must be doing something wrong.

When I swap the drives and hit Ctrl-H to rescan partitions, also Ctrl-I, and Ctrl-X for rescan all boot records, and toggle swap driver id.  Nothing happens.  The drive is still listed as a floppy.

I do not see any other options for rescan.  It just seems to look at the HD, not the entire machine.  Hence "partition rescan".

When I try to install SMB, with the CD drive in nothing happens.  It keeps scanning the CDrom.  I guess the entire contents of the floppy are not loaded to ram.

If I leave the SMB floppy in the drive and install all goes ok.  The problem is the system still thinks the CDrom drive is a floppy drive.  It must be a firmware problem with the drive.

I will need to install grub again.  No biggie.  I am just messing around with this machine.

Shouldn't the SMB install be able to boot my DSL from HD?  Or is this due to SMB wiping out Grub?

---

### Post by durand on 2008-06-28
SMB will boot DSL off your hard drive but you may need to configure it a bit first.

---

### Post by zmjjmz on 2008-06-28
You're better off running the DSL boot floppy and doing "dsl fromhd=/dev/hda1"
(if hda1 us the partition with DSL on it.)

---

