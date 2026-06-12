---
title: "xmms GUI  problem (gutsy)"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by psixpsi on 2008-06-18
hi gang!

i have a strange problem with my beloved xmms under gutsy:
it does not appear when i run it but it runs anyway!

i mean when i run from either terminal or menu it simply doesn't
show up, there is no error message in the terminal, nothing. 
but when i use it to open files it plays them 
(i mean there is the sound + i see xmms on the process list)
but no trace of xmms window anywhere :S 
(i have to manually kill the process to stop it)
i tried reinstalling it several times. no success.
any ideas??

thanks!
psixpsi

---

### Post by wootah on 2008-06-18
> **psixpsi said:**
> hi gang!

i have a strange problem with my beloved xmms under gutsy:
it does not appear when i run it but it runs anyway!

i mean when i run from either terminal or menu it simply doesn't
show up, there is no error message in the terminal, nothing. 
but when i use it to open files it plays them 
(i mean there is the sound + i see xmms on the process list)
but no trace of xmms window anywhere :S 
(i have to manually kill the process to stop it)
i tried reinstalling it several times. no success.
any ideas??

thanks!
psixpsi

Interesting. Have you tried a purge and reinstall?

```

sudo apt-get remove xmms --purge
sudo apt-get install xmms

```

---

### Post by psixpsi on 2008-06-18
IIRC, i did it once. it worked ok, but now the problem came back.
i'm totally confused as there is no error message at all ??:confused:

---

### Post by wootah on 2008-06-18
Run the program and try a dmesg | tail. Also check the /var/log/Xorg.0.log

Perhaps there is something near the end of those that might help.

---

