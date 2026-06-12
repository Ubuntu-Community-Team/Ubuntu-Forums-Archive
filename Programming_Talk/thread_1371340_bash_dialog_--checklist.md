---
title: "bash dialog --checklist"
date: 2010-01-03
forum: Programming Talk
---

### Post by VCoolio on 2010-01-03
If I use dialog --checklist, how do I use the output to show me the chosen item strings instead of the tag numbers? Suppose I have a file file.txt with random content. This is what I can come up with:

```
#!/bin/bash

n=1
for pkg in $(cat file.txt)
    do
        echo "$n $pkg off" >> /tmp/output.txt
        n=$[n+1]
done

dialog --checklist "Choose item:" 80 40 20 \
$(cat /tmp/output.txt)

#commented to check on script
#rm /tmp/output.txt
```

Now how do I use the dialog output to for example just echo the items that belong to the tags I checked in the dialog checklist? For example, file.txt contains five lines with "var1" "var2" ... "var5", how do I get a line printed that says "You've chosen var2 and var3" when I checked 2 and 3?

---

### Post by dwhitney67 on 2010-01-03
Doesn't the man-page for 'dialog' say anything wrt your query?

I do not have 'dialog' installed on my system, but I do have zenity.  Perhaps they are similar.  Zenity returns the choice(s), as a string, as output when running the command.  This string may then need to be parsed.

---

### Post by VCoolio on 2010-01-03
My problem was that where zenity prints the choices, dialog prints the tags, but I tricked it by using the file.txt input as tags and a numbered list that I don't need as items. If there is something better I'm listening.

This is a working example:

```
#!/bin/bash
n=1
for pkg in $(cat file.txt)
    do
        echo "$pkg $n off" >> /tmp/output.txt
        n=$[n+1]
done

dialog --checklist "Choose item:" 80 40 20 \
$(cat /tmp/output.txt) 2>/tmp/output2.txt

echo you chose $(cat /tmp/output2.txt)
rm /tmp/output*

```

---

### Post by dwhitney67 on 2010-01-03
Here's your code, rewritten to use two less output files:
```

#!/bin/bash

pkglist=""
n=1
for pkg in $(cat file.txt)
do
        pkglist="$pkglist $pkg $n off"
        n=$[n+1]
done

echo $pkglist

choices=`/usr/bin/dialog --stdout --checklist 'Choose item:' 80 40 20 $pkglist`

if [ $? -eq 0 ]
then
        for choice in $choices
        do
                echo "You chose: $choice"
        done
else
        echo cancel selected
fi

```

Here's *equivalent* code using Zenity:
```

#!/bin/bash

pkglist=""
for pkg in $(cat file.txt)
do
        pkglist="$pkglist FALSE $pkg"
done

choices=`/usr/bin/zenity --title="Package Choices" --width=400 --height=400 \
                         --text="Choose item:" \
                         --list --column="Selected" --column="Package" \
                         --checklist $pkglist`

if [ $? -eq 0 ]
then
        IFS="|"
        for choice in $choices
        do
                echo "You chose: $choice"
        done
        IFS=""
else
        echo cancel selected
fi

```

---

### Post by VCoolio on 2010-01-03
Cool, thanks; no output files is always good. I'll mark this thread 'solved' as a wiser man.

I had a working zenity example by the way, and that was one line code:

```
sudo apt-get install $(python /usr/lib/update-notifier/apt_check.py -p | sort | zenity --list --checklist --width=300 --height=620 --title "Select packages to update" --column "" --column "Available packages:" --separator=" " --multiple)
```

---

