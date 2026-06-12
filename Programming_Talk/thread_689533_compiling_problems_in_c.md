---
title: "compiling problems in c"
date: 2008-02-06
forum: Programming Talk
---

### Post by rob21 on 2008-02-06
using c in linux and compiling in a ddd debugger, all my projects compile and source code appears in the ddd console. All except for one-I get the message "/home/robert/2213/assign1/init.c:no such file or directory" and also "Line number 1 is out of range for init.c". Can someone please help me.
                          thanks

---

### Post by stroyan on 2008-02-06
Does the file '/home/robert/2213/assign1/init.c' exist?
Perhaps /home/robert/2213/assign1 is not in gdb's source search path.
Use ddd's Edit->GDB Settings menu item.
About half way down the scrollable settings you will find 'Search path for source files'.
If you have source files in directories that are not listed there, then add those directories.
The $cdir pattern in the path is the directory that each source file was originally compiled from.
That can be seen in a debuggable program using readelf to look at the debug info.
```
readelf --debug-dump=info a.out | awk '/DW_AT_name/{n=$NF}/DW_AT_comp_dir/{print $NF "/" n}'
```

---

