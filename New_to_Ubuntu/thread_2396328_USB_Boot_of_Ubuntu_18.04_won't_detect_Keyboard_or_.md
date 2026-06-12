---
title: "USB Boot of Ubuntu 18.04 won't detect Keyboard or Trackpad"
date: 2018-07-13
forum: New to Ubuntu
---

### Post by deedongle on 2018-07-13
This is my first attempt at installing any Linux OS. The machine is a Toshiba Satellite C55. I can boot Ubuntu 18.04 from my USB drive, which has the .iso on it, but no inputs produce any reaction--the mouse cursor will not move and the keyboard seems to have no effect, including Ctrl+Atl+t.

I am probably missing something simple. Does it matter that I have not wiped/reformatted the hard drive of the laptop, which still has Windows 8?

The inputs work normally when I boot from the hard drive on Windows.

---

### Post by oldfred on 2018-07-13
Have you turned UEFI Secure boot off?
Many UEFI have settings for USB ports, make sure they are for full support & allow booting.

       Toshibs C55-B5356 "Failed to open \EFI\BOOT\grubx64.efi - Not Found" 
[https://ubuntuforums.org/showthread.php?t=2387851](https://ubuntuforums.org/showthread.php?t=2387851) 
Toshiba Satellite C55-C5241  Windows vs. Ubuntu
 [URL="http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1"]http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1
      [/URL]
 Toshiba C55D-A5163 - Installation of Lubuntu on computer with Windows 8.1 Feb 2015
[http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279) 
    [URL="http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1"]
[/URL]

---

