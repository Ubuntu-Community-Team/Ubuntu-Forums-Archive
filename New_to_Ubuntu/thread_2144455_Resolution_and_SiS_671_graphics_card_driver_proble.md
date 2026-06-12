---
title: "Resolution and SiS 671 graphics card driver problems"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by rootle on 2013-05-12
Hello, I know that it has been asked many times, but I couldnt find the right answer. I am trying to install Sis mirage 3 671 graphics driver and change my resolution to 1366x768, because now I can only use 1024x768. I have tried many tutorials including:

[http://www.sudo-juice.com/change-lxde-screen-resolution-ubuntu-lubuntu/](http://www.sudo-juice.com/change-lxde-screen-resolution-ubuntu-lubuntu/)
[http://askubuntu.com/questions/95977/set-a-specific-screen-resolution-with-xrandr](http://askubuntu.com/questions/95977/set-a-specific-screen-resolution-with-xrandr)
[http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/)

And I am using Lubuntu version 12.04 because of this tutorial:
[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)

None of these tutorials worked, all the time something was broken and I had to remove xorg files through command line.
Please help me to change my resolution, and install those drivers.

---

### Post by Pjotr123 on 2013-05-12
> **rootle said:**
> Hello, I know that it has been asked many times, but I couldnt find the right answer. I am trying to install Sis mirage 3 671 graphics driver and change my resolution to 1366x768, because now I can only use 1024x768. I have tried many tutorials including:

And I am using Lubuntu version 12.04 because of this tutorial:
[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)

None of these tutorials worked, all the time something was broken and I had to remove xorg files through command line.
Please help me to change my resolution, and install those drivers.

I am the author of the how-to at Easylinuxtipsproject. Are you sure that you've applied the instructions carefully and with precision? Because I've applied the method described in that tutorial myself, and with success. Repeatedly.

---

### Post by rootle on 2013-05-12
> **Pjotr123 said:**
> I am the author of the how-to at Easylinuxtipsproject. Are you sure that you've applied the instructions carefully and with precision? Because I've applied the method described in that tutorial myself, and with success. Repeatedly.

Thank you for your reply. Yes I am sure I did exactly the same method.. Maybe my graphic card is somehow different, or something else is different. I tried it several times and no success..

When I enter ```
[COLOR=#111111][FONT=Consolas]lspci[/FONT][/COLOR]
```[COLOR=#111111][FONT=Consolas] to terminal, I can see that I have [/FONT][/COLOR]Silicon Integrated Systems [SiS] 671MX . Is this card the same with yours? 

P.S sorry for bad english

---

### Post by Pjotr123 on 2013-05-12
> **rootle said:**
> I can see that I have Silicon Integrated Systems [SiS] 671MX . Is this card the same with yours? 

Unfortunately I can't check that, because I don't have that machine anymore. It was a SiS 671, but I don't know about the MX.

Did you check whether you've used the right files for your system architecture (32 bit or 64 bit)?

---

### Post by rootle on 2013-05-12
Yes I have checked everything, I did it few times. And after reboot all I get was black screen and console, so all the time I had to remove xorg.conf file to get it working again

Edit:
I have used tutorial on [http://project-smansa.blogspot.co.uk/2012/12/vga-sis-671672-sis-mirage-3-sisimedia.html](http://project-smansa.blogspot.co.uk/2012/12/vga-sis-671672-sis-mirage-3-sisimedia.html) this website and it's working now! I had to translate from Indonesian though.

---

### Post by bellera on 2014-02-27
Other solutions, tried with 12.04 LTS 32 bit...

[http://blog.bigsmoke.us/2011/01/18/ubuntu-sis-671-driver](http://blog.bigsmoke.us/2011/01/18/ubuntu-sis-671-driver) (only 1024x768)

[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis) (1280x800). The page says that it doesn't work for 12.04.3 and after, but it worked for me.

[FONT=courier new]# lshw -class video

*-display UNCLAIMED
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:9000(size=128)[/FONT]

However, xrandr command doesn't show the two connections of the card, LVDS1 and VGA1.

---

