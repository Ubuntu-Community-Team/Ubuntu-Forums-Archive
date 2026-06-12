---
title: "scripting help"
date: 2016-12-02
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-12-02
running lubuntu 16.10.  i put this script in .config autostart
#!/bin/bash
xset s off && xset -dpms && exit
 
will not autostart but if i run it in the terminal ./88(name) after i am logged in it works.
any ideas/tks

---

### Post by papibe on 2016-12-02
Hi rburkartjo.

I believe you only can put only .desktop scripts there (read answer 9 [here]("http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up")).

Another alternative, is to create the script using 'Startup Applications'. Add a script, and in the command field paste this:
```
sh -c 'xset s off && xset -dpms'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by rburkartjo on 2016-12-04
tks pap will give it a try and let you know the results

---

### Post by rburkartjo on 2016-12-08
pap tks that did the trick

---

