---
title: "Bash: Getting everything into 1 line"
date: 2005-11-23
forum: Programming Talk
---

### Post by bashhelp on 2005-11-23
Oh, great!  I just typed up my whole message, spell checked it, and the creativity is all gone when I clicked submit, because my login timed out!  Here I go again.

Here's the sample script:

```

#!/bin/bash
echo -n " Link:  "
read link
echo -n "Start:  "
read start
echo -n "  End:  "
read end

while test "$start" -le "$end"
do
wget -c $link$start.foo
start=$[start+1]
done
```

If I were to run this, it would look something like this:

```

bashhelp@linuxbox ~ $ ./script
 Link: http://site.com/dir/file
Start: 1999
  End: 2005

```

How do I get it to behave like this:

Task: [site] [start] [end]
```

bashhelp@linuxbox ~ $ ./script
Task: http://site.com/dir/file 1999 2005

```

Once it runs, it will download file1999.foo, file2000.foo, up until it gets to file2005.foo.

Please help?

---

### Post by 23meg on 2005-11-23
You need positional parameters. See here for the theory: [http://www.linuxcommand.org/wss0130.php]("http://www.linuxcommand.org/wss0130.php") ; the practice is up to you.

---

### Post by Leif on 2005-11-23
change your script to 

```

#!/bin/bash

for i in `seq $2 $3`;
do
wget -c $1$i.foo
done

```

then call with ./script site start end

---

### Post by bashhelp on 2005-11-23
I had no clue what that very long script was trying to tell me.  Perhaps what I wanted to know was in Lesson 13.  And it required me to have previously read the 12 other Lessons in order to understand.

But nonetheless, I really appreciate you trying to help, 23meg.

WOW, Leif!  When I first saw that, I thought it was a joke!  I thought the original script would have to be expanded 2-5 times longer to get something like that working.  Took me by surprise; 4 lines!  Thanks a lot!

---

### Post by 23meg on 2005-11-23
If you're serious about getting serious in bash, do read the linuxcommand.org lessons in order. It's the best bash primer site I've seen.

---

### Post by bashhelp on 2005-11-23
I am interested.  But for now, I am just trying out different tasks to see if it is difficult and can it do what I want or not before learning the whole thing and taking it seriously.

I would be smacking my face on the keyboard if I went half way only to know what I am trying to do is harder than I thought.

---

### Post by 23meg on 2005-11-23
It's never too hard; there's always help, don't be afraid. Bash is very rewarding.

---

