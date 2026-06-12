---
title: "shell script to copy files from damaged hard drive."
date: 2011-04-14
forum: Programming Talk
---

### Post by mfrancis107 on 2011-04-14
I have hard drive that has lots of corrupt images on it.  However, there are more good images than corrupt ones.

When I attempt to copy a corrupt file it takes a very long time and gives errors.

What I want is a script that will go through and copy each file one at a time.  If it takes more than say 10 seconds to copy, cancel the process and move on to the next image.

---

### Post by Crusty Old Fart on 2011-04-16
Howdy:

I started writing a script for you, but part of my code was using the find command. I began to wonder if the find command would hang just like your copy command is hanging.

So...before I put too much work into this little project, I'd like to ask you to perform a test on a corrupt file.

Suppose the corrupt file is named: badfile.jpg

What happens if you get into the directory where the corrupt file is located and you issue the following command 
```

find . -name badfile.jpg -type f -print

```Do you get output that looks like this:
```

./badfile.jpg

```Does the command hang?

Please let me know...thanks,

Crusty

---

