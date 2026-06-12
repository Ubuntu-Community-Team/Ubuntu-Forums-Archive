---
title: "where is the struct file defined?"
date: 2008-06-24
forum: Programming Talk
---

### Post by abacan on 2008-06-24
Some reference says the struct file defined in include/linux/fs.h, but, while I had looked up in include/linux/fs.h, even if whole of the include directory, I could't find the definition of the struct file. where is the struct file defined?

---

### Post by kknd on 2008-06-24
What struct?

---

### Post by dwhitney67 on 2008-06-24
edited...

Ok... you're interested in the kernel's struct file!  It is located in **fs.h**, which in turn is located in **/lib/modules/`uname -r`/build/include/linux** directory.  When you open the header file, look around line 770.

---

### Post by LaRoza on 2008-06-24
> **dwhitney67 said:**
> The structure for FILE is defined in stdio.h.  This is the structure type returned by the C library call fopen().

If you are referring to a different  "file" structure, then I share kknd's confusion as to what you are asking about.

I was going to say that also, but "file != FILE".

---

### Post by stroyan on 2008-06-24
The linux kernel source defines a real 'struct file' inside of
include/linux/fs.h .
It is not clear why there is any mention of 'struct file' in
the user space header file include/linux/fs.h.  It is possible
to use a pointer to a struct type without any declaration of the
contents of the struct.  But I don't see any system call that uses
a struct file, even as an opaque pointer type.  It seems that any
header file reference to it is a simple error or a remnant of things
long ago removed.

---

### Post by outskut on 2011-02-12
Oh.  Thank you dwhitney67.  I was wondering the same thing because I was reading /usr/include/linux/fs.h which had only a list of macro definitions and I was wondering what I was missing.  The command  [**gedit /lib/modules/`uname -r`/build/include/linux/fs.h**] literally accesses the header file.  And btw, in Lucid Lynx 10.04 LTS  as of 2/12/11 the struct definition starts on line 911.

---

