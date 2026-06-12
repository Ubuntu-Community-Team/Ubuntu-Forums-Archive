---
title: "Simple bash-zenity frontend for du"
date: 2011-07-24
forum: Programming Talk
---

### Post by threarth on 2011-07-24
Hi, i've made a simple bash-zenity frontend which could be added to xfce-thunar to see disk usage: you can select one or more items, right-click and use the script by adding it to custom actions with "/usr/bin/zendu.sh %F".

The problem is that it is difficult to handle complex filename with bash; to avoid whitespace problems, i divided the fields that i needed to put in the zenity-list with "|"; so, if any file contained a "|" the script wouldn't work. I read somewhere that one could use "\0" to separate fields, but how could be used a '\0' in a string?

Daniele

Here's the script:

```
#!/bin/bash
#Simple du frontend by threarth

if [ -z "$1" ]; then
    zenity --width 260 --title="Simple disk-usage (du) frontend" \
           --error --text="Error: no file selected."
    exit 1
fi

TMPFILE="/tmp/zendu.tmp"

if [ -e "$TMPFILE" ]; then
    cp "$TMPFILE" "$TMPFILE.bak"
fi

echo -n '' > $TMPFILE
n_args=0

#save output of du in $TMPFILE
for i in "$@"; do
    if [ -e "$i" ]; then
        du -sh --apparent-size "$i" >> $TMPFILE 
    else
        zenity --width 260 --title="Simple disk-usage (du) frontend" \
               --error --text="Error: file $i doesn't exist."    
        exit 1
    fi
done

#here we separate the fields with a '|'; fields are
#1. False -> checkbox not selected
#2. Size 
#3. Filename

while read line; do
    count=$(echo $line | wc -w) 
    OUTPUT="$OUTPUT\"False\"|"
    OUTPUT="$OUTPUT\"$(echo $line | cut -d " " -f 1)\"|\"" 
    for i in `seq 2 $count`;
    do
        OUTPUT="${OUTPUT}$(echo $line | cut -d " " -f $i) "
    done
    OUTPUT="$OUTPUT\"|"
    OUTPUT="$(echo $OUTPUT | sed 's/\ \"/\"/')"
    let n_args=$n_args+1
done < $TMPFILE

let height=100+$n_args*35

OUTPUT="$(echo $OUTPUT | sed 's/\"//g')"

#Here we change the IFS to '|'

IFS="|"
result=$(zenity --width 660 --height $height --list --title="Simple" \
        --checklist --column="Selected" --column="Size" --column="Name" \
        --separator="|" --print-column=3 $OUTPUT) 

OUTPUT=""
rm $TMPFILE

if [ -n "$result" ]; then 
    for i in $result; do
        i=$(echo $i | sed 's/\"//g')

        if [ -d $i ]; then
            find $i -maxdepth 1 | while read line; do 
                if [ -d "$line" ]; then echo "$line/" >> $TMPFILE 
                else echo "$line" >> $TMPFILE 
                fi
            done
        else
            echo "$i" >> $TMPFILE
        fi
        
    done

    OUTPUT=$(cat $TMPFILE | tr "\n" "|" | sed 's|//|/|g') 

    $0 $OUTPUT
fi
exit 0
```

---

