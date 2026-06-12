---
title: "Using Tee and Grep together to get output but also send output to a file"
date: 2019-01-30
forum: New to Ubuntu
---

### Post by jodan87 on 2019-01-30
Hello everybody,

I recently ran into the following problem:

I want to put my output of a command into a file like this:

```
ls >> example.txt
```

but at the same time i want to see the output of it.

Now if I would type 

[HTML]ls[/HTML]

i would get as output:

```

file1
file2
file3

```

Now i want to grep only file1 and redirect the output "file1" into my example.txt while still being able to see all 3 files as output of my ls in my normal shell.

I got to the conclusion that i can use tee but i won't see the full output if I only use it with grep.

Desired result:

Input:
```
This is what I want
```

output in shell:
```

file1
file2
file3
```

example.txt
```
file1
```

---

### Post by Impavidus on 2019-01-30
Use process substitution:```
ls | tee >(grep example >> example.txt)
```
The >(...) syntax creates a named pipe. tee will write to this pipe and to the terminal, the shell connects standard input of whatever is in the parentheses to the reading end of the pipe.

Edit: An interesting example I occasionally run:
```
cat file1.tex file2.tex file3.tex | sed -f glsstuff.sed.00 | sed -f glsstuff.sed.01 | sed -f filter.sed | \
tr -s ' ' '\n' | tr '[:upper:]' '[:lower:]' | sed /^$/d | sort | tee >(uniq -c | sort -no wordfreq.txt) | uniq | \
tee wordlist.txt | while read w; do echo ${#w} $w; done | sort -no wordlength.txt
```
This reads a bunch of .tex files, runs them through some filters and uses tee to generate three word lists: all words by frequency, alphabetically and by length. Note the process substitution on the second line.

---

