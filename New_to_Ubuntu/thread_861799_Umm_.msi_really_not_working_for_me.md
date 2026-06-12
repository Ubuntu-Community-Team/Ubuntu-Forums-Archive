---
title: "Umm? .msi really not working for me"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by lockerhaxor on 2008-07-16
Hey everybody, it's been a long time since I've touched my Linux machine due to work. But now when I get back to it, I decided to install steam, so I can atempt to play my games.

Obviously I thought stream was a .exe and thought WINE would take care of it. But eveidently it's an MSI. Everything I've read has not helped really. I got this code when I entered the "msiexec steaminstaller.msi" code.

```

oliver@oliver-ubuntu:~$ msiexec steaminstaller.msi
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
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
oliver@oliver-ubuntu:~$ 

```

Can someone explain what exactly happened?

EDIT: I tried it again, and my screen flickered violently, and went black. Had to unplug and replug the monitor to get it to run again. *ahem* NOT GOOD!

Thanks,
Lockerhaxor

EDIT: Even though this didn't answer my question I did find a .exe installer of steam. [http://www.cstrike-planet.com/files/1](http://www.cstrike-planet.com/files/1)! Just in case someone is looking for one. If someone can help me out still though, please do!

---

### Post by maddog39 on 2008-07-16
You should try this command instead:
```

wine msiexec /i ./steaminstaller.msi

```
Works flawlessly for me on a variety of distros.

---

