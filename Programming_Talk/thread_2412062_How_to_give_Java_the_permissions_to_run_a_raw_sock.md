---
title: "How to give Java the permissions to run a raw socket(Ping)"
date: 2019-02-07
forum: Programming Talk
---

### Post by thesouthernsanta on 2019-02-07
I have a Java library which runs the Ping command, however Java doesn't run the Ping command properly since it doesn't have the permissions to do so, even though I can ping in my terminal without root or su.


I would prefer if the answer did not involve the use of root or su since I would not want to allow my app to become a vulnerability.


I would like to look into the possibility of invoking a separate service user that holds those permissions.


Sorry, I'm new to linux.

---

### Post by spjackson on 2019-02-07
> **thesouthernsanta said:**
> I have a Java library which runs the Ping command, however Java doesn't run the Ping command properly since it doesn't have the permissions to do so, even though I can ping in my terminal without root or su.

ping works because of the setuid bit.
```

$ ls -l /bin/ping
-rwsr-xr-x 1 root root 68520 Aug 29 09:25 /bin/ping

```

> 
I would prefer if the answer did not involve the use of root or su since I would not want to allow my app to become a vulnerability.

I would like to look into the possibility of invoking a separate service user that holds those permissions.

I don't think this can easily and safely be done with Java. See [https://stackoverflow.com/questions/51757591/fail-to-seteuid-in-java-by-calling-jni](https://stackoverflow.com/questions/51757591/fail-to-seteuid-in-java-by-calling-jni) for some further discussion.

---

### Post by thesouthernsanta on 2019-02-07
Thanks for your quick response. Someone else on another forum told me the exact thing, but didn't explain it properly.
Sigh, well that's that idea out the window for me.

Thanks for your help though

---

### Post by thesouthernsanta on 2019-02-18
Hey, just a bump with another question..
Is there a safe way about using sudo in Java without changing any setuid bits?

---

