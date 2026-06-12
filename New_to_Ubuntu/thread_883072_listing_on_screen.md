---
title: "listing on screen"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by catia2000 on 2008-08-07
Hi,
I am new to this ... Just installed the server version and trying to learn Linux .... this is a simple one ...  many of the commands list more than what is shown on a screen .. how do I show output one screen at the time ?

---

### Post by Tatty on 2008-08-07
not sure if this is the best way to do it but i tend to pipe commands to "less" to do this :

<command> | less

eg...

```
locate home | less
```

---

### Post by silkstone on 2008-08-07
putting |more at the end of the command should display the output page by page.

---

### Post by sisco311 on 2008-08-07
pipe the command to [I]less
[/I]```
*command *| less
```

example:
```
dmesg | less
```

(q to quit)

---

### Post by catia2000 on 2008-08-07
Thanks .... !!

---

### Post by scorp123 on 2008-08-07
... Or you could pipe the output into a file maybe? This is useful if you e.g. want to mail the output to someone else?
```
dmesg > dmesg_output.txt
```

If you want to append output to an existing file without overwriting the previous content you could add one chevron, e.g.```
dmesg >> dmesg_output.txt
```

You could still read the file page by page later on if you need to, e.g. with the commands the other posters here have supplied.
```
less file.txt

more file.txt 
```

---

