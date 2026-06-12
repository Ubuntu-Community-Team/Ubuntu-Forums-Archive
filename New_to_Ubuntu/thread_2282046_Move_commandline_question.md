---
title: "Move commandline question?"
date: 2015-06-11
forum: New to Ubuntu
---

### Post by efonde on 2015-06-11
Hi,

I remember vaguely reading it somewhere here, move (mv) command line where it display the result without actually executing the command. 
Sorta like echo but echo give rather long lists display with no line breaks.  The one i remembered displayed with line breaks.
I don't remember the link to the thread since I didn't save the link. Hope someone could help me.

Thank you for helping.

---

### Post by Lars Noodén on 2015-06-11
The [mv](http://manpages.ubuntu.com/manpages/trusty/en/man1/mv.1.html) utility has a **-i** option which goes interactive to ask if you really want to overwrite an existing file.  But there is no preview that I know of.  The 'rename' utility, however, does have a **-n** or **--no-act** option to preview what it plans to do without actually doing it.  The syntax is different and it is more capable than 'mv' but it could be used in place of 'mv' in many instances.

---

### Post by ajgreeny on 2015-06-11
The mv command can also be made verbose; I have my system set with an alias of **alias mv='mv -iv'** so I get to say whether or not I actually want to overwrite a file if the mv would do that, and I also see what really happened.

eg, I just made a file called test with **touch test** then changed it to test-new with the mv command and got the output **&#8216;test&#8217; -> &#8216;test-new&#8217;**.
If I now try to change a second file to the name test-new I see the output **mv: overwrite &#8216;test-new&#8217;?** and can use y/n to accept or not.  If I accept with a y I will get the same output as before, if I use n to decline I get no output.

---

### Post by efonde on 2015-06-16
thank you guys. i thought rename and move the same with mv ?

---

### Post by Lars Noodén on 2015-06-16
> **efonde said:**
> thank you guys. i thought rename and move the same with mv ?

mv is a small binary program that just renames files.  rename is a larger, complex perl script that can take full advantage of basic perl expressions including variables, operations and [perl regular expressions](https://www.cs.tut.fi/~jkorpela/perl/regexp.html).  

The manual pages don't say much,

```

man mv
man rename

```

but the latter is much more flexible.  You can rearrange or even renumber file names with it.

---

### Post by leunam12 on 2015-06-16
I think you can do ```
rsync --dry-run --remove-source-files -av /blah/blah/here/ /blah/blah/there
```Don't know about renaming with this command, though.

---

### Post by efonde on 2015-06-17
thank you. I'll mark this thread solved.

---

