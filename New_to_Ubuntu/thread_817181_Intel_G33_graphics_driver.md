---
title: "Intel G33 graphics driver?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by brownii on 2008-06-03
I just installed ubuntu on a homebuilt computer. when i boot up, before i even log into ubuntu, a screen comes up that tells me that it had trouble detecting my graphics stuff and that i am running in low graphics mode and that i need to configure the graphics myself. so i run currently in 800x600 resolution, and would really like to run at higher res. i have already tried running the intel experimental graphics driver and when i run gksudo displayconfig-gtk, i choose that driver, test it, and it works. when i go to reboot, the same error comes up, and i select the intel driver, and still nothing happens - its like the driver wont take effect or something. any help is greatly appreciated!

---

### Post by Eclipse. on 2008-06-03
> **brownii said:**
> I just installed ubuntu on a homebuilt computer. when i boot up, before i even log into ubuntu, a screen comes up that tells me that it had trouble detecting my graphics stuff and that i am running in low graphics mode and that i need to configure the graphics myself. so i run currently in 800x600 resolution, and would really like to run at higher res. i have already tried running the intel experimental graphics driver and when i run gksudo displayconfig-gtk, i choose that driver, test it, and it works. when i go to reboot, the same error comes up, and i select the intel driver, and still nothing happens - its like the driver wont take effect or something. any help is greatly appreciated!

Hmm, weird.Your screen config should be automatically preconfigured.

Close all programs you have running and do this:

Open a terminal,
sudo /etc/init.d/gdm stop (this then rolls back to the command line)
sudo X -configure (has to be a capital X)

Then run the command displayed on the screen.

Report back what happens.

Thanks

---

### Post by bumanie on 2008-06-03
If the restarting of X sever doesn't work, you could try compiling a driver from intel's site [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)

---

### Post by brownii on 2008-06-03
wow, well i thought i had messed everything up because i typed the first line of code into the terminal and i got to a black screen that i always see at startup. it shows status of starting certain things with ok's on the right side of the screen. then i typed the second line, hit enter and nothing happened. so i had to reboot. then when i restarted, i suddenly have great screen res, and ubuntu automatically recognized my monitor and everything. thanks so much yall!

---

### Post by Eclipse. on 2008-06-03
Delete please.

---

