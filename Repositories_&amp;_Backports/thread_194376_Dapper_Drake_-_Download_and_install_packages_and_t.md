---
title: "Dapper Drake - Download and install packages and their dependencies under windows"
date: 2006-06-11
forum: Repositories &amp; Backports
---

### Post by pfadfinder on 2006-06-11
Hello,
For establishing a isdn Fritz!Card PCI connection with Dapper Drake, i need according to the wiki the following packages:

> 
build-essential
isdnutils (unter Breezy und Dapper in universe)
isdnutils-base
capiutils
pppdcapiplugin
isdnactivecards (universe)
libcapi20-3 (unter Hoary ist libcapi20-2 verlangt)
libcapi20-dev (unter Hoary in universe)
kernel-headers-uname-r (universe)[


I would usually simply download them & their dependencies with the Synaptic Packages Manager, but since I don't have web access..

First: How/from where can I download those packages AND their dependencies under Windows? From where do i know what dependencies each package got?

2nd: If I  have downloaded all of them, what then?

Greetings

---

### Post by jobezone on 2006-06-11
Mark those packages you want to install in synaptic, as well as their dependencies. Then see under the File menu, there should be a "create script to download packages" (or simillar) menu option. Use it to create a script. Copy this script to the windows machine, and put wget for windows in the same directory of the script as well. Add a **.bat** extension to the script, and run it. Once it downloads everything, go back to gnu/linux, and in Synaptic, again in the File menu, there should be an option to install the downloaded packages.

Hope I wasn't too confusing!

EDIT: But you have a problem. You won't be able to find some of those packages in Synaptic since they are in Universe, and you can't download the list of packages from universe on that off-line computer...
Well, a second option is to go hunt them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
EDIT2: Also, to install the .deb packages, you could use Synaptic like I showed before, or just run this command in the directory which contain them:
```
sudo dpkg -i *.deb
```

---

### Post by pfadfinder on 2006-06-11
Hello,
Thanks for your reply. I have installed all packages except the universe- maybe someone with dapper could upload the script for the packages 
> isdnutils
isdnactivecards
kernel-headers for k7
and their dependencies.

Or, is there any other solution? If i have to select each dependency of each package and each dependency of their dependencies, I will grow old..

Greetings

---

### Post by jobezone on 2006-06-11
[QUOTE=pfadfinder]Hello,
Thanks for your reply. I have installed all packages except the universe- maybe someone with dapper could upload the script for the packages 

and their dependencies.

Or, is there any other solution? If i have to select each dependency of each package and each dependency of their dependencies, I will grow old..

Greetings[/QUOTE]

Sorry, but I'm not in Dapper right now. This monday I'll be able to create, and put in this thread the script.

---

### Post by jobezone on 2006-06-12
Well, it's monday, and I still don't have acess to the Dapper I maintain (a friend's laptop)!
As soon as I do, I'll put here the script. But anybody can do this:
Mark these packages for installation in Synaptic: ```
isdnutils
isdnactivecards
kernel-headers for k7
``` then go to File->create script to download packages.
Then just put here the script.

---

### Post by pfadfinder on 2006-06-13
Thanks for your help. I solved my problem by downloading the files with another Ubuntu machine in LAN and my windows machine as gateway.

Greetings

---

