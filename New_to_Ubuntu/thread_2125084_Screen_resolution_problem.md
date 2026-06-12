---
title: "Screen resolution problem"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by BXRBuddha on 2013-03-12
Hi all,

Trying to fix my screen resolution was following the tutorial given here.
[https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens](https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens)
Was trying to edit using the terminal (GUI wasn't saving changes). When I typed 

sudo service lxdm stop

into it, it kept returning 

lxdm: unrecognized service

(Can someone also explain how to type code into a forum post properly)

Thanks

---

### Post by quickk on 2013-03-12
Hi BXRBuddha, 

    Probably you have another display manager installed.   Try 

```
sudo service lightdm stop
```

or maybe 

```
sudo service gdm stop
```

To type code into the forum posts, hit the # button, or use the enclose your code in [ CODE][ /CODE] tags (without any spaces between after the square braces: [CO.. and not [ CO...)

---

### Post by BXRBuddha on 2013-03-13
Thanks a lot quickk!

---

