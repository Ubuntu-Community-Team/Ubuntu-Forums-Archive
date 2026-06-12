---
title: "Named pipes and unnamed pipes , what are the differences , when to use it?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by sohaikia1 on 2008-07-06
Hi,

I would like to know the differences between '|' and '>', how do they work and in what circumstances should I use them. 

Thanks

---

### Post by sdennie on 2008-07-06
The title of your thread is misleading.  "|" is pipe and ">" is redirection.  The difference is that piping a command means that you are sending its output to another command for processing whereas redirecting the output of a command usually means you are going to create a file with the output of the command.  For instance:

```

du | sort -n > file_usage.txt

```

That means, "run du, send the output to sort and then send that output to a file called file_usage.txt".

---

### Post by bab1 on 2008-07-06
You can also redirect to a device such as a printer as in:```
du | sort -n > lpt1
```

---

### Post by sohaikia1 on 2008-07-06
So for example if I type in this command

cat>file1.txt

and file1.txt does not exist , which one will create the file? the shell or the kernel?

---

### Post by sdennie on 2008-07-06
> **sohaikia1 said:**
> So for example if I type in this command

cat>file1.txt

and file1.txt does not exist , which one will create the file? the shell or the kernel?

That particular command has strange properties.  "cat > file1.txt" will create a file called file1.txt but, you'll have to type into the terminal to put information into file1.txt and then hit Ctrl-D to save the file (probably after hitting enter).

---

### Post by bab1 on 2008-07-06
The shell talks to the library of functions (usually in C) to crate the file.  The command  cat is the "calling" program.

You have to cat something.  As in:
```
cat /etc/fstab > afile.txt
```

---

### Post by sohaikia1 on 2008-07-06
Thanks guys, that clears most of the confusion that I had. So basically pipes and redirection are shell features right?

---

### Post by bab1 on 2008-07-06
yes

try this:```
man bash
```

in a terminal

---

