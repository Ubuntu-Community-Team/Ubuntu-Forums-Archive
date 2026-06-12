---
title: "Problems running Ubuntu 11.10"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by RichDavey on 2011-10-29
Hi there, 

I've been trying to get Ubuntu up and running on my Laptop (Toshiba Satellite with HP pavillion monitor) and don't seem to be having much joy. 

Recently, my hard drive developed problems, but I was able to run Knoppix live CD to extract all my work, but can only run it in vesa mode- anything else and i get black and white stripes. Since then, my drive has been wiped and I don't want to put Win XP back on it if I can help it. 

Now, I want to install Ubuntu and have managed to use the USB boot up to get to the options screen, but I can't get it to load without the black and white stripes. I tried looking at the help options, but whenever I tried boot: rescue or something like that, it just said something about the kernels.

I am a relative newbie to linux and if anyone can lend a hand it would be greatly appreciated!

Many thanks,
Rich

---

### Post by roger_1960 on 2011-10-29
Hi

Do you get the stripes on the laptop screen and the monitor? Does it happen if you unplug the monitor before booting the live CD?

---

### Post by RichDavey on 2011-10-29
> **roger_1960 said:**
> Hi

Do you get the stripes on the laptop screen and the monitor? Does it happen if you unplug the monitor before booting the live CD?

Hi Roger,

I should have said that the screen on my Laptop is broken, which is why I've been using the monitor.

---

### Post by tartalo on 2011-10-29
Try "safe graphics mode"
[http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/](http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/)

---

### Post by RichDavey on 2011-10-29
Thanks for that Tartalo - I tried the suggestions in the guide, but still no joy - even tried using Ubuntu 10.10 that I had on CD. I keep getting so far before it crashes - I got to the desktop once but the whole thing froze.

---

### Post by LinuxFan999 on 2011-10-29
> **RichDavey said:**
> Thanks for that Tartalo - I tried the suggestions in the guide, but still no joy - even tried using Ubuntu 10.10 that I had on CD. I keep getting so far before it crashes - **I got to the desktop once but the whole thing froze**.
Did you mean that 10.10 or 11.10 froze?

---

### Post by RichDavey on 2011-10-29
10.10 froze - I got a bit further with it a while ago: using the F6 options- noapic, nolapic, nomodeset, edd=no, I got to the desktop again. when i tried to connect to wireless the system froze again.

---

### Post by nogoodnamesleft on 2011-10-29
> **RichDavey said:**
> Hi there, 

Recently, my hard drive developed problems, but I was able to run Knoppix live CD to extract all my work, but can only run it in vesa mode- anything else and i get black and white stripes. Since then, my drive has been wiped and I don't want to put Win XP back on it if I can help it. 

Rich

If the machine (or the drive) is broken or unreliable I would replace it. You're only going to lose everything again, otherwise. Who knows, it might even install properly after. What you are saying sounds like hardware, in all honesty. Linux - especially maverick - doesn't really generally die like this. You get some odd issues but most modern OS are stable (even XP, out of the box, before you load programs onto it) and just do not randomly randomly crash on new installs on working hardware.

---

### Post by LinuxFan999 on 2011-10-29
> **RichDavey said:**
> Hi there, 
 
I've been trying to get Ubuntu up and running on my Laptop (Toshiba Satellite with HP pavillion monitor) and don't seem to be having much joy. 
 
Recently, my hard drive developed problems, but I was able to run Knoppix live CD to extract all my work, but can only run it in vesa mode- anything else and i get black and white stripes. Since then, my drive has been wiped and I don't want to put Win XP back on it if I can help it. 
 
Now, I want to install Ubuntu and have managed to use the USB boot up to get to the options screen, but I can't get it to load without the black and white stripes. I tried looking at the help options, but whenever I tried boot: rescue or something like that, it just said something about the kernels.
 
I am a relative newbie to linux and if anyone can lend a hand it would be greatly appreciated!
 
Many thanks,
Rich
 
> **RichDavey said:**
> Hi Roger,
 
I should have said that the screen on my Laptop is broken, which is why I've been using the monitor.
 
> **RichDavey said:**
> Thanks for that Tartalo - I tried the suggestions in the guide, but still no joy - even tried using Ubuntu 10.10 that I had on CD. I keep getting so far before it crashes - I got to the desktop once but the whole thing froze.
 
> **RichDavey said:**
> 10.10 froze - I got a bit further with it a while ago: using the F6 options- noapic, nolapic, nomodeset, edd=no, I got to the desktop again. when i tried to connect to wireless the system froze again.
I recommend that you replace your laptop, since it is clear that you are having hardware issues. You can get a new Toshiba if you want, but you could try other brands like Dell or HP if you want to give up on Toshiba.

---

### Post by chris-desford on 2011-11-09
I have been running 11.04 quite seamlessly since April. I upgraded to 11.10 this morning and I am faced with a completely blank screen (apart from the wallpaper and a Home icon). There is a blank menu bar - apart from, in the top left corner "File . .  . . .Help", which doesn't give me any useful options. If I click on "change Desktop Background", I can access some configuration aspects, but nothing linked to Unity Desktop. 
I have no icons on the menu bar, no Unity launcher and the only way I can access programs is to open Home, navigate to /usr/bin/ and double click on the program I want to run. I can only shut down by using the terminal and "sudo shutdown now" which I start by the above method)
I have activated the NVIDIA recommended driver - that made no difference. If I start programs they work (at least so far)

I am assuming that the Desktop is not fully loading for some reason. I am a pretty seasoned linux user, but have so far wasted 4 hours trying to get a usable computer. (including visits to as many sites as I can find with this problem listed) 
Any suggestions would be gratefully received

---

