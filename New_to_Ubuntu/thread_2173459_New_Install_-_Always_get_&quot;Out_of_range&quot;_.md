---
title: "New Install - Always get &quot;Out of range&quot; upon bootup"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by michael63 on 2013-09-09
[FONT=arial]I have recently installed Ubuntu 12.04 Desktop version.  Everytime I attempt to boot "normally" the start up never completes, and the screen says "out of range."


When I get to Grub, if I change to "recovery mode" startup, and choose "safe graphics mode" I am able to boot to the "desktop" using the "lower graphics" option.


I have used grub customizer twice to try and set some different resolutions, but no matter what I do, I still get the "out of range" error, even though the resolution of the screen does change--I can see that when it gets to Grub.

[/FONT]
[FONT=arial]see [/FONT][paste.ubuntu.com/6081192/]("http://paste.ubuntu.com/6081192/")  [paste.ubuntu.com/6081429/]("http://paste.ubuntu.com/6081429/")

Any help would be greatly appreciated.  I really never expected this to be so difficult.  I can install XP by just throwing the disk in the drive, and be done with it.  Too bad Linux/Ubuntu is not as easy.

---

### Post by oldfred on 2013-09-09
What video and what monitor?

Recovery mode uses nomodeset by default, but that is just to get you into system so you can install the correct proprietary driver. But if Intel it just should work.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by michael63 on 2013-09-09
Thank you for the quick response.

Forgot to mention I did run the "boot repair" application, but that did not help either.

I can try a different monitor, but since I plan to run it headless, I am using a 14 inch monitor I had sitting around.  With XP, I can run the monitor at almost any resolution, from 800*400 to 1600*1900.  As for the graphics card, it is built in.  I have the driver for windows, any chance that can help me out.  How can I find the chipset information, and then download the Linux driver for it?

I have tried the F6 nomodeset option, but when booting outside of recovery, I still get the "out of range" error.

Also, I saw some instructions about un-commenting out certain lines in Grub, but none of the lines in the grub file are commented out, and also, they do not say the word "grub" in front of them.

Thanks,
Michael

---

### Post by Jonathan Precise on 2013-09-09
> **michael63 said:**
> [FONT=arial]I have recently installed Ubuntu 12.04 Desktop version.  Everytime I attempt to boot "normally" the start up never completes, and the screen says "out of range."


When I get to Grub, if I change to "recovery mode" startup, and choose "safe graphics mode" I am able to boot to the "desktop" using the "lower graphics" option.


I have used grub customizer twice to try and set some different resolutions, but no matter what I do, I still get the "out of range" error, even though the resolution of the screen does change--I can see that when it gets to Grub.

[/FONT]
[FONT=arial]see [/FONT][paste.ubuntu.com/6081192/]("http://paste.ubuntu.com/6081192/")  [paste.ubuntu.com/6081429/]("http://paste.ubuntu.com/6081429/")

Any help would be greatly appreciated.  I really never expected this to be so difficult.  I can install XP by just throwing the disk in the drive, and be done with it.  Too bad Linux/Ubuntu is not as easy.

Get [Linux Secure Remix]("http://sourceforge.net/p/linux-secure/wiki/Home/"). Use boot-repair. Go to advanced options. Look in "Grub options" for an option named:

> **Uncomment GRUB_GFXMODE** (solves the [out-of-range] error)

Check that option. Then click apply. Wait...
Problem (should be) solved!

---

### Post by michael63 on 2013-09-09
Thanks for your response.

I checked out the link, and it seems it is specifically for running a dual boot system.  I plan on installing only Ubuntu (though currently, I have it dual booting because of the install issues I am having)  Also, I edited my prior post to indicate that when I attempt to edit the boot info when I get to the Grub screen, there are not entries with the word "Grub" in front of it, and there is nothing to un-comment out.  

I will, however, try it when I am back at the computer later.  I am willing to try it to get things working.  I did try and use [http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/) to fix the Out of Range issue with not resolution.

Thanks Again,
Michael

---

### Post by Jonathan Precise on 2013-09-09
> **michael63 said:**
> Thanks for your response.

I checked out the link, and it seems it is specifically for running a dual boot system.  I plan on installing only Ubuntu.

That means Linux Secure Remix is made for dual-booting. Boot-repair works in most, if not all, cases.

> **michael63 said:**
> I[COLOR=#000000] Also, I edited my prior post to indicate that when I attempt to edit the boot info when I get to the Grub screen, there are not entries with the word "Grub" in front of it, and there is nothing to un-comment out. [/COLOR]

I think you are misunderstanding. Edit grub.cfg. Lines that are commented out have a # sign. Example:

> # This is an example of a comment:
# some-command=some-variable

Take out to make grub read it:

> # This is an example of an (un)commented command:
some-command=some-variable

or:

> # Description
GRUB_GFXMODE=**something**
.

Make sure to run *update-grub*&#8203; afterwards!

To do this graphically, run boot-repair as advised.

---

### Post by michael63 on 2013-09-09
Thanks,

I will try it as soon as I am the computer.

Michael

---

### Post by michael63 on 2013-09-10
So, I figured out that the VGA chipset is an Intel 82945G Express Chipset.  Went to the intel site, and found a Linux Driver.  Downloaded, and it is a tarball.  I have extracted the file, but now I can't figure out to execute the install, or update the driver.  I ran hardinfo, and found the following
 -Display-
Resolution        : 1024x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.13.3
-Monitors-
Monitor 0        : 1024x768 pixels

-OpenGL-
Vendor        : Unknown
Renderer        : Unknown
Version        : Unknown
Direct Rendering        : No

It would be great to somehow update the driver, just to see if that will cure my issues.  For now, I am booting into Grub, hitting "e", and editing in the "nomodeset" to boot normally.  I will run boot-repair to add it permanently, but I hope the correctdriver update will do the trick.

Michael

---

### Post by Jonathan Precise on 2013-09-10
> **michael63 said:**
> ... but I hope the correct driver update will do the trick...

I really don't recommend this:(. Stick to the driver you have. Just run boot-repair.

---

### Post by michael63 on 2013-09-10
Okie Dokie.  Will try that.  Thanks.

P.S.  Can someone please explain how to install applications which I have downloaded.  While I am fine with Firefox, I like Chrome.  I dl'd that as well, but can't figure out how to install the application.  I downloaded GDebi, but that has been no help either.

Thanks,
Michael

---

### Post by Jonathan Precise on 2013-09-10
> **michael63 said:**
> P.S.  Can someone please explain how to install applications which I have downloaded.  While I am fine with Firefox, I like Chrome.  I dl'd that as well, but can't figure out how to install the application.  I downloaded GDebi, but that has been no help either.

Thanks,
Michael

Go [here]("https://www.google.com/intl/en/chrome/browser/thankyou.html") to install Chrome. Save the file. Right-click. Choose "Open with" -> "GDebi". Click install.
Wait.....................
Go to the dash applications section, and click on "Google Chrome". DONE!

---

### Post by michael63 on 2013-09-10
Will try that.  Thanks again.

---

