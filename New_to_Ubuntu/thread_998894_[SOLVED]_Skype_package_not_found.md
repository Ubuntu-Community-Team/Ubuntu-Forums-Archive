---
title: "[SOLVED] Skype package not found"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by groundnut on 2008-12-01
I have just installed Intrepid Ibex.
Now I'm trying to install Skype.
I was able to do the first two steps below, but Synaptic does not find the Skype package.

What could be the problem?


1. Add the Skype repository*: deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
   
2. Reload or update the package information

3. Install the skype package.

---

### Post by __Ryan__ on 2008-12-01
Try adding the medibuntu repository, it contains Skype.

---

### Post by girishsasikumar on 2008-12-01
Try adding medibuntu repo and then install skype

for 8.10
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install skype
```

---

### Post by groundnut on 2008-12-01
got it.

Thanks to the three lines of code.

---

### Post by Sef on 2008-12-02
moved to absolute beginners.

---

