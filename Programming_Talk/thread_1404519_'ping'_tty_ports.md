---
title: "'ping' tty ports?"
date: 2010-02-11
forum: Programming Talk
---

### Post by rockom on 2010-02-11
Is their a method with code to check on the existence and availability of tty ports (ttyS0, ttyUSB0, etc...) without actually opening them? 

For example, if the port is already in use how do know if it's not available or no-existent.
Something like setserial that returns a list of tty's would be great.

Thanks,
-Rocko

---

### Post by GeorgeVita on 2010-02-15
Hi **rockom**, some ideas and 'retrigger' of this thread:

Existence of port: **ls /dev/ttyS* /dev/ttyU***
Used & locked by any program: **ls /var/lock/*ttyS* /var/lock/*ttyU***

>>> /dev/ttySx exist always as they are h/w reserved

Use minicom (must be installed) to 'lock' any port and check again.

More reading at: [http://tldp.org/HOWTO/Serial-HOWTO.html](http://tldp.org/HOWTO/Serial-HOWTO.html)

Regards,
George

---

### Post by rockom on 2010-02-16
Thank you for the reply.

I downloaded the source code for setserial to see how it's being done by that solution.  It looks like setserial actually opens each port momentarily to check the status and gather information.

-Rocko

---

### Post by meastwood on 2010-02-16
You could try playing around with 'lsof' - this will list open files - it uses a device cache file.  The man page says it is not great on reporting all locks.  The down side also is that to read some information you need root access -

```
$ sudo lsof /dev/tty[0-9]
      Output information may be incomplete.
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
getty     2269 root    0u   CHR    4,4       652 /dev/tty4
getty     2269 root    1u   CHR    4,4       652 /dev/tty4
getty     2269 root    2u   CHR    4,4       652 /dev/tty4
getty     2270 root    0u   CHR    4,5       655 /dev/tty5
getty     2270 root    1u   CHR    4,5       655 /dev/tty5
getty     2270 root    2u   CHR    4,5       655 /dev/tty5
getty     2274 root    0u   CHR    4,2       646 /dev/tty2
getty     2274 root    1u   CHR    4,2       646 /dev/tty2
getty     2274 root    2u   CHR    4,2       646 /dev/tty2
getty     2276 root    0u   CHR    4,3       649 /dev/tty3
getty     2276 root    1u   CHR    4,3       649 /dev/tty3
getty     2276 root    2u   CHR    4,3       649 /dev/tty3
getty     2277 root    0u   CHR    4,6       658 /dev/tty6
getty     2277 root    1u   CHR    4,6       658 /dev/tty6
getty     2277 root    2u   CHR    4,6       658 /dev/tty6
console-k 2806 root   12r   CHR    4,0      1808 /dev/tty0
Xorg      2994 root    5w   CHR    4,7      2318 /dev/tty7
getty     3395 root    0u   CHR    4,1       643 /dev/tty1
getty     3395 root    1u   CHR    4,1       643 /dev/tty1
getty     3395 root    2u   CHR    4,1       643 /dev/tty1
```

An extra flag can be used to make the output more friendly for scripts - such as 'awk'.

---

