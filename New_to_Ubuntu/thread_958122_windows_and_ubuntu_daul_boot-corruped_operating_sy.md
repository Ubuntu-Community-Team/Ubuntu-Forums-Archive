---
title: "windows and ubuntu daul boot-corruped operating systems"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by carrierpilot1357 on 2008-10-25
:confused:    
       
        please help me! I have 2 hard drives. one has ubuntu 8.04 on it (d:/)(primary slave) and the other has windows xp home edition on it (c:/)(primary master). Win xp got corrupted so I went on to ubuntu and mounted my win xp drive in ubuntu and started backing up files. When I finished backing up files onto the ubuntu disk, I booted onto the win xp installation cd and re-installed xp. When xp was installed and fixed, I reebooted too get into ubuntu and put the files on a portable hard drive, and the menu asking me too boot into ubuntu 8.04 or win xp home edition dissapered and it just booted win xp home. By the way, there were many errors with win xp. I could boot into it before, but there was no power down button, no usb device support(thats why I didnt put the files onto the portable hard drive through windows xp) and so on.. so back too the story. So I reebooted again, this time I went into setup and selected my ubuntu hard drive as the primary boot device, saved my changes, it reebooted, and I got a message saying "error loading operating system". (I did not move any win xp system folders into ubuntu by the way) so I ended up digging through my piles of cd's too get my ubuntu live cd and I loaded the live cd too transfer the files onto the portable hard disk and I got all my files onto the new windows installation, deleted all the files I put onto the ubuntu hard disk, reebooted, still no daul-boot menu (the one asking my which operating to boot up). so I went into setup again, selected my ubuntu hard disk as the primary boot device, and I got the same error saying "error loading operating system".

so, is there a way too get my daul-boot menu back and get ubuntu 8.04 up and running again along with win xp on the other drive, or do I have too do the same thing I had did with windows? Please help me!

---

### Post by bumanie on 2008-10-25
This is a common issue when one has to reinstall windows. Windows' bootloader does not recognize any other bootloader and thus overwrites the mbr. To reinstall grub , either [follow this]("http://ubuntuforums.org/showthread.php?t=224351") or get [super grub disk]("http://www.supergrubdisk.org/index.php?pid=5").

---

