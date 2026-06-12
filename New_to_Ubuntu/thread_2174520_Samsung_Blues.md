---
title: "Samsung Blues"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by dyers2 on 2013-09-14
When I first installed my printer, Ubuntu found it, and installed drivers for it in no time. I can even print to a degree, but printing is not consistent. Sometimes, it prints rightly, but other times, it prints one line of uninteligible symbols, and characters, and does the same on the next several pages until I abort the operation. Google ferreted wisdom suggests that I use Samsung drivers, and their website makes downloading them very convenient; I downloaded their Universal Print Driver, a tar.gz archive. I used Synaptic to unpack it to /home/user where it created a new directory called cdroot which contains a folder called Linux, which in turn contains the file install.sh  Then, 

> ~/cdroot/Linux$ [COLOR=#0000ff]sudo sh install.sh[/COLOR]
(guiinstall:10896): IBUS-WARNING **: The owner of /home/dave/.config/ibus/bus is not root!
(process:13808): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
~/cdroot/Linux$ [COLOR=#0000ff]cd /home/dave/.config/ibus[/COLOR]
~/.config/ibus$ [COLOR=#0000cd]sudo chown root ~/.config/ibus/bus[/COLOR]
[sudo] password for dave: 
~/.config/ibus$ [COLOR=#0000ff]sudo sh install.sh[/COLOR]
sh: 0: Can't open install.sh
~/.config/ibus$

The file bus is now owned by root as it seems that it should be.  I also tried using the printer wizard - twice - and now have 3 incidents of this printer, all with drivers other than those I downloaded. My question is to know how best to get these Samsung drivers installed. If you can offer any suggestions, or directions, I'll be pleased to hear from you.

[SIZE=4]&#9774;[/SIZE]  Dave

---

### Post by dyers2 on 2013-09-16
I thought I'd put this out there again in hopes that someone who knows more than I do can offer a hand.

[SIZE=4]&#9774;[/SIZE]  Dave

---

