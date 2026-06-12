---
title: "Strange error while opening eclipse"
date: 2008-12-27
forum: Programming Talk
---

### Post by shafi on 2008-12-27
Hi folks,
My friend encounter to a problem in eclipse, he is not able to open eclipse anymore , while he tries to open, he gets the following error in terminal:

[HTML]
./eclipse
LOG: [0xb7eb66b0] exception thrown while VM is initializing: 
LOG: [0xb7eb66b0] NULL: java.lang.Object
LOG: [0xb7eb66b0] Aborting...
Aborted
[/HTML]

anyone knows the reason? thanks.

---

### Post by tinny on 2008-12-27
Looks like you have a problem with your Java install.

Have you changed something to do with Java lately?

What is the output of this command.

```

sudo update-alternatives --config java

```

---

### Post by shafi on 2008-12-27
> **tinny said:**
> Looks like you have a problem with your Java install.

Have you changed something to do with Java lately?

What is the output of this command.

```

sudo update-alternatives --config java

```

Thank you,
the problem solved now.

---

### Post by kacper86 on 2009-03-29
thank you! i have a similar problem and it's solved now :)

---

