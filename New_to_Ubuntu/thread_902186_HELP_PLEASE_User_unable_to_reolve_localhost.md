---
title: "HELP PLEASE User unable to reolve localhost"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by hvc123 on 2008-08-27
hi all,

got a really wierd thing going on.

my normall user cannot resolve 'localhost'. hy /etc/hosts is correct and my hostname is set correct.

the extra little twist to this is that my root user can resolve localhost back to 127.0.0.1

the permissions on /etc/hosts is correct i.e 644 

an even stranger twist is that my normal user can nsllokup localhost and resolve it back to 17.0.0.1 yet can not ping it 

this is doing my swede in ..... 

thanks


i thought that maybe i had some rubbish in my home area. so i re-created my home and it still wont resolve





OK FIXED 


my /etc/nsswitch.conf permissions was set to 600 i changed this to 644 and now YAY its alive

---

### Post by neurostu on 2008-08-27
If you fixed this then please mark this thread as solved using Thread Tools

---

