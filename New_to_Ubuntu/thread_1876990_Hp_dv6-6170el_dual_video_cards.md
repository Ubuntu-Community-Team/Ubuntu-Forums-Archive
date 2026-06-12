---
title: "Hp dv6-6170el dual video cards"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by IulianPeride on 2011-11-07
Hello, I have a notebook with the intel core i7-2630qm cpu and it has an integrated video card that should be used when i don't need high performance. Also it has a [B]AMD Radeon 6770M video card. 

I installed ubuntu 11.10 because i don't like windows. 

The question is this: Does ubuntu choose automatically which video card is needed? On windows there was not a lot of rumor until i was using the amd radeon card but since i started ubuntu the rumor is quite high even if the cpu usage is lower than 10% so i assume that is using the Ati radeon card and not the intel graphics. Is there something i can do to or maybe there is a way to manually choose between them?
Thanks in advance.

Ps. i am using this laptop at the university so i need it quiet.
[/B]

---

### Post by khelben1979 on 2011-11-07
No, Ubuntu does not automatically choose which video card to be used, it's something you need to do manually.

If you need quiet operating with the AMD video card, I suggest you go for the non-free version of the AMD driver because it makes your CPU work less and it's more efficient. You can find the driver on the AMD webpage and make sure you choose the correct one which suits your pc hardware.

To say that it solves your problem, making it as quiet as you want to, that I don't know, so you need to test that out before you enter the library, I think. ;)

---

### Post by Mark Phelps on 2011-11-07
If your PC comes with the new Switchable Graphics (meaning, in Windows, it automatically switches between video chips, depending on what is being done with the PC), I'm guessing that the onboard graphics is an Intel chipset -- and that to use the AMD chipset in Ubuntu, you will have to find a way to disable the Intel graphics.

Otherwise, I believe that Ubuntu will use the Intel graphics by default and will not allow you to select the AMD graphics.

---

### Post by IulianPeride on 2011-11-11
> **Mark Phelps said:**
> If your PC comes with the new Switchable Graphics (meaning, in Windows, it automatically switches between video chips, depending on what is being done with the PC), I'm guessing that the onboard graphics is an Intel chipset -- and that to use the AMD chipset in Ubuntu, you will have to find a way to disable the Intel graphics.

Otherwise, I believe that Ubuntu will use the Intel graphics by default and will not allow you to select the AMD graphics.


Something isn't right at all. If ubuntu will use the intel graphics then the temperature shouldn't go over 55grades just as it is on windows. But when i turn on ubuntu, without mdoing anything apart opening the terminal and typing -sensors the cpu temperature is over 65 grades and it goes up if i try opening the browser or anything else. On windows the temperature was about 70 grades when i was playing crysis2 or the Witcher and never more than 60 grades if i was listening to music or browsing the internet. 
Also, yes, on windows the switch was automatic and i didn't had the option to switch it manually. :(

---

### Post by Mark Phelps on 2011-11-11
From what I read, what is supposed to happen with these new switchable graphics PCs -- in Windows -- is that you use the "lower-power" GPU by default until you do something (like launch a game) that needs a higher GPU -- then it switches automatically to the other one.

As far as I know, nothing like that is available in Linux distros. Thus, you will be using the same GPU all the time.

Plus, from what I read, you have to disable one of the GPUs in the BIOS in order to use the other -- and the problem then is that you've also disabled the switchable graphics function for Windows.

The fact of the matter is, that when hardware vendors introduce new options like this in MS Windows, it takes the Linux community some time to catch up.

---

### Post by khelben1979 on 2011-11-11
> **Mark Phelps said:**
> The fact of the matter is, that when hardware vendors introduce new options like this in MS Windows, it takes the Linux community some time to catch up.

Since there's a interest towards going away from the present X.org server system to [Wayland]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29"), maybe there's hope for them to fix this issue? Does anyone know their future plans?

---

