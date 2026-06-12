---
title: "Bios blackscreen after I install Linux"
date: 2021-01-17
forum: New to Ubuntu
---

### Post by kiliankier on 2021-01-17
[COLOR=#141414][FONT=&amp]I use an Acer Aspire A315-51 laptop and I tried to install several distroutions (Ubuntu, POP OS, Arch, Manjaro, ...) but every time when everything is installed, after I press the bios key F2 a blackscreen with a white line appears (see attachment). I can still select the operating system via the F12 boot menu, but I can no longer change the boot order without access to the bios...


[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-01-17
Hold SHIFT at boot and then you can add the boot option:

nomodeset

This may help. Is this a dual boot or is Ubuntu the only OS on the system, please?

---

### Post by tea for one on 2021-01-17
Is F2 the key to enter the UEFI set up pages (i.e. before you choose the OS)?

Keyboard or other hardware problem?

---

### Post by yancek on 2021-01-17
Newer Acer machines have a requirement to set a Supervisor Password in the BIOS firmware and enable Trust in order to use an OS other than what is preinstalled.  Of course, if I am reading your post correctly, you are saying you can't access the BIOS.  If that's the case you will need to go to the Acer site or contact them to find out how to resolve this.  You might try doing an online search for the problem specifying Acer or your specific Acer model or looking for an online manual for your specific Acer.

---

