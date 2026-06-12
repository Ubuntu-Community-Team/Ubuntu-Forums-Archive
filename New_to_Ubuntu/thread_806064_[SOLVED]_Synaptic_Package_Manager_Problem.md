---
title: "[SOLVED] Synaptic Package Manager Problem"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by magwhyte on 2008-05-24
I have screwed up!  I was following the instructions on [http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron](http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron) to include some extra repos.

Now when I try to open the Synaptic Package Manager I get the following Error Message.  Then Synaptic closes itself down.

"E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

Please help.

Adrian

---

### Post by forestpixie on 2008-05-24
Open a terminal and do

```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```

Then do these one at a time
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by forestpixie on 2008-05-24
Been to look at the site you linked to - it's out of date - if you didn't look at the comments at the bottom you wouldn't know, if course if you were new it wouldn't make a lot of sense either :)

---

### Post by magwhyte on 2008-05-24
It WORKED!

Many thanks.  I thought for a few moments I would have to reinstall.

Many thanks...

Adrian

---

### Post by forestpixie on 2008-05-24
Glad it helped - it might in future be worth googling the error message - it's quite a frequent error that one :)

Could you mark thread solved please

---

### Post by Matt640 on 2008-05-24
Re: Synaptic Problem!
Hey.
I'm sorta having the same problem here only the cause was something different. I'm using the ordinary Desktop Edition of Ubuntu 8.04 not the 64AMD one. So I read from the Forums that by installing Sun Java 6, I can get my FrostWire up and running again. So I use my SPM to find it and download it. In the middle of Download/Installing, it hanged/jammed and my only option was to reboot. After I did, I realize that I can't open my SPM and it ask me to manually run sudo dpkg --configure -a. When I do, this turns up:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

As you can see, I'm in desperate need of HELP! Can anyone encrypt this for me?

---

