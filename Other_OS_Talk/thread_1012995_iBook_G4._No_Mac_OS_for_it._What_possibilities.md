---
title: "iBook G4. No Mac OS for it. What possibilities?"
date: 2008-12-16
forum: Other OS Talk
---

### Post by Roasted on 2008-12-16
I love Ubuntu, but from what I understand they dropped PowerPC support. What's the next best option? Does Linux Mint support PowerPC? 

I'd really like something as close to Ubuntu as possible.

---

### Post by fistfullofroses on 2008-12-16
Slackintosh.

---

### Post by mips on 2008-12-16
You could also try Debian, Gentoo, Arch, OpenBSD, FreeBSD, NetBSD

See these links for more options.
[http://penguinppc.org/about/distributions.php](http://penguinppc.org/about/distributions.php)
[http://lowendmac.com/linux/index.shtml](http://lowendmac.com/linux/index.shtml)

---

### Post by init1 on 2008-12-16
> **Roasted said:**
> I love Ubuntu, but from what I understand they dropped PowerPC support. What's the next best option? Does Linux Mint support PowerPC? 

I'd really like something as close to Ubuntu as possible.
You could use an older version of Ubuntu. Gutsy was the last official PPC release, but there's an unofficial Hardy. 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by fistfullofroses on 2008-12-16
Of all of those listed at any site, the only ones that stand out as worth while are Slackintosh and Gentoo. Debian distros are over done, and so many packages have been so heavily modded to be x86 only that you end up having only a handful of ppc compatible packages. You would likely only be able to use source debs. Arch isn't a bad option, I personally just do not care too much for arch.

---

### Post by Roasted on 2008-12-24
Any other ideas? I tried Slackintosh but it's kind of confusing. It's telling me to run mac-fdisk to set up partitions... yet I run the command and it yells at me. Yeah...

Any other choices? I may try Debian... since I'm an Ubuntu fan and all... But I figured I'd ask here again.

---

### Post by DeadSuperHero on 2008-12-24
Hmm. It's PowerPC. Theoretically, you COULD run AmigaOS 4.1 on it.
If that works, and works well, than I sure know what I'm buying this coming year!

---

### Post by mips on 2008-12-24
> **Mr. Psychopath said:**
> Hmm. It's PowerPC. Theoretically, you COULD run AmigaOS 4.1 on it.
If that works, and works well, than I sure know what I'm buying this coming year!

Won't work. It works to some degree on certain macminis.

---

### Post by zmjjmz on 2008-12-24
How about ArchPPC? Just make sure you follow the Arch beginner's wiki.

---

### Post by notwen on 2008-12-24
+1 [Debian PPC]("http://www.debian.org/ports/powerpc/").

---

### Post by Roasted on 2008-12-24
Is the install CDs for PowerPC Debian supposed to be 20 CDs long? Or am I not understanding something right on their download section of their site...

---

### Post by zmjjmz on 2008-12-24
> **Roasted said:**
> Is the install CDs for PowerPC Debian supposed to be 20 CDs long? Or am I not understanding something right on their download section of their site...

AFAIK, the first one is the installer, the rest are the repos

---

### Post by Roasted on 2008-12-24
So I take it I dont need them all?

---

### Post by Roasted on 2008-12-25
I installed Debian. But now my wireless + wired doesn't work. I know the wired works cause I used it before with OS X, but Debian doesn't pick it up, under both DHCP and Static. Grr...

---

### Post by jrusso2 on 2008-12-25
> **fistfullofroses said:**
> Of all of those listed at any site, the only ones that stand out as worth while are Slackintosh and Gentoo. Debian distros are over done, and so many packages have been so heavily modded to be x86 only that you end up having only a handful of ppc compatible packages. You would likely only be able to use source debs. Arch isn't a bad option, I personally just do not care too much for arch.

I don't know Linus has a PowerPC and runs Fedora on it so there must be
something good about it.

---

### Post by mikjp on 2008-12-25
For example Debian and NetBSD.

---

### Post by redsoxreed on 2008-12-25
I would personally go for Debian.  If you really like Ubuntu, you can get community supported, up to date powerpc releases here:

[http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/)

---

### Post by billgoldberg on 2008-12-25
What are you talking about, Ubuntu 8.10 has a power pc version.

[http://cdimage.ubuntu.com/ports/releases/8.10/release/](http://cdimage.ubuntu.com/ports/releases/8.10/release/)

---

### Post by Roasted on 2008-12-25
> **billgoldberg said:**
> What are you talking about, Ubuntu 8.10 has a power pc version.

[http://cdimage.ubuntu.com/ports/releases/8.10/release/](http://cdimage.ubuntu.com/ports/releases/8.10/release/)

Wow. What in the world? Did Ubuntu just drop official support for PPC with LiveCDs? Or what?

---

### Post by redsoxreed on 2008-12-25
It's really hard to find a PowerPC live cd for *any* distro nowadays.  I gave up the search long ago.

---

### Post by Roasted on 2008-12-25
> **redsoxreed said:**
> It's really hard to find a PowerPC live cd for *any* distro nowadays.  I gave up the search long ago.

Oh. I don't need a LiveCD. I can manage with an alternative install. I'm just so confused over why I kept hearing official support dropped when it's obviously here via alternate install.

Pop Quiz Question of the Day: If I install PPC Ubuntu 8.10 for this iBook G4, which is listed as officially supported with this PPC version, should the wireless work? I could not connect to my wireless network (even with security off) when I was running Debian on it.

---

### Post by redsoxreed on 2008-12-25
I suspect that it would work out of the box, but I may be wrong.  You might need to install a driver package.  A typical debian install is lighter than a typical ubuntu install, so less wireless cards are supported without installing drivers yourself.

---

### Post by Roasted on 2008-12-26
New problem. Installing Ubuntu 8.10 on the alternate CD. Eventually it says that my CD rom drive isn't found to load the necessary files. Yet, I'm booted to the CD and I'm in the installer. LOL?

---

### Post by redsoxreed on 2008-12-26
You may have to do a netinstall.  Or a USB key install.  Either way, you're probably going to end up with a minimal system which may require you to manually install a wireless driver.

---

### Post by Roasted on 2008-12-26
Do you have any idea where I would retrieve 8.10 drivers for an iBook G4? I've googled a bit but the only things I dug up on wireless/ibookg4/ubuntu was people with problems with it.

---

### Post by redsoxreed on 2008-12-26
Do you have access to a terminal?  Type in the command "lspci" so we can identify your network chipset.  Airport extreme?

---

