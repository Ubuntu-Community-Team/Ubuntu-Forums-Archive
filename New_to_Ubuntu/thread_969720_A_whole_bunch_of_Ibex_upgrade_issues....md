---
title: "A whole bunch of Ibex upgrade issues..."
date: 2008-11-03
forum: New to Ubuntu
---

### Post by brodiesel on 2008-11-03
So.... my poor little battered toshiba satellite stayed up all night trying to install Ibex, and finally finished this morning. As soon as the restart happened, things started going wrong. 

When it restarted I let it boot in the new kernel (which someone else can remind me of the number) and the first time it didnt boot. screen just stayed black. 

then i tried the old kernel, which i had been using flawlessly for the last few months, and when the login screen popped up, i saw half of the screen, and there was noise for the second half of the screen. And, of course, the audio freaked out and the computer froze. 

i tried the new kernel a second time, but i cant get the wireless to work. it says the wireless has been disconnected, but i know its not the network. it remembers my old network, but wont connect. what am i doing wrong here? what would have changed with the wireless from one kernel to another?

and what the hell is happening with the login screen of the old kernel?

---

### Post by LowSky on 2008-11-03
The old Kernel is not going to work, because too much of the new software is dependent on the new kernel.

As for the network, have you tried rebooting your router? Did you need to load the driver when you install the last time, you might have to do it again.

---

### Post by brodiesel on 2008-11-03
thanks lowsky. good to know about the kernel, but unfortunately the router reset didnt do anything.

So a quick update that I cant wrap my thick head around.... 

I am currently using my wireless after booting with the live disc for Hardy. As soon as it was booted, I went to the wireless icon and it showed me all of the available networks. This didn't happen when I tried in Intrepid. What is different between the two? It would seem my machine has the required drivers...

Compunding the situation is that i dont have a disc for ibex, and i dont have a wired connection. 

any tips on what to do?

---

### Post by jimmy the saint on 2008-11-03
you need to be specific about your hardware.  If you have an nvidia card, try to use a different video driver, that should address your graphics issue.  As for the wireless, I have seen lots of reports about wireless issues with intrepid.  Its funny that Hardy seemed to fix a lot of wireless issues, but Intrepid brings a lot more with it.  look for fixes regarding your specific hardware as opposed to your laptop.

---

### Post by brodiesel on 2008-11-03
okay, you got me there. I think i was frustrated enough to not actually think about what I was doing. Let me be more specific. 

When, using the live disc, as i am now, i go system>administration>hardware drivers, and it show me as using several proprietary drivers, namely the Atheros HAL and Support for Atheros 802.11 wireless LAN cards. When I do the same in Ibex, it shows me using no proprietary drivers, nor can I enable them because I dont have a wireless connection.

So...

Is there a way to enable these devices in Ibex without downloading them again? They obviously exist somewhere on my HD. I have used them in XP, Gutsy, Hardy, etc....

And also, why do they release versions that don't automatically do this kind of stuff? I don't remember having this problem when I upgraded to Hardy.

---

