---
title: "[SOLVED] aptoncd  cannot restore in  Hardy"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by fourscore on 2008-04-30
Have installed Hardy successfully,  When I try to use the restore function in  AptonCd,    the load button does not respond.  Pls help

---

### Post by kshtjsnghl on 2008-04-30
hi
 Even i am facing the same problem

 Alternatively, you can extract the cd image of apt on cd and just copy the packages /var/cache/apt/archives and then click on the corresponding applications you want to install in the add/remove application.

 Besides, you will have to copy them from the terminal with root priviledges.

But even i am not getting to restore the apt on cd directly..:(

---

### Post by fourscore on 2008-05-02
> **fourscore said:**
> Have installed Hardy successfully,  When I try to use the restore function in  AptonCd,    the load button does not respond.  Pls help

HELP

---

### Post by aeiah on 2008-05-02
isnt this expected? aptoncd acts like a cd repository, no? well ill guessing you're coming from gutsy, so hardy cant see and hardy stuff on your newly added repo cd, only gutsy software. thats what im guessing has happened. i may be wrong though but i didnt think aptoncd was supposed to be used for upgrades.

---

### Post by kshtjsnghl on 2008-05-02
The main problem is that it kind of hangs after you click as soon as you click on load. By this time no cd image has been loaded. 
I think there is some problem with hardy. Because i tried both the apt on cd application of gutsy and the updated version for hardy, but they pose the same problem in hardy...

---

### Post by fourscore on 2008-05-03
This is a reported bug. See link - [https://bugs.launchpad.net/ubuntu/+source/aptoncd/+bug/199600](https://bugs.launchpad.net/ubuntu/+source/aptoncd/+bug/199600)

---

### Post by Bri0 on 2008-05-07
In the meantime do this.

[B]
- extract the ISO (right click on it and hit 'Extract Here')[/B]

**- In terminal:**
Note: change "you:you" to your username that you login with.

sudo chown you:you /var/cache/apt/archives

Enter, then your password, Enter


This will give you permission of that folder in the filesystem ( /var/cache/apt/archives ), then copy over the packages (in the packages folder) from the extracted ISO to the archive folder (Filesystem/var/cache/apt/archives).

[B]
- Once done go into terminal and put this in, which will bring the folder back to root permission.[/B]

sudo chown root:root /var/cache/apt/archives

Enter

---

### Post by kshtjsnghl on 2008-05-07
yeah or you can precede the copy command with sudo when you copy from the extracted files to /var/cache/apt/archives in terminal...

---

### Post by rogerdean on 2008-05-31
i've found a stopgap solution by removing aptoncd using synaptic, and then installing the version downloaded from the aptoncd site - [http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb](http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb)

---

### Post by rogerdean on 2008-05-31
and now there's a fix for aptoncd coming. in the meantime you can install the unreleased fix from 

[http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb](http://www.cypherbios.org/aptoncd/packages/aptoncd_0.1.98-1ubuntu1/binary/aptoncd_0.1.98-1ubuntu1_all.deb)

---

### Post by fourscore on 2008-06-24
The official fix has been finally released.  
Closing this as solved.

---

