---
title: "Failed to download repository information"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by aroch1234 on 2013-01-30
I can't update ubuntu 12.10. I get these when i try to update.

W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by arpanaut on 2013-01-30
[http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/)

No packages for quanal in that repository, you will need to remove the references to that ppa in software sources.
after that things should work properly.

---

### Post by ankur1993 on 2013-01-30
please,dear change server location beause it may possible your internet turn on under proxy . i refer the server viet nam.:mad:

---

### Post by GCbon on 2013-01-30
> **arpanaut said:**
> [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/)

No packages for quanal in that repository, you will need to remove the references to that ppa in software sources.
after that things should work properly.
But how do you find the reference to remove it? I'm not finding mine -  QuickFox - by searching.  If I go further into the line and look for that, I get thousands of names, none of which I understand.  If I could just tell it to forget about the whole thing I would be so happy.

---

### Post by sammiev on 2013-01-30
This will work but you really need to know what you are doing.

in Terminal

```
sudo -i
```

type in your password

```
gedit /etc/apt/sources.list
```

add a # sign and a space in front on the line(s) you want to temp kill. then save the file. If all works great then go back into the file and delete that line or lines.

---

### Post by Bucky Ball on 2013-01-30
Welcome to the forums.

... or go into Software Sources> Other Software and untick them. Refresh.

I think you will need:

```
gksudo gedit /etc/apt/sources.list
```... to delete the lines with the method given in the last post.

---

