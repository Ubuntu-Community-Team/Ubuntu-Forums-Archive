---
title: "[SOLVED] steam install attempt failing"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by ChrisMaybury on 2008-05-17
hey, i am completely new to ubuntu, and linux in general. I am tring to install steam and failing miserably, i have wine installed and have tried to follow many tutorials and nothing is working. this is how far I've got

wine installed..
gecko installed..
tahoma font in font folder...

then i msiexec the steaminstall.msi and get this...

christopher@christopher-laptop:~$ msiexec '/home/christopher/Steam/SteamInstall.msi' 
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron
christopher@christopher-laptop:~$ 
christopher@christopher-laptop:~$ 


please can someone help me!!!!

---

### Post by Canis familiaris on 2008-05-17
Instead of:
```
msiexec '/home/christopher/Steam/SteamInstall.msi' 
```
Try:
```
msiexec /i '/home/christopher/Steam/SteamInstall.msi' 
```

---

### Post by shifty_powers on 2008-05-17
eerm, just download the steam install, right click opn it and select run with wine?

thats what i did...

---

### Post by ChrisMaybury on 2008-05-17
thank you anurag_panda, im hoping ill pick all this up soon, also shifty_powers i did try that but it wouldn't work for me, i don't know why.

just to say thanks you guys on here, you're brilliant at what you do and the rate of reply is just excellant.

---

### Post by Canis familiaris on 2008-05-17
> **shifty_powers said:**
> eerm, just download the steam install, right click opn it and select run with wine?

thats what i did...

It would rather be as Open as and select run with msiexec /i. It is an .msi installer.

---

