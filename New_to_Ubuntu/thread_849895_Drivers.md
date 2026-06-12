---
title: "Drivers"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by valthyx on 2008-07-05
Hi, i am new to ubuntu, so i need some help. I was using windows xp previously and just installed linux(dual-boot).
When i run linux i noticed that my speaker, wifi and some other hardwares are not working. So, i just want to ask where i can get the drivers to get my hardware functioning.
i have searched but no good answers returned. I ubuntu is  updated.

one more thing, i cant play divx,xivx,dat format movies. I have downloaded all codex from the updates. please help, thanks in advanced.

---

### Post by Dark_Stang on 2008-07-05
What type of hardware do you have that is not working?

---

### Post by miwaypet on 2008-07-05
Can't help without some hardware info. As for your multimedia there are some good threads on the forums that can help, but i recently found this:[http://blogs.zdnet.com/hardware/?p=2061&page=1]("http://blogs.zdnet.com/hardware/?p=2061&page=1"). It is simple and to the point. 

Now, get me some hardware info. Thanks.

---

### Post by steveneddy on 2008-07-05
Some of the links in my sig may help you with the sound and video issues.

---

### Post by ChameleonDave on 2008-07-05
> **valthyx said:**
> 
one more thing, i cant play divx,xivx,dat format movies. I have downloaded all codex from the updates. please help, thanks in advanced.

Open Synaptic.  Go to Settings > Repositories > Third Party Software > Add.

Add this repository:

```

deb http://packages.medibuntu.org/ hardy free non-free
```

Click "Reload".

Install the package *non-free-codecs*.

As for your other problems, we can do absolutely nothing until you say what they are.

---

### Post by valthyx on 2008-07-05
I am using intel pro wireless 3945abg(wifi card built-in)
realtek sound(speaker)

And can anyone tell me where can i get the c compiler? because i cant compile some tar balls.

---

### Post by ChameleonDave on 2008-07-05
> **valthyx said:**
> And can anyone tell me where can i get the c compiler? because i cant compile some tar balls.

Make sure you actually need to install from source code first.  There may be DEBs or repos available.

To compile software, enter this command:

```
sudo apt-get install build-essential
```

---

### Post by ChameleonDave on 2008-07-05
> **valthyx said:**
> I am using intel pro wireless 3945abg(wifi card built-in)
realtek sound(speaker)


It might be best to make two totally separate posts in the appropriate forum for each of those issues, giving full details of the hardware, current behaviour and what you want to achieve.

---

### Post by valthyx on 2008-07-05
>  Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


i dont have the drivers for linux for those hardwares, where can i get them?. Thank you.

---

### Post by ChameleonDave on 2008-07-05
> **valthyx said:**
> i dont have the drivers for linux for those hardwares, where can i get them?. Thank you.

How are you sure that you don't have the drivers?  If you are not getting any sound, there may be some simple configuration you need to you.

I repeat: I believe the best result would come from posting a separate query on each of the issues you have.  Not in this thread.  Not just giving the exact name of the hardware (though that is good).

---

