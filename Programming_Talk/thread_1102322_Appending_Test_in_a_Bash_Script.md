---
title: "Appending Test in a Bash Script"
date: 2009-03-21
forum: Programming Talk
---

### Post by ferdose on 2009-03-21
Hello

I wrote a simple shell script to copy videos from youtube via my /tmp folder and put them in ~/Videos. Here is the code:

```


#!/bin/bash

cd /tmp; ls

echo "Enter first name: "; read var1
echo "Enter last name: "; read var2

mv /tmp/$var1 ~/Videos/$var2


```

Although the video is saved as an flv file, the extension isn't there. I want to use another program to convert flvs to mpegs, and the .flv extension needs to be there. Is there an append command I can use in my shell script to just add .flv after $var2 (the renamed version)?

I searched online for a linux command to append text and I found the sed command, but I'm not too sure how to use it in my shell script. Looking from the website ([http://linux.about.com/od/commands/l/blcmdl1_sed.htm](http://linux.about.com/od/commands/l/blcmdl1_sed.htm)) I think the options I need to use are one of these, but I really have no idea:

> 
a \
text
    Append text, which has each embedded newline preceded by a backslash. 
i \
text
    Insert text, which has each embedded newline preceded by a backslash. 

thank you for reading this much :)
and I did read the FAQ

---

### Post by geirha on 2009-03-21
It's easier than you think. Made some minor other modifications on your script as well
```
#!/bin/bash

# ls -ltr uses long listing format and sorts by modification timestamp in reverse order,
# so the last modified file will be listed last
cd /tmp; ls -ltr  

# The -e option to read enables readline support, which means you can tab-complete
# the filename
echo "Enter first name: "; read -e var1
echo "Enter last name: "; read var2

# Just add .flv after $var2. Also, always quote variables containing paths; that allows
# you to use spaces in filenames.
mv "$var1" ~/Videos/"$var2.flv"

```

---

### Post by Nevon on 2009-03-21
I don't see where the test part comes into play. But if all you want to do is add .flv to the end of the filename, then change the mv line to this:
```
mv /tmp/"$var1" ~/Videos/"$var2".flv
```

---

### Post by ferdose on 2009-03-21
Thank you very much geirha and Nevon, I can't believe it was so easy.

---

