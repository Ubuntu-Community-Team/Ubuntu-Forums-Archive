---
title: "Unable to include thread_info.h"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by karthikbalaji on 2008-06-11
Hi all,

I am trying to compile a small program to print all the process id's.

#include <stdio.h>
#include <stdlib.h>
#include <linux/sched.h>
#include <asm-i386/thread_info.h>

int main()
{
	struct task_struct *task;
	for_each_process(task) {
		printf("%s[%d]\n",task->commom,task->pid);
	}
}

When i compile it i get the following error,

ptre.c:4:34: error: asm/thread_info.h: No such file or directory.

Ya i could see no such file under /usr/include/asm. Is there any specific packages i have to install to get these header files ?.

Thanks

---

### Post by me208 on 2008-06-11
you could try installing libc6-dev
```
sudo apt-get install libc6-dev
```
hope that helps, it probably won't  but it's worth a try

---

### Post by Cypher on 2008-06-11
You will need to install the Kernel sources to get the thread_info.h file..
```

sudo apt-get install linux-source
cd /usr/src
sudo tar -jxf linux-source-<version>-tar.bz2
sudo ln -s linux-<version> linux

```
Now when you compile your file, you'd want to include the directory "/usr/src/linux/include" in your include paths with "GCC -I/usr/src/linux/include...."

---

