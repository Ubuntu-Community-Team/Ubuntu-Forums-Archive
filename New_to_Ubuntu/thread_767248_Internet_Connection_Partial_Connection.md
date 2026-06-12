---
title: "Internet Connection Partial Connection"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Hairy Hobbit on 2008-04-25
Hi.

First of all, thanks to all who are working overtime to answer all the issues and keep loading the coal into the servers.  We all really appreciate it, I'm certain.

OK, my issue.

I loaded HH using Wubi.

I have a USB connected Linksys Wireless G device to connect to my Linksys Wireless G router.  

HH recongnises the connection, and asks me for the security key, which I entered and got the "two green dots".  I also see entries in the network connection properties which seem to suggest I am getting a connection.

I couldnt update, speeds were down to 128bytes per second - but put this down to understandably busy servers.  But at least it showed some dload activity.

However, when opening and using Firefox, everything is slowed to an absolute crawl when trying to connect to any website.

Does anyone have any ideas?  I tried the same PC and devices under Windows and all works fine, so it's not coincidental hardware failure.

Thanks,
Dave

---

### Post by 123456789123456789123456 on 2009-03-29
the driver that Ubuntu is using is not fully compatable with the device.  I had a simular problem.  I used 8.04, and it reconized the usb wirless device, it even managed to use it limited, off and on connection.  when I upgraded to 8.10, all these problems were eliminated.  You can try using ndiswrapper, and install the windows driver for the device.  ndiswrapper is designed to convert the windows driver to a driver ubuntu can use, and install it.  I don't understand exectly how it works, but that would deffinatly salve the problem.  I am not sure in HH has that program already installed, 8.10 does, so it should.

---

### Post by 123456789123456789123456 on 2009-03-29
you access ndiswrapper from the terminal.

---

