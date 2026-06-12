---
title: "Found and ran Boot Repair; does not boot, flashing cursor; Alt-Spx reisub no response"
date: 2014-10-31
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-10-31
Found and ran Boot Repair; no boot, Alt-Spx reisub no response; flashing cursor left corner top.

Prior thread:  [http://ubuntuforums.org/showthread.php?t=2249489](http://ubuntuforums.org/showthread.php?t=2249489)  ; [http://paste.ubuntu.com/8724377](http://paste.ubuntu.com/8724377)

BIOS has usb live first and HD seecond, with  usb removed should boot to HD. What now? I appreciatte all the help I have received, thank you.

---

### Post by grahammechanical on 2014-10-31
> [COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would purge [COLOR=#666666]([/COLOR]in order to [COLOR=#AA22FF]enable[/COLOR]-lvm[COLOR=#666666])[/COLOR] and reinstall the grub2 of sda2 into the MBRs of all disks [COLOR=#666666]([/COLOR]except USB without OS[COLOR=#666666])[/COLOR].
The boot flag would be placed on sda2.
Additional repair would be performed: unhide-bootmenu-10s

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

No change has been performed on your computer.

You have a choice. 1) Run Boot Repair again and this time accept its recommendation and let Boot Repair do the repair. 2) Think of another way to fix the problem. 

> [COLOR=#666666]===================[/COLOR] Final advice in [COLOR=#AA22FF]**case **[/COLOR]of recommended repair
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda [COLOR=#666666]([/COLOR]160GB[COLOR=#666666])[/COLOR] disk!
Regards.

---

### Post by nu2u904 on 2014-10-31
Thank you:
```

[COLOR=#000000]Found and ran Boot Repair; no boot, Alt-Spx reisub no response; flashing cursor left corner top.[/COLOR]

[COLOR=#000000]Prior thread: [/COLOR][http://ubuntuforums.org/showthread.php?t=2249489](http://ubuntuforums.org/showthread.php?t=2249489)[COLOR=#000000] ; [/COLOR][http://paste.ubuntu.com/8724377](http://paste.ubuntu.com/8724377)

[COLOR=#000000]BIOS has usb live first and HD seecond, with usb removed should boot to HD. What now? I appreciate all the help I have received, thank you.

```

I accepted the recommended  repair option and ran; that is in /2249489 listed above.   If no usb live is  inserted doesn't BIOS automatically jump to the hard drive?


[/COLOR]

---

### Post by yancek on 2014-10-31
I would expect the behavior you are seeing if you have a non-bootable flash drive plugged in and set to first boot priority.  Tested it on my HP and that's what happened.  With the flash still set to first boot priority but no plugged in it boots in the standard manner.  Don't know if that works with every BIOS.

---

### Post by nu2u904 on 2014-10-31
Thank you. I'll try that. I wasn't aware that plugged  in non-bootable flash drives, or non-bootable usb hard drives could impact the effective boot order even though the bootable usb flash drive was removed before rebooting.

---

### Post by yancek on 2014-10-31
> Thank you. I'll try that. I wasn't aware that plugged  in non-bootable  flash drives, or non-bootable usb hard drives could impact the effective  boot order even though the bootable usb flash drive was removed before  rebooting. 		

It can at least on some computers.  If it is set to boot from a specific drive then it will be looking for something bootable.  I've seen the same behavior with a CD/DVD drive when it is set to first boot priority and there is a non-bootable CD/DVD in the drive.  It might depend on the manufacturer or mother board manufacturer I don't really know.

---

### Post by nu2u904 on 2014-11-01
> **yancek said:**
> It can at least on some computers.  If it is set to boot from a specific drive then it will be looking for something bootable.  I've seen the same be you and you were right on.havior with a CD/DVD drive when it is set to first boot priority and there is a non-bootable CD/DVD in the drive.  It might depend on the manufacturer or mother board manufacturer I don't really know.

Thank you and you were right on. I shutdown u14.04 live. Then I disconnected the usb hub and unplugged the live usb. I booted the computer and it booted ok. I reconnected the usb hub and proceded to update  and install new programs. I did a suspend and checked that recovered ok. I apprecdiate the help of all in guiding me resolving this issue. I learned a great deal.

---

