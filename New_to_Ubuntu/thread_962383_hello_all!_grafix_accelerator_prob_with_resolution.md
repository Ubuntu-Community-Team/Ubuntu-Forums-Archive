---
title: "hello all! grafix accelerator prob with resolution&amp;hertz"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by kokoni on 2008-10-29
im a new user of ubuntu and i have a little problem with my grafix.when i enable the nvidia grafix accelerator and i reboot my pc goes out of hertz out of range with the screen.. i can only use display resolution 800*600 if i dont enable the grafix accelerator!so what i have to do now? maybe a command from the terminal or something? 

p.s tnx for your time ;) :popcorn:

---

### Post by random turnip on 2008-10-29
Ah, i had this exact same problem.  All you will probably need to do is make sure you have enabled the use of the graphics card for the user, if you have Nvidia Ubuntu will already have recognised it, but in the hardware list you need to type your password in to let your user have permission to use the graphics card. After you have done this you will have more options when you go to choose the screen res.

---

### Post by kokoni on 2008-10-29
ubuntou had already recognized my nvidia, how do i type my password in to let me have permission to use the graphics card?(it always ask me a pass for those updates and i put it right ;) i made a test now,hardware test...so i think even with my pass everything goes wrong :/

p.s as you see i have 2 options! 800*600 resolution with enabling anything or enable my accelerator and get black screen and out of range!

---

### Post by igknighted on 2008-10-29
> **kokoni said:**
> ubuntou had already recognized my nvidia, how do i type my password in to let me have permission to use the graphics card?(it always ask me a pass for those updates and i put it right ;) i made a test now,hardware test...so i think even with my pass everything goes wrong :/

System->Administration->Hardware Drivers

---

### Post by kokoni on 2008-10-29
yea bro tnx i did it already see the results

---

### Post by random turnip on 2008-10-29
You need to click in the tick box for the "enabled" collumn, it should then let you choose the proper screen res.  Warning, don't set the screen res too high for your graphics card or screen, it cos do damage over time, but you should be able to tell whats right anyway.

---

### Post by igknighted on 2008-10-29
Run this command in the terminal and post back the output, please:
```
glxinfo | grep direct
```

---

### Post by kokoni on 2008-10-29
xmm ok im sure i already did it and i got black screen after the reboot..let me try one more



i did it !!so same results if i enable it requires restart.if i restart i got black screen!!what the hek is going on :D

---

### Post by kokoni on 2008-10-29
> **igknighted said:**
> Run this command in the terminal and post back the output, please:
```
glxinfo | grep direct
```



the results :

---

### Post by heimo on 2008-10-29
Are you using Ubuntu 8.04? Have you tried 8.10 beta release? I believe 8.10 release is schedule to tomorrow, and if you're not already using it, give it a try and let us know if your experience is any better. :-) Good luck!

---

### Post by kokoni on 2008-10-29
im checking something give a sec ;)

---

### Post by kokoni on 2008-10-29
i tried with envy prog but nothing happened ........


does anyone knows what to do???

---

### Post by usafe7ret on 2008-10-29
Which nVidia card do you have?

Which driver file do you have?

I had a update the loaded a newer version of the driver for my FX5200 and it gave me the same symptoms.

I had to go out to nVidia's site and get an older version, copy it to my local directory, then follow a 12 step process to remove Envy, the old xserver.conf file, install the new driver and restart the xserver before the problem was corrected.

Now, I have the same issue again, and a lot worse, so I am going to reinstall Ubuntu  and then keep my fingers crossed the new release will help.

---

### Post by kokoni on 2008-10-29
my card is on board nvidia 7100 512 ram.. and the drivers i think that they are from the last update ...

---

### Post by kokoni on 2008-10-30
so nothing more for me?

---

