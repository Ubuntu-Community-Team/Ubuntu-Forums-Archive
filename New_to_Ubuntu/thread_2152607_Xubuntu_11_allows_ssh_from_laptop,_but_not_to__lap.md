---
title: "Xubuntu 11 allows ssh from laptop, but not to  laptop"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by Banyailaci on 2013-06-08
I have installed Xubuntu 11 on an older Thinkpad. Everything works well, but strangely enough I can connect by ssh to other Computers, but the ssh from other computers (whether in the same home network or outside) is refused. I suppose, there is an ssh setting that is wrong. May somebody help me?!

---

### Post by Banyailaci on 2013-06-08
I cannot ssh to the laptop with Xubuntu 11, although I can ssh from the laptop. Presumabily ssh settings!? Please help!

---

### Post by steeldriver on 2013-06-08
Hello and welcome to the forum

First off, did you actually install the ssh server (openssh-server) on the laptop? The client (needed to connect **to **other computers via ssh) is a separate component / package from the server (needed to connect in **from **other computers) - the server is not installed by default in most desktop / laptop versions

```

dpkg -l | grep ssh

```

If the server is installed then the next things to check would be that it is running and bound to the expected port

```

service ssh status

sudo netstat -nlp | grep ssh

```

After that, you'd need to start looking at firewalls

---

### Post by Iowan on 2013-06-08
Merged duplicate threads. From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

### Post by deadflowr on 2013-06-08
Did you install the ssh server packages?

The system has a ssh-client package built in, but not a server package.

---

### Post by Banyailaci on 2013-06-09
Thank You!
I did not know about not having istalled the server. I got it now from the software package and it is perfect.):P

---

### Post by Banyailaci on 2013-06-09
Thank You very much!
I did not know about not having istalled the server. I got it now from the software package and it is perfect.):P

---

### Post by Banyailaci on 2013-06-09
Thank You very much for the rapid help! Now it is OK.

---

### Post by Banyailaci on 2013-06-09
[QUOTE=steeldriver;12682888]Hello and welcome to the forum

First off, did you actually install the ssh server (openssh-server) on the laptop? The client (needed to connect **to **other computers via ssh) is a separate component / package from the server (needed to connect in **from **other computers) - the server is not installed by default in most desktop / laptop versions

[CODE]

Thank you very much! The problem is now solved.:p

---

