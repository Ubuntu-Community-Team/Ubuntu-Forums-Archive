---
title: "ndiswrapper does not exist on my system"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Heresy64 on 2008-08-23
Am I the only poor sap that cannot find ndiswrapper on my system. I'm trying to install a wireless adapter and need ndiswrapper to do so. However, whenever I attempt to follow instructions posted on how to do it, the program does not exist. I can't find it in the synaptic package manager and it is not listed in programs to add. I think I must have gotten a defective install! ;). More likely is that I'm doing something wrong, which is too bad because I was having no problems with my Ubuntu install until now.

---

### Post by steveneddy on 2008-08-23
```
locate ndiswrapper
```

---

### Post by seagullplayer77 on 2008-08-23
As far as I know, you need to install ndiswrapper--it doesn't come with Ubuntu by default.

> **ToM-X said:**
> Ok try this...

download ndiswrapper and save to your **Home** folder.

```
http://wifix.sourceforge.net/software.php?title=ndiswrapper
```

Then open the terminal:

```
tar xvf ndiswrapper-1.51.tar.gz
```

```
pushd ndiswrapper-1.51
```

```
sudo make uninstall
```

```
make
```

```
sudo make install
```

```
popd
```

Then Ndiswrapper should be installed.

Got the tutorial from [http://ph.ubuntuforums.com/showthread.php?t=766529&page=6](http://ph.ubuntuforums.com/showthread.php?t=766529&page=6)

---

### Post by ctswhole on 2008-08-23
What repositories do you have enabled?

---

