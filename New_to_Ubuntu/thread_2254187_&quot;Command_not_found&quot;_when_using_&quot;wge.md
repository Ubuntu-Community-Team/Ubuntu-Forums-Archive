---
title: "&quot;Command not found&quot; when using &quot;wget&quot; in sudo"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by andrei14 on 2014-11-25
Hi All,

I am running a Vagrant VM and get a syntax error when trying to run a bootstrap. The command I'm executing is: 

    ```
wget xtuple.com/bootrstrap -q0- | sudo bash

```
The error I get is: 

    ```
bash: line 1: Usage:: command not found
    bash: line 3: unexpected EOF while looking for matching ``'
    bash: line 4: syntax error: unexpected end of file
```

Can you please give me some advice on this?

Many thanks,
Andrei

---

### Post by Lars Noodén on 2014-11-25
That should be an "oh" rather than a "zero"  
-qO-  instead of -q0-

but that aside, it looks like an unsafe method to take a file from the net and pipe it into a root shell
Myself, I'd download it first then look at it then, maybe, run it.

---

### Post by andrei14 on 2014-11-25
Thank you so much for all the advice! I'm just starting to get the grasp of Linux

File shuld be safe, I trust the source but thanks for the warning!

Appreciate it!

---

