---
title: "Conky in Pangolin ..."
date: 2013-12-28
forum: New to Ubuntu
---

### Post by czgirb on 2013-12-28
remembered, conky is install and use it before ... but it was un-check and delete from my startup application
and now, it won't show up again ... is the applcation still there? What's wrong with my conky?
Would somebody willing to guide me how to solve this problem?
Please ...........................

---

### Post by deadflowr on 2013-12-28
What happens when you run conky from a terminal?
Simply, conky

---

### Post by czgirb on 2013-12-28
> **deadflowr said:**
> What happens when you run conky from a terminal?
Simply, conky

as requested
> 
czgirb@czgirb:~$ conky
The program 'conky' can be found in the following packages:
 * conky-cli
 * conky-std
Try: sudo apt-get install <selected package>
czgirb@czgirb:~$ 


---

### Post by deadflowr on 2013-12-28
It seems conky isn't installed after all.
But just to be on the safe side try
both
```
apt-cache policy conky
```
and
```
apt-cache policy conky-all
```
if neither show as being installed, then install conky-all.

When you do finally figure it out, go conkyrc huntin'.

---

### Post by czgirb on 2013-12-28
> **deadflowr said:**
> It seems conky isn't installed after all.
But just to be on the safe side try
both
```
apt-cache policy conky
```
and
```
apt-cache policy conky-all
```
if neither show as being installed, then install conky-all.

When you do finally figure it out, go conkyrc huntin'.

here it is:
> 
czgirb@czgirb:~$ apt-cache policy conky
conky:
  Installed: (none)
  Candidate: 1.8.1-6
  Version table:
     1.9.0-2~ubuntu12.04.1 0
        100 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-backports/universe i386 Packages
     1.8.1-6 0
        500 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
czgirb@czgirb:~$ apt-cache policy conky-all
conky-all:
  Installed: (none)
  Candidate: 1.8.1-6
  Version table:
     1.8.1-6 0
        500 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
czgirb@czgirb:~$ 


---

