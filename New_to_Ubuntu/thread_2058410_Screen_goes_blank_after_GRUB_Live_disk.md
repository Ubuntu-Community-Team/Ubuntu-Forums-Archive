---
title: "Screen goes blank after GRUB Live disk"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by volos on 2012-09-15
I am trying to upgrade to 12.04.  Made a live cd and usb drive.  Both md5sums look good and both disk check out with no problem on my desktop.  Trying to install on my Asus U50F now.  GRUB loads then no matter which option is chosen, the screen goes black (everything is still on any kind of progression stops).

So then I went back, pressed 'e' to mod the boot comands.  I tried adding both nomodeset and/or acpi_osi=off with no change.  I added these on the line that starts with Linux before the '--'

What else can I try/do?  The 11.10 cd doesn't seem to have this problem.

Using the 64-desktop, considering my slow connections, downloading the alternate iso would be my last choice.

Thanks

Also I didn't quite know if this should go in install or Asus support, and I'm still pretty knew so I put it here.
I know think I've tried everything here with no luck:
[http://askubuntu.com/questions/133467/ubuntu-12-04-boot-hangs-with-a-black-screen-before-grub-menu-after-upgrade-gma5](http://askubuntu.com/questions/133467/ubuntu-12-04-boot-hangs-with-a-black-screen-before-grub-menu-after-upgrade-gma5)

---

### Post by Bashing-om on 2012-09-15
volos; Hi ! Welcome to the forum.

 Be advised you are not being ignored. Just at this time I am scratching my head as what else to advise you of.
1. You are attempting to install along side windows as dual boot ?
 2. Please post your system's full specs ....will see what I can find out as to why you are having such difficulties (like not enough room for ubuntu to install on ? or windows has all 4 primary partitions used ?).
3. In booting ubuntu ...can you boot up in the "try ubuntu" mode ? 
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by volos on 2012-09-15
> **Bashing-om said:**
> volos; Hi ! Welcome to the forum.

 Be advised you are not being ignored. Just at this time I am scratching my head as what else to advise you of.
1. You are attempting to install along side windows as dual boot ?
 2. Please post your system's full specs ....will see what I can find out as to why you are having such difficulties (like not enough room for ubuntu to install on ? or windows has all 4 primary partitions used ?).
3. In booting ubuntu ...can you boot up in the "try ubuntu" mode ? 
[INDENT]regards <==BDQ
[/INDENT]

1) yes I've been dual booting with win7 for years now.  My bandwidth is a premium, and I don't do much online, so I tend to jump a few versions each time I upgrade.  I've got the hd split into 3 partitions: win7, ubuntu 11.10, and the swap.  I want to go over the previous install, and I don't think space is a problem anyway.

Infact, given as this happens after I make my selection from the grub menu, I don't think this is related to the HD at all.  Further proof of that is found when I just did a reinstall of 10.04 kubuntu and subsequently an install of 11.10 all from live dvds.

I orginally, before my first post, thought my problem was my iso file, even though md5 checked out and the live disk (usb) checked out on my desk top (as well as installing there).  So I downloaded the iso again (major deal for me because low bandwidth and paying by useage), and burned it on a dvd.  Again everything checks out when tested on desktop.

I run into this problem with both live diskd (usb and dvd).

2) here are the specs:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220763](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220763)

3) no as I mentioned in the first post, it doesn't mater which selection, they don't work.  The memory test isn't an option just try w/o install, install, and check disk.  None of them work.  I can play around in GRUB but I really don't feel comfortable there.

I would try to report this as a bug, but I don't even know how I would get log information out of this.

Any ideas will be appreciated.

---

### Post by Epodx64 on 2012-09-15
try appending this to grub
"acpi_osi=Linux"

if that doesn't work could be KMS is pulling the wrong or failing to auto-detect you're EDID for your display so you might have to force the display with this

"video=1280x1024-24@75"

---

### Post by volos on 2012-09-16
I had already tried "acpi_osi=Linux" but it didn't work. 

This was the trick "video=1280x1024-24@75" 	
Well I changed it to the native res (1366 x 768) but it worked.

I did have to hard code it in now, and so it's working on reboot.

Thanks.

Is there a way to try to get a bug on what went wrong, so maybe it can be fixed?

---

### Post by bogan on 2012-09-16
Hi!,** Epodx64,**

You Posted:> you might have to force the display with this

"video=1280x1024-24@75"Please clarify: does that mean either add that code to the Linux Boot line in the grub menu script, or add it as a new line in /etc/default/grub; or should it be added to the: 'GRUB_CMDLINE_LINUX=' line in the later.

Is that code the equivalent of 'VGA-795', or other value?
Thnkx,

Chao!, **bogan,**

---

### Post by Epodx64 on 2012-09-16
> **bogan said:**
> Hi!,** Epodx64,**

You Posted:Please clarify: does that mean either add that code to the Linux Boot line in the grub menu script, or add it as a new line in /etc/default/grub; or should it be added to the: 'GRUB_CMDLINE_LINUX=' line in the later.

Is that code the equivalent of 'VGA-795', or other value?
Thnkx,

Chao!, **bogan,**

You should amend "video=1280x1024-24@75" to the Linux Boot line 
It's not the equivalent of VGA-795 because it will load the i915 (or ageing radeon cards with the open source radeon drivers) driver what's happening is the KMS auto detection fails with either a rare or incorrect EDID from the monitor.

---

### Post by Epodx64 on 2012-09-16
> **volos said:**
> I had already tried "acpi_osi=Linux" but it didn't work. 

This was the trick "video=1280x1024-24@75"     
Well I changed it to the native res (1366 x 768) but it worked.

I did have to hard code it in now, and so it's working on reboot.

Thanks.

Is there a way to try to get a bug on what went wrong, so maybe it can be fixed?

As far as I know there's already been a bug fix committed to the Kernel for some reason KMS auto detection fails because the monitor (display) either has a rare EDID or is giving the wrong EDID.

by the way EDID=Extended display identification data

---

