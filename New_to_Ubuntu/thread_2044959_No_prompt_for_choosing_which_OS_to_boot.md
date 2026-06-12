---
title: "No prompt for choosing which OS to boot"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by coloreporter on 2012-08-20
I just installed Ubuntu to dual boot with Vista.  There was an automatic restart after installing Ubuntu and then Vista loaded.  There was no screen to chose which operating system to boot up.  The screen with different f- (e.g. f2) options shows up only for a second so I can't read the options.

How do I access Ubuntu?

---

### Post by NikTh on 2012-08-20
Hi , 
probably Grub bootloader not installed correctly. 

Please boot from a LiveCD/Usb and click "Try Ubutu" , then open a terminal and apply below commands (copy-paste them from here to terminal for more accuracy) 

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
``` 
when window opens you will click the [Recommended Repair] option. When its done , reboot your system. 
Thanks

---

### Post by coloreporter on 2012-08-20
> **NikTh said:**
> Hi , 
probably Grub bootloader not installed correctly. 

Please boot from a LiveCD/Usb and click "Try Ubutu" , then open a terminal and apply below commands (copy-paste them from here to terminal for more accuracy) 

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```when window opens you will click the [Recommended Repair] option. When its done , reboot your system. 
Thanks
Thanks

---

### Post by Mark Phelps on 2012-08-20
BEFORE ... you do that, you need to tell us if you installed from INSIDE Vista using Wubi.  Why? Because, Wubi does NOT use GRUB, and forcing an install of GRUB is only going to make matters worse in a Wubi install.

---

### Post by critin on 2012-08-20
> **coloreporter said:**
> I just installed Ubuntu to dual boot with Vista.  There was an automatic restart after installing Ubuntu and then Vista loaded.  There was no screen to chose which operating system to boot up.  The screen with different f- (e.g. f2) options shows up only for a second so I can't read the options.

How do I access Ubuntu?

You probably have a zero or one second delay for speedy boot up.    Not a good idea in any case.  IMO.

I don't know Vista, but on XP AND Win8 you'd do this.   I imagine Vista is the same.
 Right click on Computer and click  on Properties.  Once on System Properties, choose Advanced. 

 At the bottom see  Startup and Recovery--click Settings.  At the top there are two check boxes for Time to display Operating Systems.    Choose the time in seconds. 

I also advise choosing time to show Recovery Options at the same time.  Click OK and you're done.

---

### Post by NikTh on 2012-08-20
> **Mark Phelps said:**
> BEFORE ... you do that, **you need to tell us if you installed from INSIDE Vista using Wubi.**  Why? Because, Wubi does NOT use GRUB, and forcing an install of GRUB is only going to make matters worse in a Wubi install.
Hi ,
Very good point and sorry I missed that. 
I assumed OP would say if installed Ubuntu with Wubi (but we must not count on guess).
Thanks

---

