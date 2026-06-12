---
title: "script to copy files from multiple folders"
date: 2008-03-11
forum: Programming Talk
---

### Post by stratus_ss on 2008-03-11
After searching around on the net for several hours I havent been able to find an answer to the following question (perhaps I am not using the right search terms)

Anyways I am trying to copy multiple files from .kde/share/emoitcons
The problem is that there are multiple folders. 

If someone could point me in the right direction I would appriciate it.
This is something I would like to upload so that others may run it to put all emots into a single folder so gui methods are obviously out and I would like to be able to use the most general /bin/bash codes as I can

---

### Post by themusicwave on 2008-03-11
You could write a python script to handle the task.

The python library you want is called shutil.

I am not at home so I can;t test this but try:

 ```

import shutil, os

print "Source path:"
srcPath = raw_input()
print "Target path:"
targPath = raw_input()


#check the course folder is valid
if(not os.path.exists(srcPath) ):
    print "Source path does not exist!"
   
else:
    shutil.copytree(srcPath,targPath)

```

save it as copyfolder.py

run it with python copyfolder.py

I hope it works, I am just heading out from work so no time to actually test it...

---

### Post by stroyan on 2008-03-11
The find command can be used to find all files under a starting point.
The "-type f" option limits it to files.
The "-exec cp {} D \;" option runs cp to copy each file into directory D.
```
$ mkdir A A/B A/C D
$ touch A/1 A/B/2 A/C/3 
$ ls -R A D
A:
1  B  C

A/B:
2

A/C:
3

D:
$ find A -type f -exec cp {} D \;
$ ls -R A D
A:
1  B  C

A/B:
2

A/C:
3

D:
1  2  3
$ 
```

---

### Post by stratus_ss on 2008-03-11
thanks for the quick reply

I decided against the python library because I wanted to make this as light weight and mobile as possible

ended up putting this together from your suggestions
```

find /home/$USER/.kde/share/emoticons -type f -name "*.png" -print | xargs -i cp "{}" /home/$USER/.kde/share/emoticons/default

```


my next chore is trying to append all the xml files into one file.
I was thinking of doing a hack job by moving all the xml's into the default folder and then just cat append. However the problem with this is that all the xml files are called the same thing so I would have to move and rename them and then cat them

there has to be a more simple way to do this.

And thanks so much for your replies!

---

### Post by themusicwave on 2008-03-11
Glad you figured it out.

Did my script even work?  I had no time  to test it at work...

---

### Post by mssever on 2008-03-11
> **stratus_ss said:**
> ```

find /home/$USER/.kde/share/emoticons -type f -name "*.png" -print | xargs -i cp "{}" /home/$USER/.kde/share/emoticons/default
```
One refinement: Instead of /home/$USER/.kde/... use $HOME/.kde/... It's shorter and more portable. (There's no rule that says that home directories must live under /home. In fact, the user joe could have a homedir in /foo/joe or even /home/jane. In Ubuntu, root's homedir is /root. $HOME will catch that; /home/$USER will fail.

---

### Post by ghostdog74 on 2008-03-11
> **stratus_ss said:**
> 

my next chore is trying to append all the xml files into one file.!
for the simpliest case, cat is what you need
```

cat *.xml > new.xml

```

---

### Post by stratus_ss on 2008-03-12
> **mssever said:**
> One refinement: Instead of /home/$USER/.kde/... use $HOME/.kde/... It's shorter and more portable. (There's no rule that says that home directories must live under /home. In fact, the user joe could have a homedir in /foo/joe or even /home/jane. In Ubuntu, root's homedir is /root. $HOME will catch that; /home/$USER will fail.

Thanks for that! I made an amature assumption glad you caught that. I spend most of my day repairing hardware so I am really lax on the software/scripting side of things

as for the 
```
cat *.xml > new.xml
```

will this actually grab only the files from the emoticon sub folder?
if not does it have to be like 

```
 cat /$home/.kde/share/emoticon *xml > new.xml
```


as for the python script I didnt have time to test it, sorry mate

---

### Post by mssever on 2008-03-12
> **stratus_ss said:**
>  ```
cat *.xml > new.xml
```will this actually grab only the files from the emoticon sub folder?
if not does it have to be like 

```
 cat /$home/.kde/share/emoticon *xml > new.xml
```
The first command will get just the emoticon subdir if your script cds to that dir first.

Revision of your second command:
```
cat $HOME/.kde/share/emoticon/*.xml > new.xml
```
[LIST]
[*]No / before $HOME
[*]$HOME is in all caps
[*]Spaces in filenames must be escaped. In this case, that space should have been a slash[/LIST]

---

