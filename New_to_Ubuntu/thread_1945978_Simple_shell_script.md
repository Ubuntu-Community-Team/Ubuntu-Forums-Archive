---
title: "Simple shell script"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by Roter1337 on 2012-03-24
Hello, im sortof a newbie to the world of scripting, I would like to know how to remove the .py at the end of some file names.
Heres my code so far. I need it to remove the .py.

```

for f in *.py
do
chmod 755 $f
cp $f /usr/bin
done

```
any help would be appreciated.
Thanks
- Roter

---

### Post by papibe on 2012-03-24
Hi Roter1337.

First, a couple of suggestions:
[LIST]
[*]I would really recommend that you take advantage of your own ~/bin that when created is added to the path automatically (it'll work for new open terminals).
[*]The structure 'for f in *.py' works ok only if there's no spaces on the filenames.
[/LIST]
Now to your concern, I see a couple of options: the easiest one (using a renaming command), and one that let's you learn a little more of bash scripting.

Let's start with the last one: you can use bash's parameter substitution with the format {variable%%pattern}. That will trim the longest match from the end.

For instance:
```
var=program.py

newvar=${var%%.*}

echo "$newvar"
# it will print 'program' (no quotes).

```
That assumes that the file name doesn't contain other dots. If they do, use this format instead: {var%.*} which means to trim the shortest match from the end.

The skeleton structure for renaming the files would be:
```
for f in *.py
do
    ...
    new_f="${fr%%.*}"
    mv "$f" "$new_f"

    # or  mv "$f" ~/bin/"$new_f"
    ...
done
```
Now, the easy way. There's a command named 'rename' that can by itself rename all the files at once using a regular expression. It is just easy as:
```
rename 's/\.py//' *.py
```
where
[INDENT]s means replace string.
/\.py/ is for '.py' ('\' is used to escape the '.').
// means nothing.
Then: replace .py for nothing in all files that match *.py.[/INDENT]

In your example, I would use it at the end of the 'for':
```
for f in *.py
do
    ...
    cp ... ~/bin/
    ...
done
rename 's/\.py//' ~/bin/*.py

```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by vivekpandey1991 on 2012-03-24
```

#!/bin/bash
# 



E_BADARGS=65

case $# in
  0|1)             # The vertical bar means "or" in this context.
  echo "Usage: `basename $0` old_file_suffix new_file_suffix"
  exit $E_BADARGS  # If 0 or 1 arg, then bail out.
  ;;
esac


for filename in *.$1
# Traverse list of files ending with 1st argument.
do
  mv $filename ${filename%$1}$2
  #  Strip off part of filename matching 1st argument,
  #+ then append 2nd argument.
done

exit 0

```

un it as ```
 sh filename.sh py ' " 
```

---

### Post by vivekpandey1991 on 2012-03-24
sorry 2 corrections needed . replace the line
```

 mv $filename ${filename%$1}$2

```
by 
```

 mv $filename ${filename%.$1}$2

```
the reason is the first line prints the . also but not the second

and to run use 
```

sh 2.sh py " "

```

---

### Post by codemaniac on 2012-03-24
The below script would remove all the .py extensions to your files in the current directory .
```

#!/bin/bash
for i in *.py
do
        mv $i $(basename $i .py)
done
```

---

### Post by Roter1337 on 2012-03-24
thanks for all the responses, very helpful. Especially papibe. Thanks to all.

---

