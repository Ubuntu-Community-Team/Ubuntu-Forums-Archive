---
title: "i feel so stupid..."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Modnar1 on 2008-06-04
basically i have uninstalled network manager on xubuntu in the hope that i could then get wifi-radar to work in case there were program conflicts, so after i unistalled network manager i still couldn't connect to wifi, and now i can no longer connect to the internet via LAN either. can someone please give me a step by step guide to reinstalling network manager given that i don't have internet on my linux machine but i do have access from my laptop running vista. thanks in advanced. btw i'm running xubuntu if that makes any difference

---

### Post by django0909 on 2008-06-04
Try doing a search on 'network-manager' in Synaptic...

---

### Post by Inxsible on 2008-06-04
Try installing it by ```
sudo apt-get install nm-applet
``` If you hadn't purged it while installing, the package might still be in the system -- I forget where exactly such packages lie.

I could be wrong though.

---

### Post by AOZ on 2008-06-04
He wont be able to because he has no internet connection. Try getting the package from ur laptop, put it on a usb and put that on ur linux box

---

### Post by django0909 on 2008-06-04
> He wont be able to because he has no internet connection.

Ha ha, oh yeah, sorry, missed that bit!

Isn't there anything on the Live CD?

---

### Post by anderskitson on 2008-06-04
yeah shouldn't he be able to search it in synaptic, and make sure live cd is checked in software sources, and pull it off there.

---

### Post by Modnar1 on 2008-06-04
okay i'v downloaded the package from my laptop and put it on my linux systemm, but when i ran ./configure i got this error:

checking for DBUS... configure: error: the pkg-config script could not be found or is too old. make sure it is in your PATH or set the PKG_CONFIG environment variable to the full path to pkg-config

---

### Post by django0909 on 2008-06-04
Are you in the right directory? (i.e. the one with the package in?)

---

### Post by AOZ on 2008-06-04
if your having issues with installing the package id say go with what the other guys suggested by putting the ubuntu CD into ur comp and get it off synaptic once you've set the live CD as a source...assuming you've kept the cd

---

### Post by Modnar1 on 2008-06-04
yes

---

### Post by django0909 on 2008-06-04
Is that 'yes' to my question? If so, are you trying to run the script from the usb drive I assume you transferred the package over with? Or are you running it from the Ubuntu machine itself?

---

### Post by Modnar1 on 2008-06-04
how do i set the cd as a source (i assume the live cd is just the installation cd)

---

### Post by Modnar1 on 2008-06-04
> **django0909 said:**
> Is that 'yes' to my question? If so, are you trying to run the script from the usb drive I assume you transferred the package over with? Or are you running it from the Ubuntu machine itself?

that was a yes  to your question, soz i didn't see the other post below yours, and i'm running it from my desktop itself not my usb

---

### Post by django0909 on 2008-06-04
On Ubuntu 8.04 you open Synaptic, goto Settings-Repositories, and check the box at the bottom. Should be something along the same lines in Xubuntu...?

---

### Post by AOZ on 2008-06-04
yes the live cd = cd you used to install ubuntu

go to System->Administration->Software Sources

then chekc the box at the bottom "Installable from CD/DVD

---

### Post by Modnar1 on 2008-06-04
okay i selected the disc as a source, it then went on to try and download it from the internet still so i un-checked them as sources so now the only source was the cd and then it couldn't find anything

---

### Post by sam_delta on 2008-06-04
insert your installation cd and type the following (youll get some errors on the second command, thats ok since you dont have internet connection but you should type it to update repos from cd
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install network-manager
```

sam

---

### Post by Modnar1 on 2008-06-04
thanks for all your help guys, i'm just gonna give up and reinstall with ubuntu, it seems like that its easier to do things such as installing themes and such anyway

---

### Post by blazercist on 2008-06-04
DONT REINSTALL, i cant believe you guys dont know this, just do "sudo apt-get install nm-applet".

It will work he doesn't need internet, the package is cached somewhere on the harddisk it will not need to download again it will install from the harddrive.  WOW.  You all make me sad.

---

### Post by AOZ on 2008-06-04
He's already tried that and it didnt work

---

### Post by blazercist on 2008-06-04
> **AOZ said:**
> He's already tried that and it didnt work

He must've purged it, should never do that with standard packages.  But he doesn't need the applet to connect.  He could manually configure his wifi and then install the package normally.

Use ifconfig and iwconfig.  Sure its not automagical but it works.

---

### Post by Modnar1 on 2008-06-11
it was already too late for my xubuntu i'd already installed ubuntu, but how do i use ifconfig to configure my wifi as i'm still having problems with my wifi on ubuntu and when i run ifconfig it just tells me information and that's it

---

