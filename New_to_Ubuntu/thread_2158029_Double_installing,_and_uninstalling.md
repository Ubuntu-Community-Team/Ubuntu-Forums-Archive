---
title: "Double installing, and uninstalling"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by RangerK on 2013-06-27
I'm about 1 week into using my first Ubuntu box.  I'm sure that I've accidentally installed (through apt-get) the same packages twice.

Are there any negative consequences to this?  It never prompts me, as Windows does, telling me that it's already installed.  Does this install a second instance of the software? or does the second installation overwrite the first?

Secondly, what should I do if I install something that I realize I don't want / need.  Uninstalling seems like quite the chore on Ubuntu.  Is there a good guide for this?

Thanks!

---

### Post by Impavidus on 2013-06-27
No harm done, if you install something a second time it just [s]overwrites the first[/s] (sorry, that was reinstall) says it's there already.

I understand you installed via```
sudo apt-get install <package name>
``` Then you can uninstall via```
sudo apt-get purge <package name>
```To remove any dependencies you no longer need after uninstalling some package you use```
sudo apt-get autoremove
```

---

### Post by grahammechanical on 2013-06-27
May I suggest that you use the Ubuntu Software Centre in future? If an application is not installed the Software Centre will give us an Install button. If the application is installed then the Software Centre will give us a remove button. The software Centre does all the work. That is what it is there for. It will make sure that the application has all the dependencies (libraries) it needs. It will even install for us software we download as deb files.

But we should keep in mind that software listed in the Software Centre has had a code audit to make sure that the code will not mess with the OS or our data. Applications downloaded from a web site do not gives us that security.

Ubuntu is designed to be easy for ordinary users. Being Linux each of us is free to make things hard for ourselves by using the terminal. This is what I get when I just now tried to install a tool called gksu that I had already installed 30 minutes ago:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
_gksu is already the newest version._
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This explains about apt-get

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by newb85 on 2013-06-27
+1
apt-get won't let you install two instances of the same package, unless it has been renamed.

---

### Post by RangerK on 2013-06-28
Thanks, guys.  Great info.

Regarding the software center, I often can't find what I'm looking for there.  I'm sure there's a way to install . . . what are they called? . . . . PPA's?  But I often find ready directions for command-line installations.  So that's why I'm gravitation toward using the console.

---

### Post by Impavidus on 2013-06-28
apt-get from the terminal and the software centre give you the same available software, but they have a completely different way of finding it. You can also try synaptic. I prefer it over both the software centre and the command line. You can install it from the command line with```
sudo apt-get install synaptic
```

---

### Post by newb85 on 2013-06-28
> **RangerK said:**
> Thanks, guys.  Great info.

Regarding the software center, I often can't find what I'm looking for there.  I'm sure there's a way to install . . . what are they called? . . . . PPA's?  But I often find ready directions for command-line installations.  So that's why I'm gravitation toward using the console.

Adding PPAs is a great way to expand your options. Make sure you trust the source. Also, if aPPA is hosted at launchpad.net, you can look the PPA up there and see when recent updates have been made.  (This can give you an idea of how well-maintained it is. )

---

