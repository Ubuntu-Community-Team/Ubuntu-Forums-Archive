---
title: "CPU Temp Monitor Programs"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-07-05
when using some temp monitoring programs it shows two different temps for, let's say, the CPU. One temp is for the core and the other simply says CPU Temp. The CPU I have installed is an AMD Athlon 64 X2 4600+ Brisbane core AM2 65W cpu and the AMD website says Max operating temperature (°C) 55 - 68 so which temp in the monitoring program (core or cpu temp) will display this temp range? Also, is the following true because mune is running at 33 C most of the time ?

Minimum and Maximum operating temperatures specify the range of temperatures in which the CPU is guaranteed to function. It is not recommended to operate the CPUs at temperatures lower than the minimum ...


thanks for any feedback

---

### Post by cariboo on 2008-07-06
I've got an older core2 amd 3200, I just monitor the two core temps as they are always within a degree of the cpu temp. On average they run at 42°C, but with the warmer temps we've been having lately, mid 30°'s C, and installing an os in kvm I've seen temps as high as 58°C. I've got the shutdown temp set at 60°C. The thing I'm more worried about is hdd temp, as my case is fairly small and I've cooked one drive already.

My den is fairly small and normally I've got at least 3 computers running plus a 32" High Def monitor, High Def satellite PVR and stereo receiver running so that tends to keep the room fairly warm. With all the equipment running it keeps the room nice and toasty when  the outside temp is -20°C.:)

Jim

---

### Post by silkstone on 2008-07-06
The important parameter is the 'critical temperature' above which the CPU could be damaged. This varies according to the type of CPU, and you should be able to find the information on the manufacturer's website. Typically, critical temperatures are somewhere between 65C and 80C - for example, the E4600 in this machine has a critical temperature of 73C. Ideally, it's best if the temperature stays at least 20C below the critical value in normal use. There is no recommended minimum temperature - the cooler the better!

The core temperatures and CPU temperature should be very close, so you can display either. I usually display the CPU and GPU temps on the top panel - any more than this takes up too much space!

---

### Post by sdennie on 2008-07-06
I've not used AMD machines before but, a max operating temperature of 68C seems very, very low to me.  I have an Intel T9300 and under very heavy load it will happily go to 70-80C.  It idles in the high 30C range but isn't shy about more than doubling the temperature.  

Regardless, modern CPUs protect themselves against overheating.  If the machine gets too hot, the CPU will limit the max frequency.  If that doesn't work, it will simply shut down.  You would quickly notice either of these effects so, if you aren't seeing them, you probably aren't having a problem.

Still, compressed air is your friend.  If you clean out your machine with compressed air once a month, I can guarantee that it will run noticeable cooler.

---

### Post by Canis familiaris on 2008-07-06
> **vor said:**
> Still, compressed air is your friend.  If you clean out your machine with compressed air once a month, I can guarantee that it will run noticeable cooler.
Sorry for lack of my knowledge! But what exactly is compressed air? Vacuum? Air-conditioning?

---

### Post by wrtpeeps on 2008-07-06
> **Anurag_panda said:**
> Sorry for lack of my knowledge! But what exactly is compressed air? Vacuum? Air-conditioning?

You can buy tins of compressed air. Use them to get rid of dust etc.

---

