---
title: "Installing 14.04.2 or 14.10 on Thinkpad Pentium M 1399MHz"
date: 2015-03-03
forum: New to Ubuntu
---

### Post by CBBC on 2015-03-03
Hey there,

I successfully installed an older version of Ubuntu (12 something, with Linux 2.6.35-22 and GNU GRUB version 1.98+20100804-Subuntu3) on a Thinkpad Pentium M 1399MHz, 2 GB RAM. 
It downloaded the update packages from Ubuntu.com but refused to install them afterwards, for security reasons. 

So I am now trying to install one of the later versions: the 14.04.2 or 14.10.2, but it reads that I have to "choose a version with the right Kernel" for my laptop. When I try and install "at my own risk" anyway, it reads that the "PEA is missing"...

Does anyone know which version (and/or flavor/s) would work with this laptop, or have a solution to the issue? 

Any assistance would be much, much appreciated! 

Thanks,

CBBC

---

### Post by nerdtron on 2015-03-03
This link will probably help: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by CBBC on 2015-03-06
Thanks for your prompt repsonse and link, Nerdtron!
Unfortunately, I do not get the screen displayed in your link. On the Thinkpad, the blue screen reads the following options: 
Default
Help
Try Ubuntu without installing
Install Ubuntu
Boot
Check hard disk for defects
Test memory

I have tried selecting "Default", "Try Ubuntu without installing" and "Install Ubuntu". The only outcome is this text at the bottom of the screen: 
"Warning pae disabled. Use parameter 'forepae' to enable at your own risk"
But typing is not possible on that screen ... Do you have a Plan B? 

Thanks,

CBBC

---

### Post by nerdtron on 2015-03-06
You are booting from a USB right? Those options that you said are not the default ones when you boot from CD.
What tool did you use to create that installer? unetbootin?

---

### Post by CBBC on 2015-03-06
Yes, I am booting from USB and I used unetbootin (from a different computer) to create the installer.

---

### Post by CBBC on 2015-03-06
.

---

### Post by CBBC on 2015-03-06
.

---

### Post by nerdtron on 2015-03-06
Hhhmm.. so the main goal is to have that F6 option to edit the boot config of the installer. I'm not sure if Unetbootin allows that. Have you tried other usb creators like [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) Maybe they can allow you to edit the boot options.

Else last resort, maybe you need to burn the iso to a DVD. In this case, you can surely have that F6 boot options.

---

### Post by grahammechanical on 2015-03-06
> [COLOR=#000000] "choose a version with the right Kernel"[/COLOR]

That could mean that you are trying to install a 64 bit operating system on a 32 bit CPU and that will never work.

> [COLOR=#333333][FONT=Ubuntu](PAE) is a feature found on almost all 32 bit processors produced after Pentium Pro, ie. younger than around 1995. Because PAE is close to being a standard it is now a requirement for Ubuntu: _During installation the processor is prompted for the PAE flag, and only if present the process will carry on._ [/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]Lubuntu and Xubuntu offered a PAE and a non-PAE release up to and including 12.04, but from 12.10 only the PAE releases are maintained. [/FONT][/COLOR]

I am quoting the wiki link. 

> [COLOR=#333333][FONT=Ubuntu]A number of older [/FONT][/COLOR][Pentium M]("http://en.wikipedia.org/wiki/List_of_Intel_Pentium_M_microprocessors")[COLOR=#333333][FONT=Ubuntu] processors produced around 2003-4 (the Banias family) _do not display the PAE flag, and hence a normal installation fails_. However, these processors are in fact able to run the latest (and PAE-demanding) kernels if only the installation process is modified a little. The problem is not missing PAE, it's about the processor not displaying its full capabilities.[/FONT][/COLOR]

Please confirm that you have downloaded the i386 ISO image and not the amd64 ISO. In the past the default option on the download page was i386 but that is now changed and the default option is amd64. 

Regards.

---

### Post by CBBC on 2015-03-06
I will try the alternate installer your suggest, thanks Nerdtron. 
Could the problem be that I created the USB content / the installer on a different laptop than the Thinkpad? 
As for the DVD, I don't have that option, regrettably ...

---

### Post by nerdtron on 2015-03-06
> **CBBC said:**
> 
Could the problem be that I created the USB content / the installer on a different laptop than the Thinkpad? 


No. the problem is about unetbootin/other-usb-installers replacing the boot splash of Ubuntu where you get to edit the boot options. You are stuck on the boot screen they present to you.


And yes, please try the 32-bit version of Xubuntu or Lubuntu. If I remember correctly, Lubuntu 32-bit by default has a non-pae kernel which may work on your case.

---

### Post by CBBC on 2015-03-06
Thanks for your response, Grahammechanical! I confirm that I dowloaded the[COLOR=#000000] i386 ISO image, yes.[/COLOR]

---

### Post by CBBC on 2015-03-06
@Nerdtron: thanks for your quick answer. I will try the Lubuntu 32-bit you suggest and let you know how this fares.

---

