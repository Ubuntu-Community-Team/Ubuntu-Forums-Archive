---
title: "Can't get SeaMonkey to use Java plugin"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by graceful1 on 2008-09-30
I have installed the sun-java packages. I can run Java applets in Firefox 3 but not in SeaMonkey. 

I wonder if it is because I am not using the SeaMonkey provided in the synaptic package? I downloaded and installed SeaMonkey 1.1.12 because Synaptic only had 1.1.9.

I tried creating a symbolic link to the libjavaplugin_oji.so file, but that didn't work.

Any help would be appreciated. :D

---

### Post by aysiu on 2008-09-30
What steps did you take to "install" Seamonkey?

---

### Post by graceful1 on 2008-09-30
In the SeaMonkey home page, if you are using an older version of SeaMonkey, there is a link to download the version. I followed this link and downloaded the compressed files. I extracted the files and ran the installer program (after first creating the directory /usr/local/seamonkey as per the directions in the readme). The files were installed to that directory, and I can run SeaMonkey from there. I created a button for SeaMonkey in the Panel so I can launch it easily. 

I hope have answered the question to your satisfaction. I am quite new to this. :D

G.

---

### Post by graceful1 on 2008-09-30
So, is there anyone who uses SeaMonkey and knows how to get this to work?

It seems to be just a Java thing; I was able to successfully install the Flash plug-in.

---

### Post by gandaran on 2008-09-30
I don't use seamonkey, but it should be easy to set up java just like any other browser
find the firefox java plugin **libjavaplugin.so** and make a copy to seamonkey plugins folder, should work
to find the plugin use this command **locate libjavaplugin.so**

---

### Post by aysiu on 2008-09-30
This may help you out:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

---

### Post by graceful1 on 2008-09-30
> **aysiu said:**
> This may help you out:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)
Wow! Thanks, I didn't even know Ubuntuzilla existed. I am going to try this right now. -g.

---

### Post by graceful1 on 2008-09-30
> **aysiu said:**
> This may help you out:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)
I was not keen to use a script, so I followed the instructions for manual installation at the web page you gave me. It installed perfectly, even giving me a launcher for the panel -- HOWEVER, I still cannot run Java plugins!

---

### Post by graceful1 on 2008-09-30
More information that may help:

$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 6
model name	: AMD Athlon(tm) Processor
stepping	: 2

$ lsb_release -rd
Description:	Ubuntu 8.04.1
Release:	8.04

$ apt-cache policy sun-java6-plugin
sun-java6-plugin:
  Installed: 6-06-0ubuntu1
  Candidate: 6-06-0ubuntu1
  Version table:
 *** 6-06-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
        100 /var/lib/dpkg/status

---

### Post by blithen on 2008-09-30
Just install seamonkey from the repos...
```
sudo apt-get install seamonkey
```

---

### Post by gandaran on 2008-10-01
just installed seamonkey from the ubuntuzilla project
got java working in less than ten seconds by just coping the firefox java plugin.

---

