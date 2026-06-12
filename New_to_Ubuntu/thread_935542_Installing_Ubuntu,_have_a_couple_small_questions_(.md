---
title: "Installing Ubuntu, have a couple small questions (mostly about partitions)"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Vunutus on 2008-10-01
I have XP Home on a 127GB partition. When I initially installed XP, I forgot about how it limits you to 130GB or so without updating the installer, so I have an extra 100GB of unformatted hard drive floating around. It's been this way for a long time and I haven't bothered to do anything about it since I don't need the space (my 130GB partition isn't even filled up).

I've been learning about Linux recently and really admiring how it's built, so I want to give it a whirl. Before I install, I have a few questions:

1. Is it safe to partition away some of that 100GB of empty storage , format it, and install Ubuntu on it? I don't imagine there's any risk of damaging my Windows partition (unless I go out of my way to do so), but I want to make sure.
2. Would it be possible to create another partition for music that is shared between Windows and Ubuntu, or is that a bad idea? I assume it would have to be NTFS since Windows doesn't take kindly to Linux file system, so I further assume I should use the Windows Disk manager to make this partition?
3. I have a 64 bit CPU, but run 32 bit XP because I've heard so many horror stories about 64 bit XP. Will I have any regrets if I install 64 bit ubuntu? Will I have any sort of weird problems if I run 32 bit windows programs in wine under 64 bit linux?
4. I may upgrade to Vista on my windows partition soon (mainly because I can get it free legally). If I get my aforementioned configuration set up THEN decide to upgrade to vista, will I be able to blow away my XP partition and install vista in it's place or will vista have problems with linux being on the drive?

Thanks in advance

---

### Post by kansasnoob on 2008-10-01
> **Vunutus said:**
> I have XP Home on a 127GB partition. When I initially installed XP, I forgot about how it limits you to 130GB or so without updating the installer, so I have an extra 100GB of unformatted hard drive floating around. It's been this way for a long time and I haven't bothered to do anything about it since I don't need the space (my 130GB partition isn't even filled up).

I've been learning about Linux recently and really admiring how it's built, so I want to give it a whirl. Before I install, I have a few questions:

1. Is it safe to partition away some of that 100GB of empty storage , format it, and install Ubuntu on it? I don't imagine there's any risk of damaging my Windows partition (unless I go out of my way to do so), but I want to make sure.
2. Would it be possible to create another partition for music that is shared between Windows and Ubuntu, or is that a bad idea? I assume it would have to be NTFS since Windows doesn't take kindly to Linux file system, so I further assume I should use the Windows Disk manager to make this partition?
3. I have a 64 bit CPU, but run 32 bit XP because I've heard so many horror stories about 64 bit XP. Will I have any regrets if I install 64 bit ubuntu? Will I have any sort of weird problems if I run 32 bit windows programs in wine under 64 bit linux?
4. I may upgrade to Vista on my windows partition soon (mainly because I can get it free legally). If I get my aforementioned configuration set up THEN decide to upgrade to vista, will I be able to blow away my XP partition and install vista in it's place or will vista have problems with linux being on the drive?

Thanks in advance

1. Yes, but you must know what you're doing. Here's a really good in depth guide:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Pay particular attention to the section on "'Desktop CD' graphical installations".

Simpler guide:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

2. Yes. Ubuntu has good NTFS support. I always add ntfsprogs which enables excellent read and write support for NTFS partitions. There are also other options. Some are discussed in the aforementioned Dual boot Guide.

3. Not something I know enough about to comment, other than to say each operating system is independent of the other in a dual boot so I think it'd be okay.

4. Upgrading to Vista after installing Ubuntu will mess up Grub - the Grand Unified Bootloader, so I'd study and wait until you've upgraded before installing Ubuntu. Look at these two guides:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

The latter gives you an idea what you'll end up with for bootloader problems after upgrading to Vista.

4.

---

