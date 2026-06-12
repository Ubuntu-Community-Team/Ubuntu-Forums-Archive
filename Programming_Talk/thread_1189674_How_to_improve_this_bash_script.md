---
title: "How to improve this bash script?"
date: 2009-06-17
forum: Programming Talk
---

### Post by Dill on 2009-06-17
I'm working on a large PHP project for my school, where each PHP file has a header template that includes lines like:

```
Date created: 2009-06-05
Last edited: 2009-06-07
```

It's the responsibility of each person who edits the file to change the modification date and add a comment about the edit. However, we often forget to change the date. Go figure...

I wanted to automate this behaviour, changing the "Last edited" date in the file to automatically match the modification date. However, editing the file changes the modification date, so I have to "retain" the modification date before editing the file, then replace the old modification date after editing the file.

I'm looking for suggestions on how to make this script better. Specifically, all the calls to *stat* seem like too much. I'm basically building up the string to use with *touch*, but I feel like there's an easier way. Any suggestions would be much appreciated:

```
#!/bin/bash

# updateLastEdited.sh - updated the time files in a given directory were
#                       last updated

TARGET_DIR="/var/www/test"
KEYWORD="Last edited"

# For each PHP file in $TARGET_DIR...
for FILE in $(find $TARGET_DIR -type f -name '*.php')
do
  # Find modification time and date

  CC=`stat -c %y $FILE | awk '{print $1}' | cut -c1,2`
  YY=`stat -c %y $FILE | awk '{print $1}' | cut -c3,4`
  MM=`stat -c %y $FILE | awk '{print $1}' | cut -d- -f2`
  DD=`stat -c %y $FILE | awk '{print $1}' | cut -d- -f3`
  hh=`stat -c %y $FILE | awk '{print $2}' | cut -d: -f1`
  mm=`stat -c %y $FILE | awk '{print $2}' | cut -d: -f2`
  SS=`stat -c %y $FILE | awk '{print $2}' | cut -d: -f3 | cut -d. -f1`
  
  # Find the "real" modification time from the output of ls
  CURRENT_MOD_DATE=`ls -l $FILE | grep -o '[0-9]\{4\}-[0-9]\{2\}-[0-9]\{2\}'`

  # Find the modification date in the $KEYWORD part of the file
  OLD_MOD_DATE=`grep "$KEYWORD" $FILE | grep -o '[0-9]\{4\}-[0-9]\{2\}-[0-9]\{2\}'`

  # Replace $OLD_MOD_DATE with $CURRENT_MOD_DATE on everyline where $KEYWORD appears
  sed -i "/$KEYWORD/s/$OLD_MOD_DATE/$CURRENT_MOD_DATE/g" $FILE

  # Finally, "re-touch" the file so that we replace the modification time with the old mod time
  touch -t "$CC$YY$MM$DD$hh$mm.$SS" $FILE
done

exit 0
```

---

### Post by ghostdog74 on 2009-06-17
```

find /var/www/test -maxdepth 1 -type f -name "*.php" -printf "%TY-%Tm-%Td#%f#%p#%t\n" | awk 'BEGIN{
    FS="#"
    q="\047"
}
{
    timestamp=$1
    filename=$2
    fullpath=$3
    touchtime =$4    
    while(( getline line < fullpath) >0) {
        if ( line ~ /Last edited/){
            line = "Last edited : "timestamp
        }
        print line > "temp"
    }
    cmd = "mv temp "q fullpath q
    # system(cmd) #uncomment to use
    cmd = "touch -d "q touchtime q " " fullpath
    # system(cmd) #uncomment to use    
}'


```

---

### Post by Dill on 2009-06-17
Thanks, ghostdog. I'll have to brush up on my awk... it all seems so "awk-fuscated" to me now : )

Cheers,
Dylan

---

### Post by ghostdog74 on 2009-06-17
> **Dill said:**
> Thanks, ghostdog. I'll have to brush up on my awk... it all seems so "awk-fuscated" to me now : )

Cheers,
Dylan
see my sig 3rd link for the manual.

---

### Post by geirha on 2009-06-17
Here's how you can shorten it down a bit by using date instead of stat and ls:
```

TIMESTAMP=`date -r "$FILE" +%Y%m%d%H%M.%S`
CURRENT_MOD_DATE=`date -r "$FILE" +%Y-%m-%d`
#...
touch -t $TIMESTAMP "$FILE"

```

---

### Post by soltanis on 2009-06-17
Also look into the -t option for stat, which prints the data in a more awk-friendly way.

---

