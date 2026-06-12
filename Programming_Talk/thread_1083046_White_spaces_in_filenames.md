---
title: "White spaces in filenames"
date: 2009-02-28
forum: Programming Talk
---

### Post by jonofan on 2009-02-28
Hi all,

I am writing a bash script to convert all files with a certain extension in certain directories on my system. I am using the `find` command to get the file paths, but because the files have spaces in them, I cannot run the conversion script.

Is there a way to list all these files with backslashes before the spaces?

---

### Post by lswb on 2009-02-28
Usually spaces in file names can be handled in scripts by using quotes. Why not post a line or 2 from your script that is causing trouble and we can see what needs fixing.

---

### Post by jonofan on 2009-02-28
Awesome, thanks a lot. Putting it in quotes worked fine.

```
find /media/disk -iname "*.mkv" > temp.txt

while read line
	do
	sh ~/vidconv.sh "$line"
done < temp.txt
```

I did not previously have quotes around $line.

---

### Post by jonofan on 2009-02-28
Hmm it seems I now have a new problem. Can I still post it in this thread?

```
sh ~/vidconv.sh "$line"
```

is only run on the first line of temp.txt then the script finishes after the vidconv.sh is successfully completed. I would like it to run on each line however. I have tested that the script can read each line debugging with echo.

---

### Post by apmcd47 on 2009-02-28
> **jonofan said:**
> Awesome, thanks a lot. Putting it in quotes worked fine.

```
find /media/disk -iname "*.mkv" > temp.txt

while read line
	do
	sh ~/vidconv.sh "$line"
done < temp.txt
```

I did not previously have quotes around $line.

How about[PHP]find /media/disk -iname '*.mkv' -print0 | xargs -0 myprog.sh[/PHP]where myprog.sh has[PHP]for line in "$@"
do
sh ~/vidconv.sh "$line"
done [/PHP]
Or modify vidconv.sh to accept multiple arguments and put the [COLOR="Red"]for line in "$@"[/COLOR] loop round the main code in that program.

Andrew

---

### Post by jonofan on 2009-02-28
Thanks Andrew, that works great.

Is it possible to have both of these in the same script?

for instance:
[PHP]list=find /media/disk -iname '*.mkv' -print0
for line in $list
do
sh ~/vidconv.sh "$line"
done  [/PHP]

or will this not work? I am a bit new to shell programming as you may have noticed :)

---

### Post by eightmillion on 2009-02-28
> **jonofan said:**
> Thanks Andrew, that works great.

Is it possible to have both of these in the same script?

for instance:
[PHP]list=find /media/disk -iname '*.mkv' -print0
for line in $list
do
sh ~/vidconv.sh "$line"
done  [/PHP]

or will this not work? I am a bit new to shell programming as you may have noticed :)

I would use something like this:

[php]
while read line; do
    sh ~/vidconv.sh "$line"
done < <(find /media/disk -iname '*.mkv')
[/php]

---

### Post by Mr.Macdonald on 2009-02-28
Maybe this is helpful
```
echo hello fellow programmer | sed s/\ /\\\\\ /g
```

the sed part is probably what you need

---

### Post by ghostdog74 on 2009-02-28
> **jonofan said:**
> 
Is there a way to list all these files with backslashes before the spaces?

use quotes to deal to "spaces", coupled with while read loop
```

find ......  | while read file_found
do
 # do something with "$file_found"
done

```

---

### Post by lswb on 2009-03-01
If you include "#!/bin/sh" as the first line of your vidconv.sh script, you can then
issue the command "chmod +x vidconv.sh" to make it executable and you will not have to use "sh vidconf.sh filename", just "vidconv.sh filename"

You can also use find to execute a command directly. The syntax can be a little tricky, so check the man page for find. For your example it would be something like:
```

find /media/disk -iname "*.mkv" -exec vidconv.sh '{}' \;

```
or
```

find /media/disk -iname "*.mkv" -execdir vidconv.sh '{}' \; 

```

The -execdir option executes the command as if the directory where the target file was found was the current directory; the command is run for every matching file. '{}' is replaced by the file name. The single quotes are necessary because the shell will otherwise treat the bracket characters as shell commands. The colon indicates the end of the arguments to be passed to (in this case) 'vidconv.sh' and it also needs to be backslash escaped (or single quoted) to prevent the shell from treating it as a special character.

---

### Post by jonofan on 2009-03-02
> **lswb said:**
> 
```

find /media/disk -iname "*.mkv" -execdir vidconv.sh '{}' \; 

```


Thanks for that, worked great and removed the need for my script in the first place haha.

Jono

---

