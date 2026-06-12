---
title: "HDD gone after failed install"
date: 2018-11-14
forum: New to Ubuntu
---

### Post by xartx2 on 2018-11-14
Hello,
I tried the USB test Ubuntu method, which boots from USB drive.
It was to compile and run a particular program, and for that session everything worked, could connect to servers to get missing components, etc.
Program in question ended up working fine.

Next session it was like I&#8217;d never used it before. I assume everything I did was in RAM or a test/temp directory that I could not find.
Ubuntu find command could not find the program source download or compiled version, so I decided to install Ubuntu properly.

The PC only had the USB drive it booted from, and an SSD data drive that is built into the PC. It did not contain any operating system, but was full of data).
The installation failed, which is fair enough, but it looks as though it tried to install onto the SSD it had no business writing to.

Now back in Windows, using another operating system hard drive, with the data SSD still installed, my SSD which may or may not be still full of data is not visible.
Using command line Diskpart list command I can see the drive, but can&#8217;t access it or see it in Windows GUI to try looking for data.

My questions/comments now have nothing to do with Ubuntu, other than:
1) How about some warning if the installer is going to try to write to a drive that wasn&#8217;t the boot drive?
2) The installer appears so far to have wrecked at least the data on the drive, and even then, the installer had one job that it didn&#8217;t do anyway.
3) Does anyone know of a way I can try accessing the data on the drive? Diskpart may be able to fix it by formatting it, but I&#8217;d prefer not to.
4) For the USB test version, why would it be assumed that any changes made, and files written weren&#8217;t wanted?
Cheers.

---

### Post by xartx2 on 2018-11-14
I was only able to format it. No longer interested, thanks.

---

