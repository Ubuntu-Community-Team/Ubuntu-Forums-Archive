---
title: "Application for opening Google earth installer???????"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by johnnyflips on 2008-09-10
Hi all, I just tried to download Google earth and had a little bit of a problem. I downloaded the BIN file, but when I try to open it I get "there is no application for this file type". So I manually choose to open it with archive manager, right?? But then I get a message telling me it can't open this type of archive. Any ideas?? I've been running Ubuntu for bit, but never tried to install Google earth before before because quite frankly it just really not that big of a deal, but finding something Linux won't run is, any ideas on what I'm doing wrong.......

---

### Post by dmurat on 2008-09-10
i guess you can find it already downloaded in the system. check the synaptic package manager.

---

### Post by ad_267 on 2008-09-10
No no no.

You just right click on the file, select properties > permissions and tick "allow executing as a program".

Then when you double click you just select "Run".

Edit: Ok that might not work, change the permissions then rename it and delete the ".bin" extension and then run it.

---

### Post by Vivaldi Gloria on 2008-09-10
Google Earth is available in the medibuntu repos:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the howto there to add medibuntu to your repo list. If you have ubuntu 8.04 hardy heron then open a terminal and give the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now you can install GE using synaptic:

system menu > admin > synaptic

---

### Post by oldos2er on 2008-09-10
> **johnnyflips said:**
> Hi all, I just tried to download Google earth and had a little bit of a problem. I downloaded the BIN file, but when I try to open it I get "there is no application for this file type". So I manually choose to open it with archive manager, right?? But then I get a message telling me it can't open this type of archive. Any ideas?? I've been running Ubuntu for bit, but never tried to install Google earth before before because quite frankly it just really not that big of a deal, but finding something Linux won't run is, any ideas on what I'm doing wrong.......

 Open a terminal, issue the following commands one at a time:

cd Desktop

chmod a+x GoogleEarthLinux.bin

./GoogleEarthLinux.bin

---

