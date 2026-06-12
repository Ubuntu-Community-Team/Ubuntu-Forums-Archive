---
title: "Comparing wordpress files for differences."
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Jonas thomas on 2012-09-12
Hi I kind of got myself between a rock and a hardplace on a wordpress website I've been working on

Basically in hindsite, I should have set up a child template, because when I update the template, the tweaks that I needed to do have been wiped out.

Anyway, I'm thinking of setting up a child template and doing it correctly.

Short of using git, is there some wonderful magical Linux command/ incantation that will recursively search two folders and sub folders and point out the differences in the files?

Thanks in advance

---

### Post by Bucky Ball on 2012-09-12
There is a program called Meld in the repos. The files need to be on the same local drive but it will compare them, show different files and merge if required.

---

### Post by sandyd on 2012-09-12
> **Bucky Ball said:**
> There is a program called Meld in the repos. The files need to be on the same local drive but it will compare them, show different files and merge if required.

You can also use diff, which Meld is a frontend off.

---

### Post by marinara on 2012-09-13
diff -r

---

### Post by tienlbhoc on 2012-09-13
And how to comparing text in files for differences at where?

---

