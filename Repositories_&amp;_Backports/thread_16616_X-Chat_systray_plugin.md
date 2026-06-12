---
title: "X-Chat systray plugin?"
date: 2005-02-22
forum: Repositories &amp; Backports
---

### Post by andrewski on 2005-02-22
What is the best way to get the X-Chat systray plugin installed?  I came from Gentoo, which had it in its repository alongside X-Chat, but there is no such package in any of the Ubuntu repositories (I have multiverse and universe enabled also).  Any tips?

---

### Post by kassetra on 2005-02-22
[QUOTE=andrewski]What is the best way to get the X-Chat systray plugin installed? I came from Gentoo, which had it in its repository alongside X-Chat, but there is no such package in any of the Ubuntu repositories (I have multiverse and universe enabled also). Any tips?[/QUOTE]

Is it in the hoary repositories or the backports?

---

### Post by scoon on 2005-02-22
Hey there, 

You can get more info about it here: [http://www.blight.tk/](http://www.blight.tk/)


scoon

---

### Post by andrewski on 2005-02-22
I know where I can find the plugin; my question is whether or not I should expect to install it with an Ubuntu package or not since one is not available.

---

### Post by scoon on 2005-02-22
Hey there, 

Since a deb is not available, install it locally. 


scoon

---

### Post by dejitarob on 2005-03-17
There's a deb [http://prdownloads.sourceforge.net/xchat2-plugins/xchat-systray-integration_2.4.5-2_i386.deb?download](http://prdownloads.sourceforge.net/xchat2-plugins/xchat-systray-integration_2.4.5-2_i386.deb?download) and also a patch to blink on channel message [http://bombersman.com/xchat/systray-2.4.5-modified.tar.gz](http://bombersman.com/xchat/systray-2.4.5-modified.tar.gz)

---

### Post by haller on 2005-11-17
hi,
i had problems with the .deb on [http://www.blight.tk/](http://www.blight.tk/). so icons and stuff.

but there is a "xchat-systray" package in universe (breezy).

i just installed it...
and it works fine.

ubuntu ist supercool :KS

---

### Post by MemoryDump on 2005-11-17
[QUOTE=haller]hi,
i had problems with the .deb on [http://www.blight.tk/](http://www.blight.tk/). so icons and stuff.

but there is a "xchat-systray" package in universe (breezy).

i just installed it...
and it works fine.

ubuntu ist supercool :KS[/QUOTE]

this worked like a charm for me on breezy!
thxs
-MD

---

### Post by MemoryDump on 2005-11-17
ok.. so I know it's installed 
"SysTray Integration Plugin Version 2.4.5 successfully loaded"
however how is it used? (first timer here) when I click the X/close in the main X-Chat window shouldn't it still keep on running in the background? Like gaim does for example..
thxs
-MD

---

### Post by bored2k on 2005-11-17
Not quite. If you want to remove X-Chat from the windowlist you double click on the tray Icon. Also, when you receive highlighted messages or DCC requests the icon will blink in a very nice. As an extra, you can configure application shortcuts to it, but that's not really useful.

---

