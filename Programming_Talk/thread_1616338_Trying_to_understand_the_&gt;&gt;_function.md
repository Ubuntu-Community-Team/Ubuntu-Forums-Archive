---
title: "Trying to understand the &gt;&gt; function"
date: 2010-11-08
forum: Programming Talk
---

### Post by Drenriza on 2010-11-08
im using the following command
```
diff test2 test1 | grep -E '^>|^<'
```What i want to do is check to different files, to see what new lines that has been added.
when doing this i get this output (random text i added, to test the command)
```
cristian@cristian-Znote:~/Skrivebord$ diff test2 test1 | grep -E '^>|^<'
> las vegas(ny)
> jail(ny)
> jaw(ny)
```What i would like to do with this output is copying it to a file with the > symbol.
But when i try to do
```
diff test2 test1 | grep -E '^>|^<' | > test3
```i just get an empty file. I dont get the output of the previously command pasted into the file. Hope you can see what i am trying to do. Dont rly know how to explane it :(

Anyone who can tell me what i'm doing wrong?
Thanks on advance.

---

### Post by r-senior on 2010-11-08
You don't need the pipe ('|') before the redirection ('>').

```

diff test2 test1 | grep -E '^>|^<' > test3

```

or, if you want to append each time ... 

```

diff test2 test1 | grep -E '^>|^<' >> test3

```

---

### Post by Drenriza on 2010-11-08
Thanks, so far so good :)

But when i do > diff test2 test1 | grep -E '^>|^<' > test3How do i then place the test3 in a pre-defined path?
for example i want to place it in > /home/cristian/something/something

---

### Post by r-senior on 2010-11-08
```

$ diff test2 test1 | grep -E '^>|^<' > /home/cristian/something/something/test3

```

or use the ~ expansion for your home directory: 

```

$ diff test2 test1 | grep -E '^>|^<' > ~/something/something/test3

```

---

### Post by Drenriza on 2010-11-08
Thanks alot :)

---

