---
title: "what is difference between unlink and rm?"
date: 2010-02-23
forum: Programming Talk
---

### Post by vksingh on 2010-02-23
Hi,

what is difference between unlink and rm?

As both removes a file

# unlink file_name
# rm file_name


Please help.


Thanks,

Vivek

---

### Post by falconindy on 2010-02-23
On a simplistic level, they perform the same task. However, rm has a lot more features than unlink.

---

### Post by Fougner on 2010-02-23
> The unlink() function removes a link to a file, and decrements the link count of the referenced file by one. When the file's link count becomes 0 and no process has the file open, the space occupied by the file is  freed, and the file is no longer accessible. If one or more processes have the file open when the last link is removed, the link is removed before unlink() returns, but the removal of the file contents is postponed until all references to the file are closed.

Unlink is a "nicer" way, waiting for processes using the file, to close.

---

### Post by gmargo on 2010-02-23
> **Fougner said:**
> Unlink is a "nicer" way, waiting for processes using the file, to close.

Sorry, that's not right.

The **unlink(1)** command will remove a single file with the **unlink(2)** system call.
It does not handle multiple files or directories.

The **rm(1)** command has many options and can handle multiple files and directories
and recursion.  Ultimately it uses the **unlinkat(2)** system call which is
a fancy interface to **unlink(2)** and **rmdir(2)**.

The **rm(1)** and **unlink(1)** commands do not wait for processes to close the file.  If the inode link count decrements to zero, the file data will still linger around if some process has it open.  The disk space is recovered by the system after the last process closes the file.

---

