---
title: "Help Installing ktechlab"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by cddpys on 2011-11-04
Hi

 i downloaded ktechlab and unzipped the folder,  i have no idea how to preceded now to install the program.  I have tried using apt-get install to install ktech and i get the messabe saying unable to locate package

could someone please help me on how to install

thanks

---

### Post by azmyth on 2011-11-04
You need to follow the instructions in the install file in the main directory as you will have to compile. There's a deb file on the ktechlab web site but it's over 4 years old so it probably wouldn't install correctly.

---

### Post by jmajeremy on 2011-11-04
I would say go ahead and try the .deb file first. Just do ```
sudo dpkg -i filename.deb
```

---

### Post by cddpys on 2011-11-04
ok i tried going through the install file but the first step is do run configure by ./configure

when i do this however i get the error:


configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly

---

### Post by azmyth on 2011-11-05
sudo apt-get install kde-config

You'll probably get more of these types of errors which will require you to install the dependencies.

---

### Post by cddpys on 2011-11-05
i tried sudo apt-get install kde-config and got this error message:

E: Unable to locate package kde-config

i also tried running sudo apt-get update and retried and got the same message

---

### Post by azmyth on 2011-11-05
Try installing the package deb file located here

[http://sourceforge.net/projects/ktechlab/files/ktechlab/ktechlab_0.3.6_i386.deb/](http://sourceforge.net/projects/ktechlab/files/ktechlab/ktechlab_0.3.6_i386.deb/)

follow the instructions jmajeremy provided.

If this doesn't work, you'll need to understand how to compile and how to solve dependency issues which is probably beyond what we can provide through a forum.

---

### Post by cddpys on 2011-11-05
ok i tried that and it did not work.  Thanks for the trying to help though.

Do you have any suggestions for other circuit simulators for linux, i am trying to find a replacement for multisim?

---

