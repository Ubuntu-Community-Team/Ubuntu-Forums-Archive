---
title: "[Perl] Difficulties with Regex"
date: 2009-09-16
forum: Programming Talk
---

### Post by DishBreak on 2009-09-16
[FONT="Courier New"][/FONT]Hi all,

I'm playing with a perl script that does a comparison of two files. Because the order can be jumbled between the files, a simple line-by-line diff won't work.

I've been using the [FONT="Courier New"]grep()[/FONT] function in Perl as follows.
```

@matches = grep (/$searchTerm/, @fileLines);

```

This works well...except when the [FONT="Courier New"]$searchTerm[/FONT] scalar contains special characters (i.e. $, +, etc.) Instead of taking these characters literally, they're taken to be significant to the the regex. 

What can I do to make sure the string is taken literally? I'm almost at the end of my rope, so anything would help.

---

### Post by Mirge on 2009-09-16
> **DishBreak said:**
> Hi all,

I'm playing with a perl script that does a comparison of two files. Because the order can be jumbled between the files, a simple line-by-line diff won't work.

I've been using the [FONT=Courier New]grep()[/FONT] function in Perl as follows.
```

@matches = grep (/$searchTerm/, @fileLines);

```This works well...except when the [FONT=Courier New]$searchTerm[/FONT] scalar contains special characters (i.e. $, +, etc.) Instead of taking these characters literally, they're taken to be significant to the the regex. 

What can I do to make sure the string is taken literally? I'm almost at the end of my rope, so anything would help.

[http://www.anaesthetist.com/mnm/perl/Findex.htm#regex.htm](http://www.anaesthetist.com/mnm/perl/Findex.htm#regex.htm)

```

\Q  quote (disable) pattern metacharacters till \E 

```

---

### Post by ghostdog74 on 2009-09-16
if you want to use Perl to do comparison of files, you can use modules such as File::Compare. If Perl is not a must, you can sort your files using sort first, then use diff

---

### Post by DishBreak on 2009-09-17
@Mirge: Thanks! That seemed to have solved my problem.

@ghostdog74: The files I'm comparing are configs for Cisco routers. the config is split into blocks of code. For example, each interface has its own code block, and the blocks contain similar commands. If the blocks are out of order in the file I'm comparing with, a line by line diff (which is what the File::Compare module looks like it's doing) will not work on its own. Neither will sorting the files.

It does seem to be a useful module, though. I'll likely use it in the future, I'm sure. Thanks! =)

---

