---
title: "Minimal BASH-like line editing is supported"
date: 2017-02-04
forum: New to Ubuntu
---

### Post by jamiek22 on 2017-02-04
[COLOR=#111111][FONT=Ubuntu]I have a laptop that has Ubuntu 16.04 and Windows 7 on it. On startup it used to let me choose between Ubuntu and Windows.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Today I was trying to clone Ubuntu to a USB using Clonezilla. After Clonezilla completed, I removed the USB and restarted the laptop. Now there is no UI to choose which OS I want, just a prompt that says:[/FONT][/COLOR]
```

[ Minimal BASH-like line editing is supported. For the first word, TAB
  lists possible command completions. Anywhere else TAB lists the possible
  completions of a device/filename. ]

grub>
```

How can I fix this so the UI shows up so I can choose which OS to start?

I tried [https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/) and nothing changed (the report is here: [http://paste2.org/KJfs5BIN](http://paste2.org/KJfs5BIN)).

I tried [http://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash](http://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash) but am told "ls" is an unrecognized command.

Thank you in advance.

---

### Post by leunam12 on 2017-02-04
If you didn't change anything in your BIOS settings then I would run boot-repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2017-02-04
Your boot repair output shows Grub Legacy installed to the MBR of sda, the 238GB drive.  Don't know how you managed that as Ubuntu hasn't used Grub Legacy for over 7 years.  You should have had Grub2 code there.  You also show files for the syslinux bootloader as well as Grub2 bootloader including some EFI files on the first partition, sda1.  That isn't right.  The syslinux.cfg menu file doesn't show anything other than clonezilla boot entries??

 You have only one partition on each drive and no ntfs partitions where windows might be.   Not sure what you could do to repair this, if anything.  I'd suggest waiting to see if someone else posts.

---

### Post by jamiek22 on 2017-02-04
Someone tried to help me here: [http://chat.stackoverflow.com/rooms/134878/discussion-between-alan-p-and-david-van-rijn](http://chat.stackoverflow.com/rooms/134878/discussion-between-alan-p-and-david-van-rijn)

Seems I made a catastrophic mistake somewhere with Clonezilla.  Thank goodness for external backups.

---

