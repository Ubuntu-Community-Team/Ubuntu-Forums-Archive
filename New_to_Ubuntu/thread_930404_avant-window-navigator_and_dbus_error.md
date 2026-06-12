---
title: "avant-window-navigator and dbus error"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-09-26
I installed Ubuntu then replaced gnome with Xfce 
then i installed avant-window-navigator via apt-get
when i run it from the command prompt i get this error and it fails to run
```
joe@lappy:~$ avant-window-navigator 

** (avant-window-navigator:6742): WARNING **: Failed to make connection to session bus: Failed to connect to socket /tmp/dbus-gPUiDwE3xZ: Connection refused

** (avant-window-navigator:6742): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:6742): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:6742): WARNING **: There was an error requesting the name: (null)

** (avant-window-navigator:6742): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed
Screen is composited.
Segmentation fault
joe@lappy:~$ 

```

when i run it with sudo it runs fine 

So this leads me to believe that it is just a permission error.
However i know nothing about Dbus to be able to fix this
I google it, I found same error but they had dependences missing that kept it from running. So they only needed to install them and it worked. I am fairly curtain i have all of them.

I don't wanna run it as root because thats bad ... security hole any one?

thank for your help
sorry about the spelling though think I did ok this time

p.s. will see if the error is duplicated on my desktop, it is running plan ubuntu. So i can see if it is something with the Xfce environment

---

### Post by vikramaditya on 2008-09-26
have you tried adding awn in system/preferences/sessions?

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-09-26
> **vikramaditya said:**
> have you tried adding awn in system/preferences/sessions?

hum I am very new to Xfce(though not ubuntu) and don't know exactly were to look for system/preferences/sessions
when right click on the desktop it gives me a menu and it has system in it but there is not a preference tab in there

if you could check the launcher and see what command it runs i will just run that in the terminal

also i just installed it on my desktop it runs fine with out a hitch even the drag and drop of launchers works so ether its Xfce or i broke my install or miss configured some thing ... :/

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-09-26
bum

---

