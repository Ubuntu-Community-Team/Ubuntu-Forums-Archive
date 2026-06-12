---
title: "Problem connecting to home internet"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by caiyo on 2011-09-20
Hi all,

I got a new netbook and installed ubuntu on it last week, and everything has been working fine until yesterday. Yesterday i was watching a youtube video when my computer froze. I  couldnt figure out for a while what was causing it to continuously freeze when rebooting and logging into my account, but i realized that it froze whenever i tried to connect to my home internet. But the thing is, its only does that when connecting to my home internet. when i connect to wifi at work or at school, there is no problem, but at home, my computer freezes and if i want to do anything on it, i have to run it in safe mode or turn the wifi switch off. 

I have no idea why this is happening, the only thing i could possibly think of is that me hooking up a new modem/router might have caused some problems, but my other laptop works fine(not running ubuntu). Has anyone heard of a similar problem happening before and/or know how to fix it? it would be greatly appreciated. Thanks!!

---

### Post by ipadm on 2011-09-20
I can't help you, but can suggest how to get helped here. 

1. Open terminal and type: ```
lshw
```
2. Post results here.

3. In terminal and type: lspci
4. Post results here.

5. In terminal and type: lsb_release -a
6. Post results here.


P.S.: It is possible your WiFi driver is guilty. I had some times frizzes using firmware driver of WiFi.

---

