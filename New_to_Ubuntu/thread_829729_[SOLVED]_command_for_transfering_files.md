---
title: "[SOLVED] command for transfering files"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-06-15
I have hundreds of jpeg files on my desktop. What command would I use to transfer them all into home/me/photos, removing them from home/me/Desktop at the same time. There is nothing else on my desktop btw.
 Thanks in advance.

---

### Post by quinnten83 on 2008-06-15
probably something like

```
mv ~/Desktop/*.jpg ~/photos
```

but don't quote me on the syntax
Als i would use

```
cp ~/Desktop/*.jpg ~/photos
```
and then 
```
mv ~/Desktop/*.jpg
```
Which means, copy first and then delete.

But again, don't quote me on the syntax, because I understand the essence of those commands but haven't been able to work properly with them yet.

---

### Post by acidsolution on 2008-06-15
If you want to move than 
```

mv /home/me/Desktop/*.jpg  ../photos/

```

---

### Post by wormser on 2008-06-15
> **quinnten83 said:**
> 
```
mv ~/Desktop/*.jpg ~/photos
```.

That looks right to me.

---

### Post by nothingspecial on 2008-06-15
```
cp ~/Desktop/*.jpg ~/photos
```

This moved them thankyou
```

mv ~/Desktop/*.jpg
```

That didn`t remove them. So I tried - 

```
rm ~/Desktop/*.jpg
```

which retuned

```
rm: remove regular file `/home/me/Desktop/Photo-0001.jpg'? 
```

so I pressed y so it asked me if I wanted to remove 000.2.jpg and so on, so I pressed y 121 times and they`re all gone.

I guess I have my photo`s where I want them and not where I don`t but I`d still like to know the command that does it in 1 hit.

---

### Post by Kronie on 2008-06-15
or, you could just select'em all, ctrl+x and then ctrl+v in ~/photos :P

---

### Post by quinnten83 on 2008-06-15
according to man remove

rm -f would have done the trick.
you would not have been prompted.

---

### Post by StooJ on 2008-06-15
acidsolution's command would have been the one click wonder. So would quinnten83's first command. They are both pretty much the same. I personally prefer quinnten83's solution because copying and pasting the command would work. (Rereading the OP I notice that acidsolution's command was perfect for C&Ping too, if your username is indeed me
```

mv ~/Desktop/*.jpg ~/photos
```

mv is move files (or think of it as a "copy files then delete the originals")

~ is a nice shortcut to the current user's home directory. If you compare quinnten83's command to acidsolution's command:
```

quinnten83:   mv ~/Desktop/*.jpg ~/photos
acidsolution: mv /home/me/Desktop/*.jpg  ../photos/

```

acidsolution's example relies on your user name being "me". Obviously you would replace this with your user name, perhaps : /home/nothingspecial/Desktop
quinnten83 uses the tilda, so the command understands it as being /home/nothingspecial/Desktop automatically. If I had a user account on your computer, I would type ~/Desktop and it would resolve to /home/stooj/Desktop

I'm sure you're probably familiar with wildcards, but just in case:
* means "anything". I'll use the ls command in these examples, ls lists the contents of a directory.

```
ls *
``` will list all the files in the current directory

```
ls P*
``` will list all the files starting with the letter P in the current directory.

```
ls *.jpg
``` will list all the files with a jpg extension (any file, as long as it's a jpg picture)

So, back to quinnten83's command.

```

mv ~/Desktop/*.jpg ~/photos
```
Move all the jpg pictures on my personal desktop into my personal photos folder.

I hope this helps

---

### Post by nothingspecial on 2008-06-19
Forgot to mark this solved - sorry.

---

