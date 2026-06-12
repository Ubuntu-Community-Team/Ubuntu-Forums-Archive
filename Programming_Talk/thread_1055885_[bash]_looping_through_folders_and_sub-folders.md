---
title: "[bash] looping through folders and sub-folders"
date: 2009-01-31
forum: Programming Talk
---

### Post by m4lte on 2009-01-31
**SOLVED**

Hi there!

I want to make a simple shell script to execute a command in a certain folder and all sub folders. I couldn't find anything on google.

In particular I have a collection of photos, that is heavily branched. I want a script that searches all subdirectories and removes certain files (thumbnails).
What is the best way to loop through all sub folders recursively?

cheers!
malte

---

### Post by geirha on 2009-01-31
I'd say the find command.
```

# List all jpegs.
find /path/to/folder -iname "*.jpg"
# find all jpegs with thumb in their name. 
find /path/to/folder -iname "*thumb*.jpg"

``` 

If you manage to get a find command to list all the files you want deleted, add "-delete" to the end of the find-command. That will delete the files permanently (not go through the trash).

---

### Post by m4lte on 2009-01-31
Thanks geihra,
the find command does exactly what I need.

---

