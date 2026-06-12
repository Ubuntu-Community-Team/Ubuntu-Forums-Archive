---
title: "Adding repositories written in DVD to software resources"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by chaware on 2011-11-21
Hi All Ubuntu Geeks
 
I am desperately looking for help.

I have installed ubuntu 10.04 and is working fine. I want to install additional packages but have very slow Internet connection. 

I had earlier downloaded .iso images of ubuntu repositories for lucid from the following link when had access to  good Internet connection
[http://ubunturepo.hnsdc.com/lucid/](http://ubunturepo.hnsdc.com/lucid/)
it is set of 8 DVD images. I have written the images in DVDs. I want to use these DVDs to select the packages and install

I am having following problem

1. When I insert the DVD and  use "software sources" -->"Other Software" --> "Add CD-ROM" of "Synaptic Package Manager"

it says 
**Error scanning the CD**
**E:Failed to mount the cdrom**

While the DVD is already mounted. I can see the contents in the DVDs. for example the  first DVD is mounted as
"**/media/Ubuntu10.04_1_of_8**"
"**ls**" gives list of two directories which contains all the stuff in sub directories
[B]dists 
pool[/B]
 

Thanks in advance

---

### Post by corncob on 2011-11-21
I just tried to duplicate the problem but the only choice I get in Software sources is the Lucid installation CD -- as if its not set up for anything else.

---

### Post by tartalo on 2011-11-21
With the DVD mounted, does this work?
```
sudo apt-cdrom add
```

---

