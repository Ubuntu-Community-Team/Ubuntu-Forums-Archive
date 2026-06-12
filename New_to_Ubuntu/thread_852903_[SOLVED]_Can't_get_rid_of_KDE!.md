---
title: "[SOLVED] Can't get rid of KDE!"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Patricrawley on 2008-07-08
I installed KDE to see what it was like, but I didn't like it so I logged out and changed to a gnome session and set it to default. Then I removed all of the KDE stuff in synaptic, but kio-unmounter won't uninstall and I get this error:
```
E: kio-umountwrapper: subprocess post-removal script returned error exit status 2
```

 Now, when I start up the PC, it says kubuntu is loading (I installed ubuntu) and it makes me go into a text login because KDE isn't there and I have to sudo gdm  to get ubuntu running. How do I fix this?

---

### Post by lisati on 2008-07-08
```
sudo install ubuntu-desktop
```

---

### Post by Patricrawley on 2008-07-08
Ok will this just make it default again? It wont double my files right?

---

### Post by lisati on 2008-07-08
As far as I know it won't double your files......

---

### Post by bigken on 2008-07-08
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Patricrawley on 2008-07-08
Ok, so I had to put aptitude in front of it, but when it ran it still didn't get rid of kio-umountwrapper but it did get rid of a whole bunch of other stuff that it wanted to before but kio-unmountwrapper wouldn't let happen.

---

### Post by Patricrawley on 2008-07-08
I went to the website and I ran both code for kubuntu and it still would not remove kio-unmountwrapper

---

### Post by bigken on 2008-07-08
read the whole page and use the second option to remove kde

---

### Post by bigken on 2008-07-08
here you go found this 

[https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729)

---

### Post by Patricrawley on 2008-07-08
Thanks, all of that worked for getting rid of kio-unmountwrapper and getting the ubuntu lauch back.

However, it still says no kinit reboot image and I have to text login and sudo gdm still. How do I get the gui back?

---

### Post by bigken on 2008-07-08
sudo apt-get install ubuntu-desktop

give that a try

---

### Post by bigken on 2008-07-08
also found this 

[http://ubuntuforums.org/showthread.php?t=713959](http://ubuntuforums.org/showthread.php?t=713959)

---

### Post by Patricrawley on 2008-07-08
Thanks, I have everything back to normal now, I have no KDE stuff anymore, minimal programs in gnome and the login gui is back. Thanks for your help!

---

