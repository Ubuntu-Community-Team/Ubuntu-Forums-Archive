---
title: "Upgrade to 22.04 stalls at &quot;Searching for obsolete software&quot; - what to do??"
date: 2022-10-03
forum: New to Ubuntu
---

### Post by cwmoser2 on 2022-10-03
My upgrade to 22.04 has stalled at "Searching for obsolete software".
What should I do?
I tried ^C but it says it will leave the installation in a "broken state".

This is what is on the screen:
```

.
.
.
> Cleaning up
   Restarting the Computer

Found Ubuntu 20.04.4 LTS (20.04) on /dev/sda1
Found Ubuntu 20.04.4 LTS (20.04) on /dev/sdb1
Found Ubuntu 20.04.4 LTS (20.04) on /dev/sdb4
Found Ubuntu 20.04.4 LTS (20.04) on /dev/sdc1
done
Processing triggers for menu (2.1.47 ubuntu4) ...
Processing triggers for sql-base (1.30) ...

Searchign for obsolete software
```

---

### Post by cwmoser2 on 2022-10-03
I found out what happened ... a window waiting for OK to remove 301 obsolete packages was hidden.
Found it and selected OK and installation was successful and complete.
Came close to just doing a manual restart.

---

### Post by oldos2er on 2022-10-04
Thank you for sharing this. Would you mark your thread 'Solved' using Thread Tools at the top of the page? It will help others who might be having the same problem.

---

