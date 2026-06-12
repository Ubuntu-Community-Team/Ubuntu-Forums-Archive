---
title: "Wireless not working after update of ubuntu 10.04"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by Ashish Mishra on 2012-05-25
The wireless in Dell mini inspiron is not working after i updated ubuntu 10.04. I am not able to see the various wireless networks available in network manager icon. somebody please help.

---

### Post by wildmanne39 on 2012-05-25
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by gnusci on 2012-05-25
Could you please add more information so we can assist you:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Ashish Mishra on 2012-05-26
I upgraded to 12.04 last evening, now the wireless is working fine. Thanks to both of you trying to help me.

---

### Post by wildmanne39 on 2012-05-26
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

