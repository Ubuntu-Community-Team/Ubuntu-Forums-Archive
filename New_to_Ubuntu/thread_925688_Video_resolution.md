---
title: "Video resolution ?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by larry Price on 2008-09-20
Just installed HH and when I go in and look at my video resolution the highest in the list is 832x624. In an effort to install a better driver for my ATI 3D RAGE IIC AGP card I tried ENVYNG. It just errors out. I'm guessing I have some odd ball video card without a good common driver. Any idea's?
Thanks
Larry

---

### Post by larry Price on 2008-09-21
Never mind, the whole thing blew up... all I get now is a white screen... this is not any where near being a really easy OS to get going...

---

### Post by dhtseany on 2008-09-21
Simple method of testing:
Try booting off of the LiveCD and see how the video works out. If it's ok try reinstalling UB to start fresh. Retrace your steps and figure out what happened that caused all the problems. We're here to help but don't get too p'ed off at us because you had a bad experience. Remember, many times Windows needs drivers installed after a fresh install too. The only way to learn is to ask questions.

Peace
Sean

---

### Post by larry Price on 2008-09-21
> **dhtseany said:**
> We're here to help but don't get too p'ed off at us because you had a bad experience. 
Peace
Sean
Thanks Sean, I'm not po'd at anyone on this board. I am mad at myself for falling for the hype. I should have looked at this board first. I would have realized just by the shear volumm of the Absolute Beginner Talk that Ubuntu was no plug and play OS. My fault. I have reloaded the OS again, along with the 265 updates again. Things are back to the way it was until I started messing with the ATI driver package. I am just going to accept that my ATI card is not supported by this varient of linux. I may try to find another card that is a better match. It shouldn't be too hard to find something that will support resolutions in the 1200 range. Thanks for responding.

---

### Post by roger_1960 on 2008-09-21
Hi

Try in Terminal: (applications, accessories, terminal)

sudo displayconfig-gtk

Enter your password (which wont appear), then change the settings in the GUI until you get what you think it should be.  You may need to log out and log in again.  Good luck!

---

### Post by dhtseany on 2008-09-21
Agreed. 

Also, try going to System -> Administration -> Hardware Drivers (enter password) and see if any additional drivers are available. Try that out and see if that helps. And don't beat yourself up too much. 

Of course there is a learning curve just like if your were trying to migrate from Windows XP to Mac OS X. Things take some getting used to but eventually I think that if you stick with it you'll be pleased with what you find.

Peace
Sean

---

### Post by dew5 on 2008-09-21
First off welcome to linux.

secound i have nvidia and had to do alot of searching before i found a good vga driver. 

third ive help ppl heaps with ubuntu and linux and you never stop learning.

Good on you for joining in on the fun of linux.

Dont give up.

dew5

---

### Post by larry Price on 2008-09-22
Roger, Sean, and Dew5, thanks for the responses. I've played with the sudo displayconfig-gtk for a little while after work today. When I run the test,what should I see? Most of the time I get a shimmery black harringbone thing. When I bring up the displayconfig, Screen is Plug 'n' Play 800x600 @ 60Hz (yuck) and the graphics tab sees my graphics card, Mach64 3D Rage IIC. Drive is none. I'm hesitant to accept any change since the last time I downloaded ATI drivers my screen went into a white out after I logged in. 
Larry

---

