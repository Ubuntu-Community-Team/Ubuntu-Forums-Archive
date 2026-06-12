---
title: "Launch Ubuntu Alternate Installer from Live CD"
date: 2011-08-20
forum: Programming Talk
---

### Post by 1proof on 2011-08-20
As you may have seen in the standard Ubuntu Desktop CD, you can "try" Ubuntu Live and then click "Install" from the Desktop icon. I am creating my own Ubuntu Remix. On the Isolinux boot menu, it has the Alternate Installer as the one that launches when you choose "Install Ubuntu", and the Live CD image (taken from the Desktop ISO) launches when you choose "Try Ubuntu". I would like the "Install" icon in the Live CD image to automatically start the Alternate Installer. Is this possible and how do I do it?

Thanks,
Andrew

---

### Post by c.cobb on 2011-08-23
I'd like to do this also, but am not sure it's possible as you describe. Does the desktop icon actually launch the alternate installer, or is it only a bootable entry in the isolinux menu?

Afaikt, the alternate installer / debian-installer / d-i is its own mini kernel and has to be booted directly. It can't be launched from a desktop icon in a try-it version of Ubuntu. If I'm wrong that would be great. Here's a page that describes [customizing the alternate install CD]("https://help.ubuntu.com/community/InstallCDCustomization").

If you find the desktop icon does launch d-i, what does the "Exec=" line contain? (The .desktop file is just a plain text file.) I spent a little time digging around in the [d-i source]("https://launchpad.net/debian-installer"), but didn't find anything that's executable from user space.

---

### Post by NiceLittleRabbit on 2012-05-28
Hello Andrew,

I would need to do the same and I would like if it is possible to launch the alternate installer from the desktop live CD.

Did you find an answer to your quest?

Cheers

Lucy

---

