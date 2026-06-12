---
title: "Can't bind a key to &quot;lock screen&quot; command"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by nLpPyXR on 2013-11-07
So I followed the instructions on [https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#I_want_to_bind_a_key_to_lock_my_screen.2C_how_do_I_do_it.3F](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#I_want_to_bind_a_key_to_lock_my_screen.2C_how_do_I_do_it.3F) which is to say, I copied and pasted the codes into LXTerminal and the Leafpad .conf file that popped out.

However, pressing the Win-key + L after saving the config file is not doing what it should. Could it be that I accidentally removed xscreensaver when I purged the XFCE4-Power-Manager package?

EDIT: sorry, forgot to mention I'm on Lubuntu 13.10

---

### Post by walterorlin on 2013-11-09
That documentation is out of date. Lubuntu 13.10 remobvd the xscreensaver package. Have you tried installing the xscreensaver with sudo apt-get update && apt-get install xscreensaver.

---

### Post by nLpPyXR on 2013-11-09
It's already installed, though for whatever reason I still can't bind a key to the lock-screen command.

---

### Post by vasa1 on 2013-11-09
I'm not sure what exactly it is you're trying to do ... 
> and the Leafpad .conf file that popped out.
I've never had that happen. What exactly did you do? Could you post the steps here?

My understanding is that binding keys in Lubuntu is currently done (painfully) by *carefully* editing **~/.config/openbox/lubuntu-rc.xml**.
For an overview of this most important  and useful file, please read at [http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) even though it's a bit old and isn't written for Lubuntu *per se*.

---

### Post by nLpPyXR on 2013-11-09
> **vasa1 said:**
> I'm not sure what exactly it is you're trying to do ... 

I've never had that happen. What exactly did you do? Could you post the steps here?

From help.ubuntu.com:

```
I want to bind a key to lock my screen, how do I do it?

In LXTerminal: 

[CODE]leafpad ~/.config/openbox/lubuntu-rc.xml
```
Locate the <keyboard> section and add following lines. 

```
<keybind key="W-l">
<action name="Execute">
<startupnotify>
<enabled>true</enabled>
<name>Xscreensaver Lock</name>
</startupnotify>
<command>xscreensaver-command -lock</command>
</action>
</keybind>
```

And now Windows (Super-Key) + L  should lock the screen.[/CODE]

---

### Post by vasa1 on 2013-11-10
There seems to be some confusion about xscreensaver/screen locking in Lubuntu 13.10 :(

See these bugs:
[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1202908](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1202908)
[https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1204052](https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1204052)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1205384](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1205384)

I don't use screen locking and so I hope someone who does comes around.

---

