---
title: "I just downloaded the newest screenlets. How do I install it?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Rukaru on 2008-08-02
It really doesn't make it clear how you install this thing.  I know you can run something like "install screenlets" in the terminal, but I'm pretty sure this gives you an old version, since synaptic says 0.0.12 is the latest, and the one I'm trying to get is 0.1.2...so...big difference.  So far, the tar.bz2 file is downloaded and extracted.  What next?


EDIT: Already resolved. I don't need any more help with this.

---

### Post by Rukaru on 2008-08-02
Here's a link to its page on gnome look.  If you have ubuntu, try it out.  

[http://www.gnome-look.org/content/show.php/Screenlets+0.1.2?content=82586](http://www.gnome-look.org/content/show.php/Screenlets+0.1.2?content=82586)

---

### Post by ion072002 on 2008-08-02
did you try the usual ./configure, make ,make install?
if it won't work, try this: [http://compiz.org/Desktop_Screenlets](http://compiz.org/Desktop_Screenlets)



le: in rukaru's link there is a .deb package that will spare you the trouble i think

---

### Post by northern lights on 2008-08-02
You need not install from source.

There's a 0.1.2 .deb file - [http://www.getdeb.net/release/2748]("http://www.getdeb.net/release/2748")

It should install by double-clicking. If not, install 'GDebi' via Synaptic or run ```
sudo apt-get install gdebi
```

---

### Post by Rukaru on 2008-08-02
> **ion072002 said:**
> did you try the usual ./configure, make ,make install?
if it won't work, try this: [http://compiz.org/Desktop_Screenlets](http://compiz.org/Desktop_Screenlets)



le: in rukaru's link there is a .deb package that will spare you the trouble i think

No I didn't try that.  How do you do it?  I'm still fairly knew at this.  

I looked at the deb thing...it it safe?  I am always nervous about installing things. Anyway, I wouldn't mind doing it the usual way that you mentioned if you will tell me how to do it.

---

### Post by northern lights on 2008-08-02
> **Rukaru said:**
> I looked at the deb thing...it it safe?

Safe as in no malicious downloads?
A. Both websites (getdeb & gnomelook) can be trusted. 
B. This is *nix

Safe as in you won't break anything yourself?
Certainly much safer than compiling from source.




> **Rukaru said:**
> [Compiling from source] No I didn't try that.  How do you do it?  I'm still fairly knew at this.

Once, run ```
sudo apt-get install build-essential
```then to compile```
cd /path/to/folder
./configure
make
sudo make install
```
The second line is only necessary if it came with a configuration script.

---

### Post by Rukaru on 2008-08-02
> **northern lights said:**
> Safe as in no malicious downloads?
A. Both websites (getdeb & gnomelook) can be trusted. 
B. This is *nix

Safe as in you won't break anything yourself?
Certainly much safer than compiling from source.






Once, run ```
sudo apt-get install build-essential
```then to compile```
cd /path/to/folder
./configure
make
sudo make install
```
The second line is only necessary if it came with a configuration script.

Oh okay well I got and installed the deb one.  Now what?

---

### Post by sharks on 2008-08-02
open the deb file and install it.

---

### Post by northern lights on 2008-08-02
> **Rukaru said:**
> Oh okay well I got and installed the deb one.  Now what?
You're done. I don't understand what you're asking.

---

### Post by sharks on 2008-08-02
i think you should install it via synaptic and the updates will come for screenlets.

---

### Post by SunnyRabbiera on 2008-08-02
Installing and using screenlets should be very easy.
On this site [http://www.getdeb.net/search.php?keywords=screenlets](http://www.getdeb.net/search.php?keywords=screenlets) there is a debian installer, once its downloaded just double click the installation file and it will install similar to a windows .exe

---

### Post by Rukaru on 2008-08-02
> **SunnyRabbiera said:**
> Installing and using screenlets should be very easy.
On this site [http://www.getdeb.net/search.php?keywords=screenlets](http://www.getdeb.net/search.php?keywords=screenlets) there is a debian installer, once its downloaded just double click the installation file and it will install similar to a windows .exe

Okay got it.  Thanks everyone for your help!

---

### Post by northern lights on 2008-08-02
> **sunnyrabbiera said:**
> installing and using screenlets should be very easy.
On this site [http://www.getdeb.net/search.php?keywords=screenlets](http://www.getdeb.net/search.php?keywords=screenlets) there is a debian installer, once its downloaded just double click the installation file and it will install similar to a windows .exe

> **northern lights said:**
> there's a 0.1.2 .deb file - [http://www.getdeb.net/release/2748]("http://www.getdeb.net/release/2748"):smile:

---

