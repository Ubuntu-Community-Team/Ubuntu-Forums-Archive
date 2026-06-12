---
title: "HOWTO Get rid of those annoying &quot;Use 'setkeycodes e02a &lt;keycode&gt;&quot; messages"
date: 2006-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-01-19
The best solution seems to be in the  [Wiki]("https://wiki.ubuntu.com/'setkeycodes_e02a_%3ckeycode%3e'_issue?highlight=% 28e02a%29") (21-3-2006: Not any more, some fool has deleted it!)

There are a lot of complaints of copious dmesg output resembling this:

[4314715.415000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4314715.415000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

On some machines, this keycode triggers a hibernate event and is therefore disabled. On other machines e02a is an arrow key and this just causes a mess in dmesg. To quiet these error messages, remove the line from /usr/share/hotkey-setup/generic.hk that reads

setkeycodes e02a 256

and run

sudo /etc/init.d/hotkey-setup restart

and your dmesg should stop filling up with these messages.

---

