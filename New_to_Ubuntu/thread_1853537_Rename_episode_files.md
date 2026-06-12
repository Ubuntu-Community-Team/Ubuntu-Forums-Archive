---
title: "Rename episode files"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by m3_del on 2011-10-02
All,

I have a directory filled with many subdirectories of tv episodes. I am looking to get to an end state with a simple script that leaves me with the season/episode number of sxxexx. Right now the majority of the files (but not all) are formatted showname - 1x23 - epname.ext. I have a Regex that identifies files that include the numbering pattern. [0-9]*[0-9]x[0-9][0-9] this catches episodes without the 01x01 pattern. I am unsure about how to make this rename to the desired pattern. Any help would be appriciated.

---

### Post by TeoBigusGeekus on 2011-10-02
Personal opinion: it would be too dangerous to do it with a script - you could create a big mess of unrecognizable video files.
Install thunar and look at its tool Bulk Rename.

---

### Post by m3_del on 2011-10-02
This is going to be a good way for me to learn some bash scripting so I would like to move forward. I can test in small folders in the meanwhile.

Struggling trying to figure out how to set a variable. When I run the following command without trying to set a variable it gets me exactly what I want. But the following

```
episodes=$(ls -R | grep [0-9]*[0-9]x[0-9][0-9])
```

just gets me

```
media:~/Movies/TV$ $episodes
2: command not found
```

At work I primarily script in Powershell so I am still learning the ways of bash. Is it object oriented?

---

### Post by papibe on 2011-10-02
There's a very helpful GUI application called pyRenamer, that is perfect for that. It is on the Software Center.

Regards.

---

### Post by m3_del on 2011-10-03
This is a headless server and I am looking to learn some bash scripting in the meanwhile. Thanks though

---

### Post by papibe on 2011-10-03
Have done that myself, I would suggest a few things from experience:
[LIST]
[*]Start by backing up your data.
[*]Test your code by echoing the commands instead of executing them.
[*]It is easier to write and run a few simple scripts, that try to design and write the perfect script that take care of all cases.
[/LIST]
Here an skeleton script that can get you started. This script change the file names to all caps:
```
#!/bin/bash

find -iname '*[0-9][0-9]x[0-9][0-9].*' | \
while read -r filename
do
    newfilename=${filename^^}  # key line for renaming
    echo mv -b -- "$filename" "$newfilename"
done
```
This is safe to execute since I'm echoing the 'mv' line, and not actually renaming anything.

I hope this helps,
Regards.

---

### Post by Grenage on 2011-10-03
> **m3_del said:**
> All,

I have a directory filled with many subdirectories of tv episodes. I am looking to get to an end state with a simple script that leaves me with the season/episode number of sxxexx. Right now the majority of the files (but not all) are formatted showname - 1x23 - epname.ext. I have a Regex that identifies files that include the numbering pattern. [0-9]*[0-9]x[0-9][0-9] this catches episodes without the 01x01 pattern. I am unsure about how to make this rename to the desired pattern. Any help would be appriciated.

While my way is probably not particularly eloquent, here's what I might do.  To rename the following files:

```
Chuck.The.Woodpecker.1x56.randomdata
Chuck.The.Woodpecker.1x57.randomdata
etc
```

From the directory containing the files:

```
for f in *
do echo $(echo "$f" | sed 's/Chuck\.The\.Woodpecker\.1x\([0-9][0-9]\)\.randomdata/chuck\.the\.woodpecker\.s01e\1\.newdata/'
done
```

Which will simply echo what the new file names would be.  If you're happy with the new names, then you can simply change the initial echo to a mv:

```
for f in *
do mv "$f" $(echo "$f" | sed 's/Chuck\.The\.Woodpecker\.1x\([0-9][0-9]\)\.randomdata/chuck\.the\.woodpecker\.s01e\1\.newdata/')
done
```

Which gets you:

```
chuck.the.woodpecker.s01e56.newdata
chuck.the.woodpecker.s01e57.newdata
etc
```

---

### Post by sisco311 on 2011-10-03
prename should do the trick:

```

prename -n 's/([0-9]x[0-9][0-9])/0$1/' *[!0-9][0-9]x[0-9][0-9]*.avi
prename -n 's/(.*[0-9]x)([0-9].*avi)/${1}0$2/' *[0-9]x[0-9][!0-9]*.avi

```

---

### Post by sisco311 on 2011-10-03
> **m3_del said:**
> This is going to be a good way for me to learn some bash scripting so I would like to move forward. I can test in small folders in the meanwhile.

Struggling trying to figure out how to set a variable. When I run the following command without trying to set a variable it gets me exactly what I want. But the following

```
episodes=$(ls -R | grep [0-9]*[0-9]x[0-9][0-9])
```

just gets me

```
media:~/Movies/TV$ $episodes
2: command not found
```

At work I primarily script in Powershell so I am still learning the ways of bash. Is it object oriented?

ls shows you a representation of files. They aren't file names, so don't try to parse it.

If you want to learn bash, check out the links in my signature.

In bash, I'd try something similar to what Grenage suggested:
```

#!/bin/bash

shopt -s nullglob

for file in *[!0-9][0-9]x[0-9][0-9]*.avi
do
    newname="$(printf '%s\n' "$file" | sed -e 's/\([0-9]x[0-9]\)/0\1/')"
    echo mv -- "$file" "$newname"
done

```

@papibe

Check out BashFAQ #20. File names may contain newlines and other special characters. You should use find's -print0 option:
```
while IFS= read -r -d '' file
do
    printf '%s\n' "${file^^}"
done< <(find /path OPTIONS -print0)

```

---

