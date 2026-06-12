---
title: "[C/C++] Use of &lt;&gt; versus &quot;&quot; when #include'ing"
date: 2009-07-23
forum: Programming Talk
---

### Post by wbest on 2009-07-23
So I have some code that I'm maintaining.
It was originally for Windows, but I'm trying to get it to work in Linux using g++

I keep coming across includes like this:

#include <core/file.h>

As if it were a native file like iostream or string.

But the compiler can't find the file at all, unless I use "" instead of <>.

So why use the <> when using "" will yield working results?

---

### Post by Sockerdrickan on 2009-07-23
> **wbest said:**
> So I have some code that I'm maintaining.
It was originally for Windows, but I'm trying to get it to work in Linux using g++

I keep coming across includes like this:

#include <core/file.h>

As if it were a native file like iostream or string.

But the compiler can't find the file at all, unless I use "" instead of <>.

So why use the <> when using "" will yield working results?
<> searches include dirs and "this is mostly a constant local path/filename"

---

### Post by MadCow108 on 2009-07-23
<> will search in the default include path and in paths given by -I
"" searches in the current directory first and then in the -I path and default include path

so you usally use <> for standard headers and those of installed libraries and "" for your own headers.
like that you can actually have headers with the same filename as headers of other libraries and still get the correct result as long as your files are not in the default include path or -I path.
But I would still recommend distinct filenames :)

---

### Post by dribeas on 2009-07-23
Acording to the standard, all standard headers must be included with <> and don't need to be backed in files (the compiler could inject the definitions itself instead of actually including the file.  All other includes should be with double quotes "" and must actually be text files that get copied at the position the include directive is.

But real life differs from the standard. There is no c++ implementation (compiler+standard libraries) that does not have all the 'headers' in a file somewhere in the file system. Some compilers will treat <> and "" as being exactly equivalent definitions. Some compilers will use different search orders for the files ("" starting with the current directory and then all the include paths, while <> starting in system include paths and adding the current directory at the end) some will have different but similar behaviors (<> will not search the current dir, "" will not search the compiler/STL header directories)...

At some point, due to how the compilers behave, general consensus is that standard/system headers are usually included with <> while project files are included with "", with external libraries falling one way or the other.

At the end, almost all includes should be with double quotes, but it is so much nicer having <> surronding the file name...

---

### Post by soltanis on 2009-07-23
If you want to stop that from happening without having to change all the <>'s to ""'s, you can use the -I flag in gcc thus

```

gcc -I. [other options] ...

```

-I. tells it to search the local path for library includes. In general, gcc searches the path it knows first, then paths supplied by -I.

If this doesn't work, then find where the core/ directory is and replace the . after -I with that path. This would only happen if you were in a different directory from the source file doing the compilation, I think.

Using <> for non-system-header files is generally bad practice; using "" is better (no need for the -I flag and doesn't rely on gcc semantics to compile).

---

