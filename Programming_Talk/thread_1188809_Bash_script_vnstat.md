---
title: "Bash script vnstat"
date: 2009-06-16
forum: Programming Talk
---

### Post by linuxrockz on 2009-06-16
Hi all :)

Here is my bash script. I want it to return the current percentage of my net usage (download) so that I can use the value as *execbar* in conky. (My monthly limit being 1024MiB).

```
#!/bin/bash
# Read internet usage from vnstat and store value of download in file.txt
vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3}' > file.txt
# Store the value in file.txt as a variable usage
usage= `cat file.txt`
# Calculate the usage percentage with two decimal points and store the value in file1.txt
echo "scale=2; ($usage/1024)*100" | bc > file1.txt
```

When I execute it i get the following error

```

./bashcalc.sh: line 5: 962.57: command not found
(standard_in) 1: syntax error

```

By the way this is my first bash script and I am no way a programmer, I am just an end user. Frankly speaking I know nothing of programming. :(

Any help would be appreciated.

---

### Post by ghostdog74 on 2009-06-16
put set -x in your script and run it again

---

### Post by kpkeerthi on 2009-06-16
It could be the space after the = in line#5

---

### Post by linuxrockz on 2009-06-16
Thanks a lot kpkeerthi the bug was the space :biggrin: removing it solved the problem.
And thanks to you too ghostdog74; i learnt a new thing "set -x" :D

---

