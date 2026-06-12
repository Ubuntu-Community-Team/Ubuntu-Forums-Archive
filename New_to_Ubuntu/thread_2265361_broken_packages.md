---
title: "broken packages"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by newblank25 on 2015-02-14
I was using update manager I got this message Error occurred, please run package manager from right click menu or apt-get in terminal to see what is wrong. The message was 'error:broken Count >0' this usually means packages have unmet dependencies. So I went to terminal & typed i apt-get which gave commands to remove packages but didn't show me the names of them. How can I fix this problem?

---

### Post by Bashing-om on 2015-02-14
newblank25; Hi !

There is a lot about package management I do not know, but I will start this ball rolling.
Post back the complete outputs - Between Code Tags, please - of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

To get an idea of what the package manager thinks, and where to go to from here.

It is a process ->
[INDENT][INDENT][INDENT]only does what it is told to do ( when possible)
[/INDENT][/INDENT][/INDENT]

---

