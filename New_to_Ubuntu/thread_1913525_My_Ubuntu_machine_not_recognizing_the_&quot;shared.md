---
title: "My Ubuntu machine not recognizing the &quot;shared&quot;  Windows 7 connection"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2012-01-22
Hi,

I have my Windows 7 laptop connected to our home WiFi. I have a Desktop running Maverick Markeet but cannot get the WiFi card to work.

I am sharing my internet connection on my Windows machine, and I have an ethernet cable running from my computer into a router. I then have a second cable from the router to my Ubuntu machine.

I can't connect to the internet on the Ubuntu machine.

Do I need to do anything in Ubuntu to make it recognize the internet connection?

Thanks in advance,

Chris

---

### Post by pierreyy on 2012-01-22
hey

if ur connecting through ur windows 7 you need the samba package to get your ubuntu to read the windows connection 
```
 sudo apt-get install samba smbfs 
```

and follow this link for mor info.

>  [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/) 

good luck!!

---

### Post by giowck on 2012-01-22
> **pierreyy said:**
> hey

if ur connecting through ur windows 7 you need the samba package to get your ubuntu to read the windows connection 
```
 sudo apt-get install samba smbfs 
```

and follow this link for mor info.



good luck!!


I think the topic is not about file sharing with samba...

it is about internet connection sharing over ethernet. Am I right?

---

### Post by pcvchriskmg on 2012-02-04
> **giowck said:**
> I think the topic is not about file sharing with samba...

it is about internet connection sharing over ethernet. Am I right?


Yes, that is absolutely correct. This is about the Ubuntu machine recognizing/using the windows connection.

chris

---

