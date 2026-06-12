---
title: "Script to count and move files into subdirs"
date: 2007-08-29
forum: Programming Talk
---

### Post by qpieus on 2007-08-29
Hi - first time posting in the programming forum :)

I have a recurring task that I'm sure a script can handle easily, but I have no idea on how to construct it. I searched our forums here and didn't find anything close to what I wanted, that I could modify. Anyway, I'm hoping someone can help me out.

Here's the task: I have a directory with a lot of pictures in it, say 3000 (although it could be more or less than 3000). I want a script to move these 3000 pictures into subdirectories with 500 pictures per subdir. The subdirs do not already exist and so the script will need to create them. The subdirs can be named simply 1, 2 ,3, etc. Once the pictures are moved, then no more subdirs are needed and the script can end.

In researching this, it looks like a loop process could be employed, or maybe use a command that can count files (if that exists). I read through the bash command reference, but I was pretty confused after reading it :(

Thanks in advance for the help!

---

### Post by stylishpants on 2007-08-29
Here's a long ruby one-liner to do the job.

```
ruby -rfileutils -e 'Dir::glob("*").each_with_index { |f,i| dir=(i/500).to_s; next unless File::file?(f); Dir::mkdir(dir) unless File.exist?(dir); FileUtils::move(f,dir); }'
```

It doesn't move directories around, only files.

---

### Post by AlexThomson_NZ on 2007-08-29
Ohh I love bash hacking :)

Here's a start (showing the first 500 entries in a directory):
```
ls -1 | sort | head -500
```

Shouldn't be too hard to wrap in a loop, and supply the output to a 'mv' command

---

### Post by pmasiar on 2007-08-29
> **qpieus said:**
> Hi - first time posting in the programming forum :)

Don't worry, we like people who are eager to learn and [url=http://catb.org/~esr/faqs/smart-questions.html[ask smart questions[/url]. You will find that instead of ready-made answers we will often suggest what other questions you need to ask yourself to find out what is best answer **for your exact situation**.

> In researching this, it looks like a loop process could be employed, or maybe use a command that can count files (if that exists). I read through the bash command reference, but I was pretty confused after reading it :(

Looks like you do have some background in programming. There are multiple ways to solve this. Which way is "best"  depends what you want (what it **your** value for best). 

- Do you want just quick solution, and be done with it? 
- Do you want to become bash expert, and you want pointers to read? 
- Do you prefer to learn more universal language, which will let you solve this kind of problems, and more? 

If you want to learn non-bash way to do it (using universal language), I would suggest Python. It can do anything bash can, and much more. See wiki in my sig for more.

I will not solve it for you, just get you links, so you have some fun:

[module os](http://docs.python.org/lib/os-file-dir.html): listdir(path): Return a list containing the names of the entries in the directory
[module shutil](http://docs.python.org/lib/module-shutil.html): copy(src, dst): Copy the file src to the file or directory dst.

You can post your solution for comments if you want to.

---

### Post by qpieus on 2007-08-30
stylishpants - thanks so much. Your code worked great and it'll save me so much time (I usually manually create the subdirectories and manually move the files). Is  there a way to make the subdirectories start at 1 rather than 0? I looked at your code but it was not obvious to me how the directory names are made. Thanks again for the code, that's really cool.

AlexThomson_NZ - thanks for the start there, I appreciate your helping.

pmasiar - thanks for the python links. I do want to learn something new this year, maybe it'll be python. That's what I love about linux - there's always something to learn.

---

### Post by stylishpants on 2007-08-31
No problem.  Here it is written out on multiple lines, for easier understanding and maintenance.  This version starts numbering from one instead of zero.

```

#!/usr/bin/ruby -w
require 'fileutils'

Dir::glob("*").each_with_index do |f,i|

    next unless File::file?(f)  # ignore directories

    dir=(i/500 + 1).to_s        # choose dir name

    Dir::mkdir(dir) unless File.exist?(dir)
    FileUtils::move(f,dir)
end

```

---

### Post by ghostdog74 on 2007-08-31
> **qpieus said:**
> That's what I love about linux - there's always something to learn.

start with shell programming before going into more advanced languages.

---

### Post by pmasiar on 2007-08-31
> **ghostdog74 said:**
> start with shell programming before going into more advanced languages.

or maybe: Don't waste time on bash, learn Python which as easy to learn, can do all bash does, and can do more :-)

Every opinion about what language to learn has counter-opinion :-)

---

### Post by ghostdog74 on 2007-08-31
> **pmasiar said:**
> Don't waste time on bash, learn Python which as easy to learn, can do all bash does, and can do more :-)

this may not apply to every case. for a sysadmin, learning shell is definitely a must. Also, not every system has Python and not every environment/company policies will allow the installation of Python...so you have to fall back to good old shell..for simple tasks, shell is more handy...not forgetting, start up scripts. etc..for everything that's equal, i agree with you that Python is powerful and easy to learn.

---

### Post by pmasiar on 2007-08-31
I agree with you 100%. I just don't think bash is most usefull or "the best" language to learn for a beginner, in part because there are not many things interesting to a beginner to do in it. Bash definitely **is** very good language to know tho.

---

