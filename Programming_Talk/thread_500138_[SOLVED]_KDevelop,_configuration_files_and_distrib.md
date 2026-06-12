---
title: "[SOLVED] KDevelop, configuration files and distributing"
date: 2007-07-13
forum: Programming Talk
---

### Post by juice_fi on 2007-07-13
I've made an application which has a database file and a configuration file. Usually configuration files will be in /etc/application/ directory and db files in /usr/share/application/ diretory. How can I specify that "make install" installs these files into those directories?

---

### Post by juice_fi on 2007-07-13
Err... my stupidity is simply overflowing. I can't imagine I spent days pondering this... of course the best way to do this would be creating them on the fly during the first startup. I figured this out just before I fell asleep last night :)

---

