---
title: "What's the best way to do a complete Ubuntu install?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-08-17
I found I like Ubuntu enough to do a complete install rather than dual-boot with windows vista like I'm doing now. I have another computer I can run windows on if I ever needed to so I'm only looking at ways to have Ubuntu take over the remainder of my hard drive on my acer 4315 laptop. 

What is the best way to accomplish this without losing my wi-fi connectivity (it works now), programs I've installed, files etc? I still have the live-boot hardy heron disk but I'm afraid that if I choose the "guided" option so Ubuntu takes over my hard drive, it'll erase my newly installed programs and files. 

Something else I discovered is that I installed hardy 8.04 using the opposite side of my install disk meaning I installed the 64 bit Ubuntu on my windows vista 32 bit laptop. Maybe that's the reason my computer doesn't restart using the GUI restart icon and instead I have to first shut down, then turn computer back on? Will it hurt to keep using 64 bit Ubuntu or should I just start over and use the 32 bit Ubuntu?

---

### Post by sharks on 2008-08-17
most of them have 32 bit. while installing select **use largest continous space **or **select manual and create a own partiton**

Note:
please wait for others advice.

---

### Post by erickghint on 2008-08-17
First things first... do you have a 64bit processor? If so, no worries. Keep 64-bit Ubuntu. If not, I'm not sure... I would say install 32-bit Ubuntu and start over. 

As to your question about installing Ubuntu over your Windows install. My personal opinion is that instead of installing Linux on the whole drive (depends on how large it is, honestly), create a small partition for Linux to reside in (this can be done from the LiveCD without messing up your current Ubuntu install) and use the rest of the disk for storage. This way, if you ever need to reinstall for any reason, you don't have to lose any files that you may have wanted to keep. If you would like, I can do my best to explain that process to you. 

 If anyone else who is more experienced than I am thinks I'm off base with this, PLEASE tell me so I know in the future.

---

### Post by Brian_Newbie on 2008-08-17
> **erickghint said:**
> First things first... do you have a 64bit processor?

When I boot into windows vista it says "32 bit operating system." Is there a command line that'll illustrate if it's both 32 and 64 bit since when I installed ndiswrapper to make my wireless work, one of the lines in the terminal read "x86_64"

---

### Post by Ryadt on 2008-08-17
> **Brian_Newbie said:**
> When I boot into windows vista it says "32 bit operating system." Is there a command line that'll illustrate if it's both 32 and 64 bit since when I installed ndiswrapper to make my wireless work, one of the lines in the terminal read "x86_64"

Post the output of ```
uname -a
```

---

### Post by erickghint on 2008-08-17
If the laptop is fairly new, it should be a 64bit proc. Do you know what kind it is? (i.e. AMD or Intel, dual-core or single, etc...)

---

### Post by Brian_Newbie on 2008-08-17
brian@brian-laptop:~$ uname -a
Linux brian-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux
brian@brian-laptop:~$

Looks like a 64 bit from this result. My Laptop is an acer 4315. I'm just worried that if I do a complete install from the live-boot disk that it'll destroy my wireless connectivity since it took me awhile to get wireless to work.

Is there any advantage to have linux take over my hard drive completely?

---

### Post by Brian_Newbie on 2008-08-17
> **erickghint said:**
> If the laptop is fairly new, it should be a 64bit proc. Do you know what kind it is? (i.e. AMD or Intel, dual-core or single, etc...)

It's an intel celeron processor, not sure about dual-core, it's low end laptop so likely single

---

### Post by Ryadt on 2008-08-17
If you are happy with your system just leave it as it is. Use g-parted to format the vista partition and use it as a second drive or whatever.

---

### Post by erickghint on 2008-08-17
> **Ryadt said:**
> If you are happy with your system just leave it as it is. Use g-parted to format the vista partition and use it as a second drive or whatever.

Exactly what I was getting at :)

---

### Post by jerome1232 on 2008-08-17
Just a side note, a 64 bit OS would never have installed on a 32 bit processor so you know your processor is 64 bit. I would continue using 64 bit unless you have a low amount of ram (like 512 or less even 512 should be fine), 64 bit programs use a little bit more ram than 32 bit programs do.

---

### Post by Brian_Newbie on 2008-08-17
Thanks everyone for your advice. I think I'll just leave everything alone since most everything is working fine now. I could likely use external hard drives for more storage when I need it as has been suggested here. 

Perhaps this should be a new post. But the only thing that doesn't seem to work is the "restart" GUI icon or using sudo reboot in the terminal. If I shut down my computer then turn it back on, it works fine. However my computer won't shut down then restart automatically on its own for some reason.

Does this have to do with the BIOS settings?

---

### Post by jerome1232 on 2008-08-17
I'd have no idea where to start with that, posting a new thread with a title about that problem and finding the make of your motherboard would be a step in the right direction though.

---

