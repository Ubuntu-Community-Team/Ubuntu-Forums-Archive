---
title: "[SOLVED] Stupid question-copying files w/sub directories"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by timandjulz on 2008-10-20
Hi all... stupid question, but how do I copy files in sub directories to another folder.

e.g. I want to copy ~/Music/*.m4a to ~/Convert/*.m4a preserving the folder structure.

In Windows, this would be:
```
copy c:\Music\*.m4a c:\Convert\*.* /s
```

I tried this in Linux:
```
cp -a -r -t ~/Convert *.m4a
```

There has to be a simple way to do this.  Help!

Thanks,
Tim

---

### Post by houbysoft.xf.cz on 2008-10-20
This should be as simple as
```

cp ~/Music/*.m4a ~/Convert

```... I think I don't really understand your question : do you mean copying all files under ~/Music, even in subdirs?
If yes that would be something like
```

cp ~/Music/*/*.m4a ~/Convert

```, but not sure, I'm not on linux now can't test it out, I'm afraid this would recursively include every .m4a file in your fs.

---

### Post by unutbu on 2008-10-20
```

cd ~/Music
find . -name "*.m4a" -print | rsync -a --files-from - ~/Music/ ~/Convert
```

---

### Post by timandjulz on 2008-10-20
> **houbysoft.xf.cz said:**
> This should be as simple as
```

cp ~/Music/*.m4a ~/Convert

```

It should be that simple, shouldn't it.  But it isn't.  I am indeed trying to copy all m4a files in ~/Music and all sub directories.  So if ~/Music/a/xyz.m4a exists, I wanted it copied to ~/Convert/a/xyz.m4a.

I tried both your examples and they don't work.  Very frustrating.

"cp: cannot stat '/home/tim/Music/*/*.m4a'  No such file or directory"

I get the same regardless of */*.m4a or *.m4a.

---

### Post by Rolcol on 2008-10-20
> **timandjulz said:**
> Hi all... stupid question, but how do I copy files in sub directories to another folder.

e.g. I want to copy ~/Music/*.m4a to ~/Convert/*.m4a preserving the folder structure.

In Windows, this would be:
```
copy c:\Music\*.m4a c:\Convert\*.* /s
```

I tried this in Linux:
```
cp -a -r -t ~/Convert *.m4a
```

There has to be a simple way to do this.  Help!

Thanks,
Tim

Hm... Are you trying to copy every file that ends in .m4a inside of ~/Music and anything inside?  I don't think cp checks recursively throughout the subfolders unless you specify them manually.  You can try this:
```

find ~/Music/ -iname "*.m4a" -exec cp {} ~/Convert/ \;
```

What that command will do is find any files matching *.m4a within the folder ~/Music and then execute the command cp {} ~/Convert/ \;.  {} is automatically replaced with the path to the file.

**Edit:** I just tried this command to copy all .txt files throughout my computer into ~/Desktop/text and it didn't keep its folder structure.  Hold on while i find it.

---

### Post by timandjulz on 2008-10-20
> **unutbu said:**
> ```

cd ~/Music
find . -name "*.m4a" -print | rsync -a --files-from - ~/Music/ ~/Convert
```

unutbu, there are truly many ways to skin a cat in Linux.

Shouldn't there be an easier way?  I was trying to figure out a simpler statement like:

```
find . -iname '*.m4a' -exec cp -a {} ~/Convert/
```

But that doesn't work.  I am trying your rsync method but would like a more straight forward (and easier to remember) command.

Thanks in advance,
Tim

---

### Post by Rolcol on 2008-10-20
> **timandjulz said:**
> unutbu, there are truly many ways to skin a cat in Linux.

Shouldn't there be an easier way?  I was trying to figure out a simpler statement like:

```
find . -iname '*.m4a' -exec cp -a {} ~/Convert/
```

But that doesn't work.  I am trying your rsync method but would like a more straight forward (and easier to remember) command.

Thanks in advance,
Tim
You may not want to try mine then if it looks too complicated but I got it to save the folder hierarchy.

```
find ~/Music/ -iname "*.m4a" -print -exec  rsync -aR {} ~/Convert/ \;

```

---

### Post by timandjulz on 2008-10-20
> **Rolcol said:**
> You may not want to try mine then if it looks too complicated but I got it to save the folder heirarchy.

```
find ~/Music/ -iname "*.m4a" -print -exec  rsync -aR {} ~/Convert/ \;

```

Rolcol, this is close.  It seems like everything should be doable with rsync.  I tried this:

```
rsync -av --include=*.m4a ~/Music ~/Convert
```

But it didn't work.  Is there a way to accomplish the copy in one straight forward command?

---

### Post by timandjulz on 2008-10-20
> **Rolcol said:**
> You may not want to try mine then if it looks too complicated but I got it to save the folder heirarchy.

```
find ~/Music/ -iname "*.m4a" -print -exec  rsync -aR {} ~/Convert/ \;

```

I am going to call Rolcol's the right answer though several solutions were provided.  Rolcol is the cleanest (in my opinion).

Thanks to everyone for their help!  It is awesome how the Ubuntu community is so helpful!  =D>

Tim

---

### Post by unutbu on 2008-10-20
LOL, am I too late? :)

You are right timandjulz, there is a way to do this with one rsync command:

```
rsync -avm --include='*.m4a' -f 'hide,! */' ~/Music/ ~/Convert
```

PS. The command
```

find ~/Music/ -iname "*.m4a" -print -exec  rsync -aR {} ~/Convert/ \;
```

works fine for small jobs, but you might want to avoid this if you have lots of files to transfer. It spawns a new rsync process for each file, which will make the job run slower than if you can combine all the transferring into one rsync command.

---

### Post by garyed on 2008-10-21
Wow! I can't believe this is so complicated. 
I've copied the answer for prosperity but this is a rare occasion that I have 
to say Windows beats Linux on the command line.
Isn't this a bug in the cp command because if you use:
```
 cp -a ./music/* ./any_diredctory
``` 
it copies & preserves the directory structure but if you use:
```
 cp -a ./music/*.m4a ./any_diredctory
``` 
it doesn't.

---

### Post by timandjulz on 2008-10-21
> **unutbu said:**
> LOL, am I too late? :)

You are right timandjulz, there is a way to do this with one rsync command:

```
rsync -avm --include='*.m4a' -f 'hide,! */' ~/Music/ ~/Convert
```


Exactly what I am looking for.  But I don't understand your -f filter rule.  Can you explain what it is doing?

---

### Post by sethvath on 2008-10-21
My guess is -f = --filter=RULE

---

### Post by timandjulz on 2008-10-21
Yes, but what does the filter rule 'hide,! */' do?

---

### Post by unutbu on 2008-10-22
'*/' is a pattern which matches 'any directory'
'! */' matches anything which is not a directory (i.e. a file)
'hide,! */' means hide all files

Filter rules are applied in order, and the first rule that matches is applied.

--include='*.m4a' has precedence, so if a file ends in .m4a, it is included.
Any other file gets excluded from the list of files to transfer.

---

### Post by timandjulz on 2008-10-24
That is a very clear explanation.  Many thanks unutbu.

---

