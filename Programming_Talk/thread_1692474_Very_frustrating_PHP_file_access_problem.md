---
title: "Very frustrating PHP file access problem"
date: 2011-02-21
forum: Programming Talk
---

### Post by gradysghost on 2011-02-21
I'm having a really annoying problem.  Maybe you folks can help me.

I've got a LAMP stack running.  It works in every regard except this.  Take this code for example:

```
$fh = fopen("test.txt", 'r');
$data = fgets($fh);
fclose($fh);
echo $data;
```

This *should* open test.txt (assume for the time being that it's a real file that actually exists and contains plain text), pull the first line of text from it, and print that.

Not on my server!  I get no errors at all.  None.  But it won't open.  I also can't get any files to write.  fopen just fails all the time.  This is true even if I grant full permissions on the file and/or the directory it's in.

What's going on here?  fopen doesn't work all of a sudden!

---

### Post by LoneWolfJack on 2011-02-21
```

$fh = fopen("test.txt", 'r');
if($fh)
{echo 'ya';}
else
{echo 'nah';}

```

if it says nah, the file almost certainly doesn't exist.

---

