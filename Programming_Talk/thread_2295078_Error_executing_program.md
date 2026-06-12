---
title: "Error executing program"
date: 2015-09-15
forum: Programming Talk
---

### Post by josh148 on 2015-09-15
I am currently having an issue with executing my program. I have already compiled the program without any issues but for some reason when I run the program it gives me "Error: Missing switch -c." I can successfully run other programs so I am not really sure what it causing it. I have looked around and cant find anything about this error code or how to fix it. Any assistance would be greatly appreciated. Thanks in advance.

---

### Post by spjackson on 2015-09-16
Welcome to the forums.

There's a lot of missing detail here which makes it difficult to guess what's going on.

How are you running the program? Is it from the command line, in which case what exactly are you typing to run it? If it's from an IDE, please provide details.
What is your program called?
Could you post your source code?

My best guess is that it isn't trying to run your program but something else e.g. an alias, a shell built-in command or an installed program.

What happens if from the command line you specify the full path, e.g. type
```

/path/to/my/program/thing

```

---

