---
title: "sh input"
date: 2008-04-04
forum: Programming Talk
---

### Post by eskimspy on 2008-04-04
This will work in the terminal, but not as a sh file, I get the following error:

```
What is the extension package (with the .xpi) read: 2: arg count
read: 3: Illegal option -e
```

script.sh:
```
#!/bin/bash
read -p "What is the extension package (with the .xpi) "
read -e input
unzip $input
cd chrome
for file in *
do
filename=${file%.*i}
done
echo "@import url(chrome://"$filename"/"$filename".css);" >> ~/.gnome2/epiphany/user-stylesheet.css
echo "content "$filename" jar:file:///usr/share/epiphany-browser/chrome/"$filename".jar!/content/"$filename"/

```

---

### Post by stroyan on 2008-04-04
I expect that you put that script in a file like test.sh and ran "sh test.sh".
That would be fine on most systems.
But /bin/sh in ubuntu is a link to /bin/dash instead of /bin/bash.
Dash doesn't have the feature of reading into REPLY like bash does.
It always wants at least one a variable name for a read builtin.
You can run your script successfully with "bash test.sh" or
"chmod +x test.sh; ./test.sh".

---

