---
title: "Tribooting?"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by Da Flo-rid-eee-an on 2012-08-17
I finally have a modern computer, for the first time in my life, HP Probook blah blah blah. Anyways I know this one can be used as a Hackintosh, but I'd like to drop Lubuntu alongside Win7 as well. My problem is that before I do the lubuntu or OSX install, I have the fingerprint scanner-to-boot-up deal, and I'd like to keep this feature. Would GRUB 2 override this? Or should I disable the fingerprint scanner that pops after the BIOS? If you need any clarification, let me know, my grammar is terrible (physics freshman).

---

### Post by 2F4U on 2012-08-17
What exactly is that feature? Is this some kind of secure boot? To be more precise, when does the fingerprint scanner kick in, before the OS boots? Then it would probably be a BIOS feature and it wouldn't be overwritten by Grub. If it is a Windows feature or a feature of the Windows boot loader, Grub would probably deactivate it. However, without knowing how its implemented, the question is difficult to answer.

---

### Post by Da Flo-rid-eee-an on 2012-08-17
I believe it is part of the BIOS, but I can sign into windows using my fingerprint as well. I'll look into it on HP's website or something

---

### Post by brodedra on 2012-08-17
Keep fingerprint security on in the bios. It's on a hardware chip and Linux will take all care. I have a spare Pro book and it just works like charm!

---

### Post by Double.J on 2012-08-17
Hi there,

As others have said - so long as it's firmware then you're fine - if it's windows, then you're looking at being able to set it up again for the windows partition, but not the others. (apple did just buy a fingerprint tech company, so not too far off maybe?)

Having also added my install of lion to other machines (now its in the EULA) I'd add a couple of triple-boot tips - firstly obviously do some kind of image back up - preferably using the windows utility, that you can recover from, then do an install of OS X as a test - see what really works and what's unbearable.. see if you wanna keep it before going through multi boot options.

Finally I would not recommend grub as the primary boot loader at all, install to a boot partition and chain-loader it. Chameleon is the default option as you will be using this to boot OS X, but I find easy BCD to be by far the easiest to configure and maintain - especially as a primary loader.

Personally, I could never get the trackpad right.. virtualisation is always an option (it's become my default ;) )

Best of luck!

---

### Post by Da Flo-rid-eee-an on 2012-08-17
Alright! Thank you all, I believe I can do this pretty easily now

---

