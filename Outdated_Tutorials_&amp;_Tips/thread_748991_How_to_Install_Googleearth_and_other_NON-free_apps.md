---
title: "How to: Install Googleearth and other NON-free apps on Ubuntu 7.10 and 8.04"
date: 2008-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by buried on 2008-04-08
Now if you've tried this:
```
sudo apt-get install googleearth
```
and got this error:
```
The package "googleearth" not found
```
then this is the tutorial for that.
First we have to add Medibuntu sources to our repository, 

Ubuntu 7.10 "Gutsy Gibbon":

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```


Ubuntu 8.04 "Hardy Heron":

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Then add the GPG key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
now try:
```
sudo apt-get install googleearth
```
should work like a charm, enjoy other apps installable too
like 
```
    *

      acroread (Acrobat Reader -- not really needed because you can use free software, such as Evince, to read pdfs)
    *

      googleearth
    *

      restricted video codecs (ppc-codecs, w32codecs, w64codecs)
    *

      realplay (Real Player)
    *

      Skype

```

---

### Post by wieman01 on 2008-04-08
Nice one. I will try it out as soon as I am on Hardy. :-)

---

### Post by Nano on 2008-04-08
Or you can simply download the bin from google and install it, which works very well too.

---

### Post by wieman01 on 2008-04-08
> **Nano said:**
> Or you can simply download the bin from google and install it, which works very well too.
But then you don't receive automatic updates. That's why I would prefer this method.

---

### Post by buried on 2008-04-08
If you wanna install other non-free go to software sources and enable medibuntu non-free.

---

### Post by z0mbie on 2008-04-08
So the mediubuntu repo is pretty well maintained & up to date?

---

### Post by buried on 2008-04-08
Yep it's up to date all right.

---

### Post by Boyohazard on 2008-04-08
Thank you I was looking for a Howto on adding the medibuntu repo to Hardy

---

### Post by Timbothecat on 2008-05-04
Anyone else have a problem with google earth logging them out of their user account?

Whenever I press the link to make the app start it just sends me straight to the login screen.

---

### Post by The5thW on 2008-05-05
jack@jack-desktop:~$ sudo apt-get install googleearth
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jack@jack-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Long bad fist day for this new user.

---

### Post by Timbothecat on 2008-05-05
> **The5thW said:**
> jack@jack-desktop:~$ sudo apt-get install googleearth
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jack@jack-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Long bad fist day for this new user.

I had the same problem my friend. 
```
**sudo** dpkg --configure -a
``` should fix the problem. However, I'm wondering if that is a part of the issue that I'm having now with it logging me out etc.

---

