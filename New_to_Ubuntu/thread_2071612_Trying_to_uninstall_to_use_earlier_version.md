---
title: "Trying to uninstall to use earlier version"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by cdlam on 2012-10-15
Hey all, 

so as part of a larger set of programs I installed GMAP ([http://research-pub.gene.com/gmap/](http://research-pub.gene.com/gmap/)) using 

>  sudo apt-get install gmap However part of this program is giving me memory failure related errors. I am told that an earlier version of GMAP uses less RAM and won't give me these issues. However, I'm unsure of how to completely remove the current version. I thought I had removed it, using "sudo remove gmap" but when I went through the installation steps of the one I donwloaded and checked the version number in the terminal it displayed the most current one, rather than the older one. Does anyone know how I can fully uninstall it? Thanks

---

### Post by daslinkard on 2012-10-15
> **cdlam said:**
> Hey all, 

so as part of a larger set of programs I installed GMAP ([http://research-pub.gene.com/gmap/](http://research-pub.gene.com/gmap/)) using 

However part of this program is giving me memory failure related errors. I am told that an earlier version of GMAP uses less RAM and won't give me these issues. However, I'm unsure of how to completely remove the current version. I thought I had removed it, using "sudo remove gmap" but when I went through the installation steps of the one I donwloaded and checked the version number in the terminal it displayed the most current one, rather than the older one. Does anyone know how I can fully uninstall it? Thanks

You should be able to purge (remove) GMAP by doing
```

sudo apt-get purge gmap
```This will remove the file and then you can install the version of gmap you are wanting to.

---

### Post by Cheesemill on 2012-10-16
How did you install gmap in the first place?

---

### Post by cdlam on 2012-10-16
I used "sudo apt-get install gmap" to install it.

Yeah, I tried the purge option before. Here's what I get when I try:

> chris@ubuntu:~$ sudo apt-get purge gmap
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gmap is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.

It says it's not installed, which is....odd considering if I immediately try:

> chris@ubuntu:~$ gmap
GMAP version **2012-07-20** called with args: gmap
Need to specify the -d, -g, -1, -2, or --cmdline flag
Usage: gmap [OPTIONS...] <FASTA files...>, or
       cat <FASTA files...> | gmap [OPTIONS...]

Input options (must include -d or -g)
  -D, --dir=directory            Genome directory
  -d, --db=STRING                Genome database.  If argument is '?' (with
                                   the quotes), this command lists available databases.
....
....


And so on with more help file commands and such. Note the very recent version that is still installed. Blah. So any thoughts lol?

---

### Post by jerrrys on 2012-10-16
In terminal enter:

gksudo nautilus

Go to your "filesystem" then do a nautilus search on gmap and remove the leftovers

---

### Post by cdlam on 2012-10-16
Ah, that did it. There were config files left over in the user/local/bin directory. Thanks very much!

---

### Post by jerrrys on 2012-10-16
Welcome  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

