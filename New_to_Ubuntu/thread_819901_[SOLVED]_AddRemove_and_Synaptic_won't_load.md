---
title: "[SOLVED] Add/Remove and Synaptic won't load"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by newbeeman on 2008-06-05
After updating to 8.04 I have 'lost' my Add/Remove and Synaptic.
When selected the file load icon shows then just disappears and the program fails to load.

---

### Post by newbeeman on 2008-06-05
Bump

---

### Post by newbeeman on 2008-06-05
**PLEASE will someone help!!**

---

### Post by vfrankli on 2008-06-05
I'll be watching your thread.  I am having the same kind of problem.

---

### Post by drs305 on 2008-06-05
Check the results of the following command. The only thing you should see on one of the lines is 
```
**127.0.1.1 your_computers_name**
```

If there is anything else attached to the end of your computer's name then it is incorrect.

To fix it:
```

sudo cp /etc/hosts /etc/hosts.bak1
gksudo gedit /etc/hosts
```

and put in the line I wrote in bold.

---

### Post by newbeeman on 2008-06-05
> **drs305 said:**
> Check the results of the following command. The only thing you should see on one of the lines is 
```
**127.0.1.1 your_computers_name**
```

If there is anything else attached to the end of your computer's name then it is incorrect.

To fix it:
```

sudo cp /etc/hosts /etc/hosts.bak1
gksudo gedit /etc/hosts
```

and put in the line I wrote in bold.

Checked your suggestions, all correct. No change, still not working.

---

### Post by roadcone on 2008-06-06
Worked like a charm for me.
I had "127.0.1.1 **your_computer's_name**.local"

Thanks a million!

---

