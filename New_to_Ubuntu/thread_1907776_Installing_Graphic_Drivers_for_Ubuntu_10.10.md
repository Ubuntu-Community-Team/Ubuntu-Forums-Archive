---
title: "Installing Graphic Drivers for Ubuntu 10.10"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Gnome Defender on 2012-01-12
Hello all,

I have ATI 9100 IGP driver for my Ubuntu 10.10 laptop.  I realized my graphics driver was not installed when I opened up a simple 3D RPG.  My laptop should've been able to handle the low resolution 3D.  So I've read tutorials online, and all that I ended up doing was messing up the graphics.  I reinstalled Ubuntu, and now I'm posting here because I simply don't want to mess up again.

How do I install my ATI 9100 IGP driver?

Thanks,
Gnome Defender

---

### Post by lolpenguin on 2012-01-12
Use "Additional Drivers" (jockey-gtk for Ubuntu, Lubuntu and Xubuntu, jockey-qt for Kubuntu and jockey-text for teletype)

---

### Post by Mark Phelps on 2012-01-12
Sigh ... once again, it would be NICE if folks would do so actual RESEARCH before automatically replying with Additional Drivers whenever anyone mentions an ATI card ...

Why?

Because ATI dropped Linux driver support for this card YEARS ago!

The last Ubuntu release to include that support was 8.10 -- and the OP already indicates they are running 10.10.

The only working drivers are already installed by default, otherwise, you would not be seeing a desktop.

There are no newer drivers you can download that will work with your card and Ubuntu versions newer than 8.10.

---

### Post by waynefoutz on 2012-01-12
> **Mark Phelps said:**
> Sigh ... once again, it would be NICE if folks would do so actual RESEARCH before automatically replying with Additional Drivers whenever anyone mentions an ATI card ...

Why?

Because ATI dropped Linux driver support for this card YEARS ago!

The last Ubuntu release to include that support was 8.10 -- and the OP already indicates they are running 10.10.

The only working drivers are already installed by default, otherwise, you would not be seeing a desktop.

There are no newer drivers you can download that will work with your card and Ubuntu versions newer than 8.10.


I think the additional drivers advice is still better than telling the OP to go to ATI's website and install them manually. if the jockey application can't find them, then leave well enough alone. 


to the original poster: the open source drivers for those old ATI cards hit their peak back in  the 10.04 era, then went downhill from there. You could install that, instead of 10.10, or the latest version,  11.10, and run Unity 2d, which isn't that bad. I also wouldn't rule out installing 8.04. It's old, no longer supported with security updates, and the software in the repositories is over 4 years old, but you'd get peak performance out of that old card, because as Mark Phelps just said, the ATI drivers in that version will work with that card. Or, you could just upgrade the thing to something newer.

---

### Post by mastablasta on 2012-01-12
> **waynefoutz said:**
> I think the additional drivers advice is still better than telling the OP to go to ATI's website and install them manually. if the jockey application can't find them, then leave well enough alone. 
.
 
no- if it doesn't find them then it means you can only use opensource drivers. and if you have older version of Ubuntu you can upgrade them using PPA. more here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
>  
to the original poster: the open source drivers for those old ATI cards hit their peak back in the 10.04 era, then went downhill from there. You could install that, instead of 10.10, or the latest version, 11.10, and run Unity 2d, which isn't that bad. I also wouldn't rule out installing 8.04. It's old, no longer supported with security updates, and the software in the repositories is over 4 years old, but you'd get peak performance out of that old card, because as Mark Phelps just said, the ATI drivers in that version will work with that card. Or, you could just upgrade the thing to something newer.
what do you mean "hit their peak"?
 
They still work fine. tested a 9200 with Kubuntu11.10 on 1 GB ram. works just fine.
additionally - ran a 16MB ATI rage card on Ubuntu 10.04. OK the effects had to be disabled, but all in all it worked fine. resolution was the propper one. hadnt' noticed any issues with it.
 
Also using a 32MB built in GPU S3. ok i had to use Chrunchbang (Debian stable) cause the maschine has 256MB all together- it all works fine. flash videos, videos...no big issues.

---

### Post by Mark Phelps on 2012-01-12
> **waynefoutz said:**
> I think the additional drivers advice is still better than telling the OP to go to ATI's website and install them manually. if the jockey application can't find them, then leave well enough alone.
Since this forum is ABT, we should NOT be telling posters to do something that we already know will not work.  That will just make them more frustrated than they already are!  But, I agree that is better than their downloading the wrong drivers manually and trashing their display in the process. 

> to the original poster: the open source drivers for those old ATI cards hit their peak back in  the 10.04 era, then went downhill from there.
My experience is that the open source drivers have improved a lot with 11.10.  I get full screen resolution (again) and can run multiple monitors.  On previous Ubuntu versions, I had to use the restricted drivers to do that.

> I also wouldn't rule out installing 8.04. It's old, no longer supported ...
Again, this is ABT ... let't not be telling folks to jump into a version that is not supported.  They will have even MORE problems when they do that.

> Or, you could just upgrade the thing to something newer.
Actually -- NO they can't (probably).  They are using a LAPTOP, and given it's using a really old ATI 9xxx chipset, it most likely will NOT take a video card.

---

### Post by Gnome Defender on 2012-01-12
Thanks for your comments,

The discussion above reflects my confusion on the matter.  I'm familiar with what is being discussed -- only because I've read little about it on old tutorials and threads, etc.  I'm not so much of a frustrated idiot, as Mark Phelps continually implied in his dominating posts; however, I'm a beginning that would like to know what other graphic cards are supported by Ubuntu (even when I've just read a chart that totally contradicted what Mark just said).  Also, I would like to know if I have more options.

I've seen Ubuntu 10.10 being run with a 9xxx ATI.  I thought because of this, I would be able to run my graphics card on it.  Would downgrading be the better idea?  Or should I consider switching to Kubuntu 11.10?  I've seen the graphic card work there too, but I don't know enough about Kubuntu 11.10 to really say what it can do for sure.

Thanks,
Gnome Defender

EDIT:
This is the chart I'm referring to.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by waynefoutz on 2012-01-12
> **mastablasta said:**
> no- if it doesn't find them then it means you can only use opensource drivers. and if you have older version of Ubuntu you can upgrade them using PPA. more here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 

what do you mean "hit their peak"?
 
They still work fine. tested a 9200 with Kubuntu11.10 on 1 GB ram. works just fine.
additionally - ran a 16MB ATI rage card on Ubuntu 10.04. OK the effects had to be disabled, but all in all it worked fine. resolution was the propper one. hadnt' noticed any issues with it.
 
Also using a 32MB built in GPU S3. ok i had to use Chrunchbang (Debian stable) cause the maschine has 256MB all together- it all works fine. flash videos, videos...no big issues.


I have a laptop with an ATI "legacy" card in it, 10.04 worked pretty good. Anything after, performance got progressively worse.
Right now, I have 10.04, with the KDE desktop on it, it runs fairly well.

---

### Post by waynefoutz on 2012-01-12
> **Gnome Defender said:**
> Thanks for your comments,

The discussion above reflects my confusion on the matter.  I'm familiar with what is being discussed -- only because I've read little about it on old tutorials and threads, etc.  I'm not so much of a frustrated idiot, as Mark Phelps continually implied in his dominating posts; however, I'm a beginning that would like to know what other graphic cards are supported by Ubuntu (even when I've just read a chart that totally contradicted what Mark just said).  Also, I would like to know if I have more options.

I've seen Ubuntu 10.10 being run with a 9xxx ATI.  I thought because of this, I would be able to run my graphics card on it.  Would downgrading be the better idea?  Or should I consider switching to Kubuntu 11.10?  I've seen the graphic card work there too, but I don't know enough about Kubuntu 11.10 to really say what it can do for sure.

Thanks,
Gnome Defender

EDIT:
This is the chart I'm referring to.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

My old laptop has an ATI Radeon x1270 in it. I had the best results with Kubuntu 10.04, actually, I think it's running Linux Mint 9, KDE, which is basically the same animal.



Another great option would be LegacyOS, [http://puppylinux.org/wikka/LegacyOS]("http://puppylinux.org/wikka/LegacyOS") It's a version of Puppy Linux with the  2.6.18 kernel and an older version of Xorg, so the ATI Catalyst drivers should work, although you'd probably have to install them  yourself. This is the only dstro I know of that's aimed at older, unsupported hardware like this.

I think downgrading would be a better plan, since 10.10 is hitting end of life soon. Honestly, I'd try the latest version, 11.10. Unity 2d is not that bad.

---

### Post by Mark Phelps on 2012-01-13
> **waynefoutz said:**
> I have a laptop with an ATI "legacy" card in it, 10.04 worked pretty good. Anything after, performance got progressively worse.

My old desktop had an ATI x1650 "legacy" card and while it worked OK with Ubuntu 9x and 10x, when the 11.10 came along, the open-source drivers worked much better.

But ... maybe the only improved them for the X1nnn series of ATI legacy cards.

---

### Post by mastablasta on 2012-01-13
well KDE (Kubuntu) does draw the windows differently from gnome so why not give it a try and see what happens. it's still Ubuntu under it.

you card: 
RS300                       Radeon 9100 IGP

is in the section that says has good hardware accelerated suspport.

and it also clearly says it here:

**Getting better 3D support**

 For  r300-r500 (Radeon 9500 - X2300) cards, the r300g driver is a newer 3D  driver based on Gallium3D. It is the default 3D driver in Ubuntu  Natty/11.04 and newer releases. If you're still running an older Ubuntu release you can add the very experimental [xorg-edgers PPA]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") Likewise,  for r600-r700 cards, the r600g Gallium3D-based driver is available from  the xorg-edgers PPA. It is also enabled by default from Ubuntu  Natty/11.04 on.

edit: what is supported? a list is here but this is by far not a full list:
[http://www.ubuntu.com/certification/catalog](http://www.ubuntu.com/certification/catalog)

---

### Post by Gnome Defender on 2012-01-13
Thank you all,

After some more tweaking, I was able to install what I believe to be the graphic drivers, but as Mark predicted, the performance was not up to par on my laptop.  I think I'll give Kubuntu a try.  I'm making a disk as I type.  But for now, this inquiry has been answered. 

Cheers,
Gnome

---

