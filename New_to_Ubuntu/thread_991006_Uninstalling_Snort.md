---
title: "Uninstalling Snort"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by scribbles on 2008-11-23
I'm trying to follow bodhi.zazen's intrusion detection guide to setup snort but I already had the repo's version installed and want to uninstall the version I have in, including snort-mysql. I went to /etc/snort and tried make unnstall and got ```
make: Nothing to be done for `/etc/snort'.
make: *** No rule to make target `uninstall'.  Stop.

```

Note: Went back and ran apt-get upgrade and it said that there was one package of 0b that needed to be updated. After than ran 'dpkg-reconfigure -plow snort-mysql' which was a command shown in the installer if you did not yet have a mysql db ready to go and it said

```
/usr/sbin/dpkg-reconfigure: snort-mysql is broken or not fully installed
```

---

### Post by Michael.Godawski on 2008-11-23
Can you please post a link to  bodhi's instructions you were following?
> 
 I went to /etc/snort and tried make unnstall and got How do you went? Do you mean in terminal? What exactly did you do? :)

---

### Post by ajgreeny on 2008-11-23
Have you looked in synaptic?  Many applications, even if not installed that way, still show there and can be uninstalled using it.

---

### Post by scribbles on 2008-11-23
Bodhi's guide [here]("http://ubuntuforums.org/showthread.php?t=919472"). I went into konsole and ran 'make uninstall' from there. Are there any additional parameters I'm supposed to use? If pkgs 'snort' and 'snort-mysql' were retrieved via apt-get, does apt have its own remove command I can use?

---

### Post by Michael.Godawski on 2008-11-23
usually it's

```
sudo apt-get remove xxx
```

---

