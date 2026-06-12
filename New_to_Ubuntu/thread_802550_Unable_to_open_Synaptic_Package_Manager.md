---
title: "Unable to open Synaptic Package Manager"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Oliwer Emerich on 2008-05-21
Hi all,

When Im trying to open the Synaptic Package Manager it it looks like it is opening, but after a while the ickon disappears and nothing opens - anyone can tell me what's going on? Thanks a lot!!!


I admit I'm pretty new to Ubuntu as well as to Linux as a whole, so maybe I'm having really just some stupid problem ... But I'm stucked on this point and cannot get over it so I'll really appreciate any help!

---

### Post by dannyboy79 on 2008-05-21
> **Oliwer Emerich said:**
> Hi all,

When Im trying to open the Synaptic Package Manager it it looks like it is opening, but after a while the ickon disappears and nothing opens - anyone can tell me what's going on? Thanks a lot!!!


I admit I'm pretty new to Ubuntu as well as to Linux as a whole, so maybe I'm having really just some stupid problem ... But I'm stucked on this point and cannot get over it so I'll really appreciate any help!
i sometimes have this problem on my old dell which only has 256mb of RAM. open a terminal session and what does 

```
free -m
```  

return? do you have any memory free? you could also try to use aptitude. it's a terminal based installer. so if you wanted to install mythtv, you would first do this

```
sudo aptitude search mythtv
```

then it will show you a  list of packages with mythtv in it, then you could chose which ones you want to install, that command would be

```
sudo aptitude install mythtv-common
```

or whatever.

---

### Post by nick_h on 2008-05-21
Try opening it from a terminal using:
```
gksudo synaptic
```
Post any error messages you see.

---

### Post by Oliwer Emerich on 2008-05-21
well it did not write any error message or anything else ... I had to close the terminal manually after some time ... but the weird point is that after this all the Administrative Applications work again ... Eventhough I do not get it at all ...

Thanks a lot anyway!;-)

---

### Post by Matt640 on 2008-05-24
Re: Problem with Synaptic Package Manager
Re: Synaptic Package Manager Problem
Re: Synaptic Problem!
Hey.
I'm sorta having the same problem here only the cause was something different. I'm using the ordinary Desktop Edition of Ubuntu 8.04 not the 64AMD one. So I read from the Forums that by installing Sun Java 6, I can get my FrostWire up and running again. So I use my SPM to find it and download it. In the middle of Download/Installing, it hanged/jammed and my only option was to reboot. After I did, I realize that I can't open my SPM and it ask me to manually run sudo dpkg --configure -a. When I do, this turns up:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

As you can see, I'm in desperate need of HELP! Can anyone encrypt this for me?

---

