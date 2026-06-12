---
title: "how to install chinese input/skim?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by oliviacond on 2008-08-14
i'm using kubuntu kde 4, I'm trying to install skim/scim.
I installed smart pinyin, but i can't use it, can't switch to smart pinyin.
can somebody shows me the proper way to set up the skim for kde 4?

---

### Post by Pro-reason on 2008-08-15
Have you seen this guide: [https://help.ubuntu.com/community/SCIM/Kubuntu](https://help.ubuntu.com/community/SCIM/Kubuntu) ?

---

### Post by oliviacond on 2008-08-15
nothing happens when I press control-space / shift-space

---

### Post by Pro-reason on 2008-08-16
> **oliviacond said:**
> nothing happens when I press control-space / shift-space

When you log in, you should see a SCIM applet floating around on the right. If it's not there, then it's not set up properly.  Have you tried with both Qt and Gtk apps?  You should set SCIM up for both.

Here is my */etc/X11/xinit/xinput.d/scim-bridge* file.  Yours should be similar.

```

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=xim
fi

if   [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge-kde4
elif [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=xim
fi

DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4"


```

Here is another guide with more info:
[http://ubuntuforums.org/showthread.php?t=396135](http://ubuntuforums.org/showthread.php?t=396135)

---

