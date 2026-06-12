---
title: "Cannot browse to a windows served webpage on my network"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by power_unit on 2014-01-01
I have set up a share with Samba. I can see the windows network and open my windows computer's shared files. From windows 7 box I can see my ubuntu share and access its files.

I am serving a personal website from this windows 7 computer which I can browse to from my other windows boxes. 
I cannot browse to it from firefox on my ubuntu 12.04 boxby either name or IP.  The request either dies with no response or says it cannot be found.
I can browse elsewhere.
I can ping the computer by name and IP.


What do I need to do do browse to this win7 box with Firefox?

Thanks

---

### Post by power_unit on 2014-01-02
Solved it. *headslap*

Rechecked an "established" connection and it did not work either. Somehow web port 80 inbound got disabled. File sharing was previously disabled. How does this **** happen? Updates from hell? Grrr!

---

