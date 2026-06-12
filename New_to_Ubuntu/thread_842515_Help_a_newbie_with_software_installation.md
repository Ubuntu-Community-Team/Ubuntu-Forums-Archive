---
title: "Help a newbie with software installation"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by newbuntu123 on 2008-06-27
Hi,
I have been a long time user of Windows XP. However, today I made the switch to Linux, choosing Ubuntu as the distro of my choice.
In order to dual-boot with WIndows, I used Wubi 8.04 and Ubuntu 'Hardy Heron'.
Installation went fine, however installing software IS A REAL PAIN!:(
I want to install -Gnash-, however it wants some libaXXXX as a dependency, where on earth do I get it ?
Same goes for Deluge -> some dependency not found... its driving me crazy !:mad:
I want to install Wine ->  but it asks me to edit some "list"...
What do I do now ?
And sudo apt-get update is taking WAY too much time to complete...
Please help a confused Linux newbie...

---

### Post by Duck2006 on 2008-06-27
Do a search in your, 

System -> Administration -> Synaptic Package Manager 

and load them from there.

---

### Post by Vivaldi Gloria on 2008-06-27
> **newbuntu123 said:**
> Hi,
I have been a long time user of Windows XP. However, today I made the switch to Linux, choosing Ubuntu as the distro of my choice.
In order to dual-boot with WIndows, I used Wubi 8.04 and Ubuntu 'Hardy Heron'.
Installation went fine, however installing software IS A REAL PAIN!:(
I want to install -Gnash-, however it wants some libaXXXX as a dependency, where on earth do I get it ?
Same goes for Deluge -> some dependency not found... its driving me crazy !:mad:
I want to install Wine ->  but it asks me to edit some "list"...
What do I do now ?
And sudo apt-get update is taking WAY too much time to complete...
Please help a confused Linux newbie...

Start synaptic from your system menu and refresh and then use it to install the packages you want. It takes care of dependencies automatically.

Also you may want to enable restricted & multiverse repos in the settings menu of synaptic and  then refresh. This will give you more apps.

---

