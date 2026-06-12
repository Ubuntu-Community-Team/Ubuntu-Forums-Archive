---
title: "How can I find executable path when process starts in kernel level?"
date: 2015-07-28
forum: Programming Talk
---

### Post by agnes3 on 2015-07-28
[FONT=Helvetica Neue]I can retrieve the path of ./busybox cat or such process which is not terminated quickly.[/FONT]
[FONT=Helvetica Neue]However I cannot gather the path of processes which ended up quickly ./busybox ps[/FONT]
[FONT=Helvetica Neue]What is the easiest way to get all of the processes executable path in kernel level?

[/FONT]```

rcu_read_lock();   
    struct task_struct *task;
    struct list_head *list;``
    struct mm_struct *mm;
    struct file *exe_file;
    char *pathname,*path;
    pathname = kmalloc(PATH_MAX, GFP_ATOMIC);
    task = list_entry(list, struct task_struct, sibling);
    for_each_process(task) {
    printk("/----------------------------------/\n");
    mm = get_task_mm(task);
    if(mm != NULL) {
        exe_file = get_mm_exe_file(mm);
        path_get(&exe_file->f_path);
        path = d_path(&mm->exe_file->f_path,pathname,PATH_MAX);
        printk("CHILD  %s[%d]->%s\n\n ", task->comm, task->pid ,path);
        }
    }

rcu_read_unlock();[FONT=Helvetica Neue]

[/FONT]
```[FONT=Helvetica Neue]

[/FONT]

---

