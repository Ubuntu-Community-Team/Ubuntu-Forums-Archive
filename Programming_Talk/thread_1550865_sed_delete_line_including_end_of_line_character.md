---
title: "sed delete line including end of line character"
date: 2010-08-11
forum: Programming Talk
---

### Post by japhyr on 2010-08-11
I want to delete lines from a file, but I keep ending up with blank lines in place of the lines I want to delete.
```
>cat animals.txt
dogs heeler lab collie
cats tiger lion
snakes rattler copperhead
```
```
sed 's/.*cats.*//' animals.txt
dogs heeler lab collie

snakes rattler copperhead
```
What can I do to get this output?
```
dogs heeler lab collie
snakes rattler copperhead
```

---

### Post by Bachstelze on 2010-08-11
Use d to delete lines, not s:

```
firas@tsukino ~ % echo "dogs heeler lab collie
cats tiger lion
snakes rattler copperhead" | sed '/cats/d'
dogs heeler lab collie
snakes rattler copperhead

```

---

### Post by japhyr on 2010-08-11
Using d works, but to wrap things up how do I change the original file?  I thought this would work:
```
sed '/cats/d' animals.txt > animals.txt
```
But that results in an empty animals.txt file.  I came up with this:
```
sed '/cats/d' animals.txt > tempAnimals.txt; mv tempAnimals.txt animals.txt
```
This works, but is there a way to do this in one step, without using a temp file?

---

### Post by Bachstelze on 2010-08-11
The -i flag of GNU sed will do in-file editing. Note that this is only in GNU sed and is not part of [POSIX sed]("http://www.opengroup.org/onlinepubs/9699919799/utilities/sed.html"), so don't use it if you want to make your script portable. Without -i you can use tee:

```
firas@tsukino ~ % cat foo.txt 
dogs heeler lab collie
cats tiger lion
snakes rattler copperhead
firas@tsukino ~ % sed /cats/d foo.txt| tee foo.txt
dogs heeler lab collie
snakes rattler copperhead
firas@tsukino ~ % cat foo.txt 
dogs heeler lab collie
snakes rattler copperhead

```

---

### Post by japhyr on 2010-08-11
This is not working for me.  The sed command works, but the tee function seems to result in an empty file:
```
eric@eric-laptop:~/scripts$ cat animals.txt
dogs heeler lab collie
cats tiger lion
snakes rattler copperhead
eric@eric-laptop:~/scripts$ sed '/cats/d' animals.txt
dogs heeler lab collie
snakes rattler copperhead
eric@eric-laptop:~/scripts$ sed '/cats/d' animals.txt | tee animals.txt
eric@eric-laptop:~/scripts$ cat animals.txt

```

---

### Post by ghostdog74 on 2010-08-11
use -a option of tee to save to a file.

---

### Post by japhyr on 2010-08-12
The -a flag appends text to a file, so it doesn't do what I'm after:
```
eric@eric-laptop:~/scripts$ sed '/cats/d' animals.txt | tee -a animals.txt
dogs heeler lab collie
snakes rattler copperhead
eric@eric-laptop:~/scripts$ cat animals.txt
dogs heeler lab collie
cats tiger lion
snakes rattler copperhead
dogs heeler lab collie
snakes rattler copperhead

```

---

### Post by ghostdog74 on 2010-08-12
so tell me what you want to use tee for? If you want to save the changes back to the original file name, use the -i option of sed.

---

### Post by japhyr on 2010-08-12
Thank you, that is exactly what I was looking for.
```
eric@eric-laptop:~/scripts$ cat animals.txt
dogs heeler lab collie
cats tiger lion
snakes rattler copperhead
eric@eric-laptop:~/scripts$ sed -i '/cats/d' animals.txt
eric@eric-laptop:~/scripts$ cat animals.txt
dogs heeler lab collie
snakes rattler copperhead
```

---

### Post by Bachstelze on 2010-08-12
> **japhyr said:**
> Thank you, that is exactly what I was looking for.

That's exactly what I said in my message above...

---

### Post by japhyr on 2010-08-12
> **Bachstelze said:**
> That's exactly what I said in my message above...
You're right!  I didn't try the -i flag because I do want portability, but I forgot that reason for not using it when I read ghostdog's post later.

So can you or anyone else tell me why the tee function is not working consistently for me?  I have tried it about ten times, and it worked exactly once.  I keep coming back to this behavior:
```
eric@eric-laptop:~/scripts$ cat animals.txt
dogs heeler lab collie
cats tiger lion
snakes rattler copperhead
eric@eric-laptop:~/scripts$ sed /cats/d animals.txt| tee animals.txt
eric@eric-laptop:~/scripts$ cat animals.txt
eric@eric-laptop:~/scripts$ 

```

---

### Post by Bachstelze on 2010-08-12
Yeah, apparently Bash implements pipes in a different way than zsh. In zsh, it always works for me. Then I guess if you don't want to use -i, you will have to use a temporary file (that's probably what -i does behind the scenes).

---

### Post by Bachstelze on 2010-08-12
Or you can use ed. Actually, that's probably better because ed is really a file editor, unlike sed (Stream EDitor), which is not supposed to be used on files.

```
firas@itsuki:~$ cat foo.txt 
dogs heeler lab collie
cats tiger lion
snakes rattler copperhead
firas@itsuki:~$ echo -e "/cats/d\nw" | ed foo.txt 
66
50
firas@itsuki:~$ cat foo.txt 
dogs heeler lab collie
snakes rattler copperhead

```

---

### Post by ghostdog74 on 2010-08-12
> **Bachstelze said:**
> Or you can use ed. Actually, that's probably better because ed is really a file editor, unlike sed (Stream EDitor), which is not supposed to be used on files.

that's nonsense. ed or sed both are suitable for file processing. Even awk and using the shell + mv (for writing back to disk) are suitable.

---

### Post by Bachstelze on 2010-08-13
> **ghostdog74 said:**
> that's nonsense. ed or sed both are suitable for file processing. Even awk and using the shell + mv (for writing back to disk) are suitable.

By that logic, assembly is also suitable...  To me, it seems that being able to edit the file in-place makes it more suitable than a tool where you have to write to a temporary file, then replace the old file with the new one.

---

### Post by ghostdog74 on 2010-08-13
> **Bachstelze said:**
> By that logic, assembly is also suitable... 

its suitable only when its also practical. You are not making sense by suggesting assembly. Sure, assembly can do it, but do you really want to in real life? I am talking about common *nix tools that people have used for editing files since long ago. 

> 
 To me, it seems that being able to edit the file in-place makes it more suitable than a tool where you have to write to a temporary file, then replace the old file with the new one.
sed's -i options edits file in place, although at the back end, it still creates a temp file which you don't care about. I am refuting your point on "unlike sed (Stream EDitor), which is not supposed to be used on files.", which is totally nonsense.

---

