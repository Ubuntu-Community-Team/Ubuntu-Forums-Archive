---
title: "How do I change to a directory that has spaces in its name?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-10
I'm trying to get a list of directories on a external harddrive, but the drive name has a space in it. I haven't been able to figure out how to switch to the directory, so that I can invoke "ls -h" 

It appears that completion (using the tab key to complete filenames) isn't enabled on my version of bash, and I'm too scared to attempt to edit the file where I could enable it. 

The command I'm currently using looks like this: 

cd /Volumes/JPS External1

Which, of course, results in a "No such file or directory" message from the Terminal.

Thanks for your help.

---

### Post by idoitprone on 2012-04-10
> **jps2012 said:**
> I'm trying to get a list of directories on a external harddrive, but the drive name has a space in it. I haven't been able to figure out how to switch to the directory, so that I can invoke "ls -h" 

It appears that completion (using the tab key to complete filenames) isn't enabled on my version of bash, and I'm too scared to attempt to edit the file where I could enable it. 

The command I'm currently using looks like this: 

cd /Volumes/JPS External1

Which, of course, results in a "No such file or directory" message from the Terminal.

Thanks for your help.

backslash


cd /Volumes/JPS\ External1

---

### Post by jjbasken on 2012-04-10
I think you can wrap the directory with the space within quotes i.e. cd /Volumes/"JPS External1"

---

### Post by idoitprone on 2012-04-10
> **jjbasken said:**
> I think you can wrap the directory with the space within quotes i.e. cd /Volumes/"JPS External1"

yep

---

### Post by llamabr on 2012-04-10
And your bash most definitely has tab completion.  Hit tab twice to see the conflict.

---

### Post by jps2012 on 2012-04-10
That did it. I used the quote option. You guys are great. I wish you'd take over the stock market and start giving advice on finance.

---

