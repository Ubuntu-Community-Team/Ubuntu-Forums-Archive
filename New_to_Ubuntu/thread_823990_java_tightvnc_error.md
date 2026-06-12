---
title: "java tightvnc error"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-09
Hi all,

I am in the middle of setting up a home server with xubuntu on it. So far I have been able to access my server's shared folder thru nautilus (Connect t Server).

Now I am trying to remote control the server from another ubuntu laptop. I thought I would try using the java based vnc thing thru a web browser as I want to be able to access the server (eventually) from outside my network, i.e. over the internet from a machine where I can't install software, so providing the web browser is java enabled no problem. 

i get as far as the vnc page where you enter the password to gain control, but then it just throws an error: ```
error: old input was not completely processed
```

Any ideas what this is?

Also, I am thinking there may be an easier/better way to do this whilst at home where i can install whatever I want on my ubuntu machine... some sort of vnc viewer? 

Thanks in advance.

---

### Post by jcr1 on 2008-06-09
ok just been trying xtightvncviewer but i'll be damned if i can get it to work.

All i want to do is log in and "view" and "control" the server i.e. remote desktop.

When I run xtightvncviewer i get prompted for the server which i know is right but then get:

```
xtightvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```

---

### Post by superprash2003 on 2008-06-09
hope this helps [http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)

---

### Post by jcr1 on 2008-06-10
Hey thanks for that! 

This uses Apache instead of vncserver right? Whats the difference? or is it just that there are many different ways to achieve the same thing?

Is there a better way to do this when I am actually on my network, i.e. at home or is the java vncviewer way just as good as any?

Many thanks indeed.

---

### Post by superprash2003 on 2008-06-10
i found this method comfortable mate..you can use the same setup via LAN as well just type in [http://localip/remote](http://localip/remote) where localip is your local ip address which you should find from your ifconfig output ..

---

