---
title: "RAM and DOS error in terminal"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by minibeardeath on 2008-04-29
so i am trying to install office 2007 in WINE (i really am only doing it so i can use onenote), and when ever i try to run the setup.exe i get the following terminal error:
```
p***ck@seniorproject:~$ wine setup.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found
p***ck@seniorproject:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
p***ck@seniorproject:~$ 
p***ck@seniorproject:~$ 

```

i have no idea what this means. please help me. thanks

---

### Post by lwvmobile on 2008-04-29
Those memory errors aren't uncommon, but they generally don't keep you from running supported windows apps. You might want to thoroughly check winehq.com though, I'm not so sure Office 2007 works with wine at all.

---

### Post by skymera on 2008-04-29
Office 2003 was reported to work.
But 2007 and 2003 save in different formats, not sure if that is a problem to you though.

---

### Post by minibeardeath on 2008-04-29
at the moment it is not even letting me install the software.

and here is the link for [installing office 2007 in wine]("http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/"), so i am guessing that it is possible ;).

i will check out the link and see what i can see

---

