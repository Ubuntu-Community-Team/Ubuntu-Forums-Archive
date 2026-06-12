---
title: "How to fix Broken packages"
date: 2016-08-17
forum: New to Ubuntu
---

### Post by estherlv93 on 2016-08-17
Hi! I am very new to coding and solving problems in Ubuntu, but have used it in the past as a personal computer. Recently I tried updating the software, but an error happened and had to reset one step back from terminal, since that I can install any updates or new software, a message that says there are broken packages appears, I tried running *sudo apt-get update *and *sudo apt-f *but nothing worked.
Thank you for your help

---

### Post by Bashing-om on 2016-08-17
estherlv93;Hello' Welcome to the forum .

Show us what you see from terminal commands:
```

sudp apt update
sudo apt upgrade

```
place these outputs between between code tags ; maintains formatting and promotes the readability:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We look at the error in context,

[INDENT][INDENT]see to know where to go
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-08-18
The command to fix broken packages is not sudo apt-f but

```
sudo apt-get -f install
```

I do think that if we have Ubuntu 16.04 then this command would also do the job but I have not tested it.

```
sudo apt -f install
```

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards

---

