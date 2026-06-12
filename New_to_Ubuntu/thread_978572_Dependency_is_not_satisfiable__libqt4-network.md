---
title: "Dependency is not satisfiable:  libqt4-network"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by cwmoser on 2008-11-11
I tried to install the latest View Your Mind (VYM) program and I get this error when I click on the *.deb file:

Error:  Dependency is not satisfiable:  libqt4-network

How do I locate this library and install it?  I have googled and searched the web but no joy.  

Thanks

Carl

---

### Post by bumanie on 2008-11-11
libqt4-network is in synaptic package manager. Type it into search and you should be able to download - at least it is in my synaptic. If that's no good, go [here]("http://packages.ubuntu.com/hardy-backports/libs/libqt4-network").

---

### Post by Ryadt on 2008-11-11
```
sudo apt-get install libqt4-network
```

---

### Post by neurostu on 2008-11-11
Or you could run:
```

sudo apt-get install -f

```
that should resolve all dependency issues as long as the required files are in your installed repositories.

---

### Post by cwmoser on 2008-11-11
You guys got me thinking.  I went into Software Sourcs and noted under the Updates tab that "Unsupported updates (hardy-back-ports)" was not checked.

Now Synaptic can find libqt4-netowrk.

Thanks for the insights.

Carl

---

### Post by keets74 on 2010-01-05
hey guys - <i'm new to linux and am having trouble.  I'm attempting to install virtual machine software but get the error.  'dependency not satisfiable: libqt4-network.  I've found the package for this and installed it but each time I try to install the vm software I still get this error...even though I thought I installed it.

Any help would be great.

keets

---

### Post by neurostu on 2010-01-06
Its usually better to start a new thread when the thread has been dead as long as this one has.

---

