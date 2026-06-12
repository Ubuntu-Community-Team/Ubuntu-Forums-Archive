---
title: "How can I know when an updated ISO becomes available?"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-11-16
I'm running Ubuntu v10.04 LTS 32-bit on a Dell Inspiron 9400 laptop. I've been considering reprogramming the boot setup from scratch to have a dual-boot w/ Windows XPHE. The Ubuntu CD I have was DL'd 07/25/11, so there have been many updates since then. I was thinking I should DL a new ISO before reinstalling Ubuntu. A few days ago, I used the Update Manager, and it included update of the kernel to 2.6.32-35-generic (#78-Ubuntu SMP Tue Oct 11 15:27:15 UTC 2011). I couldn't tell from the Javascript-limited Ubuntu site DL page, whether the ISO being offered had been updated to the new kernel or not - no dating was available from there. Researching here, I found a link to [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) . That page shows the post dates of the ISO's. The most recent ISO of v10.04 LTS 32-bit on that page was posted 07/19/11. Which, is earlier than my current CD - so, isn't worth DL'ing.

I know I've had at least one kernel update before now, which means at least 2 have occurred since I DL'ed my CD. This puzzles me. Shouldn't a new kernel have triggered a new ISO? For example, v10.04.3 becoming v10.04.4?

How can I know when an ISO containing the updated kernel (& updated etc.) is available?

---

### Post by JayKay3OOO on 2011-11-16
I fear I may be missing the point, but the reason for an updated ISO is to include all the accumulated tweaks and fixes in one installation disk. Subsequent updates from the ISO launch time may be implemented as updates. The ubuntu kernel (don't ask me what they change from the stock kernel as I don't know) is likely to come out a little after the standard kernel.

In the release notes per release it makes note of new features including the new kernel so this is probably the most reliable way to know what kernel each version of Ubuntu is on.

[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)

---

### Post by mörgæs on 2011-11-16
Long time support releases come in several sub-releases, for example 10.04.0 through 10.04.4. This is done at pre-determined dates and is not connected to a particular change in packages.

Don't worry. If you can get any 10.04 installed and apply all updates afterwards, you will automagically end with the newest version.

---

### Post by scruffyeagle on 2011-11-18
> **mörgæs said:**
> Long time support releases come in several sub-releases, for example 10.04.0 through 10.04.4. This is done at pre-determined dates and is not connected to a particular change in packages.

Don't worry. If you can get any 10.04 installed and apply all updates afterwards, you will automagically end with the newest version.

I understand that - but, updates are expensive in terms of time & bandwidth. For example, the update I did a couple of days ago, that included the new kernel was 81MB. If the ISO's are out-of-date as vs. the updates, then this becomes wasteful, downloading the data for the outdated versions then downloading the data for the up-to-date versions. Take that 81MB plus the MB's for all other updates (just the most recent MB download included per program) and multiply it times the number of people who undergo this doubling of effort, and you get a measure of how much wastage is actually occurring.

---

### Post by mastablasta on 2011-11-18
but the thing is they don't have to download the updates. You can awlays check what is in updates and determine if it is actually necessary to download them. for example lets say a new kernel fixes issues with nvidia card and bluetooh. but your computer has neither fo those two so do you need to upgrade/update?
 
the ISO is always a snapshot of the OS in time. LTS as well as normal edition. the OS is under constant development. These updates are not the same as the ones done for microsoft. MIcrosoft has mostly patches (rarely new features), while in linux you also have upgrades and new features. even so they too issue so called service pack that includes the updates up to certain time but not the latest ones. for example you can download SP3 CD for WinXP, but it will not include about 2 years worth (i think it's already 2 or is it more) of updates and security patches.

---

