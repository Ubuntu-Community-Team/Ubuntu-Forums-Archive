---
title: "Can't access windows from GRUB"
date: 2019-10-05
forum: New to Ubuntu
---

### Post by tomms99 on 2019-10-05
Hello, I'm a newcomer to Linux and decided to install Ubuntu 18.04 (from the Microsoft Store)
However after installation, I noticed There wasn't a windows entry in the Grub menu upon powerup.
After some Googling I edited the /etc/grub.d/40_custom and added this:
```


menuentry 'Windows 10' {
    search --fs-uuid --no-floppy --set=root [sda1_UUID_here]
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
```

And an alternative:

```

menuentry "Windows 10" --class windows --class os {
   insmod ntfs
   search --no-floppy --set=root --fs-uuid $your_uuid_here$
   ntldr /bootmgr
}
```

I update grub and restarted but when I select Windows in Grub it raises an error message, saying bootmgfw.efi is missing.
However, when I go to the sda2 partition, where the windows files are, I can see bootmgfw.efi and boot.mgr in /windows/Boot/EFI/

I tried running the recommended repair setting from Boot-repair and still nothing.

I tried the solutions in this thread and nothing seems to work.

Please help! I really like Ubuntu but I need Windows for work reasons.

---

### Post by oldfred on 2019-10-05
You say from Microsoft store?

Did you install Ubuntu on Windows?3.[https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab)
That is not full Ubuntu but only offers the command line tools.
Since running inside Windows there is no reason to offer to boot Windows from grub.

       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Direct link to downloads page, most want  ubuntu-18.04-desktop-amd64.iso
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

---

