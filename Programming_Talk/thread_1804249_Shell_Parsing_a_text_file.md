---
title: "Shell: Parsing a text file"
date: 2011-07-14
forum: Programming Talk
---

### Post by Black Magix on 2011-07-14
I'm a server admin looking through several different system logs. What I want to do is build a parsing script that will run and look for keywords within the log "Error" "Alert" are good ones, take the entire line it found it on, and put it into another text file.

I know several programming languages so I'm sure I could get the syntax with a little practice, I just don't know where I need to start. Google search brought me back here and ubuntu forums have never let me down :)

If you have code examples or resources I can start looking I'd be much appreciative!

---

### Post by Bachstelze on 2011-07-14
Unless I missed something:

```
grep Error log.txt > error.txt
grep Alert log.txt > alert.txt
```

---

### Post by Black Magix on 2011-07-14
> **Bachstelze said:**
> Unless I missed something:

```
grep Error log.txt > error.txt
grep Alert log.txt > alert.txt
```

It'll throw the dates in the log out of order. I need it in one file as well.

I wanna be able to type ./ <filename> and have it return a file that is parsed and still in chronological order.

---

### Post by cgroza on 2011-07-14
I hope you know Perl. Really this is a relatively easy task.

Perl:
```
#!/usr/bin/perl
open(IN, "<log.txt");
open(OUT, ">>out.txt");

@lines = <IN>;

foreach $_ (@lines)
{
    if(m/(Error|Alert)/ig) { print OUT; }
}
close(IN);
close(OUT);
```You can add the rest.

---

### Post by Black Magix on 2011-07-14
> **cgroza said:**
> I hope you know perl. Really this is a relatively easy task.

Perl:
```
#!/usr/bin/perl
open(IN, "<log.txt");
open(OUT, ">>out.txt");

@lines = <IN>;

foreach $_ (@lines)
{
    if(m/(Error|Alert)/ig) { print OUT; }
}
close(IN);
close(OUT);
```
You can add the rest.


I don't know perl but I can read that easily enough. that's exactly what I want it to do...now to figure out how to write and run perl on solaris.

---

### Post by Bachstelze on 2011-07-14
```
grep -E "(Alert|Error)" log.txt output.txt
```

---

