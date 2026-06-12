---
title: "Bash script problem"
date: 2008-07-20
forum: Programming Talk
---

### Post by c0rrupt on 2008-07-20
I am working on a small Bash script to remove some of the junk files that Windows likes to leave laying around (thumbs.db, desktop.ini) but I'm having a problem with folders that contain spaces.  

When I have it echo the results everything looks fine.  All the lines are enclosed with quotation marks for any directory with spaces.  But when I try to remove the files with rm, it freaks out.

**Here is the script.**

```

#!/bin/bash

find ~/Music/ -name '*Thumbs.db*' | while read FILE
do
	FILE=\"$FILE\"
	#echo $FILE
        rm -i $FILE
done

```

**Some of the output from echo.**

```

"/home/david/Music/Albums/A Perfect Circle/Thumbs.db"
"/home/david/Music/Albums/A Thorn For Every Heart/Thumbs.db"
"/home/david/Music/Albums/Afghan Whigs/Thumbs.db"
"/home/david/Music/Albums/Against Me!/Thumbs.db"

```

**An error message from rm**

```

rm: cannot remove `"/home/david/Music/Albums/A': No such file or directory
rm: cannot remove `Perfect': No such file or directory
rm: cannot remove `Circle/Thumbs.db"': No such file or directory
rm: cannot remove `"/home/david/Music/Albums/A': No such file or directory
rm: cannot remove `Thorn': No such file or directory
rm: cannot remove `For': No such file or directory
rm: cannot remove `Every': No such file or directory
rm: cannot remove `Heart/Thumbs.db"': No such file or directory
rm: cannot remove `"/home/david/Music/Albums/Afghan': No such file or directory
rm: cannot remove `Whigs/Thumbs.db"': No such file or directory
rm: cannot remove `"/home/david/Music/Albums/Against': No such file or directory
rm: cannot remove `Me!/Thumbs.db"': No such file or directory

```

I thought that maybe it was because the space didn't have a \ preceding it, but rm accepted this command.

```

rm -i "/home/david/Music/Albums/A Perfect Circle/Thumbs.db"

```

Oh, I almost forgot.  When I tried *rm -i "/home/david/Music/Albums/Against Me!/Thumbs.db* I got this ": event not found".  The ! must be causing that one.

What is going on here?

---

### Post by johnnybravo666 on 2008-07-20
```
#!/bin/bash

find ~/Music/ -name '*Thumbs.db*' | while read FILE
do
	echo $FILE
        rm -i "$FILE"
done
```
This should work

---

### Post by ghostdog74 on 2008-07-20
```
find ~/Music/ -name '*Thumbs.db*' -print0 | xargs -0 rm 

```

---

### Post by johnnybravo666 on 2008-07-20
> **ghostdog74 said:**
> ```
find ~/Music/ -name '*Thumbs.db*' -print0 | xargs -0 rm 

```

That works better. I'll remember that. Thanks

---

### Post by c0rrupt on 2008-07-20
Thanks!  It's working fine now.

---

### Post by mssever on 2008-07-20
The lesson from this: **Always enclose any variable reference (beginning with $) in double quotes!** xargs works great at avoiding this issue, but you won't always be able to use it. So remember the above rule.

(Of course, as you learn Bash better, you'll learn when it's OK to break the rule. But there are very few situations that require you to break it.

---

