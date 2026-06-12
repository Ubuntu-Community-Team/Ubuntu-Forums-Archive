---
title: "[SOLVED] How do I remove a program?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-05-12
Bs'd

I have a windows program installed, and it works a bit through WINE. 

But I want to uninstall it and reinstall it, with other features.  How do I uninstall a program?

---

### Post by Gazneth on 2008-05-12
You can uninstall it through wine, menu option: uninstall wine software.

---

### Post by Carnivorum on 2008-05-12
Bs'd

That doesn't work.  When I try to uninstall it in WINE, then I get the uninstall window of that program, and when I go through the motions, it is still not removed afterwards.

---

### Post by SunnyRabbiera on 2008-05-12
> **Carnivorum said:**
> Bs'd

That doesn't work.  When I try to uninstall it in WINE, then I get the uninstall window of that program, and when I go through the motions, it is still not removed afterwards.

Yeh there seems to be a residual issue, I seen it happen on my system too...
the only way I was able to resolve it is by removing the hidden wine folder and reinstalling the applications I had in it.

---

### Post by Gazneth on 2008-05-12
The above post should work. Go to home folder then show hidden files look for .wine then go into that and delete the program files.

---

### Post by Inxsible on 2008-05-12
> **SunnyRabbiera said:**
> Yeh there seems to be a residual issue, I seen it happen on my system too...
the only way I was able to resolve it is by removing the hidden wine folder and reinstalling the applications I had in it.That would be a pain in the a$$ if you had multiple wine applications installed.

---

### Post by SunnyRabbiera on 2008-05-12
> **Inxsible said:**
> That would be a pain in the a$$ if you had multiple wine applications installed.

true, but I did that the last time and it worked.

---

### Post by Carnivorum on 2008-05-12
Bs'd

How do I get to homefolder?

---

### Post by Carnivorum on 2008-05-12
Bs'd

Never mind, I found home folder

---

### Post by Carnivorum on 2008-05-12
Bs'd

Do I delete everything I see in the .wine folder?

---

### Post by Gazneth on 2008-05-12
I would try to find the program folder and delete only it.

---

### Post by Carnivorum on 2008-05-12
Bs'd

After wiping out the whole .wine folder, 

After uninstalling Wine through the Synaptic PM a few times, (however, never getting rid of it or of the contents), after restarting my comp a few times, some times closing it, letting it die off, and starting it again, I managed to reinstall the program in such a way that I can use it without having to put the CD in it. 

A short while, (though never seriously) I considered a format C:, but thank God, that was not neccesary.  :)

Thanks everybody for their input.

---

### Post by Carnivorum on 2008-05-12
Bs'd

I have an old comp, 800 Mhz, 32 Mb RAM, with Gutsy on it.  When I don't open up more than 2 programs, it works, otherwise it freezes and I have to close it hard and restart it.

I just installed Wine there, and tried to install the program there, and he wouldn't do it. 

Would that be because of the fact that Wine improved in Hardy Heron, was it my too old comp, or just a glitch?

---

### Post by Magnes on 2008-05-12
> **Carnivorum said:**
> I have an old comp, 800 Mhz, 32 Mb RAM, with Gutsy on it.  When I don't open up more than 2 programs, it works, otherwise it freezes and I have to close it hard and restart it.

Are your swap partition big enough (512MB minimum in your case I think)? Maybe you just run out of memory? 32MB is to little for Gutsy.

---

