---
title: "ubuntu upgrade new kernel : big problems"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by fillemon on 2013-09-06
hello,  i got running 12.04lts,

  
i have an 2500k processor, on an sandy bridge motherboard, with video (ati) onboard.   
today i runned an update and installed a new kernel 3.5.0-40 generic 686  

now restarting the pc: the pc is extremely slow to boot.   

it takes 25 seconds before it starts to boot, the first 25 seconds it seems to do nothing... (is it looking for a boot device ? ?)

   then when i'm entering into the grub console and run the new kernel it never gets the to login screen; when i hit ctrl alt del, all of a sudden the purple background appears and the ubuntu brand appears and the system shuts down. 

  when 'im entering in the grub the "safe modus" i'm seeing a number of options. 
 (i have repaired broken packages) 
(i have cleaned space) 
(i have dropped to console but could not do anything because it was not mounted)  

when i let the pc run into normal boot, i hit the prompt; 
 whatever i type into the prompt, after a few minutes the screen doesn't show anything anymore, and i cannot do anyhting exept ctrl-alt-delete.   (if i'm fast and do a sudo apt-get update, and sudo apt-get upgrade: there seems to nothing left to be upgraded.....  

anybody knows what is going on ?   

thanks

---

### Post by Drone4four on 2013-09-07
> **fillemon said:**
> when i let the pc run into normal boot, i hit the prompt; 
 whatever i type into the prompt, after a few minutes the screen doesn't show anything anymore, and i cannot do anyhting exept ctrl-alt-delete.   (if i'm fast and do a sudo apt-get update, and sudo apt-get upgrade: there seems to nothing left to be upgraded.....  

anybody knows what is going on ?   


It could have something to do with Intel's drivers in the kernel.  You could try disabling them by using low graphics mode.  You do this by passing the 'nomodeset' parameter at the grub2 menu.  Highlight the kernel you want to boot.  Press 'e'. Then add 'nomodeset' to the end of the line that begins with 'linux.'  Then press Ctrl+X. 

Please report back here if my suggestion works (or doesn't work).  

Cheers,

---

### Post by deadflowr on 2013-09-08
Have you tried booting into the older kernel?
It would be the option after the recovery mode in the grub menu.

Ubuntu doesn't delete the older kernels until you say so.
Try that, it happens that sometimes a new kernel can cause some problems from time to time.

---

### Post by Frogs Hair on 2013-09-08
If the the old kernel works you might want to consider re-installing the newer one if you have the synaptic package manager installed .

---

