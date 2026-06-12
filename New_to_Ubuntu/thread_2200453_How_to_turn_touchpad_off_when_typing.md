---
title: "How to turn touchpad off when typing?"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by tmcclelland472 on 2014-01-19
So I have Xubuntu 12.04 installed on my mom's netbook. Whenever you type on it, you move the cursor, and usually end up messing something up. I was wondering how to turn the touchpad off when you type. [SIZE=2]**[COLOR=#ff0000]The one that comes built in is terrible (have to wait a good 3 seconds after you stop typing to do anything again with the cursor). Therefore, I need something else.[/COLOR]**[/SIZE]

---

### Post by codemaniac on 2014-01-19
There should be an option in your touchpad configuration and management tool that lets you configure the time to wait before switching the touchpad again. 

Not in a xubuntu box at the moment, I am using synaptiks which is a kde tool for touchpad management. 
[ATTACH=CONFIG]249587[/ATTACH]

---

### Post by Dave_L on 2014-01-19
If codemaniac's solution doesn't help in this case, here's another approach:

[http://ubuntuforums.org/showthread.php?t=2192864&p=12870711#post12870711](http://ubuntuforums.org/showthread.php?t=2192864&p=12870711#post12870711)

---

### Post by bertan2 on 2014-01-19
It varies from manufacturer to manufacturer. On the Acer Aspire, it's Fn + F7.

---

### Post by fosterD on 2014-01-19
Or you can set syndaemon to disable the touchpad while you are typing
```
syndaemon -i 3 -d -t -K
```
where '3' is the number of seconds to wait

---

### Post by tmcclelland472 on 2014-02-12
Sorry that I just got back to this, but thanks guys!

---

### Post by gaseabra on 2014-02-17
> **tmcclelland472 said:**
> Sorry that I just got back to this, but thanks guys!

Hello. If you are still struggling with this, that would solve the problem:

sudo modprobe -r psmouse

In case you need to disable touchpad for good, you need to create a script for it.

---

