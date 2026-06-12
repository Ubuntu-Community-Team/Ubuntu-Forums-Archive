---
title: "libsdl1.2-dev &quot;you can install a newer version from the software channel&quot;"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Inseki on 2008-07-13
I am currently attempting to install this

libglu1-xorg-dev_7.3+10ubuntu10_all.deb
[http://packages.ubuntu.com/ja/hardy/all/libglu1-xorg-dev/download](http://packages.ubuntu.com/ja/hardy/all/libglu1-xorg-dev/download) 

When I open the package installer it informs me I can install a newer version from the "software channel". And it also informs me under the status that I'm required to install 16 packages.

Are those packages the ones I am attempting to install? What is the software channel? Will anything bad happen from installing this?

Sorry for absolute beginner's questions m(_ _)m

---

### Post by nowshining on 2008-07-13
the channels are the repositories where u can download a many thoudands of software, open up synaptic package manger to browse thru them.

if need be u may have to enable the disabled repositories thru software sources - check mark what u want - and most likely leave out the SOURCE repos and click close a nd yes to reload.

u should not see many more updates.

As for the updates - it's like MS windows, these updates fix many errors, security probs, etc..

just click on the update icon to go to the updater and then click install and then enter ur pw when asked.

edit: as for the -dev - after u enable the extra repos, u can thru and install the -dev lib u need. 

u can also install  updates, etc.. thru the terminal with apt-get & aptitude.

sudo apt-get update
sudo apt-get upgrade

to search - aptitude search searchword

to install sudo apt-get install nameofprogramuwanttoinstall - u can use TAB completion within the terminal.

---

### Post by overdrank on 2008-07-13
> **Inseki said:**
> I am currently attempting to install this

libglu1-xorg-dev_7.3+10ubuntu10_all.deb
[http://packages.ubuntu.com/ja/hardy/all/libglu1-xorg-dev/download](http://packages.ubuntu.com/ja/hardy/all/libglu1-xorg-dev/download) 

When I open the package installer it informs me I can install a newer version from the "software channel". And it also informs me under the status that I'm required to install 16 packages.

Are those packages the ones I am attempting to install? What is the software channel? Will anything bad happen from installing this?

Sorry for absolute beginner's questions m(_ _)m

Hi and the software channels are the repos. Have you tried searching synaptic manager?
The 16 are most likely dependency.

---

### Post by Inseki on 2008-07-13
Thank you both very much. That is pretty much what I had thought it meant, but the terms were unfamiliar.

Thank you again m(_ _)m

---

### Post by nowshining on 2008-07-13
ur welcome. :)

---

