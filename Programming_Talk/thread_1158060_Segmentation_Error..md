---
title: "Segmentation Error."
date: 2009-05-13
forum: Programming Talk
---

### Post by huangyingw on 2009-05-13
Hello,
    I have difficulty in debugging the segmentation. Could you help me with this?
    Please kindly ignore the "printf" statements, they are used to locate the fault. While, even with so many "printf", I still not found the fault. :(
    I have used "gcc -g -rdynamic dir.c" to try to locate the fault, still, I got some error prompts, which I do not understand.
    Could someone tell me what does "0x00007ff0c94c0248 in ?? () from /lib/libgcc_s.so.1" mean?
GDB prompts as bellow:
```

*** stack smashing detected ***: /root/myproject/c-c++/linux/dir/a.out terminated

Program received signal SIGSEGV, Segmentation fault.
0x00007ff0c94c0248 in ?? () from /lib/libgcc_s.so.1

```
My codes:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <dirent.h>
#include <string.h>
#include <sys/types.h>
#include <sys/stat.h>

# define MAX_PATH 10

int depth=0;

void FindAllFile(char * pFilePath)
{
	depth++;
	printf("depth:%d\n",depth);
	printf("%s\n",pFilePath);
	printf("1\n");
	DIR * dir;
	struct dirent * ptr;
	struct stat stStatBuf;
	chdir(pFilePath);
	dir = opendir(pFilePath);
	printf("2\n");
	while ((ptr = readdir(dir)) != NULL)
	{
		printf("3\n");
		if (stat(ptr->d_name, &stStatBuf) == -1)
		{
			printf("Get the stat error on file:%s\n", ptr->d_name);
			continue;
		}
		if ((stStatBuf.st_mode & S_IFDIR) && strcmp(ptr->d_name, ".") != 0
			&& strcmp(ptr->d_name, "..") != 0)
		{
			char Path[MAX_PATH];
			strcpy(Path, pFilePath);
			strncat(Path, "/", 1);
			strcat(Path, ptr->d_name);
			FindAllFile(Path);
			printf("4\n");
		}
		if (stStatBuf.st_mode & S_IFREG)
		{
			printf("5\n");
			printf("  %s\n", ptr->d_name);
		}
		//this must change the directory , for maybe changed in the recured function
		chdir(pFilePath);
		printf("6\n");
	}
	closedir(dir);
	printf("7\n");
}

int main(void)
{
	FindAllFile("/root/myproject/linux/shell/folder/");
	printf("8\n");
	return   0;
}


```

---

### Post by Zugzwang on 2009-05-13
Your buffer "char Path[MAX_PATH];" is likely to be too small -10 characters (9 usable) is almost nothing! Always check if your data fits into a buffer before copying stuff into it.

---

### Post by Arndt on 2009-05-13
> **Zugzwang said:**
> Your buffer "char Path[MAX_PATH];" is likely to be too small -10 characters (9 usable) is almost nothing! Always check if your data fits into a buffer before copying stuff into it.

Apart from that, you (huangyingw) should check that 'opendir' actually succeeds. And since you use 'chdir' downwards, you will want to do chdir("..") at some point too.

For detecting where memory errors happen, I recommend the tool 'valgrind'.

---

### Post by Zugzwang on 2009-05-13
> **Arndt said:**
> For detecting where memory errors happen, I recommend the tool 'valgrind'.

...which is normally an excellent tool, but doesn't work so well on stuff allocated on the stack (see its FAQ).

---

### Post by Sockerdrickan on 2009-05-13
> **Zugzwang said:**
> ...which is normally an excellent tool, but doesn't work so well on stuff allocated on the stack (see its FAQ).
exp-ptrcheck

---

### Post by dwhitney67 on 2009-05-13
@ OP

Using recursion would be the proper way to go when opening a directory and delving into the sub-directories, all while looking at the contents of each directory.

The files to ignore are '.' and '..', and when performing the recursion, the file, which has been determined to be a directory by examining the stat() information, should be appended to the current directory, before the recursion begins.

I have a complete example of this on my home computer, but this gist of it would be what is shown below (... forgive me if there is a bug in it):
```

void ListFiles(const char* startPath)
{
  if (!startPath) return;

  DIR* dir = opendir(startPath);
  struct dirent* p = 0;

  if (!dir) return;

  while ((p = readdir(dir)) != NULL)
  {
    if (strcmp(p->d_name, '.') == 0 || (strcmp(p->d_name, "..") continue;

    /* allocate space for filename (includes path, a forward-slash, d_name, and null) */
    char* filename = malloc(strlen(startPath) + strlen(p->d_name) + 2);

    strcpy(filename, startPath);
    strcat(filename, "/");
    strcat(filename, p->d_name);

    struct stat buf;
    stat(filename, &buf);

    if (statBuf.st_mode & S_IFDIR)
    {
       ListFiles(filename);
    }

    /* must be a regular file (or sym link?) */

    free(filename);
  }

  closedir(startPath);
}

```

---

### Post by huangyingw on 2009-05-14
> **Zugzwang said:**
> Your buffer "char Path[MAX_PATH];" is likely to be too small -10 characters (9 usable) is almost nothing! Always check if your data fits into a buffer before copying stuff into it.
Yes, this is the fault, thank you for your guidance.

---

### Post by huangyingw on 2009-05-14
> **Arndt said:**
> Apart from that, you (huangyingw) should check that 'opendir' actually succeeds. And since you use 'chdir' downwards, you will want to do chdir("..") at some point too.

For detecting where memory errors happen, I recommend the tool 'valgrind'.
Thank you for guidance and recommendation. I will google about "valgrind".

---

### Post by huangyingw on 2009-05-14
> **Tux0r said:**
> exp-ptrcheck

So, you mean that exp-ptrcheck is better than valgrind? I will try both of them.

---

### Post by huangyingw on 2009-05-14
> **dwhitney67 said:**
> @ OP

Using recursion would be the proper way to go when opening a directory and delving into the sub-directories, all while looking at the contents of each directory.

The files to ignore are '.' and '..', and when performing the recursion, the file, which has been determined to be a directory by examining the stat() information, should be appended to the current directory, before the recursion begins.

I have a complete example of this on my home computer, but this gist of it would be what is shown below (... forgive me if there is a bug in it):

Thank you for your example, I will look into it.

---

### Post by Sockerdrickan on 2009-05-14
> **huangyingw said:**
> So, you mean that exp-ptrcheck is better than valgrind? I will try both of them.
No, exp-ptrcheck is the Valgrind tool that does great at what he didn't say it does. :p

---

### Post by huangyingw on 2009-05-14
> **Tux0r said:**
> No, exp-ptrcheck is the Valgrind tool that does great at what he didn't say it does. :p
Yes, great, I will try it. I found that even with full of "printf", I could not locate the fault...So, a tool is best choice for me..

---

### Post by huangyingw on 2009-05-15
> **Zugzwang said:**
> ...which is normally an excellent tool, but doesn't work so well on stuff allocated on the stack (see its FAQ).
hello, Zugzwang, except experience(I am lacking it now) and valgrind tool, is there other better way/tool to debug the segmentation error?
For I got following, difficult to understanding,check result with valgrind:
Maybe the only solution for me is to accumulate experience and more carefull when coding!?
```

==5581== Memcheck, a memory error detector.
==5581== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==5581== Using LibVEX rev 1854, a library for dynamic binary translation.
==5581== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==5581== Using valgrind-3.3.1-Debian, a dynamic binary instrumentation framework.
==5581== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==5581== For more details, rerun with: -v
==5581== 
==5581== My PID = 5581, parent PID = 5512.  Prog and args are:
==5581==    ./run
==5581== 
==5581== Invalid read of size 8
==5581==    at 0x55AD248: (within /lib/libgcc_s.so.1)
==5581==    by 0x55ADDFC: _Unwind_Backtrace (in /lib/libgcc_s.so.1)
==5581==    by 0x4F26BE1: backtrace (in /lib/libc-2.8.90.so)
==5581==    by 0x4E9EFBB: (within /lib/libc-2.8.90.so)
==5581==    by 0x4F2A886: __fortify_fail (in /lib/libc-2.8.90.so)
==5581==    by 0x4F2A84F: __stack_chk_fail (in /lib/libc-2.8.90.so)
==5581==    by 0x400A62: FindAllFile (in /root/myproject/c-c++/linux/dir/run)
==5581==    by 0x4009FB: FindAllFile (in /root/myproject/c-c++/linux/dir/run)
==5581==    by 0x4E354C7: (within /lib/libc-2.8.90.so)
==5581==    by 0x7FF00055F: ???
==5581==    by 0x800: ???
==5581==    by 0x4761C9: ???
==5581==  Address 0x657361622d78 is not stack'd, malloc'd or (recently) free'd
==5581== 
==5581== Process terminating with default action of signal 11 (SIGSEGV)
==5581==  Access not within mapped region at address 0x657361622D78
==5581==    at 0x55AD248: (within /lib/libgcc_s.so.1)
==5581==    by 0x55ADDFC: _Unwind_Backtrace (in /lib/libgcc_s.so.1)
==5581==    by 0x4F26BE1: backtrace (in /lib/libc-2.8.90.so)
==5581==    by 0x4E9EFBB: (within /lib/libc-2.8.90.so)
==5581==    by 0x4F2A886: __fortify_fail (in /lib/libc-2.8.90.so)
==5581==    by 0x4F2A84F: __stack_chk_fail (in /lib/libc-2.8.90.so)
==5581==    by 0x400A62: FindAllFile (in /root/myproject/c-c++/linux/dir/run)
==5581==    by 0x4009FB: FindAllFile (in /root/myproject/c-c++/linux/dir/run)
==5581==    by 0x4E354C7: (within /lib/libc-2.8.90.so)
==5581==    by 0x7FF00055F: ???
==5581==    by 0x800: ???
==5581==    by 0x4761C9: ???
==5581== 
==5581== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 9 from 2)
==5581== malloc/free: in use at exit: 8,272 bytes in 2 blocks.
==5581== malloc/free: 12 allocs, 10 frees, 30,492 bytes allocated.
==5581== For counts of detected errors, rerun with: -v
==5581== searching for pointers to 2 not-freed blocks.
==5581== checked 70,704 bytes.
==5581== 
==5581== LEAK SUMMARY:
==5581==    definitely lost: 0 bytes in 0 blocks.
==5581==      possibly lost: 0 bytes in 0 blocks.
==5581==    still reachable: 8,272 bytes in 2 blocks.
==5581==         suppressed: 0 bytes in 0 blocks.
==5581== Rerun with --leak-check=full to see details of leaked memory.


```
it tells me something wrong in: /lib/libgcc_s.so.1, while I could not find that file.

---

### Post by dwhitney67 on 2009-05-16
Is the FindAllFile() part of your project?
```

...
==5581==    by 0x400A62: FindAllFile (in /root/myproject/c-c++/linux/dir/run)
==5581==    by 0x4009FB: FindAllFile (in /root/myproject/c-c++/linux/dir/run
...

```
If so, the error is probably in there.  Consider posting that code so others can take a look at it.

Have you ran valgrind with the -v option specified?
```

...
==5581== For counts of detected errors, rerun with: -v
...

```
Or with the --leak-check=full option?
```

...
==5581== Rerun with --leak-check=full to see details of leaked memory.
...

```

---

### Post by huangyingw on 2009-05-17
> **dwhitney67 said:**
> Is the FindAllFile() part of your project?
If so, the error is probably in there.  Consider posting that code so others can take a look at it.

[huangyingw]:Hi, thank you for your patience. My real meaning is that I have difficulty at understanding the output of valgrind at this case. I have posted the code at the beginning of the thread, and Zugzwang has kindly pointed out my fault. His solution is based on his rich experience, while, concerning the experience, I am a new bird. So, I would like to seek help from tool.
> 
Have you ran valgrind with the -v option specified?
Or with the --leak-check=full option?

[huangyingw]: I have just tried the -v and --leak-check=full option. At a rough look, it just give out not so much more than what I previously posted. And, I will try more to understand the output of valgrind.
Anyway, I will try more.

---

### Post by dwhitney67 on 2009-05-17
Valgrind is not the only tool you can use.  There is gdb, or if you prefer a GUI, then ddd or kdbg (which are front-ends to gdb).

You can also strategically place assert() calls in your code to ensure that you have a valid value/pointer where you expect it.

Lastly, there is always the printf() function.

If you are still unable to track the source of the problem, then the likelihood is that it is a runtime issue; perhaps the use of a strcpy(), a memcpy(), or other "dangerous" function that has the potential to overwrite the bounds of a buffer.

---

### Post by huangyingw on 2009-05-18
> **dwhitney67 said:**
> Valgrind is not the only tool you can use.  There is gdb, or if you prefer a GUI, then ddd or kdbg (which are front-ends to gdb).


Thank you for providing ddd and pdbg. I prefer GUI. 
I think I have to seek help from tool, for I could not find the fault even with full of "printf" in my code:( ..
If you find more powerful and convenient tool, please never be hesitated to share with me. I am alway available here or email: [email]huangyingw@gmail.com[/email]

---

### Post by monkeyking on 2009-05-18
If you are into the hole frontend gui click stuff,
theres a nice one for valgrind also
[http://alleyoop.sourceforge.net/](http://alleyoop.sourceforge.net/)

You can get it in the repos also.

good  luck

---

### Post by huangyingw on 2009-05-20
> **monkeyking said:**
> If you are into the hole frontend gui click stuff,
theres a nice one for valgrind also
[http://alleyoop.sourceforge.net/](http://alleyoop.sourceforge.net/)

You can get it in the repos also.

good  luck
Great, I will try this.

---

