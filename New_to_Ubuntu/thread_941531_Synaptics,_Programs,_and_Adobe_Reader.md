---
title: "Synaptics, Programs, and Adobe Reader"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by icyest on 2008-10-08
When I was first reading about Linux, I liked the concept of an all in one program installer convenience that Linux provided. I was under the impression that the Synaptic Package manager was all there was to it, but the Add/Remove Applications button under Applications confused me.

Why are they separate, and can some explain this? Why aren't they grouped together? 

-------------------------

So the second part of my question is, my college lecture notes often come in the form of PDF files for adobe reader, that way, the students cannot edit the copyrighted files. I heard Adobe reader could make little side note attachments to their files, which would be perfect for my notes. I need a substitute for Adobe's famous "Reader" program. 
BTW, can linux also install Adobe Reader? I cant find it in the Add/Remove Applications list, so i assumed most linux users used a substitute instead.

Lastly, I've been using this default thing called Document Viewer, but I can't find it in the Applications list. Where is this pre-installed program? I don't like not knowing where hidden programs are.



Please answer each of my questions completely, and thank you for you're time.

---

### Post by billgoldberg on 2008-10-08
> **icyest said:**
> When I was first reading about Linux, I liked the concept of an all in one program installer convenience that Linux provided. I was under the impression that the Synaptic Package manager was all there was to it, but the Add/Remove Applications button under Applications confused me.

Why are they separate, and can some explain this? Why aren't they grouped together? 

-------------------------

So the second part of my question is, my college lecture notes often come in the form of PDF files for adobe reader, that way, the students cannot edit the copyrighted files. I heard Adobe reader could make little side note attachments to their files, which would be perfect for my notes. I need a substitute for Adobe's famous "Reader" program. 
BTW, can linux also install Adobe Reader? I cant find it in the Add/Remove Applications list, so i assumed most linux users used a substitute instead.

Lastly, I've been using this default thing called Document Viewer, but I can't find it in the Applications list. Where is this pre-installed program? I don't like not knowing where hidden programs are.



Please answer each of my questions completely, and thank you for you're time.

The document viewer is called "evince". 

--

Add/remove and Synaptic are just GUI front end to APT.

In synaptic you can find all packages in the Ubuntu repositories. 

Add/Remove is a more simplistic, nicer looking front end for apt to install basic applications.

Link:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

--

You can download adobe's reader from the adobe website. It will come as a .tar.gz.

But it's easier to just add another repositories to you system.

This can be done using a gui tool, but it's easier to give the command.

Go to "applications -> accessories -> terminal" and enter this command.

(copy/paste it, enter you password when prompted and press enter)

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y acroread acroread-plugins mozilla-acroread
```

This will add the medibuntu repo to your system and install adobe's reader.

---

### Post by OldGrey on 2008-10-08
Add/Remove and Synaptic basically fullfill similar functions. However Add/Remove is more user friendly in that you can easily browse through some of the major applications that are available. On the other Synaptic is far more comprehensive including a complete list of all prorammess and their dependencies but it requires a little more effort to locate what you need.

You can install the Adobe reader. One of the easy ways is to add the "Medibuntu" repositories. See :
 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

for further explanation, it also enables you to install other usful non standard programmes like Google Earth

The document reader opens automatically with PDF files so there is no need to include a launcher under applications. You could add one if it's really necessary to you.

---

### Post by kukibird1 on 2008-10-08
System > Preferences>Main Menu>Graphics Put a check mark in Document Viewer

---

### Post by snowpine on 2008-10-08
OpenOffice 3 will allow you to edit PDF files.

---

### Post by icyest on 2008-10-11
> **billgoldberg said:**
> The document viewer is called "evince". 

--

Add/remove and Synaptic are just GUI front end to APT.

In synaptic you can find all packages in the Ubuntu repositories. 

Add/Remove is a more simplistic, nicer looking front end for apt to install basic applications.

Link:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

--

You can download adobe's reader from the adobe website. It will come as a .tar.gz.

But it's easier to just add another repositories to you system.

This can be done using a gui tool, but it's easier to give the command.

Go to "applications -> accessories -> terminal" and enter this command.

(copy/paste it, enter you password when prompted and press enter)

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y acroread acroread-plugins mozilla-acroread
```

This will add the medibuntu repo to your system and install adobe's reader.

So does this install Adobe Reader into my Firefox browser, or does it actually give me the program on my desktop?

---

### Post by Perfect Storm on 2008-10-11
> **icyest said:**
> So does this install Adobe Reader into my Firefox browser, or does it actually give me the program on my desktop?

Both.

---

### Post by Keen101 on 2008-10-11
I installed adobe reader once. I just got it from the Adobe site.

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

Select Linux and (.deb).

I believe it will ask you if you want to install the firefox add-on. But, maybe that was just with the (tar.gz) source file. I don't really remember.

But, I don't use it anymore. I found it a little sluggish for my taste (although it was an older computer too).

as for add/remove:

add/remove is basically a simple installer. It doesn't include all programs. I find synaptic to my liking much better. But that's me.


Oh, and for future refrence.....

.deb and .run files are the easiest and preferred methods of installing if the programs are not included in your repositories. Of course installing from source isn't too hard once you get the hang of it.

---

### Post by SunnyRabbiera on 2008-10-11
> **icyest said:**
> When I was first reading about Linux, I liked the concept of an all in one program installer convenience that Linux provided. I was under the impression that the Synaptic Package manager was all there was to it, but the Add/Remove Applications button under Applications confused me.

Why are they separate, and can some explain this? Why aren't they grouped together? 

The Add/remove app was mainly added to help beginners, it is a nice tool to get one started in installing packages in their system.
Synaptic is a great package manager on its own but for beginners it might be a bit intimidating as for one it doesnt provide full package details, it gives partial ones yes but it does not tell you what a package does unless you tweak synaptic to show you package details and such.
It also has icons for applications too, a bit more attractive for the new user then the simple boxes that synaptic provides.

> So the second part of my question is, my college lecture notes often come in the form of PDF files for adobe reader, that way, the students cannot edit the copyrighted files. I heard Adobe reader could make little side note attachments to their files, which would be perfect for my notes. I need a substitute for Adobe's famous "Reader" program. 
BTW, can linux also install Adobe Reader? I cant find it in the Add/Remove Applications list, so i assumed most linux users used a substitute instead.
Luckily you can install adobe reader and use the linux alternatives to it like envince

> Lastly, I've been using this default thing called Document Viewer, but I can't find it in the Applications list. Where is this pre-installed program? I don't like not knowing where hidden programs are.
Well its a hidden application but I see others beat me to the punch on unhiding it.

---

