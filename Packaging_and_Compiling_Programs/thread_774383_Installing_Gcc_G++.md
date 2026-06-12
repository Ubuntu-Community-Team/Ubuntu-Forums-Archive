---
title: "Installing Gcc G++"
date: 2008-04-29
forum: Packaging and Compiling Programs
---

### Post by ali.gilani on 2008-04-29
I downloaded and unzipped the package. But how do i compile and install it? Also is there an IDE like Visual C++?

---

### Post by Jimmey on 2008-04-29
It's better to install things like this using the Synaptic Package Manager (System > Administration > Synaptic)

Search for the package "build-essential"

Alternatively you can type

```
sudo apt-get install build-essential
``` into a terminal window. 

That should make it alot easier to install.

After that, just search for some IDEs - Either using synaptic's search function, or ```
apt-cache search c++ ide
``` into the terminal window, again ;-)

---

### Post by greenkernel on 2008-10-09
> **ali.gilani said:**
> I downloaded and unzipped the package. But how do i compile and install it? Also is there an IDE like Visual C++?

[COLOR="DarkRed"]Installing G++[/COLOR]
[LIST=1]
[*]Go to System > Administration > Synaptic Package Manager.
[*]Type g++ in Search box and mark to install.
[/LIST]

I'm currently using Anjuta IDE for C++. It's quite like Dev-C++. You can install it as follows:-
[COLOR="DarkRed"]
Installing Anjuta IDE[/COLOR]
[LIST=1]
[*]Go to Applications > Add/Remove...
[*]Type Anjuta in Search box and install it.
[/LIST]
Done!

Regards,

[COLOR="DarkGreen"]greenkernel[/COLOR]

---

