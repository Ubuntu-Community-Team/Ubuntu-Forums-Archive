---
title: "bash multiline command"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by Chiel92 on 2011-11-03
Hello,

How can I execute a command that involves multiple lines, like a for loop? Just like:

```
for i in foo bar 
do
echo $i;
done;
```

Appending a backslash at the end of each line does not work, because a for loop seems to require the parts on separate lines.

---

### Post by Majorix on 2011-11-03
Why not put them together in a .sh file?

---

### Post by Chiel92 on 2011-11-03
Yeah, that's a workaround, but I thought it'd be easy and nice if I could do it directly in the terminal. That saves a file creation, chown and opening and closing your editor.

---

### Post by Vaphell on 2011-11-03
```
for i in foo bar; do echo $i; done

while read line; do echo $line; done < input.file

if condition; then echo TRUE; else echo FALSE; fi

```

also when you type in incomplete command you will get > prompt to continue
so you can write:
```
$ while true
> do
> echo stuff
> sleep 1
> done
stuff
stuff
stuff

```
done ending the while loop automatically runs it

---

### Post by Chiel92 on 2011-11-03
> **Vaphell said:**
> ```
for i in foo bar; do echo $i; done

while read line; do echo $line; done < input.file

if condition; then echo TRUE; else echo FALSE; fi

```

also when you type in incomplete command you will get > prompt to continue
so you can write:
```
$ while true
> do
> echo stuff
> sleep 1
> done
stuff
stuff
stuff

```
done ending the while loop automatically runs it

Ahh, thanks!
I used to put slashes at the end of each line. :)

---

