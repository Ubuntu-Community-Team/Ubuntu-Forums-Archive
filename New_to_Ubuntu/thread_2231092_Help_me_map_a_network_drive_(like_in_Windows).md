---
title: "Help me map a network drive (like in Windows)"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by va_cs2 on 2014-06-23
Hello guys!

First of all, I am not sure I posted this in the right section (was thinking on Networking and Wireless as well) but since I AM an absolute beginner, I thought it would be best if I ask my question here. 

So, what I want to do is to connect to a network drive that is available to everyone who lives in my dormitory. In Windows, it was really easy, I just had to click on 'Map network drive' and enter the \\server\share address. Then I had to enter my username and password, an voila! I was done. 

I am really not sure how to do this in ubuntu. Could you perhaps show me a method that does not requires the Terminal? Also, is it possible to map this networkd drive so that it 'logs me in' automatically when I boot my Ubuntu?

Thank you guys! :)

Eva

---

### Post by 3rdalbum on 2014-06-23
> **va_cs2 said:**
> Hello guys!

First of all, I am not sure I posted this in the right section (was thinking on Networking and Wireless as well) but since I AM an absolute beginner, I thought it would be best if I ask my question here. 

So, what I want to do is to connect to a network drive that is available to everyone who lives in my dormitory. In Windows, it was really easy, I just had to click on 'Map network drive' and enter the \\server\share address. Then I had to enter my username and password, an voila! I was done. 

I am really not sure how to do this in ubuntu. Could you perhaps show me a method that does not requires the Terminal? Also, is it possible to map this networkd drive so that it 'logs me in' automatically when I boot my Ubuntu?

Thank you guys! :)

Eva

In Windows, "mapping" a network drive means "assign it a drive letter". There are no drive letters in Linux - so what you want to do is mount the network drive.

This is usually trivially easy. Open a file browser window (click the little folder icon near the top-left of your screen). Click Browse Network on the side panel. Double-click the network drive if it appears there, otherwise double-click on Windows Network and browse around for it.

Making it mount automatically on startup is actually a lot more difficult, but I suggest simply bookmarking the network drive so it's quicker to get to in the future.

---

### Post by va_cs2 on 2014-06-23
3rdalbum, thank for your comment!

I was able to connect to the drive by going to Files-Connect to Server, and then entering smb://mywindowsserver/myshare. It then asked for my password and username. Still need to figure out how to connect to it automatically, but 'bookmaring' it seems like a good enough idea to me, thank, 3rdalmbum!

---

