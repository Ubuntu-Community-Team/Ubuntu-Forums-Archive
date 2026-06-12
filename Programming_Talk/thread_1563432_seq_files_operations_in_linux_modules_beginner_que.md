---
title: "seq_files operations in linux modules beginner question"
date: 2010-08-29
forum: Programming Talk
---

### Post by jamesbon on 2010-08-29
I was browsing through the source code and I came across following in include/linux/seq_file.h
```
struct seq_operations {
        void * (*start) (struct seq_file *m, loff_t *pos);
        void (*stop) (struct seq_file *m, void *v);
        void * (*next) (struct seq_file *m, void *v, loff_t *pos);
        int (*show) (struct seq_file *m, void *v);
};

```As far as my understanding is above all are related to seq_file operations with respect to /proc.

I am looking for a practical easy example if some one has ever used start,stop,next,show in their modules.
I am also not clear with what is a seq_file I have seen many a places in Kernel it has been used.
What is the void *v and loff_t above?

---

