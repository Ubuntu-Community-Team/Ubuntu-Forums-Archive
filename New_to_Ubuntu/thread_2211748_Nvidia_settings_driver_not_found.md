---
title: "Nvidia settings driver not found"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by siretfel2 on 2014-03-17
Hi all, 
First i want to thank ALL of you guys that help us noobs sort out things in ubuntu. I really want to thank you for spending time to answer our questions and provide your solutions and experience. I PROMISE you i'm not sucking up!!! Sincerely want to thank you cause i spend a week trying to solve problems in my pc running ubuntu that without YOU i wouldn't be able.

Now that i got this out, after about a week trying to setup lubunu 12.04 I finally got somwhere regarding the nvidia driver. 

I have the nvidia fx 5200 128 agp and installed the nvidia 173.14.39 driver. 
Along with the driver i got the nvidia-settings which when i opened i could't configure multiple screens cause the driver was older than the nvidia-settings version i had (it's a known bug i think)

So what i did (and MAYBE it's a solution for others like me with older systems) i googled and found nvidia-settings_295.33-0ubuntu1_i386, which is a version of nvidia-settings that WORKS with 173.14.39 driver.

Unfortunatelly i have this problem:
I set up the twinview or separate X (my card has vga and dvi) save configuration and i reboot.
After i reboot everything works fine either in twinview or separate X.

WHEN i try to open nvidia settings wtih gksudo nvidia-settings ...i get a message saying: *You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.*

To come around this issue i do the following:
1. sudo gedit /etc/X11/xorg.conf
2. Delete all the contents and save
3. sudo nvidia-xconfig
4. restart X server (alt ctrl backspace)
5. login again
6. gksudo nvidia-settings 

and now nvidia-settings work fine and i can again set twinview or separate X or whatever.

If i reboot or restart x server and try to open nvidia-settings, i get the same error to which if i follow the above steps eveyrthing works untill reboot again.

It's like nvidia settings after reboot fails to see that the driver is enabled and is in use.
Any suggestions for that?

---

