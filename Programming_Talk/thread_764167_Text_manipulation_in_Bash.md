---
title: "Text manipulation in Bash"
date: 2008-04-23
forum: Programming Talk
---

### Post by manicman on 2008-04-23
Hi I'm trying to write a simple Bash script for examining file extensions.
I'm trying to detect if a file has no file extension and if so to replace it with the text NFE

So for example if the input was
```
/home/temp/file
/home/temp/file.txt
/home/temp.1/file
/home/temp.1/file.txt
```
Then the output should be
```
NFE
/home/temp/file.txt
NFE
/home/temp.1/file.txt
```
I have tried using sed to accomplish this but with little success any help would be much appreciated.
Thanks in Advance
Chris

---

### Post by stylishpants on 2008-04-23
Good description of your problem, I like how you included example input and output.

How about this?
```

 perl -ple '$_="NFE" unless m(\.[^/]+$)'

# works with ls
ls -type f | perl -ple '$_="NFE" unless m(\.[^/]+$)'

# works with find
find . -type f | perl -ple '$_="NFE" unless m(\.[^/]+$)'


```

It treats hidden dot files (eg. ~/.bashrc) as having an extension, hopefully that's what you want.

---

### Post by ghostdog74 on 2008-04-23
> **manicman said:**
> Hi I'm trying to write a simple Bash script for examining file extensions.
I'm trying to detect if a file has no file extension and if so to replace it with the text NFE

I hope you are just finding them and not renaming them. below finds files without extension.
```

find /path -maxdepth 1 -type f \( ! -name "*.*" -a ! -name ".*" \)

```
if you really want to rename them.
```

find /path  -maxdepth 1 -type f \( ! -name "*.*" -a ! -name ".*" \)  -execdir mv "{}" NEF \;

```

---

### Post by manicman on 2008-04-24
Thanks Everyone for your help your commands worked Great :)

---

