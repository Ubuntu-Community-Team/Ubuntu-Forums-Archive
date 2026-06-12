---
title: "gnome-volume-control-applet source code"
date: 2011-01-29
forum: Packaging and Compiling Programs
---

### Post by moe46 on 2011-01-29
Hi
I'm looking to make a few modifications to this applet.
Does anyone have a link to the source code?

I'm looking to add the ability to increase the volume to over 100% to the popup slider. Also I want to add a faster way to change the per application volume. Ideally I would add it next to the minimize button in the title bar but that might be outside of my skill set.

Thank you for any help

---

### Post by SevenMachines on 2011-01-29
The applet source is part of gnome-media so unless you need a different version entirely,
```
$ apt-get source gnome-media
```

---

### Post by moe46 on 2011-01-29
Thank you for the reply.
Tried as you said and I get 

E: You must put some 'source' URIs in your sources.list

So I went in to software sources and check off Source Code. 
Now I get this

E: Unable to find a source package for gnome-media

I assume its not pointing to the right location of the files for some reason.

---

### Post by SevenMachines on 2011-01-30
Hmmm, did you update(reload repository in synaptic) afterwards? 
Here's a few different ways to get source from ubuntu repositories below anyway and see if that helps at all

_**3 Ways to Get Ubuntu Source Packages**_

note: replace terms between <brackets> with appropriate terms

*** Using apt-get**
    
- Add the src repository, this can be done using synaptic in preferences->repositories, ticking the source code box in the 'ubuntu software' tab and reloading afterwards.

    - Or, from the command line, edit /etc/apt/sources.list, copy the main repository line and add the deb-src line, eg
    ```
deb http://archive.ubuntu.com/ubuntu maverick main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted multiverse universe
```    then
    ```
$ apt-get update
$ apt-get source <package>
```[B]
* Using Dget[/B]
    
- Go to web page https://launchpad.net/ubuntu/+source/<package>
    
- Navigate to maverick version
    
- Copy link to .dsc file
    
- Then,
    ```
$ dget <copied link to .dsc file>
$ dpkg-source -x <package.dsc>
```[B]
* Using Bazaar[/B]

Note: You need to have a launchpad account with an ssh key set up for this
    ```
$ bzr branch lp:ubuntu/<package>
```    or, for a specific distribution
    ```
$ bzr branch lp:ubuntu/maverick/<package>
```

---

### Post by SevenMachines on 2011-01-30
For non-ubuntu source code look here
[http://www.linuxfromscratch.org/blfs/view/cvs/gnome/gnome-media.html](http://www.linuxfromscratch.org/blfs/view/cvs/gnome/gnome-media.html)
But if you get the source from ubuntu you also get the packaging included too so you can actually replace the package with your new one, which is what you want i imagine

---

