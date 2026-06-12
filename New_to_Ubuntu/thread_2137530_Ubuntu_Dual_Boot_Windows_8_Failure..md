---
title: "Ubuntu Dual Boot Windows 8 Failure."
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Pondweasel on 2013-04-21
So I decided to try and dual boot Windows 8 and Ubuntu 13.10 apparently and it all went well until on the restart all I could see were orange stripy lines stopping me from using Ubuntu.

I tried to get back to Windows 8 from boot menu and I a constantly get the error : 

error: no such device: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx,
grub rescue>

I can boot into Ubuntu 'try me' mode.

I used to be able to see Windows 8 on the grub boot menu but my keyboard is paralysed on that screen, and now it just freezes on it with no countdown.

Note: I am pretty much a noob.

Any advice would be amazing. Thanks in advance.

---

### Post by oldfred on 2013-04-21
Is this Windows 8 that you installed or pre-installed system.
Or more specifically is Windows 8 UEFI or BIOS?
Were drives ever RAID, Intel SRT, dynamic, or gpt partitioned and now MBR?

And did you install Ubuntu in UEFI mode?

If UEFI:
But grub2's os-prober only creates BIOS entries that do not work. You can manually add correct entries to 40_custom, examples in bug report or use Boot-Repair which will auto add them to a new 25_custom.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If not UEFI and above issue, run the Boot-Info report from Boot-Repair.

---

