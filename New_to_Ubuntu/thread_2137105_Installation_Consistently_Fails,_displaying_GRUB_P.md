---
title: "Installation Consistently Fails, displaying GRUB Prompt"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by csutherland on 2013-04-19
I have tried to install Ubuntu 12.10 a dozen times from an ISO download burned to a DVD.  It always fails the same way.  I set the BIOS to boot from the DVD.  Ubuntu tries to boot and displays the Ubuntu screen giving me the boot options.  But if I choose Ubuntu, I get a DOS screen with the grub> prompt.  So, I gave up and ordered a Live CD of 12.10 from Sir Tanon, but it does exactly the same thing.  This happens on both my Dell Studio desktop (64-bit Win 7) and my Dell Inspiron laptop (32-bit Vista).  I really want to install on the laptop.  I don't want to dual-boot, but keep it simple and let Ubuntu blow Vista away.  What can I possibly be doing wrong?  This should be easy.  Help!

---

### Post by grahammechanical on 2013-04-19
What type of Ubuntu 12.10 do you have, 64bit or 32bit? Ubuntu 12.10 64bit will not install on a machine that has a 32bit CPU. Are you sure you want to install Ubuntu by overwriting Vista? Once you do that you will find it difficult to re-install Vista. So, be sure of what you want.

Do, you get a purple screen with an icon of a keyboard and a human with the arms outstretched? If so, press Enter and at the next screen press Enter to accept English as the default install language. Then press F6 and from the list in the menu that appears select nomodeset and press Enter and then Esc to get back to the Try - Install screen and select Try Ubuntu.

Tell us what happens. Remember, we need your words to tell us what you see. There are other options in the F6 menu. You may need to try some of those options. Even a combination of them.

This page shows some images of what you will see.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by csutherland on 2013-04-19
The Live CD from Sir Tanon includes both 32 and 64-bit versions and a menu for choosing between them.  I'll decide about Vista down the road.  I do not get a purple screen with human arms outstretched.  I do not get an F6 menu.  I get a black screen with a grub> prompt.

---

### Post by csutherland on 2013-04-21
Solved, I guess (I don't see what I need in Advanced to mark it solved).  This was my solution: I found a document called "Getting Started with Ubuntu 12.10.pdf."  In this document, on page 11, "Downloading Ubuntu," is a link to [http://www.ubuntu.com/download/](http://www.ubuntu.com/download/).  I went there and drilled down to /desktop/windows-installer, where I found a button (Get the Installer) that downloads the installation tarball Ubuntu-12.10-wubi-amd64.tar.xz.  I clicked on this link and Ubuntu 12.10 was immediately and automatically installed onto my Dell Inspiron (32-bit) laptop next to Vista and both are behaving and getting along well, so far.  I still have the original problem (which I reworded and resubmitted as "how do I reply to the grub> prompt?" when I try to install).  No takers on either thread.  But I at least now have a working installation of Ubuntu 12.10 exactly as I wanted and expected to install.  Perhaps a reference to this document (117 pages of great stuff, well-written) is what many people need in the beginner's section.

---

