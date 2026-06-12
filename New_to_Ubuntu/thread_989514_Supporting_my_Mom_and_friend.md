---
title: "Supporting my Mom and friend"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by rmcellig on 2008-11-21
I installed Ubuntu 8.10 on my Mom's (a senior) new PC recently. She loves it even though she is totally computer illiterate. When I have to show her something in Ubuntu or offer her support, I would love to be able to take control of her screen from my place. What is the easiest way to do this?

I also installed Ubuntu on my sister's mother in law's computer as well so I would like to offer her the same kind of support.

Since I am new to Ubuntu, I would like to be able to take control of their computers as easily as possible.

Thanks!!

---

### Post by 73ckn797 on 2008-11-21
You might find something here:[U]
[https://help.ubuntu.com/htdocs/ubuntunew/search.html?cx=003883529982892832976%3Ae2vwumte3fq&cof=FORID%3A9&ie=UTF-8&q=remote&sa=Search](https://help.ubuntu.com/htdocs/ubuntunew/search.html?cx=003883529982892832976%3Ae2vwumte3fq&cof=FORID%3A9&ie=UTF-8&q=remote&sa=Search)

[/U]OR[U]

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)


[/U]

---

### Post by bodhi.zazen on 2008-11-21
IMO best way is via a VNC connection. If connecting over the internet use ssh to tunnel.

---

### Post by MunkyJunky on 2008-11-21
Try Gitso - [http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

Basically, if your mum needs help in doing something, she loads Gitso and clicks the 'I need help!' button. You then load up Gitso on your computer and click 'give help', and her screen loads up on your PC. 

It's a VNC thing, should have said that :D

---

### Post by nhasian on 2008-11-21
you dont need to install any special software.  

to enable remote desktop go to *system/preferences/Remote Desktop*.  Then under sharing check the boxes for *Allow other users to control your desktop* and *Require the user to enter this password*.

now you can access this remote computer from any pc with a vnc client.  in ubuntu its *Applications/Internet/Remote Desktop Viewer*.

if the remote pc is behind a router, then you will need to enable port forwarding in the router so you can connect to the remote pc.

---

### Post by rmcellig on 2008-11-22
> **nhasian said:**
> you dont need to install any special software.  

to enable remote desktop go to *system/preferences/Remote Desktop*.  Then under sharing check the boxes for *Allow other users to control your desktop* and *Require the user to enter this password*.

now you can access this remote computer from any pc with a vnc client.  in ubuntu its *Applications/Internet/Remote Desktop Viewer*.

if the remote pc is behind a router, then you will need to enable port forwarding in the router so you can connect to the remote pc.
I have a screenshot of my router setup sitting on my Mac desktop. How can I post it here so that you can see if I have my router settings properly set.

---

### Post by tuskenraider on 2008-11-22
a great place to go for router help... and port forwarding is portforward.com   find your router and they will tell you step by step how to forward the port you need.  

just my 2 centavos 

tusken

---

### Post by superprash2003 on 2008-11-22
if this is over the internet and if your mom gets a dynamic external ip, then you may want to setup a hostname to make it easier to access your mom's pc. hope this helps [http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

---

### Post by peakshysteria on 2008-11-22
A simple [Ubuntu geek howto]("http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html").

---

