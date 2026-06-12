---
title: "Evolution mail disappeared"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by jrlii on 2011-10-18
I just upgraded from Ubuntu 11.04 to 11.10.

Five years of e-mails in Evolution and several folders seem to be just gone!

It's not *really* critical but it's annoying.

Anything else?. . . I upgraded using the distribution update tool.

---

### Post by dFlyer on 2011-10-18
Did you backup before you upgrade? The the mail client is now thunderbird. Not sure if it's recoverable or not. Hopefully you did a backup.

---

### Post by jrlii on 2011-10-18
Not for a while. I've been using Ubuntu for years and never had a problem with an upgrade. I guess it lulled me into a false sense of security.

---

### Post by dFlyer on 2011-10-18
Before you give up hope have you done a search of your home folder for evolution. Hopefully it's still there under .config or somewhere else.

---

### Post by lovinglinux on 2011-10-18
Most likely they are still there. Just install Evolution to browse them.

To migrate your mail from Evolution to Thunderbird, see these:

[http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04](http://maketecheasier.com/how-to-migrate-from-evolution-to-thunderbird-in-ubuntu-intrepid/2008/12/04)

[http://linuxnorth.wordpress.com/2011/01/21/moving-on-to-thunderbird/](http://linuxnorth.wordpress.com/2011/01/21/moving-on-to-thunderbird/)

---

### Post by jrlii on 2011-10-18
Evolution did not go away in the upgrade: The little envelope pull down shows both Evolution & Thunderbird. Thunderbird still shows the mail which was in it before I transitioned my e-mail to Evolution ('cause I upgraded Thunderbird to a new version, and fell foul of a bug which had been on the bug reporting site for a couple years.)

My last backup of mail was this July, so I guess if I have to, I can restore it and lose only a few months of mail. . . but getting it all back would be better.

---

### Post by JKyleOKC on 2011-10-18
In a terminal window, try "ls ~/.local/share/evolution" to see if your mail is there. That worked for another situation not so very different from yours...

---

