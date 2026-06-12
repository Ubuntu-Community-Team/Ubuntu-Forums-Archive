---
title: "perl &quot;-d&quot; unreliable? What am I doing wrong?"
date: 2009-12-23
forum: Programming Talk
---

### Post by Xavier Oddmon on 2009-12-23
Hello! I am writing a program to batch rename files as a way to learn how to make graphical interfaces with perl. In the interface, the user selects a directory to work in, and it is supposed to list all of the files. It is not supposed to list directories. However, it is behaving in a way I can't quite explain. Here's the structure of the directory i'm working in.

```

Perl
   |-- renamer
   |   |-- DIR
   |   |   |-- a.txt
   |   |   |-- b.txt
   |   |   |-- c.txt
   |   |   `-- MY
   |   |-- Directory With Spaces
   |   |   `-- <Contains many many files>
   |   |--rename.pl
   |   |--rename.pl~
   |   `--window.glade
   `-- test
       |-- FIFO
       `-- Stopwatch

```
Now, when i point it to "renamer", it just lists rename.pl, rename.pl~, and window.glade. However, when I point it to DIR, it lists a.txt, b.txt, c.txt, and MY. It should not list MY. (It also doesn't help if there are files in MY).

Here's the code that's handling the displaying of that folder.
```

	foreach $f (@allthings)
	{
		if (-d $f)
		{
			print "$f is a directory\n";
		}
		else
		{
			print "pushing $f\n";
			push @allfiles, $f;
			$list = "$list$f\n";
		}
	}

```

And finally, for completeness, here's the output in the terminal:
```

chris@chris-laptop:~/Perl/renamer$ perl rename.pl

pushing rename.pl
pushing rename.pl~
DIR is a directory
.. is a directory
. is a directory
Directory With Spaces is a directory
pushing window.glade
                             --note: this is where i changed directory to "MY"
pushing a.txt
.. is a directory
pushing b.txt
. is a directory
pushing c.txt
pushing MY

```

This happens on and off all over my filesystem. What's going on:confused: This is very frustrating.

---

### Post by ghostdog74 on 2009-12-23
you might want to try File::Find. perldoc File::Find for more info. Also you can use find2perl.

---

### Post by matsuzine on 2009-12-29
Hey, did you ever get this resolved?  I tried your code in many variations on my machine, and wasn't able to reproduce the error.

---

### Post by Xavier Oddmon on 2009-12-29
Oh, sorry, i put this on hold when i got a new wacom tablet that i've been trying to get recognized. But I spent hours with the "-d" function, to no avail. I'm going to end up using File::Find.

---

