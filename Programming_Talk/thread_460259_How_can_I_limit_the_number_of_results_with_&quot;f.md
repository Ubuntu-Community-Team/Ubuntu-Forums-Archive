---
title: "How can I limit the number of results with &quot;find&quot; command?"
date: 2007-05-31
forum: Programming Talk
---

### Post by Yuzem on 2007-05-31
Well thats the question... I want it to stop at the first match.

---

### Post by yaaarrrgg on 2007-05-31
one simple way is to pipe it through "head" for example:

find . -name "whatever" | head -n 1

---

### Post by tkjacobsen on 2007-05-31
I always use grep together with find. E.g if i look for a conf to X11 i would do

find / -name *conf | grep X11

This will search for conf and X11 at the same time.

Output is
/media/sda6/etc/X11/xorg.conf
/media/sda6/etc/X11/gdm/gdm.conf
/media/sda6/etc/X11/imwheel/startup.conf
/media/sda6/etc/X11/dm.d/30xdm.conf
/media/sda6/etc/X11/dm.d/20gdm.conf
/media/sda6/etc/X11/dm.d/10kdm.conf
/etc/X11/xorg.conf


(I just cannot find a good example right now)

---

### Post by Yuzem on 2007-05-31
Thanks for the answers.
Here is the problem:
I want to make a script to automatically create .desktop files from a lot of folders with pictures inside. Each desktop file will link to a folder having a picture for the icon.

The problem with the suggested solution is that it will do a lot of extra work.

"locate" has an option to limit the amount of results (-n)
Can "locate" search in an specified path? How?

---

### Post by cwaldbieser on 2007-06-01
> **Yuzem said:**
> Well thats the question... I want it to stop at the first match.

Just use the -quit action.

```

$ find . -type f -print -quit

```
This finds the first regular file, prints it, and stops.  Also look at the -depth and -prune options for limiting the search space.

---

### Post by ghostdog74 on 2007-06-01
well if its just to find the first regular file, another way
```

ls -l /dir | awk '/^-/{print;exit}'

```

---

### Post by Yuzem on 2007-06-01
The -quit action works perfectly.
Thanks.

---

### Post by Yuzem on 2007-06-01
One more problem...
I need the full path to the file. The .desktop file does not work with relative paths (or I don't know how to make it work)

```

~/Desktop/test$ pwd
/home/azd/Desktop/test
~/Desktop/test$ find . -type f -print -quit
./12/test.jpg
~/Desktop/test$ echo $(pwd)$(find . -type f -print -quit)
/home/azd/Desktop/test./12/test.jpg

```
I can't get rid of that dot there.
I am sure this is a very basic thing but I am a complete beginner.

---

### Post by ghostdog74 on 2007-06-01
```

find $(pwd) -type f -print -quit

```
or define the path in a variable and use it in find.

---

### Post by Yuzem on 2007-06-01
So simple...
Thanks!

---

### Post by Yuzem on 2007-06-03
I have another problem...
When a folder name has spaces it doesn't work:

```

azd@asd:~/Desktop/test/1 6$ basename "$(find "$(pwd)" -type d -print -quit)"
1 6

```
That is good but it doesn't work in a variable:

```

azd@asd:~/Desktop/test/1 6$ album="$(find "$(pwd)" -type d -print -quit)" && echo \"$album\"
"/home/azd/Desktop/test/1 6"

```
The previous gave me what I want and with basename it works:
```

azd@asd:~/Desktop/test/1 6$ basename "/home/azd/Desktop/test/1 6"
1 6

```
But when I put all together it doesn't:
```

azd@asd:~/Desktop/test/1 6$ album=$(find "$(pwd)" -type d -print -quit) && basename $(echo \"$album\")
1

```


The code so far:
```

#!/bin/bash
for album in $(find "$(pwd)" -type d -print); do 
echo -e \
"[Desktop Entry]\n\
Encoding=UTF-8\n\
Name=\n\
X-MultipleArgs=false\n\
Type=Link\n\
URL=file://$album\n\
Icon=$(find $album -maxdepth 1 -type f -iname '*.jpg' -print -quit)" \
> "/home/azd/Desktop/test/Albums/$(basename "$album").desktop";
done

```
Only works for path without spaces.
Any ideas?

---

### Post by ghostdog74 on 2007-06-03
you can try print0 instead of print.

---

### Post by Yuzem on 2007-06-03
Is the same with print0:

```

azd@asd:~/Desktop/test/1 6$ album=$(find "$(pwd)" -type d -print0 -quit) && basename $(echo \"$album\")
1

```

:(

---

### Post by ghostdog74 on 2007-06-03
you can also use while loop with the read command and -r switch to take care of spaces
```

find "$(pwd)" -type d -print | while read -r album
do
name2save=${album##*/}
cat > "$album/$name2save.dsktop" << message 
  [Desktop Entry]
  Encoding=UTF-8
  Name=
  X-MultipleArgs=false
  Type=Link
  URL=file://$album
message
done

```

---

### Post by Yuzem on 2007-06-04
Beautiful!
It is working perfectly...
Thanks a lot!

---

### Post by Yuzem on 2007-06-28
I finished the first version.
Just in case someone is interested I made a howto here:
[http://ubuntuforums.org/showthread.php?t=486359](http://ubuntuforums.org/showthread.php?t=486359)

Thanks again.

---

