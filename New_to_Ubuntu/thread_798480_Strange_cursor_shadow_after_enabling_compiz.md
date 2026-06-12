---
title: "Strange cursor shadow after enabling compiz"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by HenrikHam on 2008-05-18
After enabling compiz in Ubuntu 8.04 my cursor is changed. It looks as if it is hidden behind a small layer of white and grey lines. This only happens I left click on the Desktop and when using the menues.

Inside application windows things are normal.

Disabling compiz and enabling metacity removes the issue.

I have not been able to find any one else who have reported this issue

I have attached a photo of the pointer issue, since it does not appear when doing a screendump

Any hints will be greatly appreciated

Thanks

---

### Post by EXCiD3 on 2008-05-18
That is interesting indeed. What video card are you using and have you tried deleting the compiz settings folder to see if this is just a weird setting that accidentally got set? (the folder is located at /home/<username>/.compiz) 

I found here,[http://www.phoronix.com/forums/showthread.php?t=8214](http://www.phoronix.com/forums/showthread.php?t=8214), that someone else is having what sounds like the same problem. It is probably video card driver related.

---

### Post by HenrikHam on 2008-05-18
Hi

Thanks for your prompt reply. The link in your post indeed described exactly what was wrong. It is related to the 1650X1050 resolution on my ATI Mobility FireGL V5250 card. Changing the resolution to eg. 1450X1050 resolves the issue. 

Unfortunately there doesn't seem to be a solution for 1650X1050. I use the driver 8.47.3, which was automatically installed by Ubuntu.

So thanks again for your post. I think this is a hard nut given my graphics card and driver.

---

### Post by EXCiD3 on 2008-05-18
Yeah, unfortunately for us the graphics drivers are free but closed source so we have to wait until the company releases a fix when its an issue related to the driver. :( Nvidia has better support, but there are lots of flickering issues instead of graphical ones.

---

