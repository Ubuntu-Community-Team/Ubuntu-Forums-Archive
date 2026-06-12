---
title: "Virtual Box on 12.04 is slow, very slooow ..."
date: 2012-06-06
forum: New to Ubuntu
---

### Post by cwmoser on 2012-06-06
Ubuntu 12.04, 64-bit
Virtual Box is very slow.
When I start Virtual Box after reboot, it works fast.
Then when I switch to another Linux App and come back
to Virtual Box, it runs so slow it freezes.
Using a WinXP VM.
To make the WinXP VM work, I have to click outside Virtual Box
and then back on the VM and something happens, and then it
freezes again.  
Weird.

In addition, CrossOver (the wine clone that you pay for) freezes too.

Carl

---

### Post by s1baker on 2012-06-07
Sounds like a memory problem.
How much memory do you have and how much memory have you allocated
to Virtual Box?
I used to have this problem, I had 1/2 gig of memory, then upgraded to
2 gigs of memory...fixed the problem.
I also have allocated about 350 megs of memory for VirtualBox.
I run XP as a guest OS under VirtualBox

---

### Post by Paqman on 2012-06-07
Also, have you got the guest extensions package thingy installed in your VM? The one that gives you a unified mouse and graphics drivers?

---

### Post by traditionalist on 2012-06-07
Almost certainly a memory issue. Too much swapping will slow things down very considerably. I have 8 GB RAM in this machine and if I allocate 4 GB to the VM it is nearly as fast as the machine alone.

---

### Post by cwmoser on 2012-06-08
Posted the issue over on forums.virtualbox.org and got a solution.

Turned off **2D Video Acceleration** for the VM.

Now Virtual Box runs fast.

Carl

---

### Post by roberto.ur on 2012-10-29
This solution worked for me [1]. 

I didn't have to reinstall the whole system again. I cloned my current machine (just in case) and set the configuration as the blog said and it does work. I don't think it is perfect but at least tolerable. The only thing I couldn't set is turn off the dynamic storage for a static one. Any ideas?

[1] [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

---

### Post by roberto.ur on 2012-10-29
This solution worked for me [1]. 

I didn't have to reinstall the whole system again. I cloned my current machine (just in case) and set the configuration as the blog said and it does work. I don't think it is perfect but at least tolerable. The only thing I couldn't set is turn off the dynamic storage for a static one. Any ideas?

[1] [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

---

### Post by RookMan on 2013-01-14
THE FOLLOWING WORKED FOR ME

Ubuntu 12.10 was running extremely slow inside VirtualBox (Oracle's VM Solution). 
I played with Video memory. Nothing. 
I played with Base memory. Nothing.
I tried to turn off "Enable 2D Video" but it was already off. 

What finally worked for me was: 
(1) If the Ubuntu VM is Paused or Running, as slow as it is, try to get the OS to do a clean SHUTDOWN. 
(2) When it finally shuts down, inside the Oracle VM VirtualBox Manager, the VM should now say POWERED OFF. Only in this state you will be allowed to change the SETTINGS
(3) Go to [Settings] [System] [Processor] 
    I selected 2 processors
        There is a warning that is displayed
(4) Go to [Settings] [System] [Motherboard] 
    Extended Features:  [x] Enable IO APIC   
(5) [Okay] then [START ->]
(6) Smile

---

### Post by pyrce on 2013-04-04
> **RookMan said:**
> THE FOLLOWING WORKED FOR ME

Ubuntu 12.10 was running extremely slow inside VirtualBox (Oracle's VM Solution). 
I played with Video memory. Nothing. 
I played with Base memory. Nothing.
I tried to turn off "Enable 2D Video" but it was already off. 

What finally worked for me was: 
(1) If the Ubuntu VM is Paused or Running, as slow as it is, try to get the OS to do a clean SHUTDOWN. 
(2) When it finally shuts down, inside the Oracle VM VirtualBox Manager, the VM should now say POWERED OFF. Only in this state you will be allowed to change the SETTINGS
(3) Go to [Settings] [System] [Processor] 
    I selected 2 processors
        There is a warning that is displayed
(4) Go to [Settings] [System] [Motherboard] 
    Extended Features:  [x] Enable IO APIC   
(5) [Okay] then [START ->]
(6) Smile

Thank you! Had the same issue with other fixes. This made my vm infinitely faster.

---

### Post by Mike_Michalak on 2013-10-07
This helped me, I had the same problem.  Once I turned off 2D and 3D acceleration my VM was fast again.

---

### Post by DuckHook on 2013-10-07
**Caution against simple answers**

I regularly experiment with some two-dozen VMs from Windows to Unix to Linux to Minix. There is no one magical solution to a slow or balky VM and each case is different, requiring different solutions. Disabling 2D and/or 3D may not be the optimal solution since this also disables much-desired functionality. For example, sometimes, the appropriate solution is to *increase* Video memory allocation. The common ingredient in solving VM issues on these forums is: *provide reams of info on both your VM settings and uses, and state the specs of your physical box*. Otherwise, it's just so many blind men groping in the dark.

It takes lots of trial and error, to say nothing of tweaking and fine-tuning, to optimize VMs. I mean, c'mon people... we are talking about running multiple instances of completely self-contained make-believe computers inside of a separate real one, all without stepping on each other's toes or corrupting the memory space of the real box. When you sit back and think about it, this involves ridiculous cheek, nerve and miracles of programming.

Last but not least, post VM questions to the VM subforum. The complexity of running VMs is why the subforum is there.

---

