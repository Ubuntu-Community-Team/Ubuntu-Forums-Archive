---
title: "HP Pavillion dv9000 &amp; Ubuntu 14.04"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by paul136 on 2014-05-17
So, after much consideration, I've decided to revive an old dv9000 with the most recent 32bit version of Ubuntu (14.04). Everything seemingly went perfect for the install, but once I boot into Ubuntu 14.04, it crashes and freezes completely. I can't even go into the terminal by using Ctrl+Alt+F1. I have found it works for a brief moment before either randomly freezing, or freezing if I click on anything. I've heard it may have something to do with either Unity problems, or Wifi driver problems, but I can't seem to get anywhere since I can't even get to console to type in commands that were suggested to me. I would love to get this working, I'm sure there's a way. Any help would be extremely useful! let me know if more information is needed in order to troubleshoot and I'll do what I can to provide it :)

---

### Post by QIII on 2014-05-17
Hello!

Could you give us the hardware specifications on that machine?  It may be that it simply is not capable of managing Unity, in which case a lighter DE (like LXCE or Xfce) might be a better choice.

Cheers.

---

### Post by paul136 on 2014-05-17
Hey QIII,

Thanks for the reply! I'll take a look and see if I can send you specifics. I know it's very low end, so it wouldn't surprise me if that was the reason. I'll get back to ya.

Sidenote, is there an easier way to check specs without Windows? Otherwise I'll have to reinstall windows on there and run dxdiag. Thanks again!

---

### Post by Vladlenin5000 on 2014-05-17
[http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?sp4ts.oid=1842187&spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c00804539-1%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken](http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?sp4ts.oid=1842187&spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c00804539-1%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken)

Looks familiar? Albeit 'old' it should run the latest Ubuntu or even Windows 7 without much trouble. I've it running in a similar hardware, same nvidia but with 256MB, and Unity is quite usable with 304.xx drivers.

---

### Post by paul136 on 2014-05-18
> **Vladlenin5000 said:**
> [http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?sp4ts.oid=1842187&spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c00804539-1%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken](http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?sp4ts.oid=1842187&spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c00804539-1%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken)

Looks familiar? Albeit 'old' it should run the latest Ubuntu or even Windows 7 without much trouble. I've it running in a similar hardware, same nvidia but with 256MB, and Unity is quite usable with 304.xx drivers.

That's the one! I've been using Windows 7 Ultimate on it recently, but it is a complete dog sometimes (10mins+ to just load Firefox. But once loaded it works well enough). I think the video card has 128MB of VRAM however (Not 100% sure, Haven't reinstalled windows on it, but the BIOS settings for VRAM max out at 128MB). Thoughts on what the next steps I should take?

Sidenote: It very well could be that something internally is broken as well, but thought I'd try out some software first before digging into it's guts. So I'm not ruling that out as a cause. It was originally a work computer and was recently given to my girlfriend, both of which I don't think took very good care of it.

EDIT: Quick update! I somehow (don't really know how) got into what seems to be some sort of safemode and used a "Clean" option and the like to see if it might fix something and then I believe I resumed the boot into this safemode, and Ubuntu worked! Somewhat sluggishly, but no freezing at all! I clicked on everything to see if I could get it to freeze, and nothing. I thought I had fixed it, so I rebooted to see what would happen, and same issue. Freezes on startup. So There's some progress. Maybe getting back into that mode is the key to fixing this?

EDIT2: Found using Left Shift got me into the GRUB menus to go into recovery mode. Running memtest 86 right now.

EDIT3: memtest showed no errors, so I'm running Ubuntu in recovery mode and hard wired it and am running "***sudo apt-get update && sudo apt-get upgrade"***

---

### Post by paul136 on 2014-05-19
Issue resolved! Here's what I did in order to get things working properly for those having a similar issue.

1. Held Down Shift during Boot to go into GRUB menu
2. Booted into Ubuntu Recovery mode
3. Hard wired laptop, opened terminal and ran "sudo apt-get update && sudo apt-get upgrade"
4. Went into System Settings>Software & Updates>Additional Drivers
5. Installed Nvidia Drivers 304.117 (The tested one crashed a lot, so I went with the other)
6. Reboot

Thanks for pointing me in the right direction guys!

---

