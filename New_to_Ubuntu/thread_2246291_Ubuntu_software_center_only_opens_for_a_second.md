---
title: "Ubuntu software center only opens for a second"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by Ben_Cook on 2014-09-29
I am running the latest Xubuntu LTS (can't remember the version number).  I could always go into software center, but today I tried and it just closed.  I open it up, it shows it is loading, then it closes.  No warning, no error message, it just stops.  Any ideas?

---

### Post by Impavidus on 2014-09-29
Let's try the lower level tools and see if we can get some meaningful error messages. Try these terminal commands and post the output:```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ben_Cook on 2014-09-29
the output of the first one is - E: Type '&#8216;deb' is not known on line 1 in source list /etc/apt/sources.list.d/acestream.list
E: The list of sources could not be read.
This is the upgrade one - 
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 acestream : Depends: python2.7-apsw but it is not installable
             Depends: python2.7-m2crypto
             Depends: python-appindicator (>= 0.4.1) but it is not installed
             Depends: libavcodec53 (>= 4:0.7-1) but it is not installable or
                      libavcodec-extra-53 (>= 4:0.7-1) but it is not installable
             Depends: libavformat53 (>= 4:0.7-1) but it is not installable or
                      libavformat-extra-53 (>= 4:0.7-1) but it is not installable
             Depends: libavutil51 (>= 4:0.7-1) but it is not installable or
                      libavutil-extra-51 (>= 4:0.7-1) but it is not installable
             Depends: libdvbpsi7 (>= 0.2.0) but it is not installable
             Depends: libebml3 but it is not installable
             Depends: libqt4-webkit but it is not installed
             Depends: liblua5.1-0 but it is not installed
             Depends: libmatroska5 but it is not installable or
                      libmatroska4 but it is not installable
             Depends: libudev0 (>= 147) but it is not installable
             Depends: libx264-116 but it is not installable or
                      libx264-120 but it is not installable or
                      libx264-123 but it is not installable
E: Unmet dependencies. Try using -f.

---

### Post by Ben_Cook on 2014-09-29
I tried getting acestream installed on my system, but I didn't really know what I was doing and gave up...maybe that is my problem

---

### Post by oldos2er on 2014-09-29
If you no longer want acestream, remove the file that is causing the problem: ```
sudo rm /etc/apt/sources.list.d/acestream.list*

sudo apt-get update
```

---

### Post by Ben_Cook on 2014-10-04
Sorry, meant to mark this as solved, which it is thanks to you, oldos2er.

---

### Post by oldos2er on 2014-10-05
Glad it's working!

---

