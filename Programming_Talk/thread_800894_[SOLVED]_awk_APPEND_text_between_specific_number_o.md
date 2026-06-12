---
title: "[SOLVED] awk APPEND text between specific number of records"
date: 2008-05-20
forum: Programming Talk
---

### Post by Claus7 on 2008-05-20
Hello,

I was able to *replace* text between certain number of records here :
[http://ubuntuforums.org/showthread.php?t=800203](http://ubuntuforums.org/showthread.php?t=800203), yet is it possible with awk to **append** text while all the other file to remain intact? For example we want to append text in a file between line 10 and 20 and to have it like this :

line1
line2
...
line9
append line 1
append line 2
append line 3
...
append line 20
line 10
line 11
and so on the rest of the file

Regards!

---

### Post by stroyan on 2008-05-20
```
 awk '{if (NR==10){for (i=1;i<=20;i++){print "append line " i}};print}' inputfile 
```

---

### Post by nick_h on 2008-05-20
You can do something very similar to your last example - you don't need the *next* command.

```
awk '    {print}
NR == 10 {printf "%6d %5d %5d  %10.5f  %15.2f \n", 4,5,6,7,8;
	  printf "%6d %5d %5d  %10.5f  %15.2f \n", 4,5,6,7,8}
' file
```

---

### Post by ghostdog74 on 2008-05-21
> **nick_h said:**
> You can do something very similar to your last example - you don't need the *next* command.

```
awk '    {print}
NR == 10 {printf "%6d %5d %5d  %10.5f  %15.2f \n", 4,5,6,7,8;
	  printf "%6d %5d %5d  %10.5f  %15.2f \n", 4,5,6,7,8}
' file
```

maybe i misinterpret something, but does the above produce the same output as OP's original solution? Or is this another different requirement?
```

awk '{
      if (NR>=10 && NR<=20)
      {printf "%6d %5d %5d  %10.5f  %15.2f \n", 4,5,6,7,8}
      else
      {print $0 }
     }' input > output

```

---

### Post by nick_h on 2008-05-21
> maybe i misinterpret something, but does the above produce the same output as OP's original solution? Or is this another different requirement?
Maybe I got it wrong but the problem seemed very similar to the original problem in the other post.

The script I posted simply matches two patterns. The first matches all lines and prints the line.  All lines in the original file are printed.

The second pattern matches line 10 after the previous pattern has printed the line.  This pattern in my example just inserts two lines but could insert any number.

---

### Post by Claus7 on 2008-05-23
Hello,

thank you all for your responses. The difference with my previous thread is that we insert lines above the old ones, in other words the lines in the old file are overwritten, whereas in this post no lines are overwritten in the original file, yet the new lines are inserted where we want them to be while the rest of the file remains intact. *nich_h* your response is similar with that of *stroyan*, yet you have always to type in every line manualy what you want to insert. The other procedure is more automated. Both of your posts are working though. 

Regards!

---

### Post by nick_h on 2008-05-23
It's good that you have a solution.  awk is a very powerful text processing language.

I kept the inserted lines simple because I just wanted to show you the concept.

---

