---
title: "Vala FileUtils error"
date: 2008-11-16
forum: Programming Talk
---

### Post by days_of_ruin on 2008-11-16
Heres the code:
> 
using GLib;
using FileUtils;

public class FileReader : GLib.Object
{
    string filename;
    string content;
    ulong len;

    public FileReader(string filename)
    {
        this.filename = filename;
        this.content = content;
        this.len = len;

        FileUtils.get_contents(filename,out content, out len);

    }
}

public int main(string[] args)
{
    var sample = new FileReader("filereader.vala");
    return 0;
}


And heres the Error I get:
```
** (valac:17333): CRITICAL **: vala_scope_lookup: assertion `self != NULL' failed
filereader.c: In function ‘file_reader_construct’:
filereader.c:45: warning: passing argument 3 of ‘g_file_get_contents’ from incompatible pointer type

```

And here is the command I was compiling it with
```
valac -o filereader filereader.vala

```

---

### Post by days_of_ruin on 2008-11-16
> **days_of_ruin said:**
> Heres the code:


And heres the Error I get:
```
** (valac:17333): CRITICAL **: vala_scope_lookup: assertion `self != NULL' failed
filereader.c: In function ‘file_reader_construct’:
filereader.c:45: warning: passing argument 3 of ‘g_file_get_contents’ from incompatible pointer type

```

And here is the command I was compiling it with
```
valac -o filereader filereader.vala

```

Never mind.
The first error was from the "using FileUtils;"
the second error was because it wanted a uint instead of a ulong, not sure
why all the documentation uses ulong.

---

