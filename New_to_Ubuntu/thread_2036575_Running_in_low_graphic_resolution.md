---
title: "Running in low graphic resolution"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by hugobife on 2012-08-02
Help!!!
My computer will not boot 12.04.
I get a dialog saying "running in Low graphic resolution and asks me to reconfigure the graphic card
I have tried to boot in recovery mode and tried the advice of other forum treads to no avail. I enable networking but am not sure if I am on the internet as when I try a get-apt command it always says "unable to connect". Also I get a line that says something like "unable to write /var"
I am using a HP compaq nc63200 with a mobile Intel 945 express chipset family graphic card.
I have a duel boot and the windows works fine
Any help much appreciated
hugh

---

### Post by techvish81 on 2012-08-02
the command should be " sudo apt-get. ...."  and you can try to connect to a hotspot using wifi,  if you have connected it before with the same system,  it may connect automatically.

or you will have to use. "sudo pppoeconf" command to give your ethernet settings and then connect to it. 

see the link below.


[https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")

---

