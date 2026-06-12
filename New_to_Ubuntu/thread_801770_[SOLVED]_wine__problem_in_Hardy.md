---
title: "[SOLVED] wine  problem in Hardy"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by fourscore on 2008-05-20
I am unable to install a windows program using wine in Hardy. When I click on the setup.exe file and try to run using wine  there is no response.
This program ran without any issues under wine in Gutsy.
Any suggestions.

---

### Post by Xiong Chiamiov on 2008-05-21
What do you get when running it through the terminal, eg
```

wine [path to exe]

```

---

### Post by Cresho on 2008-05-21
try right clicking it and run with wine

---

### Post by iaculallad on 2008-05-21
Try visiting this [link]("http://wiki.winehq.org/PreloaderPageZeroProblem"). Maybe, you bumped on the wine bug.

---

### Post by fourscore on 2008-05-21
> **Xiong Chiamiov said:**
> What do you get when running it through the terminal, eg
```

wine [path to exe]

```

Here is the output :
```

user@sg-laptop:~$ wine /home/user/.wine/drive_c/jh71full/setup.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing
```

Is this an issue with Wine or with Hardy ?

---

### Post by kentpend on 2008-05-22
I had the exact same problem after upgrading to Hardy.  I just upgraded wine to 1.0 RC1, and its working fine.

---

### Post by djrakun on 2008-05-22
Oh man, I am so glad this has finally been solved.  This has been bugging the heck out of me since I upgraded to Hardy.  My clean install of Hardy did not have this problem, just the Gutsy upgrade.

Thanks for the info. Wine 1.0 RC1 looks like it shut up that dosmem problem
:guitar:

---

### Post by m3t3ors on 2008-05-22
> **djrakun said:**
> Oh man, I am so glad this has finally been solved.  This has been bugging the heck out of me since I upgraded to Hardy.  My clean install of Hardy did not have this problem, just the Gutsy upgrade.

Thanks for the info. Wine 1.0 RC1 looks like it shut up that dosmem problem
:guitar:

what did you run to update wine as im havimg same prob (no response after clicking on .exe files)

---

### Post by djrakun on 2008-05-23
go to 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

it will give you the instructions on how to add the source to your repository.  after you do, just apt-get install wine and you'll download the 1.0 version.

* I should note that I used the synaptec package manager to completely uninstall the previous version, just so there wouldn't be any bug carryover.  I don't know if that is necessary, but I figured, upgrading blindly was what got me into this mess, so fool me once...

---

### Post by Fazz Munkle on 2008-05-24
How would one update the wine in CrossOver Games? Wait until Codeweavers some out with an update I suppose. :\

---

### Post by fourscore on 2008-06-24
> **djrakun said:**
> go to 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

it will give you the instructions on how to add the source to your repository.  after you do, just apt-get install wine and you'll download the 1.0 version....

This fixed the problem. 
Closing as solved

---

