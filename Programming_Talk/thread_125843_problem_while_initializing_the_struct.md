---
title: "problem while initializing the struct"
date: 2006-02-05
forum: Programming Talk
---

### Post by awais on 2006-02-05
Actually I am writing a device driver in ubuntu. And I have a problem while initializing the struct of file_operations. When I compile the code listed below like this
    gcc -c UsbDrv.c
then an error came like this
    the struct file_operations is of incomplete type
So, if any one knows how to fix the problem, kindly reply me.

struct file_operations fops= {
  read_device,
  write_device,
  release_device
};

---

### Post by toojays on 2006-02-05
You need to specify the types of the struct members.

---

### Post by David Marrs on 2006-02-05
Try removing "struct" from the initialisation code. If that doesn't work, can we see the definition of the struct itself?
```
file_operations fops= {
read_device,
write_device,
release_device
};
```

---

### Post by LordHunter317 on 2006-02-05
Neither of those answers are correct.  You haven't included the declaration of struct file_operations yet.  You need to include it or declare it yourself.

Also, don't start the same thread twice.

---

