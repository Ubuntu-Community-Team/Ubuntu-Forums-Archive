---
title: "Bash script: Check if a directory and file already exists in a different directory"
date: 2014-06-01
forum: Programming Talk
---

### Post by vikler on 2014-06-01
[COLOR=#000000][FONT=Arial]I need a help writing a script. So basically I have directories named by current date, like 01-06-2014 02-06-2014 and so on each of these directories has files and subdirectories inside. But sometimes there are duplicates. Like 01-06-2014 and 02-06-2014 may both have directory named d01 or file named f001.jpg, and so on[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]What I want to do is get rid of these same files and subdirectories, so that I don't use too much space (and besides, what's the point in having duplicates)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]What is the easiest way to do it? Can someone help? please![/FONT][/COLOR]

---

### Post by CharlesA on 2014-06-01
Check out fdupes

It should be in the repos.

---

### Post by ofnuts on 2014-06-02
Same name doesn't imply same content, and vice-versa...

---

### Post by CharlesA on 2014-06-02
> **ofnuts said:**
> Same name doesn't imply same content, and vice-versa...

+1. Which is why fdupes uses other methods.
[http://linux.die.net/man/1/fdupes](http://linux.die.net/man/1/fdupes)

---

### Post by matt_symes on 2014-06-02
Hi

+1 for fdupes. A great little tool.

```
sudo apt-get install fdupes
```

Hey Charles. I hope life is peachy :)

Kind regards

---

