---
title: "zip file"
date: 2015-03-23
forum: New to Ubuntu
---

### Post by liviu3 on 2015-03-23
Hello, I'm new to ubuntu 14.04 and i need help for a task.

I want to archive all files with .c extension and I don't know how to use the command in terminal to do it. i've tried it like : zip "*.c" archive.zip and it doesn't work.
If someone knows I would appreciate the help.

Thank you.

---

### Post by Impavidus on 2015-03-23
The **zip** utility expects first options (if any), then the name of the archive and then the files to be archived. Don't put *.c in quotes, as zip will then think you want to archive the file named ***.c**, not all files ending in .c. So that's```
zip archive.zip *.c
```

You can read the manual page for zip and most other commands using the utility **man**:```
man zip
```

---

### Post by liviu3 on 2015-03-23
Thank you for help

---

### Post by sandyd on 2015-03-24
Hi, if you have found a solution, please mark this thread as solved using Thread Tools -> Mark Thread as Solved.

Thanks!

---

