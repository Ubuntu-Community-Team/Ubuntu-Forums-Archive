---
title: "Boot (or login) problem, following previous SSD problems"
date: 2022-11-01
forum: New to Ubuntu
---

### Post by kbarber3 on 2022-11-01
This time I'm having problems booting/logging in. Please refer to my previous threads for context and my rather low level of knowledge. 

I'd been leaving the machine in suspend overnight, because boot from HDD is slow. This morning the screen image had disappeared and there was a uniform blue background. Apps seemed to work but I've had this before and found the machine slows down badly so rebooted. Reboot got as far as a screen with Ubuntu logo and stopped there, no change after an hour! (I'm having to send this from my tablet, both reading and writing are distinctly awkward compared with the desktop, so apologies for typos and slow responses. )

I've decided now is the time to replace the SSD, clearly I can't nurse the 'puter through to the Christmas break, so will be doing that (between clients!) over the next few days. But I'm concerned there may be something more amiss that would break another new install as well. Can anyone say whether that's likely to be so?

Also, I'm assuming a straightforward clean install to the new SSD is all I'll need to do (apart from all the necessary apps etc). But am I being hopelessly naive in that thought? (I am rather assuming Ubuntu will install preferentially to the SSD; is that more naivety? If so, how would I go about ensuring it does go there?)

As ever, thanks for any help anyone can give.

---

### Post by oldfred on 2022-11-01
What brand/model system?
What video card/chip?
What SSD? SATA or NVMe?

SSD should be fast.
Have you updated UEFI firmware to latest available, even if older system?
Did you update SSD firmware to latest.


Compare to vendors's website download.
sudo lshw | grep -m 1 -A 5 "*-firmware"
compare revision to vendor's website.
udisksctl status

Settings can also make a difference. I do use Kubuntu which is a bit lighter weight. And change a variety of settings.
Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 

To see what is slow:
 systemd-analyze
systemd-analyze blame

---

### Post by kbarber3 on 2022-11-01
Thanks for this. Perhaps should have been clearer, booting from HDD after concluding SSD had failed (my "SSD (perhaps) issues" thread, now marked solved, refers).

I am now going to change the SSD without waiting for a break. I am concerned that the failure to reach the login screen when booting from the HDD may indicate another problem entirely, but one that may cause problems when I install the new SSD.

Apologies for not being clearer, hope things will get simpler from now but don't want to trip over further problems without warning.

---

### Post by oldfred on 2022-11-01
Ubuntu installer only installs in UEFI boot mode to first drive. Whatever first drive is defined by UEFI/BIOS.
That may depend on which SATA port you use, lowest number usually is first. Or if NVMe that usually is  first.

You need an ESP & / as minimum partitions for UEFI install. And use gpt partitioning. If larger drive, you may want separate data partition(s), /home or use LVM. Often safest to disconnect other drive or partition in advance with gparted & only use Something Else install option. I do not trust installer's auto mode to make good choices with any multiple drive install. 

Best to use gpt if older system and using BIOS to boot. But the only time you really need MBR, is if installing Windows in old BIOS boot mode.
Microsoft has required vendors to install in UEFI/gpt mode since 2012, so most systems are UEFI.

---

### Post by kbarber3 on 2022-11-02
> **oldfred said:**
> Really helpful advice 

Thank you. That looks like exactly the tips I need. This forum is an amazing place, especially for rank amateurs like me who never really wanted to mess around with the innards of the machine. 

I'm about to start fitting the new SSD (wish me luck); install will be a bit protracted as I'll be doing bits when I can between clients. I'll leave this thread open for the time being in case I need yet more advice, but hopefully this will see me through. 

Hope the lines break properly when I post, looks horrid on the tablet.

---

### Post by kbarber3 on 2022-11-03
Many thanks again @oldfred.  All went remarkably sweetly, even managed it between clients, I wasn't really expecting to have a working computer today so this is a real bonus.  Just a little tidying to do now, which I hope I've enough understanding to do without further queries.  Very grateful to you and to everyone on this forum who's helped with my different problems.

---

### Post by oldfred on 2022-11-03
Glad we all could help.
If new issue, best to start new thread so title reflects issues as that may attract those who know that issue.

---

