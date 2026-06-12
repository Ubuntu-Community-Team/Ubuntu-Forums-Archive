---
title: "wine for ubuntu 12.04"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-10-19
hi all
how to install wine for ubuntu 12.04... i hope it is recomended for using any windows based software on ubuntu..(i hope it works for any windows based software e.g MSVisio or anything)...

---

### Post by Asmodai on 2012-10-19
```
sudo apt-get install wine
```

And no, you can't run all Windows software with Wine, but there are still many that work.

---

### Post by aabed91 on 2012-10-19
you can install it using terminal.
Type

```

Sudo apt-get install wine

```

or you can download it from software center.

---

### Post by lukeiamyourfather on 2012-10-19
What they said. If you want to see if something works you can check the application database.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Baldrick_NZ on 2012-10-20
> **lukeiamyourfather said:**
> What they said. If you want to see if something works you can check the application database.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

I would also use the Ubuntu PPA from this site too to make sure you have the most recent stable version, currently 1.4.1.

There is the unstable 1.5.15 as well, but this version truly lives upto 'unstable' on my PC. 

The best way of downloading/installing and adding PPA's is to use an app called 'synaptic'. ```
sudo apt-get install synaptic
```
If you use this method, after adding the PPA, type 'wine1.4' in the search box and apply. After that you should have the latest stable version installed.

Sing out if you need any help with synaptic. It can seem to be a difficult beast to start with, but becomes pretty obvious after a while.

Hope that helps.

---

### Post by Gnawnsense on 2012-10-20
I'm not sure how well it holds-up, but for my Wine needs, I've been using PlayOnLinux. Being a complete newbie to Linux, it definitely helps streamline the configuration.

However, I'm not entirely sure what the cons are for the ease-of-use that POL offers opposed to just running Wine itself.

---

### Post by Mark Phelps on 2012-10-20
> **syednasirraza said:**
> hi all
how to install wine for ubuntu 12.04... i hope it is recomended for using any windows based software on ubuntu..(i hope it works for any windows based software e.g MSVisio or anything)...

In my own experience, Wine works poorly with some MS Office components.  See the link below for the Visio ratings:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=119]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=119")

With the exception of 2007 Pro, the other ratings are so poor as to make installing it a waste of time.

---

