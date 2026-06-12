---
title: "How to auto-load UPS software?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Chimmer on 2008-05-23
Hi,

I'm using UPS software by CyberPower called PowerPanel for Linux. I can get it to work ok but every time I reboot, it stops monitoring and I have to re-install it. I get the error message "Daemon service is not found."

Is there a way that I can have it automatically load at startup?

Thanks!

---

### Post by wpshooter on 2008-05-23
Have you tried just adding the proper service program to the System/Preferences/Sessions menu ?

Might I ask if this "PowerPanel" program works properly in doing a graceful shutdown of Ubuntu in case of a power loss ?

The reason I ask is because I am stil using both APC & Belkin UPSs from my old M/S windows days and neither of them currently have software that can be used to properly monitor and shutdown the system gracefully in case of power loss (that is without you having to reinvent the wheel to attempt to get it to work) on a Ubuntu/Linux system.

Thanks.

---

### Post by Chimmer on 2008-05-23
Thanks, still learning ubuntu and hadn't explored the "sessions" feature yet. I went in and tried adding the command but it didn't work. Rebooted and UPS still isn't running.

I even went in and selected the "automatically remember running applications when logging out" and that didn't work either. 

I'll keep playing with it to see if I can get it to work.

As far as the software actually doing a shutdown after power loss, I haven't tested it yet. :)

So far I did verify that the monitoring portion works, it gives me current status, etc. 

Once I get the auto-load to work, I'll look at testing it more thoroughly.

---

### Post by wpshooter on 2008-05-23
I "think" if you can find the correct service program to add to the sessions at startup, I believe that you will have your problems solved.

May I ask if the Power Panel software is installed directly off of a CD that came with the Cyber Power UPS and was it something that had to be ran from the terminal or was it a matter of point and click ?

P. S. - It would be my suggestion that you uncheck that automatically remember running programs at restart button.

Thanks.

---

### Post by Chimmer on 2008-05-23
I'm hoping to get it working. I downloaded the software directly from the CyberPower site at [this]("http://www.cyberpowersystems.com/products/management-software/ppl.html") link.

I was able to install it correctly and by opening a terminal and using the upsstatus command, it will list the current status. After I open the terminal and enter the command, it prompts me for my password. 

I was initially looking for some type of GUI for it but gave up. I was able to create a launcher shortcut for it. 

The only thing is, every time I reboot, I have to go in and use the ./install.sh command to re-install it, otherwise I get the Daemon service not found command.

I'm sure there is an easier way but as I said, I'm new to linux (having used Windows for many years.) I think I've come a long way, but still have much to learn.

I'll make sure to uncheck the "always remember" command.

Any other ideas?

---

