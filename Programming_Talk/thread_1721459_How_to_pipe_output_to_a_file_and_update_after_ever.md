---
title: "How to pipe output to a file and update after every line"
date: 2011-04-04
forum: Programming Talk
---

### Post by chicago31415 on 2011-04-04
I am trying to pipe output to a file using
```
./command > file.dat
```

However, file.dat is updated only after several 10s of lines have been written to it. However, the output on the screen is updated after every line.

Is it possible to update file.dat after everyline so that it can be viewed using cat for example.
Thanks in advance.

---

### Post by Telengard C64 on 2011-04-04
[Bash Reference Manual, 3.6.2 Redirecting Output](http://www.gnu.org/software/bash/manual/html_node/Redirections.html#Redirections)

The **>** output redirection operator erases the file before writing to it. If you are using it inside a loop then your output file will be erased on every loop iteration which invokes the redirection. If you want to append to the output file then use the **>>** operator.

I can't tell from the OP whether or not this is the cause of your problem, but thought I'd mention it just in case.

---

### Post by chicago31415 on 2011-04-04
Thanks, but that is not my problem.

The problem is that my command is slow. What happens is that the command spits out 60-70 lines before it is visible using cat. So I have to wait till the command spits out those many lines before I see what is in the output file.

---

### Post by Arndt on 2011-04-04
> **chicago31415 said:**
> Thanks, but that is not my problem.

The problem is that my command is slow. What happens is that the command spits out 60-70 lines before it is visible using cat. So I have to wait till the command spits out those many lines before I see what is in the output file.

Your program needs to either use unbuffered/linebuffered output, or do fflush (or whatever the equivalent is in the language you're using). The default is usually to write to a rather big buffer, which is written out to the file only when it gets full.

---

### Post by MadCow108 on 2011-04-04
stdbuf -oL ./command > output

this sets the buffering mode to line buffering but read the manpage, it will not always work

---

### Post by chicago31415 on 2011-04-04
Found the solution

```
stdbuf -oL ./command > file.dat 
```

does the job. The output is now line buffered instead of the standard buffer of 4096 characters.

---

### Post by Telengard C64 on 2011-04-04
> **MadCow108 said:**
> stdbuf -oL ./command > output

Sweet! Thanks for introducing me to a new technique, MadCow108.
:)

---

### Post by Arndt on 2011-04-05
> **MadCow108 said:**
> stdbuf -oL ./command > output

this sets the buffering mode to line buffering but read the manpage, it will not always work

Where is 'stdbuf'? I don't have it, but I have coreutils installed. This is Ubuntu 10.04.

---

### Post by MadCow108 on 2011-04-05
its only been added in coreutils 8.2 which is unfortunately not in lucid.

---

### Post by geirha on 2011-04-05
There are other ways. The best is to just tell your command not to buffer. If your command has no such option, there's also unbuffer which is available in lucid's repositories. See [http://mywiki.wooledge.org/BashFAQ/009](http://mywiki.wooledge.org/BashFAQ/009)

---

### Post by jwbrase on 2011-04-05
Another thing you can do is "./command | tee output".

This will write the output both to the file and to stdout, so you don't need to cat the file to read the output.

---

