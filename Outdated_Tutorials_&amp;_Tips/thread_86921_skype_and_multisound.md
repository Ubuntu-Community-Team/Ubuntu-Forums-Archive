---
title: "skype and multisound"
date: 2005-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by eraclito on 2005-11-06
Hi,

can you use skype when you are listening music from your ubuntu?
If not (and you want it) try to follow this little howto:

1 install skype
1.1 add a new line in your source.list
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
(more info [here]("http://www.ubuntuforums.org/showthread.php?t=79449"))

1.2 then you can install skype with synaptic (or apt-get)

2 install "esound-clients" (always from synaptic)

3 try to use it
from a terminal type
```

esddsp skype 
```

if it works, change the skype's launch icon from "skype" to "esddsp skype"

4 skype use qt library, so, if it is looks ugly follow this howto:
 [HOWTO: Make QT apps look more Gnome'ish]("http://www.ubuntuforums.org/showthread.php?t=76633")


5 now listen music and talk  with you girlfriend (if you can manage both in the same time) :D 


note: it's work only in gnome, if you use kde you probably have to type "artsdsp skype" but i never try it

---

### Post by shekhark on 2005-11-06
This doesn't work. I wish it did! Skype says it has a problem with the sound device when I try to place a call after downloading your skype package and installing esound-clients.

---

### Post by eraclito on 2005-11-07
[QUOTE=shekhar@crit.org.in]This doesn't work. I wish it did! Skype says it has a problem with the sound device when I try to place a call after downloading your skype package and installing esound-clients.[/QUOTE]

mmm check if esound daemon is running... try 
```
 esd -d /dev/dsp 
```

or ```
sudo fuser -v /dev/dsp
``` to control if any application is using your audio card...

---

### Post by lonetree on 2005-11-10
I still can't install skype after adding the sources.list

when I try to apt-get install skype, it gives me the error message

The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
E: Broken packages

How do I solve this issue?

regards,

---

### Post by BetaguyGZT on 2005-11-22
[Check here.]("http://packages.debian.org/stable/libs/libqt3c102-mt")

That should fix you up. Straight from Debian.org.

I haven't tried this yet tho...just did a Google search and there it was.

---

### Post by littlepr on 2005-11-22
Use this for installing skype and other goodies:

[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Arnieboy](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Arnieboy)

And for multi-sound try this:

[http://www.ubuntuforums.org/showthread.php?t=8882&highlight=install+alsa-oss](http://www.ubuntuforums.org/showthread.php?t=8882&highlight=install+alsa-oss)

---

### Post by lonetree on 2005-11-22
thanks guys. will try that later

:-)
cheers

---

