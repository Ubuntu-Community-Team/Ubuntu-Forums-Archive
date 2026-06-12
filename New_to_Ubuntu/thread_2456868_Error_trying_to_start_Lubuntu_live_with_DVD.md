---
title: "Error trying to start Lubuntu live with DVD"
date: 2021-01-21
forum: New to Ubuntu
---

### Post by penglinuxer on 2021-01-21
Hi, I'm new to Linux and wanted to use it to recover a Pentium 3 (768MB RAM, 20GB HDD). I therefore chose to use Lubuntu 16.04.3 32 bit Desktop version. I wanted to run it live using a DVD. Unfortunately it seems that the bios does not allow, or even I am not able to set it up, to use a self-starting USB drive. So I burned the iso image with Ashampoo. When I launch the system startup I get the error:

Error 8000 reading sector 450560
No DEFAULT or UI configuration directive found!
boot:

I've read around that this error can happen but for USB drive installations. How should I behave in my case?
Many Thanks

---

### Post by Impavidus on 2021-01-21
Did you check the dvd for burning errors? That's my first guess for obscure booting errors on a live disk.

Further note that Lubuntu 16.04 is already end of life. The parts it has in common with Ubuntu 16.04 will reach end of life in 3 months. Lubuntu 18.04, which is the last version to support 32 bit systems, will reach end of life in 3 months too.

To be honest, I would hand such an old computer in for recycling.

---

### Post by guiverc on 2021-01-21
Lubuntu 16.04 LTS being a flavor of Ubuntu had only 3 years of supported life ([https://lubuntu.me/xenial-5-released/](https://lubuntu.me/xenial-5-released/) [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)) which ended 2019-April.

 Ubuntu 16.04 LTS Server (no desktop) or Desktop (Unity 7) have 5 years of supported life and are still supported. Refer release notes, or use `ubuntu-support-status` or your own system to confirm this is the case.

The error to me sounds like your ISO/media is faulty (did you check it's integrity; [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) and then then check the write to your installation media ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck))

I used pentium M & pentium 4 computers to test Lubuntu 18.04.5 LTS (August 2020), and later releases which are now EOL (eg. Lubuntu 18.10 & Lubuntu 19.04 *in* *alpha*), however I haven't used pentium II or III machines since maybe 10.04.

---

### Post by ActionParsnip on 2021-01-21
Did you burn the DVD as slowly as possible

---

### Post by penglinuxer on 2021-01-21
I burned it at 2x with verify. I'll try to investigate the posts you suggested.
Despite this could it be better to burn with the relative Windows utility?
I read that someone uses ImgBurn. Can you suggest something of reliable?
Another point: burning an iso image makes a dvd bootable by default or not? 
About the version, in the download page it seems the unique most recent to apply for a 32 bit system. There is also 19.4 but only as Alternate and maybe I'm wrong but the Desktop seems more indicated for little experience and a minimum of graphic support in order to use it live (at least as a very first beginning).

---

### Post by yancek on 2021-01-21
The sites from which you can download an Ubuntu iso (or derivative such as Lubuntu) almost always have instructions on doing an md5 or sha checksum so that you can verify the download was not corrupted.  Not much point in burning an iso to a DVD or putting it on a usb if it is corrupt.  When you write it to a DVD, the software you use should have an option similar to 'burn as an image' as simply copying it to the DVD will not make it bootable.

As pointed out by others, you are using an outdated and unsupported version of Lubuntu.  Curious about how you managed to find that?  How old is the computer hardware you are using?

---

### Post by penglinuxer on 2021-01-21
Hi yancek and khurram83, the only thing I'm thinking is that I downloaded the iso with my phone and then I moved it on the pc for burning because currently it is not connected, maybe something has changed during the passage... Anyway definitively I must verify better the iso preparation.
The available versions are on [https://lubuntu.net/downloads/](https://lubuntu.net/downloads/) and the latest is 19.4. 
The hardware is 2001 if I'm not wrong so a 32 bit distro is mandatory. 
It could be that there are others distros more supported for 32 bit but I need for a not expensive one as resource requirement (Puppy? Mint?....) and at the same time quite user-friendly.

---

### Post by Paddy Landau on 2021-01-21
Please note that [lubuntu.net]("https://lubuntu.net") is *not* the official website, and is *not* approved by Lubuntu. Lubuntu has asked the owner to close it down, but he refuses, even though it's badly out of date and keeps cropping up on internet searches. There's also no guarantee that the packages are correct.

The correct website is [lubuntu.me]("https://lubuntu.me/").

The [latest available 32-bit version]("https://lubuntu.me/downloads/") is 18.04, which is supported for another two years or so. As Lubuntu thereafter supports only 64-bit, I would avoid it and try something that does support 32-bit.

A good alternative is [Bodhi Linux]("https://www.bodhilinux.com/"). Although it's not an official Ubuntu derivative, it's based on Ubuntu and is quite popular, and might be able to cope with your ancient hardware! (Bodhi doesn't work with UEFI, but I'll bet that your hardware doesn't have it anyway.)

If even Bodhi is too much for your computer, try [antiX Linux]("https://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html"). It's based on Debian, but not Ubuntu. It comes with a light version and a "Full" version. The light version is lighter than Bodhi and might do the trick.

Keep us updated!

---

### Post by Impavidus on 2021-01-21
The official site for Lubuntu is lubuntu.me, not lubuntu.net. That's an annoying cybersquatter.

The Pentium III is a 32 bit processor, so you can only use a 32 bit operating system. 19.04 was the last version of any Ubuntu flavour that supported 32 bit, bit it was an interim release with only 9 months support, so it's dead now. 18.04 was the last long term support release with 32 bit and is still supported. That's the only somewhat viable option to try in the Ubuntu family.

There are other Linux distros specifically targeting ancient hardware like yours. Whatever you try, you'll be severely limited in the kind of software you can run on that computer. It may still be a decent typewriter.

---

### Post by CelticWarrior on 2021-01-21
First of all, DEBIAN 32-bit or, eventually, some still supported derivative that still does 32-bit. As such, nothing from Ubuntu family. Yes, there was a time when a 32-bit Lubuntu would be the best option for such machine but we passed that point already. As commented before, the last Lubuntu 32-bit release will be EoL (end of life) in April. And, incidently, the website you downloaded Lubuntu from isn't official, it's a cybersquater. [https://lubuntu.me/](https://lubuntu.me/) is the official one.

Secondly, whatever you choose as distro you'll be facing the same problems with the installation media and with the ISO file. Also as commented above you need to have a proper download, then you need to burn it correctly - it's not a DVD-ROM with the ISO file inside, a software supporting drive image files (that's what an ISO is) must be used with the function to burn image to disk. Then, the drive in the target computer must support DVDs and, obviously, be in a working condition. Given the hardware's age neither is a given.

And unfortunately, unless you're into retrocomputing and have a clear idea of what to do with it, you're wasting your time (and electricity) with something of little to no use for the current requirements.

---

### Post by Paddy Landau on 2021-01-21
> **CelticWarrior said:**
> … the last Lubuntu 32-bit release will be EoL (end of life) in April.
The last Lubuntu 32-bit release was 18.04, which will reach first-stage EOL this April, but final [EOL in April 2023]("https://lubuntu.me/downloads/") — another two years to go. Still, it's best to move on from Lubuntu for 32-bit architecture.

It won't be much longer before 32-bit becomes a specialist niche, much as 16-bit and 8-bit are today.

---

### Post by penglinuxer on 2021-01-21
Thanks for your point of view. I realize that being the first hours that I study how to approach the problem I still have a lot to learn (even to choose the official site ...).
At least for the moment I have no intention of buying more hardware because the purpose is to put on a PC that I will use for basic operations of moving files from the cloud to external drives for backup management. But this is also an excuse to have fun approaching linux. Having said that at least the DVD player still seems to work fine and so does the rest within its age limit.
So now I think locally about all the suggestions I had and start again more aware. I'll keep you up-to-date.
Thank you very much.

---

### Post by CelticWarrior on 2021-01-21
The rationality of such decision depends on how you'll use it.

Something dirty cheap as a [RockpiX]("https://wiki.radxa.com/RockpiX"), a 64-bit single board computer capable of running Windows 10 64-bit or any modern 64-bit Linux distro **for years to come**, with at least one **USB3.0** port (and several USB2.0 ports) and gigabyte **Ethernet** + **WiFi**, can boot from a cheap microSD card, is **by orders of magnitude more powerful and usable** than a 20 years old desktop PC (actually a [COLOR=#000000]Pentium 3 / 768MB RAM / 20GB HDD) is several years older than that).
The RockpiX uses ~10Wh, worse case scenario (full CPU+GPU load, several peripherals). How much does your old PC consumes? Well, it can be higher than 200Wh. So, depending on how much time it'll be running, **it can rapidly become more expensive running it than buying and running the RockpiX**.

And then there are obvious limitations that you're ignoring but shouldn't.
For
> [/COLOR][COLOR=#000000]moving files from the cloud to external drives for backup management[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]2 (two) conditions, at least, must be met, an adequate internet connection and support for said external drives. Are you really intending to use an old Ethernet, at least 10x slower than the current standard, the accepted minimum? Or WiFi? Even if you find one that works with it, it'll timeout before you reach "the cloud"... And how are you planning to connect the "external drives"? To the old USB1.1 ports? Even if they work - very unlikely for any modern USB HDD - everything will be soooooo slow to the point of being [/COLOR]*de facto*[COLOR=#000000] unusable. It'll take many hours pumping those 200W or more to do the same that the cheapest single-board computer would do in minutes![/COLOR]

[COLOR=#000000]And finally you must keep in mind at all times the age of the hardware. That means that literally anything may fail anytime, especially the 20GB HDD. Actually that one most likely already failed and if not it'll fail very very soon. You won't find a replacement but an IDE-to-CompactFlash adapter + a the card is a cheap(ish) and reliable solution moving on. If the RAM fails, forget it, even if you can find compatible replacement it'll cost you MORE that the RockpiX! The DVD drive almost certainly failed already. How exactly did you test it? Keep in mind DVD drives use two different lasers for DVDs and CDs, one may fail and not the other. If it doesn't read DVDs then it's useless even for the purpose of installing Linux. And so on and so forth...[/COLOR]

[COLOR=#000000]My suggestion: If the DVD drive actually works, install Windows 98SE, do NOT connect it to the internet under no [/COLOR][COLOR=#000000]circumstance, install some period appropriate games and enjoy its final days in an amusing way. Or send it to be recycled. Anything else is wishful thinking.

Sorry if this sounds harsh but I'm trying to save *you* from *yourself*&#8203;.[/COLOR]

---

### Post by Impavidus on 2021-01-21
> **penglinuxer said:**
> ... that I will use for basic operations of moving files from the cloud to external drives for backup management.
You may have to use a command line tool to access the cloud. Normal web browsers have needed sse2 for quite some time now, something your processor doesn't offer. It was introduced with the Pentium 4 in 2000. See for example this thread from 3 years ago: [https://ubuntuforums.org/showthread.php?t=2382079](https://ubuntuforums.org/showthread.php?t=2382079)

---

### Post by CelticWarrior on 2021-01-21
> **Impavidus said:**
> You may have to use a command line tool to access the cloud. Normal web browsers have needed sse2 for quite some time now, something your processor doesn't offer. It was introduced with the Pentium 4 in 2000. See for example this thread from 3 years ago: [https://ubuntuforums.org/showthread.php?t=2382079](https://ubuntuforums.org/showthread.php?t=2382079)

Yes, of course!!!!
I wrote a wall of text thinking I was covering everything and failed mentioning the most obvious one. Shame on me.

---

