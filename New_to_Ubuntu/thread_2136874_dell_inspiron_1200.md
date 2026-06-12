---
title: "dell inspiron 1200"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by rwhite1181 on 2013-04-18
I am new to Ubuntu and wondered if there were any suggested versions that are really compatible with a Dell Inspiron 1200 laptop. 

Intel Celeron processor 1.3GHz
1.24 GB ram

I tried the newest version, but it did not work well with my 1350 wlan pc card.

Thanks for any advice given!!!

---

### Post by Elephant454 on 2013-04-19
What wireless card does it have? If it is a Broadcom card, you need a wired Internet connection for a little bit in order to fix it, no matter what version you use. The tutorial for installing the drivers are somewhere on this page, I installed some kernel module or another. [http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers) I hope this helps you. If not, I am sure someone else can probably do a better job once we know your wireless card.

---

### Post by DuckHook on 2013-04-19
Firstly, welcome to the forums and to Ubuntu.

You will not be happy with an Ubuntu experience on this laptop because it counts as ancient technology. Ubuntu is designed for modern equipment with fast graphics cards, and yours is far too slow to give you a pleasant ride. The best distro for you is Lubuntu or smaller. If you are willing to go outside the formal Ubuntu family but still make use of the repositories, then Bodhi or CrunchBang.

Lubuntu will likely do well, but the graphics chip is a concern. I would recommend that you try Lubuntu as a LiveDVD first. Once you make sure that everything works and performance is acceptable, it is easy to install directly from the Live DVD. The saving grace in your laptop is the memory. You must have beefed it up because it's default config is 256 MB.

<edit>

Forgot to add that you will need the 32-bit non-pae kernel in any distro. Your CPU will not run 64-bit and I don't believe it is PAE enabled.

</edit>

---

### Post by mörgæs on 2013-04-19
> **rwhite1181 said:**
> 

I tried the newest version, but it did not work well with my 1350 wlan pc card.



Does it mean that everything except wireless worked? 
Are you sure it was the newest version, that is 12.10?

---

### Post by rwhite1181 on 2013-04-21
thank you for the replies. it is a dell wan 1350 wireless card. an ethernet connection worked right off the bat. i tried both 10 and 12.10. the mem on the laptop is upgraded to a full gig.  i will give lubuntu a try. thanks!!!

---

