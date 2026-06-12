---
title: "command &quot;ls&quot; 'bug'. Suggest me a solution"
date: 2010-05-05
forum: Programming Talk
---

### Post by hakermania on 2010-05-05
Hello all. I wanted to write to a file the list of the directories placing one per line.
The only I found in its manual page was **ls --group-directories-first -1**
This shows the directories first and the files(I don't want the files at all!), placing one per line.
But the command
echo `[B]ls --group-directories-first -1` > /home/$USER/Desktop/directories`
[/B]does exactly the same with
echo `**ls` > /home/$USER/Desktop/directories`**
I mean that in the file there are no lines. All are written in the same line!
I find it a very BIG BUG!
Is there any way to list ONLY the directories in a text file placing ONE per line?
Thanks for any answers!

---

### Post by PaulM1985 on 2010-05-05
Found this after looking on google:

ls -d */

Ref: [http://www.linuxquestions.org/questions/programming-9/how-can-i-list-directories-only-in-linux-375219/](http://www.linuxquestions.org/questions/programming-9/how-can-i-list-directories-only-in-linux-375219/)

I don't think what you have said is a bug.  It says that it will group directories first, not that it will omit files.

Paul

PS.  The solution is taken straight from the website.  I haven't tested it.

---

### Post by robots.jpg on 2010-05-05
And don't use echo, that's why you're losing the newlines.  Just redirect your ls command to a file.

ls -d1 */ > /home/$USER/Desktop/directories

---

### Post by ibuclaw on 2010-05-05
There is no bug with ls here, it is working to design. Your shell examples on the other hand are written in a way that you are getting feedback you hadn't intended for.


As for finding directories, try using 'find' instead.

```
find /path -type d
```

---

### Post by Portmanteaufu on 2010-05-05
```
echo "`ls --group-directories-first -1`" > /home/$USER/Desktop/directories
``` would preserve the newlines. (Note the double-quotes.) This is how bash interprets things, not an ls issue.

---

### Post by hakermania on 2010-05-06
Thz for your answers. Very helpful.

---

