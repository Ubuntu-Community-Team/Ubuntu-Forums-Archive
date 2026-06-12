---
title: "upgrade problem"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by crip720 on 2012-11-14
I did a clean install of 10.04.4 updated it, and then did an upgrade to 12.04.  After the restart,  got the 12.04 desktop with a blank top panel.  No icons/buttons will work, mouse pointer will move,  no control functions.  Shut down by REISUB.  Only error I see is at boot [something like{ no augment found}].  Did this to test if I should upgrade my main 10.04,  since I have high temps in most of the Ubuntu types of 12.04[Zorin ,Ubuntu, Mint]. Recovery option seems to be only pages of text, instead of the GUI page.   If this has been solved, pleased point to the answer, since the search on Ubuntu forums is not working for me tonight.  Thank you  Colin.

---

### Post by newb85 on 2012-11-14
Sounds like graphics card/driver issues.  The command:
```
sudo lshw -C video
```
should give us more details.

Try booting from a Live CD or USB to run that and paste the output to this thread.

---

### Post by crip720 on 2012-11-15
I am taking this from another partition on the laptop, but I do not think it is hardware related, ubuntu has always liked this laptop. description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:28 memory:d0000000-dfffffff(prefetchable) ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff

---

### Post by Mark Phelps on 2012-11-15
Just in case someone tells you to upgrade to 12.10, you need to know that this summer, AMD dropped Linux driver support for the HD 2x/3x/4x series of cards.  So, you will be relegated to the open-source drivers.

---

### Post by crip720 on 2012-11-15
The open sourced driver seems to work okay,  just want to know if I had a bad upgrade or how to fix it if possible.  This is only a test partition/upgrade before I goof up my main one.  Colin

---

### Post by monkeybrain2012 on 2012-11-15
Instead of fixing a bad upgrade I would just save the data and do a clean install. Much has changed since 10.XX and 12.04 and there are so many in between versions I would be surprised that it works at all. Clean install saves you a lot of troubles later and it is a lot faster even though you have to reinstall your software. 

BTW, if you have been using proprietary drivers or ppas you have to revert those to system default before you upgrade (OK may be this last part doesn't apply since you said you have a clean install of 10.04 then upgrade to 12.04. On second reading I am not sure what you are asking, do you want to roll back to 10.04? That would not be possible, you need to reinstall it)

---

### Post by crip720 on 2012-11-15
Just wondering if I am missing a quick fix for this.  Like I said after upgrade I just have a 12.04 desktop that does not function, and a blank top panel also.  The recovery option just shows page of terminal like text, no GUI page.  This is only a test partition, so no worries of losing any data.  Should also mention I installed X sensors and added acpi_osi=Linux to the grub of 10.04 before upgrade.  Colin.

---

### Post by crip720 on 2012-11-16
HI, was fooling with the 12.04 upgrade last night and I am able to get the terminal.  Did a update to the system.  Desktop is still not functionable.  If you know any commands I could use to fix the desktop[xserver] it would be appeiccated.  Thanks,  Colin.

---

