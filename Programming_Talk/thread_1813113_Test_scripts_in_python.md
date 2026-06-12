---
title: "Test scripts in python"
date: 2011-07-27
forum: Programming Talk
---

### Post by gameguy on 2011-07-27
I was trying to make a testing script in python, but I don't understand it completely.
I understand that I need this (not sure if this is exactly it, but it's at least pretty close):

python program.py < test1.in | diff - test1.out

basically, here is my folder structure.
program.py
tests/
    test1.in
    test2.in
    test1.out
    test2.out
    other.in
    other.out

I want a .sh file which will repeatedly run that line for all test cases. Basically, here's my pseudo code
get tests/*.in
for each result:
run "python program.py < tests/testname.in | diff - testname.out"

---

### Post by Bachstelze on 2011-07-27
```
for i in *.in; do file=`basename -s .in "$i"`; python program.py < $file.in | diff - $file.out; done
```

---

### Post by hakermania on 2011-07-27
> **Bachstelze said:**
> ```
for i in *.in; do file=`basename -s .in "$i"`; python program.py < $file.in | diff - $file.out; done
```

Nice solution :D

I cannot help but comment that you should prefer $() instead of `` :popcorn:

---

### Post by gameguy on 2011-07-27
when I run it I get this message:
```

basename: invalid option -- 's'
Try `basename --help' for more information.
ms.sh: 1: cannot open .in: No such file
diff: .out: No such file or directory
basename: invalid option -- 's'
Try `basename --help' for more information.
diff: .out: No such file or directory
ms.sh: 1: cannot open .in: No such file
basename: invalid option -- 's'
Try `basename --help' for more information.
diff: .out: No such file or directory
ms.sh: 1: cannot open .in: No such file

```
I'm running ubuntu 11.04, if it helps.
Also, how do I make it so instead of looking for .in files, it looks for .in files in the tests directory.

---

### Post by Bachstelze on 2011-07-27
Hmm yeah, my mistake, the -s syntax is non standard. Instead do

```
for i in *.in; do file=`basename "$i" ".in"`; python program.py < $file.in | diff - $file.out; done
```

> **gameguy said:**
> 
Also, how do I make it so instead of looking for .in files, it looks for .in files in the tests directory.

Just add a [font=monospace]cd test[/font] at the top of your script.

---

### Post by gameguy on 2011-07-28
```

cd tests
echo "Entered directory tests"
for i in *.in;
    do file=`basename "$i" ".in"`;
    echo "$file found"
    python ../main.py < $file.in | diff - $file.out;
    done

```

Thanks a heap. A few minor modifications needed to be done, and I decided to make it span over several lines, but that was easy enough.
Thanks :D

---

### Post by Bachstelze on 2011-07-28
A more conventional way to indent it would be

```

cd tests
echo "Entered directory tests"
for i in *.in; do
    file=`basename "$i" ".in"`;
    echo "$file found"
    python ../main.py < $file.in | diff - $file.out;
done

```

And you don't need the semicolons (except the one in the for line if you put do on the same line, otherwise you can omit that one too).

---

