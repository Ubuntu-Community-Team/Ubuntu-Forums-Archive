---
title: "Keyboard"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by hcapeleiro on 2008-08-08
I have an HP Pavillion DV6880 with american keyboard. After installing ubuntu, when I press the cedilla the outcome is "&#263;&#263;&#263;&#263;&#263;&#263;&#263;&#263;&#263;" and not "çççç" as expected. My keyboard is configured like this:

 US INTL. setxkbmap -model pc105 -layout us -variant intl.

any ideas how to solve this?

---

### Post by hcapeleiro on 2008-08-08
Keyboard
I have an HP Pavillion DV6880 with american keyboard. After installing ubuntu, when I press the cedilla the outcome is "&#263;&#263;&#263;&#263;&#263;&#263;&#263;&#263;&#263;" and not "çççç" as expected. My keyboard is configured like this:

US INTL. setxkbmap -model pc105 -layout us -variant intl.

any ideas how to solve this?

---

### Post by ebalter on 2008-08-17
> **hcapeleiro said:**
> Keyboard
I have an HP Pavillion DV6880 with american keyboard. After installing ubuntu, when I press the cedilla the outcome is "&#263;&#263;&#263;&#263;&#263;&#263;&#263;&#263;&#263;" and not "çççç" as expected. My keyboard is configured like this:

US INTL. setxkbmap -model pc105 -layout us -variant intl.

any ideas how to solve this?
From post [http://ubuntuforums.org/showthread.php?t=594736&highlight=cedilla](http://ubuntuforums.org/showthread.php?t=594736&highlight=cedilla)

Edit /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules

Adding 'en' at the end of cedilla line will make the ' + c = ç!!!

---

### Post by billgoldberg on 2008-08-17
in a terminal use

```
setxkbmap us
```

or in xorg set it to us

```
sudo gedit /etc/X11/xorg.conf
```

One of the lines in the beginning of the document should mention something like "keyboard layout".

Set it to 

"us"

---

### Post by ivainsencher on 2009-01-07
> **ebalter said:**
> From post [http://ubuntuforums.org/showthread.php?t=594736&highlight=cedilla](http://ubuntuforums.org/showthread.php?t=594736&highlight=cedilla)

Edit /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules

Adding 'en' at the end of cedilla line will make the ' + c = ç!!!
mysteriously, it works everywhere ççç except in emacs, where I get (as of today) an acute over c.
however, Alt+, gives ç.
annoying!

---

