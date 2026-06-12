---
title: "Type code directly into terminal window with gcc?"
date: 2009-01-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-22
I heard I can type the program directly into the terminal window, in gcc with the following command:
```

gcc -E - -o output

```
Then it lets me write the code. But how to stop writing it? Like when I'm finished, how can I tell gcc I want to compile it? Keystroke?

---

### Post by lykwydchykyn on 2009-01-22
Typically, ctrl-D exits a buffer like that.  Though I haven't tried doing this in gcc in particular.

---

### Post by nvteighen on 2009-01-22
Hmm... not a truly interesting feature: it just creates a preprocessed C file. It would have been great if it was compiled and then executed as perl (the Perl interpreter) does.

---

### Post by s|fr on 2009-01-22
thats one of the main difference between interpreters and compilers. gcc is a compiler.

---

### Post by nvteighen on 2009-01-23
> **s|fr said:**
> thats one of the main difference between interpreters and compilers. gcc is a compiler.
Yeah, but I guess it wouldn't be that difficult to tell gcc to take input from stdin and then compile...

---

### Post by wmcbrine on 2009-01-23
gcc - -o output && ./output && rm output

---

### Post by crazyfuturamanoob on 2009-01-23
Thats a fast way to test variable sizes in C, but for writing programs... :D

But I got this, even with sudo:
```

bash: ./output: Permission denied

```
So that was from the command in above post.

---

### Post by lykwydchykyn on 2009-01-23
> **wmcbrine said:**
> gcc - -o output && ./output && rm output

That'd be:
```

gcc - -o output && chmod +x output && ./output && rm output

```

;)

---

### Post by Reiger on 2009-01-23
And you can't just pipe the output of an echo to your gcc ? ;)

---

### Post by wmcbrine on 2009-01-23
> **lykwydchykyn said:**
> That'd be:
```

gcc - -o output && chmod +x output && ./output && rm output

```You guys must have a weird umask or something. I get the executable flag set automatically.

But, I admit, I typed that without testing it. I don't have to chmod +x, but I do have to add "-x c":

gcc -x c - -o output && ./output && rm output

---

### Post by crazyfuturamanoob on 2009-01-24
> **wmcbrine said:**
> You guys must have a weird umask or something. I get the executable flag set automatically.

But, I admit, I typed that without testing it. I don't have to chmod +x, but I do have to add "-x c":

gcc -x c - -o output && ./output && rm output

Finally, that worked. Now I just make an easy macro so I don't have to remember that. :)

---

