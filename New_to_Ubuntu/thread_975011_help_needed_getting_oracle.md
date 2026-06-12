---
title: "help needed getting oracle"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by khizar on 2008-11-08
hi 
i have am using ubuntu hardy and i have a problem.
my uni has a proxy filter that stops downloads of more then a specific size.i am trying to install oracle express edition using 

```
sudo apt-get install oracle-xe oracle-xe-client
```

 the client is downloaded but the other package gives

```
Err http://oss.oracle.com unstable/non-free oracle-xe 10.2.0.1-1.1
  403 Forbidden
Failed to fetch http://oss.oracle.com/debian/dists/unstable/non-free/binary-i386/oracle-xe_10.2.0.1-1.1_i386.deb  403 Forbidden
```

i tried to read the link from the browser but the filter message poped up saying the size is too big
my question is if this 403 forbidden is due to the filter? if yes can i bypass it sumhow
any help is greatly aprecciated

cheers 
khizar

---

### Post by m_atif on 2008-11-08
so its a uni policy..Not sure but its worth to give it a shot

try downloading .deb package(s) of oracle-xe through a bit-torrent client. 
This would only be possible if torrents are not blocked on your network.
You may also try apt-torrent, but for that you need to install that, download .deb from the link below and give it a shot!
[http://sianka.free.fr/spip.php?rubrique3](http://sianka.free.fr/spip.php?rubrique3)

---

### Post by khizar on 2008-11-08
thanx for the reply 
and yes torrents are also blocked , but i still thought to give it a shot .i have downloaded the apt-torrent and installed it but not really sure how to use it , so can u plz elaborate a bit...
 

secondly , their is a limit i guess of 70 mb for a single download on our network , is their sum way i can download it in pieces n then join them locally.
would a mutithread downloader work , n if yes can u recommend 1.

and third , isnt their sum way of hiding the size of ur download from ur server. we have a website filter here (yeah i know its a lot of restrictions but have to live with it) but we get around it very easily using web proxy sites etc. cant we just mask our download size from the server using sum software or sumthin.

---

