---
title: "dead screen at startup"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by ecrivain5 on 2008-05-03
Hi all,
       I have found a bit of a quirk, which, although annoying can be managed.
When I boot up from cold at anytime after a longish break. Ubuntu gos through start-up until the bar completed it's travels. Then a blank screen. No matter how many times I boot it will not goto the orange screen. That is until I boot windows, boot again and low and behold Ubuntu starts and will boot up fine until another lengthy turn off. ie: overnight.
The only thing I can think of is that I loaded the NVidia driver. I would like to try rebooting without that driver to see if that is the problem. Trouble is, as a newbie, I don't know how to. If you can help I will be grateful. My thanks in advance. Brian
[EMAIL="brian11smith@talktalk.net"]brian11smith@talktalk.net[/EMAIL]

---

### Post by BaffledMollusc on 2008-05-03
It seems unlikely that it's the driver, since booting into Windows first should have no effect on what driver is loaded.

Still, we can check. 

The easiest way to swap out the proprietary Nvidia driver, if you're using it, is to go to System->Administration->Hardware drivers. Is the box for the Nvidia driver ticked? If so, untick it and reboot.

Edit: How did you install the Nvidia driver?

---

### Post by ecrivain5 on 2008-05-03
Hi Mollusc
 I have removed driver and will need to wait to next COLD start-up to see if there is any change. I installed the Nvidia driver via the prompt re the nvidia driver. I will reply again tomorrow as I have no idea how long the PC has to be off before the prob shows it's ugly head. 
Thanks for now.
Brian

---

### Post by ecrivain5 on 2008-05-04
Hi Mollesc,
           Update this AM 6-25....Booted up fine without any problem. So, it looks like that driver MAY have some effect. Anyway I don't want or need 3D . Hope fully the problem is solved. I will have to wait and see. My thanks for your help. Brian

---

### Post by BaffledMollusc on 2008-05-04
Great, I'm glad it worked for you :)

I still can't figure out *why* it worked, though.

---

