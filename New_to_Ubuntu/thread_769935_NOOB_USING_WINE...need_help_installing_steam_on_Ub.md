---
title: "NOOB USING WINE...need help installing steam on Ubuntu x64"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-04-27
Trying to install steam...i already have wine installed...i did it through the add and remove programs...i have the Steaminstaller.msi...i thought i found a post that would do it but when i went to install it i got this:

[email]daniel@daniel-ubuntux64:~/.wine[/email]/drive_c/Program Files/mozcontrol$ wine SteamInstall.msi
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\Program Files\\mozcontrol\\SteamInstall.msi": Bad EXE format for 
[email]daniel@daniel-ubuntux64:~/.wine[/email]/drive_c/Program Files/mozcontrol$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

so i dont know what is up...if someone could just throw me a step by step i would greatly appreciate it.

Thanks

---

### Post by grazed on 2008-04-27
open terminal.

navigate to the folder the msi is in. and use this command...

msiexec /i filenamehere.msi

----

i would strongly suggest using the 32bit version of ubuntu for compatibility if you are a new user. you're going to run into a LOT of situations that will make you want to pull your hair out. =P

just a suggestion.^

---

### Post by dtrot55 on 2008-04-27
thanks man...got it installing now...yeah i have both the 32 and 64...just playing around for fun...if it gets really annoying will def go back to 32

---

