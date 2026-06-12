---
title: "Why does chmod with (no?) arguments not give an error message"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by venom104 on 2012-11-06
Okay the chmod man page says, "       The  operator  +  causes the selected file mode bits to be added to the existing file mode bits of each file"....

So why does this NOT  give me an error message

```

chmod + ./AdbeRdr9.5.1-1_i486linux_enu.bin 

```When this gives does give me an error message?

```

chmod ./AdbeRdr9.5.1-1_i486linux_enu.bin 

```I get it, chmod requires a parameter...what what does the + do if there isn't a valid symbolic constant after it (x,r,w)?

What does  chmod + ./AdbeRdr9.5.1-1_i486linux_enu.bin do?

---

### Post by deadflowr on 2012-11-06
It doesn't do anything.
All you said was add nothing, so it did.
Using + fulfilled the argument needed.

---

### Post by Abhinav Kumar on 2012-11-08
> **venom104 said:**
> Okay the chmod man page says, "       The  operator  +  causes the selected file mode bits to be added to the existing file mode bits of each file"....

So why does this NOT  give me an error message

```

chmod + ./AdbeRdr9.5.1-1_i486linux_enu.bin 

```When this gives does give me an error message?

```

chmod ./AdbeRdr9.5.1-1_i486linux_enu.bin 

```I get it, chmod requires a parameter...what what does the + do if there isn't a valid symbolic constant after it (x,r,w)?

What does  chmod + ./AdbeRdr9.5.1-1_i486linux_enu.bin do?
Hi
chmod stands for CHange MODe bits of the file.
when You write + option with it, it means you want to add something to the permissions of the file. (There are 3 options- r(read),w(write) and x(executable). 
Now, as deadflowr stated it, you have not given any option to the file. So, shell reports an error.

Another point to note is you are trying to change permissions of this file and  simultaneously execute this file. This can be better broken into two steps:
```

chmod +x AdbeRdr9.5.1-1_i486linux_enu.bin
./AdbeRdr9.5.1-1_i486linux_enu.bin

```

Regards,
Abhinav

---

### Post by venom104 on 2012-11-08
Thank you guys. Thread Closed.

---

### Post by Unity User on 2012-11-08
For more info, run ```
man chmod
```

---

