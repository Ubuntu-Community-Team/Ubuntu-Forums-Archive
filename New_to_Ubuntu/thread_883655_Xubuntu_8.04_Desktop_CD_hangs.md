---
title: "Xubuntu 8.04 Desktop CD hangs"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by dorothy on 2008-08-08
When I boot from the Xubuntu 8.04 (Desktop CD)I get to the menu screen when I select "Try Xubuntu without any change to your computer" or "install Xubuntu" after a few seconds the screen goes black and all I see is a flashing cursor. 

I know the CD is fine, as it works on another computer. I know the computer is fine as it boots Windows XP SP2, Damn Small Linux and Back Track 3 fine...

Any suggestions? 

By the way, the computer is an HP Omnibook 500 with 256MB RAM

---

### Post by overdrank on 2008-08-08
> **dorothy said:**
> When I boot from the Xubuntu 8.04 (Desktop CD)I get to the menu screen when I select "Try Xubuntu without any change to your computer" or "install Xubuntu" after a few seconds the screen goes black and all I see is a flashing cursor. 

I know the CD is fine, as it works on another computer. I know the computer is fine as it boots Windows XP SP2, Damn Small Linux and Back Track 3 fine...

Any suggestions? 

By the way, the computer is an HP Omnibook 500 with 256MB RAM

Hi and welcome, You may still want to check the cd for errors even though it works in another system.
Then you may want to do a checksum on the iso 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
You can also try the F4 option to change the resolution. 
Also you may try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash to see any errors. 
Lastly the 256mb memory may not be enough because some is being shared with the graphics. You may choose to install via the alternate cd.

---

### Post by dorothy on 2008-08-08
> **overdrank said:**
> Hi and welcome, You may still want to check the cd for errors even though it works in another system.
Then you may want to do a checksum on the iso 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
You can also try the F4 option to change the resolution. 
Also you may try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash to see any errors. 
Lastly the 256mb memory may not be enough because some is being shared with the graphics. You may choose to install via the alternate cd.

Thanks for your reply.

I burned the CD one of these fancy Mac towers and it verified the disk... I am fairly certaint he disk is fine.

I will try the F4 option, the F6 option and the alternate CD and post my results in this thread.

Thanks again...

---

### Post by dorothy on 2008-09-08
Turns out the CDROM just needed to be cleaned,so I got one of those CD-ROM cleaners... sorted.

---

