---
title: "installing pyscripter in wine"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by gandalf3 on 2012-04-13
I'm new to Linux, and am using Ubuntu 11.10.
i downloaded pyscripter and right clicked on the .exe to open with wine windows program loader, but i get this error:

"Python could not be properly initialized. we must quit"

i assume this is because Python is not properly installed.. but I'm not sure.
can anyone help me with this?

(also, should this be in the wine forum?)

---

### Post by Gleichsnerd on 2012-04-13
Go ahead and try
```
sudo apt-get install python
```
then try installing again.

---

### Post by donkyhotay on 2012-04-13
> **Gleichsnerd said:**
> Go ahead and try
```
sudo apt-get install python
```
then try installing again.

That won't work since you're running a windows program through wine it is looking for the windows version of python, not the linux version which is probably already installed (and if it isn't the previous commands will install it). You would have to download and install python for windows and install that from wine and then all the dependencies for your programs... it'd be a mess and I wouldn't recommend trying that. Looking at what the program is I would recommend a linux native python IDE since they don't appear to have a linux version available on their website. The one I hear of most often is eclipse though I've never used it. Personally I just use gedit with some extra plugins installed for all my coding needs, it's simple and it works. Gedit is installed by default but check synaptic for gedit plugins which gives you a little bit more functionality and customization for coding.

---

