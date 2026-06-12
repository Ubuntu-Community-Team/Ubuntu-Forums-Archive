---
title: "python and os.system(&quot;grep from *&quot;)"
date: 2011-01-15
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-01-15
I'm trying to assign the stuff that os.system("grep from *") returns, but i can't do it normally. How do i do it? Whenever i try to simply assign it to a variable it gives x = 0

---

### Post by Some Penguin on 2011-01-15
What a process returns is a single integer.  What you're looking for is the *output*, not the return value.

That said, I'm sure Python has its own regular-expression system, so why are you spawning two additional processes (a shell, to interpret the command; grep, the command actually being run) instead of using Python itself?

---

### Post by flyingsliverfin on 2011-01-15
i guess i can look up the python equivalent of bash grep... Its just that im familiar with grep and bash for maintanance tasks

---

### Post by MadCow108 on 2011-01-16
with python 2.7 there is the convenience function check_output to do that.
for older versions you need to use Popen + communicate
[http://docs.python.org/library/subprocess.html](http://docs.python.org/library/subprocess.html)

```

import subprocess, glob
files = glob.glob("*")
if len(files) > 0:
  grep = subprocess.Popen(["grep", "from"] + files, stdout=PIPE)
  print grep.communicate()[0]

```
use glob to get the files and do not use shell=True. why is mentioned on the help page.

of course you could also do what grep does directly in python in a similar amount of lines.

---

### Post by slavik on 2011-01-16
I gotta ask, what's the context of what you are trying to do.

And because I like Perl more:
```

for my $file (glob("*")) {
  open FILE, $file or die $!;
  print grep "blah", <FILE>;
  close FILE;
}

```

---

### Post by ghostdog74 on 2011-01-16
> **flyingsliverfin said:**
> I'm trying to assign the stuff that os.system("grep from *") returns, but i can't do it normally. How do i do it? Whenever i try to simply assign it to a variable it gives x = 0

if you want to use Python, then use Python. Why mix shell and Python together? Unless you really have no choice, then do it this way. It makes your code non portable.
```

for file in os.listdir("."):
    if os.path.isfile(file):
        for line in open(file):
            if "pattern" in line:
                print line.rstrip()

```

---

### Post by ghostdog74 on 2011-01-16
> **slavik said:**
> 
And because I like Perl more:

Its a Python question. Why the Perl stuff?

---

### Post by flyingsliverfin on 2011-01-16
> **ghostdog74 said:**
> if you want to use Python, then use Python. Why mix shell and Python together? Unless you really have no choice, then do it this way. It makes your code non portable.
```

for file in os.listdir("."):
    if os.path.isfile(file):
        for line in open(file):
            if "pattern" in line:
                print line.rstrip()

```

I like this one :) I'm still learning python, but this one makes sense. I'm short on time to do this (couple minutes here and there, between hw) so i don't have time to look up stuff i dont know (like glob)

Thanks

---

### Post by flyingsliverfin on 2011-01-16
> **ghostdog74 said:**
> if you want to use Python, then use Python. Why mix shell and Python together? Unless you really have no choice, then do it this way. It makes your code non portable.
```

for file in os.listdir("."):
    if os.path.isfile(file):
        for line in open(file):
            if "pattern" in line:
                print line.rstrip()

```

I like this one :) I'm still learning python, but this one makes sense. I'm short on time to do this (couple minutes here and there, between hw) so i don't have time to look up stuff i dont know (like glob)

Thanks

---

