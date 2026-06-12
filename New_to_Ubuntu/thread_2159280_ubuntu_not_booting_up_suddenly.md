---
title: "ubuntu not booting up suddenly"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by mustafi05 on 2013-07-02
(Ubuntu 12.04 , 64 bit) suddenly after un stalling cairo doc Ubuntu freezes and after that Ubuntu not booting up . its screen  showing a message >>etc/rc. local : 1: /etc/rc.local: can not create /sys/kernel/debug/vgaswitcheroo/switch: directory not existent. how do I recover Ubuntu. please help.

---

### Post by slickymaster on 2013-07-02
See if this can help you: [Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics"). Also you could see this [thread]("http://ubuntuforums.org/showthread.php?t=1873845").

---

### Post by mustafi05 on 2013-07-02
sorry , i can not make out any thing from the documentation or the thread provided by you. I am really an beginner . it will be very much helpful if you assist me step by step . I do not understand the underlined problem actually and thus do not understand how to solve it . thanks for help . please suggest what should I do now to overcome the problem.

---

### Post by slickymaster on 2013-07-03
Can you please post the output of:```
grep -i switcheroo /boot/config-*
```

---

