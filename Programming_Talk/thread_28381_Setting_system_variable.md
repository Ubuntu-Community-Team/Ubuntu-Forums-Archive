---
title: "Setting system variable"
date: 2005-04-19
forum: Programming Talk
---

### Post by defkewl on 2005-04-19
How do I set up new system variable in Ubuntu?

I already wrote it in /etc/profile and /home/*/.bash_profile but the variable didn't came out when I echoed it from the console. I even reboot my computer since changing session didn't even worked when I echoed it.

I wrote this variable:
JAVA_HOME="/usr/local/jdk1.5.0_01"
PATH="$PATH:$JAVA_HOME/bin"

It worked on other distro but it didn't work on my Hoary?

Anybody could help me on this?

Thnx in advance.

---

### Post by heimo on 2005-04-19
Try putting  *export* in front of those lines. It's actually more shell feature than distribution specific.

---

### Post by TravisNewman on 2005-04-20
yes, you need export in front of those lines. I'm not sure I've used a distribution that worked differently.

---

### Post by defkewl on 2005-04-20
I've got it now guys.

Actually in Ubuntu it is writeen in /etc/bash.bash_profile

Hopefully this is useful for those facing the same problem with me ;)

---

