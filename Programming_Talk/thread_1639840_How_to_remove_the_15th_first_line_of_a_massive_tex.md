---
title: "How to remove the 15th first line of a massive text file?"
date: 2010-12-07
forum: Programming Talk
---

### Post by hasannoori on 2010-12-07
Hi guys

I have a **much massive text file with about 6Gb of data**.

I want to remove for example first 15 lines of file, but how?
you may say that the answer is easy: "use gedit";
but since may file is much massive gedit and nano
cann't open the file in a finite time.
 I'm using the following script:
```
#!/bin/sh
tail -n +num filename.txt > result_filename.txt

```
(whereas num mean the numbber)

[U]I think that it dos not work properly,
because I cann't verify the result file.[/U]

Any suggestion or advise are welcome!

---

### Post by Zugzwang on 2010-12-07
```

tail -n +16 filename.txt > result_filename.txt

```

Tail outputs the result to the terminal unless you reroute it to your target file. Always route the data to a different file.

---

### Post by yeleek on 2010-12-07
# delete the first 10 lines of a file
 sed '1,10d'

change appropriately

[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

---

### Post by hasannoori on 2010-12-07
> **Zugzwang said:**
> ```

tail -n +16 filename.txt > result_filename.txt

```

Tail outputs the result to the terminal unless you reroute it to your target file. Always route the data to a different file.

Thank for you response.

I know, I used the same code.

the code I wrote at the first was wrong!

---

