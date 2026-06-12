---
title: "C Atomic operations"
date: 2011-03-25
forum: Programming Talk
---

### Post by jogi.nayak on 2011-03-25
Here is my simple C program to write to a file using fprintf.

void write_queue(const char *name)
{
FILE *fp;
int no_of_cores=1;
int status=1;
[COLOR=Red]**fp=fopen("job_queue","a");**[/COLOR]
fprintf(fp,"%s %d %d\n",name,no_of_cores,status);
fclose(fp);
}

[COLOR=Red]**I may have multiple processes appending to the same file "job_queue".**[/COLOR]

[COLOR=Red]**I would like to know if appending to a file using fprintf is an atomic operation.  **[/COLOR]

Thanks in advnace!!

---

### Post by Zugzwang on 2011-03-25
> **jogi.nayak said:**
> [COLOR=Red]**I would like to know if appending to a file using fprintf is an atomic operation.  **[/COLOR]


No, certainly not. Consider either (1) using some locking mechanism to make sure that the file is never opened by two processed in parallel, (2) running some kind of deamon server that collect writing requests to the file and performs it, or (3) using a database or something like that.

---

### Post by Arndt on 2011-03-25
> **Zugzwang said:**
> No, certainly not. Consider either (1) using some locking mechanism to make sure that the file is never opened by two processed in parallel, (2) running some kind of deamon server that collect writing requests to the file and performs it, or (3) using a database or something like that.

Well, the man page for 'open' says this:

      O_APPEND
              The file is opened in append mode.  Before  each  write(2),  the
              file  offset  is  positioned  at the end of the file, as if with
              lseek(2).  O_APPEND may lead to corrupted files on NFS file sys&#8208;
              tems  if  more  than one process appends data to a file at once.
              This is because NFS does not support appending to a file, so the
              client  kernel has to simulate it, which can't be done without a
              race condition.

But, on a local file system, not NFS, I do think that writing in append mode is atomic.

---

### Post by jogi.nayak on 2011-03-26
Thanks a tonne for the responses. Could someone guide me on how to go about achieving synchronization between the processes that are going to write to this file?

---

### Post by MadCow108 on 2011-03-26
depends on the kind of synchronization you want. If you do not care about the order in which the data gets written to the file you might not need any at all (O_APPEND on local file systems guarantees no overwrites).
general guide to some possibilities to implement synchronization: [http://beej.us/guide/bgipc/output/html/multipage/index.html](http://beej.us/guide/bgipc/output/html/multipage/index.html)
you probably want a file lock

---

### Post by jogi.nayak on 2011-03-27
Thank you so much!

---

### Post by ibuclaw on 2011-03-27
> **MadCow108 said:**
> you probably want a file lock

Which is flockfile(FILE) and funlockfile(FILE) respectively.

---

