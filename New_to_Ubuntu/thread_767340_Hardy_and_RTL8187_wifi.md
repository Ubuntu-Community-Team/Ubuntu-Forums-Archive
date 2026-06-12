---
title: "Hardy and RTL8187 wifi"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by xiliduur on 2008-04-25
Hello, 

I have a Netgear wifi usb dongle (RTL8187). It seems to work but the internet connection fails after 30 seconds. There's still a networkconnection but applications cant connect to the internet. 
I've searched and found several solutions regarding to RTL8187 and Ubuntu 7.10. Hardy has "build in" support, so do i need to do something else to get internet to work, or do i have to go threu all the troubles using ndiswrapper?

---

### Post by spiderbatdad on 2008-04-25
Check this thread for patch.[http://tinyshell.be/aircrackng/forum/index.php?topic=400.msg18264#msg18264](http://tinyshell.be/aircrackng/forum/index.php?topic=400.msg18264#msg18264)

---

### Post by coolbrook on 2008-04-25
Is it the WG111v#?  I find that the Realtek driver is flaky.  Consider using ndiswrapper, the Windows 98/ME Netgear driver and blacklisting RTL8187.

---

