---
title: "Fix &quot;Date Modified&quot; based on filename"
date: 2009-01-02
forum: Programming Talk
---

### Post by neilobremski on 2009-01-02
I wrote a [little app]("http://obremsdk.googlecode.com/svn/trunk/dotnet/cli-fixwdate.cs") on Windows to change the "Date Modified" property of multiple files based on date components in the filename extracted via a regular expression.  Now I'd like to write a shell script to do the same thing ...

Ubuntu is great and there's tons of information out there, but I'm fairly overwhelmed.  Can someone suggest a decent place to start out for learning shell scripts?  Alternatively I'd welcome any snippets to try right away and/or a pointer to a script/utility which already does this.

Thanks!

P.S. - The reason I need to change this value is it is zeroed out on the files I grab off my RAZR (V3c) using BitPim.  It screws with a lot of programs, such as Subversion.

---

### Post by neilobremski on 2009-01-15
If anyone else is curious, I got this working relatively easily using [Mono]("http://www.mono-project.com/"):

```
mcs cli-fixwdate.cs
./cli-fixwdate.exe "/^(?<month>\d{2})(?<day>\d{2})(?<year>\d{2})_(?<hour>\d{2})(?<minute>\d{2})(?<second>)/"
```

The first line builds the executable using Mono's C# compiler and the second runs it with a regular expression pattern matching RAZR filenames (both pictures and videos).

---

