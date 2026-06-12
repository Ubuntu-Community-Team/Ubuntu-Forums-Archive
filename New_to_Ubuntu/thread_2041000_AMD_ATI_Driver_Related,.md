---
title: "AMD ATI Driver Related,"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by HimanshuSingh on 2012-08-11
Hello all,
           My first post in ubuntu world,just installed ubuntu a few days ago.....:P:P:P

so my _**Question**_

    I am having an issue related my graphic experience
>After installing OS when i saw my system detail,in graphics tab[B]
#Driver: Unknown
#Experience: Standard

[/B]>i somehow installed **AMD proprietary graphics driver** by downloading ***.run** file from AMD support site using **terminal** (GPU-ATI radeon 4350 hd,1gb ) n ATI catalyst application is shown in applications menu.
      But now on system DEtails, in Graphics tab  it shows...
[B]#Driver:    VESA:RV710
#Experience: "Standard"

*>So how do i decide,that if iam Experiencing best "UBUNTU" Visual Experience???

"& What is difference between 2d n 3d experience ???"

[/B]
Also is there any other desktop experience than **"STANDARD"** ???



Looking Forward for reply


Thanks in advance:D:D:D:D

but some1 do reply soon :D

---

### Post by QIII on 2012-08-11
"Standard" indicates that you are not using a high end card.

Would you please enter the following in the terminal and post the results

```
fglrxinfo
```

---

### Post by HimanshuSingh on 2012-08-11
[COLOR=Navy]honey@honey-System-Product-Name:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series       
OpenGL version string: 1.4 (2.1 (3.3.11653 Compatibility Profile Context))

[COLOR=Black]Also when i Check on ***Additional Drivers**   *it shows**"No proprietary drivers are used in system"** [/COLOR]

[COLOR=Black]and it asks me to activate
**ATI/AMD** [B]Proprietary  FGLRX graphics driver


[/B]Although i have downloaded n installed this file...[B]
"amd-driver-installer-12.6-legacy-x86.x86_64.run"
[/B]it is a 101 mb file
i downloaded from the AMD website
[/COLOR][/COLOR]

---

### Post by NikTh on 2012-08-12
Hi , 
where did you find the instructions to install a driver-file from Internet ? 
Why you installed a file from web ? Who or what prompted you to install the driver from AMD's site ? I assume prompted you your recently experience from windows(am i right?)  
Ubuntu comes with pre-installed open source drivers for all types of graphic cards(including AMD/ATI). Name of open source driver is "radeon" . 
If you had a problem with open source driver , then you should try the driver provided by Ubuntu , the driver tested by Ubuntu developers . This driver show up when you open additional drivers. Usually install first this without updates.

---

### Post by QIII on 2012-08-12
First:  You do have the ATI driver installed and it is working.

Ubuntu is telling you that you don't have it because it doesn't know it's there because you did not install it from the Ubuntu repository.

The driver will work properly for now.  However, if your kernel is updated during a normal update it may not be compiled into the new kernel depending on the particular method you used to install it.  That would require a new installation from the file you downloaded from the AMD website.

When you install from the Ubuntu repo, the "record keeping" lets the system know it is there and the pieces to install it are where Ubuntu expects them to be and the driver is recompiled into the kernel automatically.

The default open source Radeon driver is very good and will serve most user's needs.  However, it does not have all the features of the proprietary driver.

Although the driver in the repo is 12.4, the differences between it and the most recent driver are probably not so important for that card that they represent any great gain.

Unless you want to reinstall when your kernel is updated, I recommend that you install from the repo using the method in the wiki in my signature in the section about using the Ubuntu repo (alternate command line method). Or simply uninstall the current driver and use the open source Radeon driver.

How you uninstall it will depend on how you installed it from the web.

Did you use the method that creates a .deb file or did you simply run the .run file you downloaded?  What is the URL of the instructions you used?

---

