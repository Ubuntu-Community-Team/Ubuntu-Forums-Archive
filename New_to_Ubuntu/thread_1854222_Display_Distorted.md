---
title: "Display Distorted"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by P05TMAN on 2011-10-03
Hey everyone! 

I couldn't wait any longer & upgraded to 11.10 beta2. I know that this is still in the works, but my display is looking a little funky. I noticed that xorg.conf is gone & every known graphics card driver is selected (not by my doing) in the Ubuntu Software Center. When I open a new window, be it LibreOffice writer or whatever, I'll close it & a 'ghost' of the previous screen is faded in the background. It's best to see the screen shot that I have attached. I'm running Onieric on a Dell Inspiron N5010, 8GB RAM, 750 HD, Intel HD graphics & Intel i5. Any suggestions to help me figure this out? Let me know if I can submit more info. 

Thanks, everyone!

---

### Post by P05TMAN on 2011-10-04
After deselecting some of the unnecessary drivers (ie ATI, Radeon, etc) the display is better, but the wireless connection just stopped working. There is a key on my computer (F2) that usually would toggle the wireless on/off but it is unresponsive. The 'wireless enable' selection in the tool bar is grayed out also. Also, my mouse pointer is flashing intermittently. Perhaps this has something to do with the Video card driver still?

---

### Post by P05TMAN on 2011-10-04
Aright! I figured it out! There were actually two Intel video card drivers that were conflicting. The ones that were installed were the X.Org X Server- Intel i8xx, i9xx & it was conflicting with the X.Org X Server- i740 display driver. Once I uninstalled the i740 driver, all was good to go. The only thing I have to t/s now is being able to disable/enable my touch pad with my function button; I'll open a new thread for that though.

---

