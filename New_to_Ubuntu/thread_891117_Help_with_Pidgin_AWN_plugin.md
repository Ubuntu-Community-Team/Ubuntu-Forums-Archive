---
title: "Help with Pidgin AWN plugin"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by GorCh on 2008-08-15
Hi there,

I am trying to install the AWN plugin for Pidgin as found here[http://awn.wetpaint.com/page/Pidgin+Plugin?t=anon]("http://awn.wetpaint.com/page/Pidgin+Plugin?t=anon")

I have unzipped and copied to ~/.purple/plugins, restarted pidgin, gone to plugins - not there.

I noticed that the other plugins were in /usr/lib/pidgin, so tried copying it there as well. Went fine (with sudo cp), but still no plugin in the plugin menu.

One thing I noticed is that the .so file in /usr/lib/pidgin does not appear to be executable, or at least is blanked out. Is this likely to be the problem? How can I change this?

Cheers,

GorCh

---

### Post by SZ07 on 2008-08-16
I'm pretty sure what you have downloaded is the source and the reason its not working is because you have not compiled it.

Anyway, I got the pidgin plugin to work by following this guide when I first installed hardy heron. It might be a bit outdated but it should still work. Scroll down to the "Tips" section for the how to.

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

---

### Post by GorCh on 2008-08-16
Thanks for that but still no joy. I've tried both - from source and the direct .so file. Still same problem, the plugin doesn't appear in the Plugins menu.

Thanks for the help though. Anyone else had this problem?

---

### Post by SZ07 on 2008-08-16
These are stupid questions but just to rule out the obvious:

Did you try restarting pidgin and awn (or your computer) after moving pidgin_awn.so to /.purple/plugins?

Are you looking in the Pidgin plugin menu and not the awn applet menu?

You did add a shortcut of Pidgin to awn before adding the plugin, right?

On a different note, what version of pidgin are you using?

---

### Post by GorCh on 2008-08-16
Yea, shortcut>> copy>> close all>> open. And definitely pidgin plugins menu. I am using pidgin 2.4.1.

Seems strange, but I can cope if it randomly doesn't work. Thanks for the help.

---

### Post by SZ07 on 2008-08-16
Well, it seems like you did everything right. I'm out of ideas. Anyone else want to try?

---

