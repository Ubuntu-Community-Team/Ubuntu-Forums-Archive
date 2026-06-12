---
title: "beginner question about updating gimp"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-07-03
Hello, thanks for taking the time to read my question. 
I checked gimp's official website and I saw that they are out with version 2.5.1 and it said to get the latest version, do (sudo) apt-get install gimp

I ran this in the terminal and it said that gimp was at the latest version, but when I checked gimp's directory, it says gimp --> 2.0
This is probably a really stupid question, but how do I upgrade to version 2.5.1?

---

### Post by ET! on 2008-07-03
reload the synaptic list and try again

---

### Post by jjblackfox on 2008-07-03
> **ET! said:**
> reload the synaptic list and try again
How do I do that?

---

### Post by ET! on 2008-07-03
or type apt-get update from terminal

---

### Post by ET! on 2008-07-03
in the first post i was mentioning the synaptic package manager in system->administration where you can easily install any package you want

---

### Post by hyper_ch on 2008-07-03
hardy features gimp 2.4.5

---

### Post by mcduck on 2008-07-03
First, 2.5 is a development version, not meant for normal users. The next stable release will be 2.6.

THen the actuall issue: Programs in Ubuntu's repositories are not updated all the time. During the development of a Ubuntu releaser the software versions are frozen,a nd updates are only usually provided for security reasons and to fix serious bugs.

Sometimes, when a package is very simple and has little or no dependencies, so it can be easily tested to not cause any problems with the rest of the system, a new version of some program may become available as an update in the BAckports-repository. 

But most of the time if you want the latest version of some program youll have to either wait until next Ubuntu release, or install the new version by yourself.

Good place to find more upt-to-date software packages is [http://www.getdeb.net/]("http://www.getdeb.net/").

---

### Post by philinux on 2008-07-03
The version currently installed by ubuntu is GIMP 2.4.5.


2.4.6 is a bug fix so i would imagine that would be available soon as an update. 

```
GIMP 2.5.1 is another snapshot from the 2.5 development series. It gives developers and interested users a view into the current development towards GIMP 2..6
```

I'd say sit tight and wait. The current version is working fine for me.

I'd enable your hardy-backports though. System>Admin>Software Sources. Updates.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

