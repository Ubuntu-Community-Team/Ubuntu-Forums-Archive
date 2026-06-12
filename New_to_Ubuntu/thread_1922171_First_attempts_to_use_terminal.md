---
title: "First attempts to use terminal"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by Ketman on 2012-02-08
I'm using 10.04, just installed yesterday. 

I ran Movie Player, just to see if that worked, and it tells me I need something called "DVD source". Is that a file?

I also tried Brasero, and it says I need "libdvdcss.so.2". After reading some documentation on terminal commands I tried to download it. I got this:

ketman@ketman-laptop:~$ sudo apt-get install libdvdcss.so.2
[sudo] password for ketman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdcss.so.2
ketman@ketman-laptop:~$ 

What have I done wrong there?

Is this going to be a continuing story, where I have to get plugins for everything, one at a time? Is there not such a thing as a complete library package you can download?

---

### Post by Rafterman414 on 2012-02-08
That library should be in the ubuntu-restricted-extras package I believe
Try this


```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by cottfcfan on 2012-02-08
If you check in Synaptic, the package is called libdvdcss2.
So in a terminal you need:
```
sudo apt-get install libdvdcss2
```

---

### Post by tjoff on 2012-02-08
You generally do not install single files with apt-get but rather "packages".
Brasero complains about a missing file, so you have to install the package containing the file, not the file itself.

In your case libdvdcss.so.2 is a file in the software package libdvdcss2 . 
When using apt-get you can use the tab key to autocomplete package names, if you are unsure of their exact names.
So run:

```
sudo apt-get install libdvdcss2
```

edit: cleaned up my post based on info from cottfcfan

---

### Post by Paqman on 2012-02-08
You don't actually have to use the terminal for installing stuff like this if you'd rather not. There's a good GUI package manager in the repos called Synaptic. The difference between it and Ubuntu Software Centre is that it doesn't try to hide the obscure system packages from you (which in this case is a good thing).

---

### Post by Rafterman414 on 2012-02-08
I apologize if I was incorrect in stating that it was in the ubuntu-restricted-extras, maybe there is a package in there that depends on libdvdcss2 and that's why I thought that. Sorry if I gave any misinformation.:oops:

---

### Post by Ketman on 2012-02-08
Thanks for the prompt replies.

> **cottfcfan said:**
> If you check in Synaptic, the package is called libdvdcss2.
So in a terminal you need:
```
sudo apt-get install libdvdcss2
```

No good for me. I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
ketman@ketman-laptop:~$ 


> **Paqman said:**
> You don't actually have to use the terminal for  installing stuff like this if you'd rather not. There's a good GUI  package manager in the repos called Synaptic. The difference between it  and Ubuntu Software Centre is that it doesn't try to hide the obscure  system packages from you (which in this case is a good thing).


Sorry - what's the "repos"?

---

### Post by ajgreeny on 2012-02-08
All the information you need is here:-
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I also find it useful to enable the [medibuntu]("http://www.medibuntu.org/") **repositories** (ie. **repos**, which are the stores of all packages for you to install with synaptic or softweare-center).
[Medibuntu]("http://www.medibuntu.org/")

---

### Post by wolfen69 on 2012-02-08
Doing: (you can copy and paste into terminal)
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs libdvdcss2 ffmpeg
```
will give you every codec you will need.

---

### Post by cottfcfan on 2012-02-08
ketman..
The repos are your software sources.
If you open up the software sources, make sure that under "other software" the  "canonical partners" & the "independant" repos are ticked. 
This will give you access to a lot more packages.
Then add the Medibuntu repo as Wolfen69 describes.
After that:
```
sudo apt-get update
```
And you should be good to go.

---

### Post by ikt on 2012-02-08
> **Ketman said:**
> ketman@ketman-laptop:~$ sudo apt-get install libdvdcss.so.2

E: Couldn't find package libdvdcss.so.2

What have I done wrong there?

So you've got your 4 main repos:

[http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/)

---
Main - Officially supported software.

Restricted - Supported software that is not available under a completely free license.

Universe - Community maintained software, i.e. not officially supported software.

Multiverse - Software that is not free.
---

So say you want to install deluge

[http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/universe/d/deluge/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/pool/universe/d/deluge/)

Deluge is located under in the universe repository, so:

sudo (super user do) apt-get (application/package manager) install (download and install) deluge (whatever the program is)

apt-get then goes to the universe list, grabs deluge and installs it.

But you need to make sure you let apt-get know about the universe to begin with.

[IMG]http://ikt.id.au/blog/wp-content/uploads/2012/02/sources.png[/IMG]

Otherwise that's all there is to. 

Installing synaptic package manager is good at helping sort out which package you want.

---

### Post by Ketman on 2012-02-08
Thanks, ikt. A very informative post. I've checked all the boxes in Software Sources.

The Restricted Formats package got me up and running with both Movie Player and Brasero. So thanks to all the posters who gave advice. No doubt I'll be back when I hit another wall, but I feel as if I'm off and running now.

---

