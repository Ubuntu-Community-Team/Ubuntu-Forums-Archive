---
title: "gdb doesn't step into a shared library compiled with -g"
date: 2010-09-11
forum: Programming Talk
---

### Post by japcrword on 2010-09-11
Briefly, I can't step into a shared library's (with debug info) function. 

Here's more detailed description of my problem. 
I've the following program (test1.cpp): 
[PHP]#include <iostream>
#include <locale>

int main (int argc, char * argv []) {
	const wchar_t * HelloWorld_wchar_t
		= L"Hello, World! == &#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";
	std::setlocale (LC_ALL, "be_BY.utf8");
	std::wcout << HelloWorld_wchar_t << std::endl;
	return 0;
}
[/PHP]
I've compiled it with 
```
g++ -g -Wl,-rpath,/usr/local/lib64,-rpath,/home/alex/bin/glibc/lib/ test1.cpp -o test1
```
(I've used -rpath in order to pass directories with libraries containing debug info to the linker)
**All the libraries** returned by ldd test1
```
	linux-vdso.so.1 =>  (0x00007fffd7cbb000)
	libstdc++.so.6 => /usr/local/lib64/libstdc++.so.6 (0x00007f18820cc000)
	libm.so.6 => /home/alex/bin/glibc/lib/libm.so.6 (0x00007f1881e4a000)
	libgcc_s.so.1 => /usr/local/lib64/libgcc_s.so.1 (0x00007f1881c34000)
	libc.so.6 => /home/alex/bin/glibc/lib/libc.so.6 (0x00007f18818db000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f18823d2000)
```
apart from linux-vdso.so.1 and /lib64/ld-linux-x86-64-so.2 were compiled with -g flag and **have debug information**. 

My **problem** starts when I run 'cgdb test1', invoke 'run' and try to step into std::setlocale with 'step'. Instead of showing the source of std::setlocale the gdb steps to the next line (std::wcout << ...). I can easily step into the std::wcout.operator<<(). But to step into std::setlocale is a problem. 
I find it puzzling because **gdb confirms that it loaded debug information** for all the libraries (except for ld-linux-x86)
```
(gdb) info sharedlibrary 
From                To                  Syms Read   Shared Object Library
0x00007ffff7ddcaf0  0x00007ffff7df5814  Yes (*)     /lib64/ld-linux-x86-64.so.2
0x00007ffff7b2ee50  0x00007ffff7b989a6  Yes         /usr/local/lib64/libstdc++.so.6
0x00007ffff7859e70  0x00007ffff7898bd8  Yes         /home/alex/bin/glibc/lib/libm.so.6
0x00007ffff7643850  0x00007ffff7653028  Yes         /usr/local/lib64/libgcc_s.so.1
0x00007ffff7306810  0x00007ffff73efa4c  Yes         /home/alex/bin/glibc/lib/libc.so.6
(*): Shared library is missing debugging information.
```

**Here are my questions**:
1. Is it possible to make gdb to give some more diagnostics as to why it cannot step into the specific function?
2. What the problem with std:setlocale may be? May it be connected with the flags CFLAGS="-fno-stack-protector -O2 -U_FORTIFY_SOURCE -g" that I used in order to compile glibc? (I know it's a bad style to use -g and -O2 together, but there wasn't much choice as without "-O2 -U_FORTIFY_SOURCE" it didn't compile at all, see [http://ubuntuforums.org/showthread.php?t=1001811](http://ubuntuforums.org/showthread.php?t=1001811), post #5)
3. How can I find out in gdb in what shared library the given function is located? In my case, it's std:setlocale. How do I know is it in libstdc++.so.6 or in libc.so.6 or somewhere else? I suppose it has to be in libstdc++. But the problem with 'step into' makes me less sure.

I'm running Ubuntu 10.04 LTS (Lucid Lynx), x86-64; GNU gdb (GDB) 7.1-ubuntu; CGDB 0.6.5.

Thank you
PS. I've looked through the FAQ

---

### Post by MadCow108 on 2010-09-11
you are probably missing the source files.

do:
set step-mode on
to stop gdb from stepping over functions and output diagnostics

setlocal is defined in locale/setlocal.c of libc (not libstdc++)

add that directory to gdb's source path:
dir path/to/libc/locale

---

### Post by japcrword on 2010-09-12
Yes, you're probably right. 

I thought that libstdc++ had its own implementation of setlocale because of 'std::' prefix. But it probably just wraps setlocale from libc into std namespace. 

Now I understand my mistake. The point is I have 2 versions of libc. The 1st one (/lib/libc.so.6) is stripped of the debug info and the 2nd (/home/alex/bin/glibc/lib/libc.so.6) that I compiled myself with -g flag. The reference in libstdc++ to libc.so.6 resolves to the 1st version of libc:
```
$ ldd /usr/local/lib64/libstdc++.so.6
	linux-vdso.so.1 =>  (0x00007fff2a9ed000)
	libm.so.6 => /lib/libm.so.6 (0x00007f9a66e4c000)
	libc.so.6 => /lib/libc.so.6 (0x00007f9a66ac9000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f9a673f7000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f9a668b1000)
```
Now when gdb sees std::setlocale in libstdc++.so.6 referencing to /lib/libc.so.6 with no debug information it steps over it.

Thank you for the reply

---

### Post by japcrword on 2010-09-12
Well, actually everything isn't so nice as it seemed to me previously. 
Gdb stubbornly refuses to step into setlocale's source despite setting step-mode to 'on' and passing the directory to setlocale.c (in my case it's /home/alex/Downloads/glibc/unpacked/glibc-2.11.2/locale). 
I've made my program even simpler (it contains only the call to setlocale) and compiled it as c-code.
[PHP]#include<stdio.h>
#include<locale.h>

int main(int argc, char *argv[])
{
  char * HelloWorld_char; 

  HelloWorld_char = "Hello, World! == &#1042;&#1110;&#1090;&#1072;&#1102;, &#1096;&#1072;&#1085;&#1086;&#1118;&#1085;&#1099; &#1089;&#1087;&#1072;&#1076;&#1072;&#1088;!";
  setlocale (LC_ALL, "be_BY.utf8");

  return 0;
}[/PHP]

When I run '(gdb) info address setlocale' in gdb it says 
```
Symbol "setlocale" is at 0x7ffff7aab9d0 in a file compiled without debugging.
```
The address belongs to libc. But I think that 'compiled without debugging' claim is not quite true -- both 'file -L /home/alex/bin/glibc/lib/libc.so.6' says that it's not stripped and gdb says libc is not missing debugging info. I suspect that it's the '-O2' option that messed up the debugging information in libc. 

I've experimented with deleting source file that libstdc++ references to. When the source file is in place gdb steps into its functions (at least some of them). But when I delete the source file and try to step into gdb says 'No such file or directory.' With libc's functions when I try to step into gdb doesn't say that it's missing the source files, it acts as if there was no debug symbols inside the shared library.

---

### Post by MadCow108 on 2010-09-12
how about just installing debug information for your main libc?
sudo apt-get install libc6-dbg

also note that ubuntu uses eglibc not glibc

why do you want to step into setlocal?

---

### Post by japcrword on 2010-09-12
> **MadCow108 said:**
> how about just installing debug information for your main libc?
sudo apt-get install libc6-dbg

Thanks. I've tried it. I probably have some problem with repositories, because from time to time it says "The following packages have unmet dependencies" during downloading. When I resolve this issue I'll try to install libc6-dbg. I didn't know about libc-dbg symbols. Though, I don't quite understand how synchronization between debug symbols and sources works. Do I need also to download sources of the appropriate version?

> **MadCow108 said:**
> also note that ubuntu uses eglibc not glibc

Thank you. I didn't know that. Maybe eglibc will be easier to compile. 

> **MadCow108 said:**
> why do you want to step into setlocal?

Actually there's nothing special about setlocale. I took it as an example. I just have 2 programs that work under Windows and try to port them to Linux (they don't work currently under Linux). I thought it's a good idea to have c/c++ libraries compiled with debugging info. It makes things easier. The first sample of code in this thread is an example that works under Windows but under Linux prints rubbish. It's not critical though, as using cout instead of wcout works fine. The point is having standard libs with debug symbols as it might be useful in the future.

---

