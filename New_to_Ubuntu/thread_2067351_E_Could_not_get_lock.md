---
title: "E: Could not get lock"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by chacank on 2012-10-06
hi all ..
help me this time again
I tried to install lazarus 1.0.0 with the command
```
$ Cd Downloads /
```
(i've downloaded the file before)
```
$ ls
$ Sudo dpkg-i lazarus_1.0-0_i386.deb
```
but failed ....

and now every time I try to type some commands in terminal
always the message fails .. :-k

this is the results .. 8-[
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chacank@chacank-K84L:~$ 

``` 

there may be from friends here who can help me in fixing this error .... please ,, help me .. [-o<

thanks

---

### Post by dniMretsaM on 2012-10-06
Make sure you don't have any other programs running that would be using dpkg (USC, Update Manager, Synaptic, etc.).

---

### Post by chacank on 2012-10-06
I also tried running the following command :
$ sudo apt-get upgrade


and this is the result:
```
chacank@chacank-K84L:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 lazarus:i386 : Depends: libgtk2.0-dev:i386 (>= 2.6.0) but it is not installed
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-compiler:i386 (>= 2.6.0)
                Depends: fpc-src:i386 (>= 2.6.0) but it is not installable or
                         fpc-source:i386 (>= 2.6.0) but it is not installable
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-ide:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-base:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-db:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-fcl:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-fv:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-gfx:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-gnome1:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-gtk:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-gtk2:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-misc:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-net:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-units-rtl:i386 (>= 2.6.0)
                Depends: fpc:i386 (>= 2.6.0) but it is not installable or
                         fp-utils:i386 (>= 2.6.0)
E: Unmet dependencies. Try using -f.
chacank@chacank-K84L:~$ 

```

please give me the solution of this problem .... [-o<

---

### Post by newb85 on 2012-10-06
My recommendation is that you follow the suggestion contained in the output:

> You might want to run 'apt-get -f install' to correct these.

```
sudo apt-get -f install
```

will probably take care of unmet dependencies.

---

