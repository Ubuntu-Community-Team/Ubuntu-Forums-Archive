---
title: "server stuff"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by playinpearls on 2008-05-02
I just starting using ubuntu at home and now at work i've been assigned to make a server, and figured ubuntu would be great at that too...

I am using desktop for the server, because i am not comfortable yet with all the command line interfaces...


I have to create a server that will be on a private network accessible only by my repair guys. No security is needed. 

however, the computer will not be able to access the internet, so with that obstacle, how will i install the packets that i need (samba) to start this file server. does the desktop edition have a samba option? is there another way around this?
any suggestions would be great!

---

### Post by Cypher on 2008-05-02
Can you plug the server to the Internet while you configure it and then put it onto the private network?

---

### Post by pseudo-random on 2008-05-02
Make a list of the software you want (SAMBA, FTP, SSH etc) Then use another internet-connected computer to download the packages with the -d switch to download only. Pop the .deb's on a pen-drive and go install them on the other box.
```
sudo apt-get install -d ssh 
```

---

### Post by Monicker on 2008-05-02
You can also see about getting the DVD version instead of the CD for the install, which should have the samba package on it already.

---

### Post by playinpearls on 2008-05-02
the internet is available only through our corporate network, i guess i could take it home to do it, but i'd rather not... :D

i might go ahead and get the dvd sent...

is there a way to download stuff from windows?

---

### Post by Monicker on 2008-05-02
> **playinpearls said:**
> the internet is available only through our corporate network, i guess i could take it home to do it, but i'd rather not... :D

i might go ahead and get the dvd sent...

is there a way to download stuff from windows?

If you have broadband internat at home, and a dvd burner, you could use a torrent to get the CD iso fairly quickly.
 
[http://torrent.ubuntu.com/releases/hardy/release/dvd/]("http://torrent.ubuntu.com/releases/hardy/release/dvd/")

---

