---
title: "viewing system information - berlarc for Linux"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by manuleka on 2011-10-22
i'm running xubuntu 11.10 and i'm wondering if there's any softwares that i can use to report my system spec (especially hardware wise)

in Windows i use to run Belarc which is quite good but unfortunately it's only for Windows... does Xubuntu have any similar program?

cheers

---

### Post by jon zendatta on 2011-10-23
open a terminal and enter:
```
sudo apt-get install sysinfo
```

Applications -> System Tools -> sysinfo.
Or in the terminal 
```
sysinfo
```:KS

---

### Post by robert shearer on 2011-10-23
you could also open the terminal and run...
```
sudo lshw
```

lshw=list hardware and will give you comprehensive reports on your hardware specifications and capabilities.

you can then cut and paste that info here or into your browser for more detailed/specific info.

---

### Post by critin on 2011-10-23
I use Belarc too and looked for a similar program.  I've used some from the Software Center and wasn't satisfied until I found this one there.

**System Profiler and Benchmark**.  I think it's the closest thing to belarc there is in linux.

If there is is something more, I hope to hear about it from someone.

---

### Post by manuleka on 2011-10-23
thanks :) i'm hunting for a Driver for my Video Card and Sound Card which isn't functioning properly on Windows XP... 

a Radeon Mobility HD4330 but unsure what the sound device is, Sysinfo reports: ATI Technology Inc. RV710/730

---

### Post by L Campbell on 2011-10-23
> **critin said:**
> I use Belarc too and looked for a similar program.  I've used some from the Software Center and wasn't satisfied until I found this one there.

**System Profiler and Benchmark**.  I think it's the closest thing to belarc there is in linux.

If there is is something more, I hope to hear about it from someone.

Thanks for your helpful suggestion here.

Kind regards.

---

### Post by critin on 2011-10-23
[I]<<Thanks for your helpful suggestion here.

Kind regards. 		                   		  		  		 		 			 				__________________[/I] [I]
				Lewis.>>

[/I]You're very welcome[I].  
[/I]

---

