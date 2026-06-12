---
title: "Listing running processes in terminal"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by virajsawa on 2012-05-27
I wanted to see the running processes in terminal.
I used : 

# ps aux | less 

(I read somewhere on internet )

Result : It showed me absolutely nothing. No process.
Can you please tell me why this happened ?

---

### Post by mlentink on 2012-05-27
try ```
top
```
Or first: 
```
man top
```

---

### Post by virajsawa on 2012-05-27
Yeah it did work ! 
Thank you.
What was the problem with ps ?

---

### Post by m_duck on 2012-05-27
Not too sure about the ps issue, but htop is a more aesthetically pleasing top.

Does your ps command work without the pipe to less? That said, both with and without it works fine on my machine.

---

### Post by virajsawa on 2012-05-27
Oh yeah I did not tried without less.
It worked fine without less ! :) 
Thanks

---

### Post by Azdour on 2012-05-28
Hi,

As a side note you may have run the command including the # character which will not produce anything. So instead of:

```
# ps aux | less 
```

use:

```
ps aux | less 
```

---

