---
title: "Ubuntu unrar external foder bash script"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by mafi127 on 2011-12-01
Can some1 help me to make a litle script what unrar files from folders when I execute script in shell, eg I run script in Documents folder whit command "bash unrar.sh /home/username/download/some folder/" then it will extract all the files in the some folder. 

I used this script to unrar files

[PHP]
#!/bin/bash
for i in $(find $(pwd) -name '*.rar')
do
cd $(dirname $i)
unrar e $i &&  rm *.r??
done
[/PHP]

Hope some1 will help me out whit this little script

---

### Post by mafi127 on 2011-12-02
Help me out plz whit this I realy need a script what can unrar files when the script file is not in the same folder. like "unrar.sh /dir/to/extract/asdf.rar"

---

### Post by papibe on 2011-12-05
Hi mafi127.

Try this:
```
#!/bin/bash

# Check if parameter exists.
if [ ! $# -eq 1 ]
then
        echo "Usage unrar.sh directory"
        exit 0
fi

search_dir="$1"

while IFS= read -r -d '' rarfile
do
    unrar e "$rarfile" && echo rm -f "$rarfile"
done < <(find "$search_dir" -name '*.tar' -print0)

```
As a safety measure I'm not deleting the rars but echoing the rm command. To actually remove the rars remove the word echo inside the while.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by mafi127 on 2011-12-08
Thank you, the script work like it should to work :).I dont figure out the way to extract the file to the same folder wher the rar is. any solutions?

---

### Post by editheraven on 2011-12-08
The "e" option from "unrar e" does that. However, if you want another approach, you can do this : (i edithed the script posted by papibe). You can use the paramater directly into unrar command but i chose this way.

```
#!/bin/bash

# Check if parameter exists.
if [ ! $# -eq 1 ]
then
        echo "Usage unrar.sh directory"
        exit 0
fi

search_dir="$1"
cd "$1"
path=$( pwd )

while IFS= read -r -d '' rarfile
do
    unrar e "$rarfile" "$path" && echo rm -f "$rarfile"
done < <(find "$search_dir" -name '*.tar' -print0)

```


le : if it doesn't work as expected, i'm sorry :( I'm really tired and stuff, but it should work ok.

---

### Post by mafi127 on 2011-12-08
Thank you for your efford but it still extracs all the files to the home directory. there is somekindo&#7811;  bug :/

---

### Post by editheraven on 2011-12-08
Try without "e" option.

---

### Post by papibe on 2011-12-08
In order to unrar the files in the same directory, you have to add the destination directory on the unrar command. This would be the syntax:
```
unrar e source.tar /path/to/destination/
```
Since in the while loop the variable rarfile contains the filename and path to the rarfile, you just need to get the path out of it.

Replace the main line of the while with:
```
    unrar e "$rarfile" "${rarfile%/*}" && echo rm -f "$rarfile"
```
Hope it helps.
Regards.

BTW, editheraven's idea was correct, but it needed a little more development.

---

### Post by mafi127 on 2011-12-10
Thank you, works great now :)

---

