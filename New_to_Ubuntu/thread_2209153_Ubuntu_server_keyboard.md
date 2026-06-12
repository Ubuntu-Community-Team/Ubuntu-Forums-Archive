---
title: "Ubuntu server keyboard"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by ilqar on 2014-03-04
Hi! I am new in Ubuntu and I have problem with keyboard. I cann't type key "~" from left top corner of keyboard but from disabled numeric keyboard 3 (?). Also I cann't type "<" and ">" and I cann't find these keys.  Ubuntu server version 10.04.3 LTS (lucid).
i tried 
cat /etc/default/locale, it gave me "en_GB.UTF-8".

---

### Post by ilqar on 2014-03-04
help please

---

### Post by grahammechanical on 2014-03-04
What keyboard layout did you select when you installed Ubuntu? You need to find a keyboard layout that matches the actual layout of keys on your keyboard. There are two things that will effect the layout of the keys, the language and the type of keyboard that we told the Installer we was using. For example, I chose UK, extended Winkeys to describe my keyboard. It places the tilde ( ~ ) character in a different position to where it is on your keyboard. Different placings would happen if I selected US, extended Winkeys.

Not much help but you are the only person who knows what you chose as a description for you keyboard. And I am not familiar with 10.04 either desktop or server.

Regards.

---

### Post by Lars Noodén on 2014-03-04
I used to always use the US keyboard layout on servers.  Even on international teams that was kind of the agreed on default.   Nowadays, if I can find | and < and > and ~ then I'm set, as long as the rest of the layout is reasonably QWERTY-like.  So missing those keys would be a big deal for me, too.

But to change the layout used in the console try [dpkg-reconfigure](http://manpages.ubuntu.com/manpages/saucy/en/man8/dpkg-reconfigure.8.html)

```

sudo dpkg-reconfigure keyboard-configuration

```

You can use tab-completion to spell all that out rather that type it all.

---

### Post by whitesmith on 2014-03-04
Compose key sequences are another possibility, albeit something of a PITA (see [http://hermit.org/Linux/ComposeKeys.html](http://hermit.org/Linux/ComposeKeys.html)).

---

