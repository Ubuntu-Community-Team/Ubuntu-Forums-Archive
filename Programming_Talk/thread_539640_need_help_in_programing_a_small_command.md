---
title: "need help in programing a small command"
date: 2007-08-31
forum: Programming Talk
---

### Post by adam_r on 2007-08-31
hello,

i need a command that "accually" goes into /root/wireless/ipw3945-1.2.1 and the run's ./load debug=0

how do i write that?

i tried just running /root/wireless/ipw3945-1.2.1/load but it's not working, only if i "cd /root/wireless/ipw3945-1.2.1/" and then "./load" it works. anyone have a suggestion?

---

### Post by Henry Rayker on 2007-08-31
cd /root/wireless/ipw3945-1.2.1/ && ./load

should work...at first glance, at least. Let me know.

---

### Post by adam_r on 2007-08-31
nope, tried that allready, it behaves like i'm not in the folder

---

### Post by Henry Rayker on 2007-08-31
You tried it as all one command? The && operator works fine on my system like that.

EDIT:
Also, where is "load"? This could be part of the issue as well. If load is in the directory you're starting from, you'll need to use the full path.

The reason why /root/wireless/ipw3945-1.2.1/load doesn't work is that load is not available in the directory /root/wireless/ipw3945-1.2.1/

The reason why my command "cd /root/wireless/ipw3945-1.2.1/ && ./load" should work is that it executes the first, then the second.

---

### Post by adam_r on 2007-08-31
it worked when i added "sudo" before ./load :)

---

### Post by Henry Rayker on 2007-08-31
Excellent. I'm glad I could help.

---

