---
title: "System Information"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by will_s54 on 2008-07-11
Is there something like Everest available that will show me my complete hardware and the drivers used in my Linux setup ?

---

### Post by drs305 on 2008-07-11
> **will_s54 said:**
> Is there something like Everest available that will show me my complete hardware and the drivers used in my Linux setup ?

You can run this to create an html file on your Desktop of system hardware:
```
sudo lshw -html > ~/Desktop/hardware.html
```

---

### Post by Xerp on 2008-07-11
System - Preferences - Hardware Information

---

### Post by will_s54 on 2008-07-11
> **drs305 said:**
> You can run this to create an html file on your Desktop of system hardware:
```
sudo lshw -html > ~/Desktop/hardware.html
```


thanks, that helps a little but still cant see what I want which is the video drivers that Ubuntu are using ie 173.14.5    

Yes , still used ti Windows but am slowly starting to understand Ubuntu  and I mean slowly  :-)

---

### Post by will_s54 on 2008-07-11
> **Xerp said:**
> System - Preferences - Hardware Information

not there

---

### Post by leomelo on 2008-07-11
sudo apt-get install hardinfo

---

### Post by bab1 on 2008-07-11
I'm looking at mine right now.  Maybe you did System > Administration instead of Preferences.  ;-)

---

### Post by drs305 on 2008-07-11
For nvidia, you can run the following:
```
gksu nvidia-settings
```

Is that what you are looking for?

---

### Post by will_s54 on 2008-07-12
> **bab1 said:**
> I'm looking at mine right now.  Maybe you did System > Administration instead of Preferences.  ;-)

am looking at it now and definitely not there. maybe its something that has to be installed ?

the only time I see hardware mentioned is when I go system/admin and it shows hardware drivers or hardware testing but in sys/pref it aint there

---

### Post by will_s54 on 2008-07-12
> **drs305 said:**
> For nvidia, you can run the following:
```
gksu nvidia-settings
```

Is that what you are looking for?

2.1.2 NVIDIA 173.14.05 I can now find in thaat panel

thankyou for that

Am having problems with my graphic card and I think it may be the card but at the moment have now got it working ok

---

### Post by chewit on 2008-07-12
> **drs305 said:**
> You can run this to create an html file on your Desktop of system hardware:
```
sudo lshw -html > ~/Desktop/hardware.html
```

I have justed used that command, very useful tool.

However, when I was reading through the html document, I found this:

id:	cpu
description: 	CPU
product: 	Celeron (Coppermine)
vendor: 	Intel Corp.
physical id: 	4
bus info: 	
cpu@0
version: 	6.8.3
slot: 	Socket 370
[B]size: 	633MHz
capacity: 	1GHz[/B]
width: 	32 bits
clock: 	66MHz
capabilities: 	fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up


Does this mean that I could change the speed of my cpu via the BIOS to 1GHz?

---

### Post by will_s54 on 2008-07-12
> **leomelo said:**
> sudo apt-get install hardinfo

I assume that installed system profiler and Benchmark:)

Thankyou   :guitar:

---

