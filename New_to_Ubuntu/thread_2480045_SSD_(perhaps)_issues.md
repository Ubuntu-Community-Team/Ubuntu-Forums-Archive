---
title: "SSD (perhaps) issues"
date: 2022-10-17
forum: New to Ubuntu
---

### Post by kbarber3 on 2022-10-17
This is the next stage, really, to my 'Numerous problems...' thread of a couple of weeks ago.  Mods: if you feel this belongs in 'Hardware', please move it and accept my apologies.

**My level of experience**
More-or-less rank beginner.  (*e.g.* I don't even know where to  look for system logs etc if anyone needs information from them.)  But  I'm not afraid of the command line and if someone holds my hand for a  while I can probably start to work out some of the simpler things for  myself.  Anything complicated will need spelling out, preferably in  words of one syllable.

**The Problem**
Following the saga of my previous thread I did a clean install, which seemed to resolve all the problems I'd been having.  After that was completed, the 'disks' utility showed just the 4TB HDD, leading me to conclude the SSD had failed.  Spent the rest of the week getting things set up; about halfway through the week I had to reboot the machine but in doing so I didn't think to check the boot order so can't say exactly what happened next.

At some point I looked at the 'disks' utility again and the HDD had been joined by the 500GB SSD!  Around the end of the week, the symptom of trying to open a program but nothing happening recurred, so I tried rebooting the machine.  This time it stopped going in before reaching the login screen and nothing I could do (including altering the boot order) would change it.  In the end the only way out that I could conceive was another clean install (even the 'try Ubuntu option on the bootable USB, although it worked, didn't seem to offer a way to get the installed version to boot).

All now seems to be well and the SSD is once more absent from the 'disks' utility, but I'm nervous; I don't have the time (or the patience) to do a clean install every weekend.

**Questions/advice I need**
When the machine was new the SSD was for software and the HDD for data.  Is that normal?  I imagine the SSD may have some kind of intermittent fault; is this a  reasonable conclusion?  If so, and if it remains sufficiently early in  the boot order, could it have been the means by which the machine did its midweek boot?  (I hadn't thought such a thing might be happening because I set the machine up to encrypt the disks when I first acquired it and there was no request for any encryption password during that boot.)  More to the point, is there some way in which a PC is biased to go to the SSD for software when one is visible?

If a PC is biased to load software from an SSD if one is visible, I imagine a failing SSD would cause the same sort of accumulating problems I reported in my previous thread?  Or at any rate, if it has booted from the SSD, it would presumably never look at the version installed on the HDD?  So is there any way (short of physical removal) I can lock out the SSD so the dud installation can no longer cause problems?  Will that have to be done every time the machine boots or can it be set and left?  (I'm rather assuming ensuring the SSD isn't in the boot order will prevent it being used to boot; if that's not the case I guess it will be physical removal?)

I found there's a Smart test option in the disks utility; I don't know if that's just a GUI controlled version of smartctl or something else?  I'm currently running a long test on the HDD with it, desperately hoping it's not going to spoil the result if I keep working as it runs.  I imagine it can't be used to test the SSD unless that disk is visible?  If I were to reboot the machine and let it use the SSD (if it wants to), what is the likelihood I can run a test on that without causing damage to the current good installation on the HDD?

I may well post further information, particularly test results (I hope others will be able to interpret them better than me) as they emerge.

I imagine (hope) installing a new SSD is reasonably straightforward physically, when the time comes?  But I guess it will need a clean install to put Ubuntu and all the software I use on the SSD?  At the moment, the strategy I have in mind is to nurse the machine through to the Christmas break, when I will have time to actually do the work so, subject to some of the answers I may get, you may find me seeking particular help then.

In the meantime, any answers or thoughts folk may have would be most welcome.

---

### Post by oldfred on 2022-10-17
Do you have good backups?
Or is second install on HDD your main install?
You need at minimum, backup of /home, any system settings you manually change in /etc and export of list of installed apps to make it easy to reinstall.

When you do not see SSD, does UEFI/BIOS see drive?
If drive not seen in UEFI/BIOS, no software will be able to find it.
That might indicate loose connection, bad cable or bad drive.

Is SSD a SATA drive or newer NVMe type?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

And to better document hardware, preferably when SSD seen:
Hardware doucumentation script, one line using && \ to make as one entry
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && \
chmod +x system-info && \
./system-info

---

### Post by Impavidus on 2022-10-17
It's normal to use the HDD for documents or media files and use the SSD for software: small stuff that you frequenly need on the fast drive and big stuff that you rarely need on the cheap drive. But this isn't built-in in the computer in any way. It's completely determined by how you install and configure your operating system. If your OS is on the SSD and it isn't visible, the OS won't boot. What could be the case is that you've got two Ubuntu installs, one on the SSD and one on the HDD. If the SSD is seen and is first in the boot order, the computer loads the bootloader on the SSD and then the OS pointed to by that bootloader; else it boots the one on the HDD. And with an intermittent fault on the SSD, strange things can happen.

Instead of a broken SSD, it could simply be a loose connector. That's likely to be intermittent and easily fixed.

Booting one OS and running some smart tests shouldn't affect the OS on the other drive. Not unless you start formatting it or mount it and delete some files.

---

### Post by TheFu on 2022-10-17
SSDs come in a few different types based on the protocol the connectors speak to the motherboard.

NVMe is the very, very, fast version.  The SSD looks like a RAM stick with electrical contacts on the short end.

SATA is the same protocol used by HDDs, but with much faster retrieval and storage of data than any HDD can come close to.  The SATA style SSDs come in 2 major types. One physically looks like the NVMe with electrical contacts on the short end, but it has a "key" slot to deferentiate between NVMe versions.  The other SATA SSD type looks like a 2.5 inch HDD to be compatible with older laptops. It has the exact same connection that any other SATA HDD of any size would have.

The SATA type like HDDs usually has 4 screws to hold it in place. Replace these just like any other 2.5 inch HDD replacement.

The SSD that looks like a RAM stick usually has 1 screw that fits at the far end (opposite to the electrical contacts). To install it, we slide the key'd electrical contacts into the slot on the motherboard at 15°-30° angle until it is seated, then push the long end down so it is flat against the motherboard and insert the tiny screw.  I think there's a tiny spring to hold the unscrewed SSD up at the angle.

It is harder to describe in words than to see it and immediately know what is necessary.

Don't loose the tiny screw.  If you ever get extras, keep them!

As for partitioning and formatting the new storage, that's a different question and what needs to be done depends on how you plan to get an OS onto the new SSD.  If you will do a fresh install using the "whole disk", then you don't need to do anything in advance to the storage.

There are also cheap external USB enclosures that can accept an SSD, but connect like any other storage via a USB3 or USB3.2 connector.  These can be handy and fast.  USB 3.2 (usually with a red tab) is a 10 Gbps bus.  This is faster than any SATA connection can reach, but NVMe SSDs can be well over 10 Gbps speed.  Some get into the 30 Gbps speeds, though for users like you and me, anything over 500Mbps is crazy fast.  SATA SSD enclosures tend to be cheaper ($9-$25), but as NVMe becomes even more popular, NVMe SSD to USB enclosures are getting cheaper.

1 last thing related to SSDs that look like RAM.  They come in different lengths from 42mm to 80mm.  80mm is the longest side and the most common.  This size applies to both NVMe and SATA versions.  You may see "2242" or "2280" on the specs.  22mm is the width and 80mm is the length.

I've had a SATA-SSD 2242 to  USB3-c enclosure for almost a decade.  Initially, I replaced the 16GB SSD in a cheap chromebook for a 120GB SSD and wanted to use the 16GB SSD for something.  For an emergency Linux to boot while away from home, a SSD in an external enclosure is awesome as a backup or to mitigate the "evil maid" attack.

I've found the SMART data for NVMe SSDs to be completely lacking in useful information.  I have a Samsung 970 EVO in a system here and the SMART data it complaining about errors, increasing an error count but none of the typical SATA SMART data is being reported.  I have 2 other 500GB SATA SSDs - one in a desktop and another in a laptop - the SMART data from them is just like for HDDs. That is to say, useful.

I run weekly "short" SMART tests on all my storage and monthly "long" tests.  The reports for these things get stored in the ~/SMART/ directory with a datestamp for review later.  SMART data is most useful to watch as it changes over time.  For example, there's a drive that has 2 error sectors in my storage.  Those 2 errors have been there over 5 yrs, but no more errors have shown up, so I leave the drive installed and doing what it does.  If the error count increased every week, then that would be cause for replacement.  If I didn't keep the old reports, I wouldn't be able to do those comparisons over time.

As was already said, ensure you have excellent backups.  That's the difference between a minor inconvenience and a "freak-out" disk failure.  All storage fails. Some in the first week and some after 20 yrs.  Sadly, we don't get to pick when the failure happens, so we need to be ready every day for a drive to fail.

With all this written, about 18% of the time drives fail without any warning at all.  All the SMART monitoring in the world can't seem to fix that.  I've had 2 SSDs fail. They were extremely cheap (at the time)  and both started by entering read-only mode.  A reboot would bring them back to read-write for a few days, but then they'd go read-only again.  I understand that I was very lucky.  Often, SSDs just fail and never work again without any warning.  A good friend had an extremely popular, well-known brand+model fail in the first month after purchase.  The company replaced it, but he had to wait a few days for the RMA process to work.

---

### Post by kbarber3 on 2022-10-19
Thanks for this, apologies for the long silence; workload plus I needed to decompress a bit.  Unfortunately, you've brought me hard up against the limits of my ignorance, please excuse some entry-level questions.

> **oldfred said:**
> Do you have good backups?
Or is second install on HDD your main install?
I imagine you're asking if the most recent install on the HDD is what I'm relying on to run the machine, leaving the SSD effectively bypassed?  That's certainly the intention (and I believe is what I've managed to achieve), until I have a chance to get more clear on what's happening to the SSD.  I might get a chance, sometime, to rummage around inside for loose connections but in the light of what @TheFu says about failing SSDs entering read-only mode (one of the symptoms in my earlier thread) I'm inclined to think it'll be a new SSD.

> **oldfred said:**
> You need at minimum, backup of /home, any system settings you manually change in /etc and export of list of installed apps to make it easy to reinstall.
I think I've managed the first, albeit by a different route (as my /home seems to include the cloud drive I back up to, I reckon a full backup of that might be overdoing it, so I've set up syncs to the directories I use for data).  I've only just worked out where to find /etc, I'll add that to the syncs.  Does Ubuntu keep a list of installed apps or do I need to maintain that manually?

> **oldfred said:**
> When you do not see SSD, does UEFI/BIOS see drive?
If drive not seen in UEFI/BIOS, no software will be able to find it.
That might indicate loose connection, bad cable or bad drive.
Is there a way to access the UEFI data other than by restarting the machine?  Not what I want to do in the middle of a working day, nor after a 22:00 finish, so it may be end of week before I can answer that for certain, but I *think* the SSD was visible when I last booted.

> **oldfred said:**
> Is SSD a SATA drive or newer NVMe type?
Just dug out the spec... it's a Samsung 970 EVO Plus (NVMe PCle); not sure if the additional information is useful or not.

> **oldfred said:**
> Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

And to better document hardware, preferably when SSD seen:
Hardware doucumentation script, one line using && \ to make as one entry
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && \
chmod +x system-info && \
./system-info
Please forgive me, I think every sentence here will be a learning curve for me.  Hopefully I'll be able to start working my way through it over the next few weeks (and hopefully the hints you've already given - thanks again - will enable me to nurse it along until I can properly sort it out).

---

### Post by oldfred on 2022-10-19
New NVMe drives need latest firmware. And system may need UEFI firmware to work with newest NVMe drives.
Difficult to have loose connection with NVMe drives. They are more like RAM and plug into a M2 connector and are held in place with a tiny screw.
[https://en.wikipedia.org/wiki/M.2](https://en.wikipedia.org/wiki/M.2)
[FONT=arial]This will show revision:
[/FONT][FONT=monospace][FONT=arial][COLOR=#000000]udisksctl status
Or install nvme-cli
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list
[/COLOR]
I downloaded latest NVMe driver ISO fro my Samsung NVMe drive. It only has that one update for that one drive.
Bootable ISO like any ISO, but seemed like an old DOS screen came up to update firmware.
[https://semiconductor.samsung.com/consumer-storage/support/tools/](https://semiconductor.samsung.com/consumer-storage/support/tools/)

As part of my backup script, I export a new list of installed apps and save in /home. You can also extract those that are manually installed.
Manual:
apt-mark showmanual > manually_installed.txt
All packages:
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)

I only edit a few files in /etc like grub files. So I just copy to a folder in /home. You typically do not want to restore all of the files in /etc with new install, but may want some. Settings may change with new version. The /etc folder is not large so can be fully backed up if desired.
[/FONT]
[/FONT]

---

### Post by kbarber3 on 2022-10-24
Thanks hugely - yet again - for all these responses.  This forum is a pretty amazing resource and I'm grateful to everyone who makes it possible as well as to you who have come up with all these suggestions.

I think I'm going to mark this as solved, for the time being at least.  I've pretty much concluded the SSD is failing (latest reboot has it showing in the Disks utility, although it wasn't before) and this time I made sure I booted from the HDD (and, as @Impavidus hinted, it certainly was slow).  So it looks as if I can nurse the machine through to Christmas, when I'll have a few days that won't be completely manic and can do the necessary work with a bit less hassle; that's my strategy now.

Thanks to @TheFu and (particularly) @oldfred for your comments too, all very much appreciated.  As and when I get time I'll try to work through the suggestions and see what I come up with; even if it's a bit academic, it will be useful learning.  I hope it'll be OK, if I get stuck, to unsolve this and ask for help with the specific thing I'm trying to do, or indeed to post outputs for help interpreting them (pastebin will be another learning curve so all this is going to take time).

Thanks all and perhaps be back for more sometime.

---

