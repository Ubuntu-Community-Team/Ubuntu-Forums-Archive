---
title: "[SOLVED] can't install cinelerra"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by chilimac02 on 2008-10-31
Ok folks... I'm using ubuntu 8.10 clean installed from CD... I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=388875](http://ubuntuforums.org/showthread.php?t=388875)

I get this error when trying to run the command sudo apt-get install cinelerra

justin@justin-laptop1:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (= 1:2.1.0-2svn20082807ubuntuubuntu1) but it is not going to be installed
E: Broken packages

---

### Post by ezramorris on 2008-10-31
Try undoing all that and using the method on cinelerra.org. Note that the one your were using was for Edgy (4 releases ago)
1. ```
sudo gedit /etc/apt/sources.list
```
and remove
```
 #ubuntu edgy
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./
```

2. Save and exit and do
```
sudo apt-get update
```

3. To use the new method:
```
echo deb http://akirad.cinelerra.org akirad-intrepid main | sudo tee /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add -
sudo apt-get update

sudo apt-get install cinelerra
```
[RIGHT]Taken from [here]("http://cinelerra.org/getting_cinelerra.php#intrepid").[/RIGHT]

Hope this helps. It works for me, please let me know how you get on.

---

### Post by b3n0 on 2008-11-29
Thanks, that worked well for me! :D

---

### Post by Perlependium on 2009-01-30
Also worked for me! Thanks.

---

### Post by DanJarus on 2009-02-24
Me too! It was a long fight until these instructions...
Thanks.

---

### Post by tonyrp on 2009-04-01
Man .... what a simple fix. I'm new to Linux and Ubuntu after 24 years on Windows OS. I've been working on trying to get Cinelerra working for three days, found your post and had it working in less than 5 minutes. Thanks

---

### Post by keyboardslave on 2009-07-12
Argh why does everyone have to have it fix so easy for them :P

Im still getting,

The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv but it is not going to be installed or
                      cinelerrahv but it is not installable

Using the above method..
Any hints?

---

### Post by bluehue83 on 2010-01-19
> **keyboardslave said:**
> 
The following packages have unmet dependencies:
  cinelerra: Depends: cinelerracv but it is not going to be installed or
                      cinelerrahv but it is not installable



Me too.:(

---

