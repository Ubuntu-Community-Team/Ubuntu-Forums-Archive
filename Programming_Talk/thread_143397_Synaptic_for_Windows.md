---
title: "Synaptic for Windows?"
date: 2006-03-12
forum: Programming Talk
---

### Post by Xecuter on 2006-03-12
Yes, it sounds weird, but is there any programers out there that is capable to make this program. Let me tell you how it should work:

Me, and many other Ubuntu users out there, who doesn't have Internet are suffering from getting stuff, and getting the right stuff and things that are needed. So, the program looks like Synaptic, and works allmost the same way. I can run it from my USB-disc on a Windows box (no installation, since I will be getting stuff from school where the security is a little high).
I will have a copy of my source.list on my USB-disc so that this "Synaptic" know where to get it's packages. But then the smart part of this plan comes. Synaptic will not install the packages, just save them on the disc. 
Later, when I get home I will edit the origional Synaptic to get packages in local repositories, which I know is possible. Voila!

Now, do you think this is a little far fetched or is it possible?

---

### Post by knalle on 2006-03-12
synaptic on windows aint gonna happen im afraid, but you can use a windows remote site synchronization tool to keep a ofline copy of the repositories and burn on dvds

---

### Post by toojays on 2006-03-12
Xecuter, what you are wanting to do can be done using the apt-zip package. It doesn't have a pretty GUI, but it will create a list of URLs which you need to download on your Internet-connected PC. You then copy these files to /var/cache/apt/archives, and Synaptic won't need to download them from the net.

---

### Post by Xecuter on 2006-03-13
[QUOTE=toojays]Xecuter, what you are wanting to do can be done using the apt-zip package. It doesn't have a pretty GUI, but it will create a list of URLs which you need to download on your Internet-connected PC. You then copy these files to /var/cache/apt/archives, and Synaptic won't need to download them from the net.[/QUOTE]

Tell me more! How can this be done? It seems like just the thing I am after. :)

---

### Post by doclivingston on 2006-03-13
As well as apt-zip, you can also get the list of URIs with normal apt-get

```
sudo apt-get --print-uris -y install package-name
``` will print the list of uris, and their MD5 sums (in case you want to check). Just download those, stick them in /var/cache/apt/archives, and then install normall with apt-get/synaptic.


In Synaptic (on Dapper) you can use "File->Create download script" to make a bash script that will download them all. The script itself won't help on windows (unless you have mingw/cygwin and wget), but it will contain the list of URIs too.

---

### Post by Xecuter on 2006-03-14
This only returned a lot of errors and stuff. 

How does this apt-zip package stuff work?

This is what exactly what I meant with my program. TO MAKE STUFF EASIER!
Just click there, download that, copy here and install...

---

### Post by doclivingston on 2006-03-14
[QUOTE=Xecuter]This is what exactly what I meant with my program. TO MAKE STUFF EASIER!
Just click there, download that, copy here and install...[/QUOTE]

The problem is that the program the figure out what you have to download needs to know what you have installed.

The two solutions are:
a) have a program on your Ubuntu macheine generate the list of files to download, then have the 'net-connected machine download them.
b) have your Ubuntu machine write a list of what it has installed to a file, and a program on the 'net connected machine figure out what to download.


The disadvantage of (a) is that the machine without a 'net connection needs up-to-date package lists (which you get off the 'met). The disadvantage of (b) is that the 'net connected machine needs a list of what version of which packages you have installed (which can be large).

---

### Post by Xecuter on 2006-03-14
Thank you! Finally :D

Yes, I can see the probleme here. How about both solutions? The Ubuntu machine generates a list of files to get, and a list of files installed? Then when you get to the net-connected machine, it downloads the files I'm interested in plus updates, if there are any.
I'm just thinking out loud here.

The more I think of it, what you said about Synaptic in Dapper, would be the greatest solution.

---

