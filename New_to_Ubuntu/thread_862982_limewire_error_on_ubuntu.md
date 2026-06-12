---
title: "limewire error on ubuntu"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-07-18
i'm getting an error when i try to install limewire on the terminal:

edwin2105z@edwin2105z-desktop:~$ sudo apt-get install limewire
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package limewire
edwin2105z@edwin2105z-desktop:~$

limewire is already installed but it tells me couldnt find package limewire

---

### Post by SunnyRabbiera on 2008-07-18
limewire isnt that great anyhow, try frostwire:
[http://www.frostwire.com/](http://www.frostwire.com/)
it works just the same.

---

### Post by edwin2105z on 2008-07-18
installed frostwire but also doesnt work thats why i think its something in ubuntu. any suggestions

---

### Post by SunnyRabbiera on 2008-07-18
possibly... it might be java as both frostwire and limewire need java...
now there is a version of java preinstalled with ubuntu but its not all that great.
remove openjdk for starters via synaptic, enable the multiverse repositories and install regular java...
If you need instructions I can give them to you.

---

### Post by tinny on 2008-07-18
Limewire is just one of many gnutella client applications (gnutella is the p2p network that these apps talk too).

The "default" application on Ubuntu for gnutella p2p is gtk-gnutella.

Doing a search for "gnutella" from "Add / Remove applications" will give you the option to install gtk-gnutella.

Done :) Didnt even need the command line and it doesnt require java.

BTW: To test what your default java is...

```

java -version

```

I would recommend you use the Sun Java version

```

sudo apt-get install sun-java6*

```

---

### Post by hopelessone on 2008-07-18
amule is the best...

---

### Post by lisati on 2008-07-18
As far as I can make out, frostwire and limewire are pretty much the same application, but with different skins. You should be able to download Linux-friendly versions from their  web sites....

---

### Post by Canis familiaris on 2008-07-18
> **lisati said:**
> As far as I can make out, frostwire and limewire are pretty much the same application, but with different skins. You should be able to download Linux-friendly versions from their  web sites....
Frostwire claims to have all features of Limewire Pro for free.

---

### Post by tinny on 2008-07-18
> **hopelessone said:**
> amule is the best...

Yes it is!!!

"Add / Remove applications" search for "amule"

Still no command line :)

---

### Post by Leed on 2008-07-18
Just get Limewire from the website... however due to bad HMTL coding, the site doesn't work properly with firefox, as a result the download function on the Limewire.com page doesn't work...

but you still get it using the following address

[http://www.limewire.com/LimeWireSoftLinuxDeb]("http://www.limewire.com/LimeWireSoftLinuxDeb")

---

### Post by |{urse on 2008-07-18
Installing viruses on windows with limewire was more fun, on linux this crappy java program isn't as entertaining.

---

