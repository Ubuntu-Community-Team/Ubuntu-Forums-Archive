---
title: "need zenity help with Thunar"
date: 2013-09-23
forum: Programming Talk
---

### Post by sam_baker2 on 2013-09-23
I am trying to configure a custom action in Thunar that uses zenity.
What I want to do is have a shred command that asks for verification before proceeding.
I have tried this:
```
zenity --question;if [$? = 0];then shred -fuz %F;fi 
```
The question box comes up asking "are you sure you want to proceed" with the "Yes No" buttons, but the 
command will not work.

Any ideas?
This is 12.04 with kernel 3.2.0-53 
Thanks

---

### Post by Toz on 2013-09-23
I believe that there need to be spaces after and before the test characters "[]". Try:
```
zenity --question;if [ $? = 0 ];then shred -fuz %F;fi
```

---

### Post by sam_baker2 on 2013-09-23
Thanks Toz, that was it.

---

