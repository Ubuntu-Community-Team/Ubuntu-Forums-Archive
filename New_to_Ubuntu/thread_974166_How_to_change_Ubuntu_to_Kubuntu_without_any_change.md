---
title: "How to change Ubuntu to Kubuntu without any changes...."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Swan_Htet_Aung on 2008-11-07
:lolflag:
Hey Friends, my sister would like to use Kubuntu but we have only Ubuntu 8.10.
How can we change to Kubuntu without changing any data?
This is for my sister, she don't like Ubuntu theme and appearance.
So, she want to change Kubuntu.
Please reply me.............
I am waiting to you..........
:)

---

### Post by Coreigh on 2008-11-07
Well there are probably more than two ways to do this.

1. Set up a user for your sister's login, and configure her session to us the KDE desktop. This allows her to use KDE and other users to still use Gnome. I am not sure if this will fully work or how to do it.

2. Install the package kubuntu-default-settings this *I think* changes everybody's login sessions to the KDE environment.

3. Install the KDE programs your sister want to use. They will still work the same but just look slightly different.

4. ... I am sure there are other ways but ... ?

---

### Post by SuperSonic4 on 2008-11-07
```
sudo aptitude install kubuntu-kde4-core
```

This will only install the very basics of kde4 such as dolphin, kdelibs and konsole amongst others. You then add others such as amarok, krusader and whatever else you like XD

---

### Post by bhendry on 2008-11-07
> **SuperSonic4 said:**
> ```
sudo aptitude kubuntu-kde4-core
```

This will only **_[SIZE="3"]install[/SIZE]_** the very basics of kde4 such as dolphin, kdelibs and konsole amongst others. You then add others such as amarok, krusader and whatever else you like XD

install???

Do I have to download the kubuntu-kde4-core package first?

When I run "sudo aptitude install kubuntu-kde4-core" - I get all kinds of errors:

root@knox:/home/bob# sudo aptitude install kubuntu-kde4-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-kde4-core"
Couldn't find any package whose name or description matched "kubuntu-kde4-core"
The following packages have been kept back:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch)

Suggestions?  (Please remember the name of this forum . . .  

Bob Hendry

---

### Post by SuperSonic4 on 2008-11-07
Doesn't the OP's sister want kubuntu? I suppose the OP could just change the themes on his sister's account.

---

### Post by halitech on 2008-11-07
open a terminal and type
```
sudo apt-get install kubuntu-desktop
```

this will install the Kubuntu desktop and all the apps used in Kubuntu. Then just train her to select the KDE desktop when she logs in

---

### Post by kansasnoob on 2008-11-07
Look here:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

And also here:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Just read carefully!

---

