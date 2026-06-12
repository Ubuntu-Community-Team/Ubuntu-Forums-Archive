---
title: "Made a HUGE mistake"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Libertine on 2008-08-21
Hey everyone, I just bought a new Sony Vaio and decided to install Ubuntu on it, completely formatting the hard drive. Ubuntu didn't work out completely since there were issues with the wireless card and the onboard speakers, so I threw in my old Windows XP CD with the intention of installing that but I got a message telling me that the installer couldn't find a hard drive. I assumed this was because my hard drive had an ext3 partition, so I booted up on an Ubuntu Live CD and deleted it, creating an ntfs partition. Then I booted up using my XP disc and it still can't find a hard drive. As you can see, this leaves me with a laptop that doesn't work :(

Can anyone help me install Windows XP? I received no recovery disks with my laptop (unfortunately).

---

### Post by adult swim on 2008-08-21
dont worry, your hard drive isnt messed up.  xp doesnt natively install on a SATA drive like you probaly have.
i dont have any experience with this but check out this site
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

---

### Post by Libertine on 2008-08-21
> **adult swim said:**
> dont worry, your hard drive isnt messed up.  xp doesnt natively install on a SATA drive like you probaly have.
i dont have any experience with this but check out this site
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)
Thanks a lot, I'll try this :KS

---

### Post by ooobuntooo on 2008-08-21
*post removed by user*

---

### Post by Libertine on 2008-08-21
Okay well it seems that I can't use that method since Sony does not provide XP drivers for their new laptops. Will I have any troubles installing Vista on a SATA drive?

---

### Post by adult swim on 2008-08-21
vista will install.  i would bet if you dugg deep enough, you could find an xp driver.  do you know the model of your hard drive?

---

### Post by Loaded.len on 2008-08-21
Just go into your BIOS and turn off AHCI.  Some BIOS are a bit different, it might only give you options to configure the SATA operation as RAID, or AUTO-DETECT.  But basically it's the Advanced Host Controller Interface that XP doesn't support natively.

---

### Post by Libertine on 2008-08-21
This is the required Vista driver: [https://esupport.sony.com/CA/perl/swu-download.pl?mdl=VGNFW140D&upd_id=3638&os_id=28](https://esupport.sony.com/CA/perl/swu-download.pl?mdl=VGNFW140D&upd_id=3638&os_id=28)

I would try it for XP, but nLite requires .inf files, not .exe files.

---

### Post by Libertine on 2008-08-21
> **Loaded.len said:**
> Just go into your BIOS and turn off AHCI.  Some BIOS are a bit different, it might only give you options to configure the SATA operation as RAID, or AUTO-DETECT.  But basically it's the Advanced Host Controller Interface that XP doesn't support natively.
The BIOS is very limited on this machine, the only options I can change are the time/date, passwords, and boot orders.

---

### Post by adult swim on 2008-08-21
from nlites website
"My drivers are exe files! How do I integrate them?
It's only possible with extractable drivers. Extract that exe file with right click and choose Extract To... (you can use Winrar for that). After extraction find folder with INF file(s) in it and select any of them."

---

### Post by Loaded.len on 2008-08-21
Well, if that's the case, you have the following options...


[LIST=1]
[*]hack the BIOS. (void your warranty, and maybe brick your laptop) - not recommended.
[*]slipstream the Intel Matrix Storage Manager into your XP disc (there are a ton of forum posts around the net on how to do this...as also referenced by previous replies to this thread)
[*]Install Vista (supports AHCI out of the box)
[/LIST]

One thing I haven't tried, but is probably the easiest is to hit F6 during setup and give it the drivers on seperate media.

---

### Post by Libertine on 2008-08-21
> **adult swim said:**
> from nlites website
"My drivers are exe files! How do I integrate them?
It's only possible with extractable drivers. Extract that exe file with right click and choose Extract To... (you can use Winrar for that). After extraction find folder with INF file(s) in it and select any of them."
This didn't work for me :(

---

### Post by Libertine on 2008-08-21
> **Loaded.len said:**
> Well, if that's the case, you have the following options...


[LIST=1]
[*]hack the BIOS. (void your warranty, and maybe brick your laptop) - not recommended.
[*]slipstream the Intel Matrix Storage Manager into your XP disc (there are a ton of forum posts around the net on how to do this...as also referenced by previous replies to this thread)
[*]Install Vista (supports AHCI out of the box)
[/LIST]

One thing I haven't tried, but is probably the easiest is to hit F6 during setup and give it the drivers on seperate media.

I think I'll just install Vista...today has put me off messing around with operating systems for a little bit :lolflag:

---

### Post by bitninja on 2008-08-21
> **Loaded.len said:**
> Well, if that's the case, you have the following options...


[LIST=1]
[*]hack the BIOS. (void your warranty, and maybe brick your laptop) - not recommended.
[*]slipstream the Intel Matrix Storage Manager into your XP disc (there are a ton of forum posts around the net on how to do this...as also referenced by previous replies to this thread)
[*]Install Vista (supports AHCI out of the box)
[/LIST]

One thing I haven't tried, but is probably the easiest is to hit F6 during setup and give it the drivers on seperate media.

I'd try slipstreaming the driver like this guy suggested.

---

### Post by icecloud on 2008-08-21
not to be a tard but you should be able to format it with a seperate program there are some programs specifically designed to erase hard drives (boot & nuke) programs that run outside of windows and just inside dos but there should be just straight formating software you should be able to find it online (i'd try cnet) and see if there are any that work with formating a sata drive for xp installation. but the fact that your disc will not allow you to reformat the drive is puzzling in the fact that even if your pc is formatted in a different way your bios should tell the disc/program that runs from the disk whether or not you have a drive installed. it wont tell it its current configuration but it will usually allow you to see a drive. so you may also want to look into doing a bios update to see if that possibly helps the issue.

---

### Post by bitninja on 2008-08-21
Well that's the problem, XP doesn't even recognize the drive since it's a SATA drive. XP needs a driver slipstreamed in to be able to recognize the drive during the install. Whether it's formatted or not, if XP doesn't recognize the drive is even there it wouldn't matter.

---

### Post by icecloud on 2008-08-21
true...sorry :s didnt know if it would work or not just a couple of ideas :D

---

### Post by kelvin spratt on 2008-08-21
You need a proper xp install disk the original not the later upgrade discs that are issued of late I have 3 sata machines all built from new with XP. a XP install disk with sp2 will reconise your hardrive with no problem an upgrade install will not.

---

### Post by sherin on 2008-08-21
backing kelvin :)

---

### Post by anewguy on 2008-08-21
If it was a new laptop, did you truely remove ALL partitions?  I ask this only because most laptops (and a lot of desktops) now come with a "recovery" partition to reinstall the OS if you need to.  It won't help with your XP problem unless your pc came with XP.

---

