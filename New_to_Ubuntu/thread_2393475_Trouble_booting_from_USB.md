---
title: "Trouble booting from USB"
date: 2018-06-04
forum: New to Ubuntu
---

### Post by danwillm on 2018-06-04
Hi all,

So, I tried installing ubuntu and after trouble with the live installation, I successfully installed ubuntu onto my native drive,but I am met with a grub rescue prompt. So, I thought I would try lubuntu as a fix to my os as ubuntu's iso was acting up.

Here's the problem: Whenever I boot from the live USB I am met with a black screen whether I tried nomodeset or not. I'm troubled about how to install now.

Specs:
CPU: Celeron N3060
GPU: Intel Integrated Graphics (I looked for the specific model)
RAM: 2gb DDR3 @ 1600Mhz

All wrapped up in a Acer Cloudbook 14.

All answers appreciated!

---

### Post by TheFu on 2018-06-04
Chromebooks require special boot efforts.  Did you do all those necessary steps?  On my Acer chromebook, I had to download new BIOS, force developer mode and remove a  "write protect" screw from inside the case before anything other than chromeOS would work.  

If this is a windows computer, there was a thread here yesterday about installing to USB with some info about Acer systems needing special help.

---

### Post by danwillm on 2018-06-05
This is a windows 10 computer with UEFI bios. Windows came pre-installed with it.

---

### Post by TheFu on 2018-06-05
> **danwillm said:**
> This is a windows 10 computer with UEFI bios. Windows came pre-installed with it.

Did you find that thread?  Oldfred and I were both responding. Oldfred put in lots of links specific to Acer. Use it as a reference, but best to keep your specific issues here.

---

### Post by oldfred on 2018-06-05
A lot of Acer have needed UEFI updates from Acer.
And with Meltdown and Spectre CPU vulnerabilities, all systems UEFI need updates. Both Windows and Linux have updated kernels for those issues.
And Atom may not be as vulnerable, since it is not pre-loading next command.

Not sure why installer not booting, may be UEFI needs update.
But once installed you need to enable "trust" which is unique to Acer, but better than many other systems that need various work arounds.

       Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
      [/URL]
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
I thought most of the Celeron bay trail issues were fixed. 
       Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162) 
    
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

