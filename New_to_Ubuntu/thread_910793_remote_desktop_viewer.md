---
title: "remote desktop viewer"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by patchido on 2008-09-04
well... a friend of mine who has an apple needs for me to help her but she cant explain me her problem correctly... i saw this in the applications menu.. is it possbile for me to connect to her... she gave me the ip

---

### Post by jbrown96 on 2008-09-05
If she has a vnc server installed. that can be done fairly easily. I imagine you will need a graphical environment, but if not, ssh is the way to go. ```
ssh username@ip
``` replace username with her username and ip with the address. you will need her password. she could also create an account for you.

---

### Post by HermanAB on 2008-09-05
You need a reverse VNC server and client:
[http://www.vncscan.com/vs/oneclickVNC.htm](http://www.vncscan.com/vs/oneclickVNC.htm)
[http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)

Cheers,

H.

---

