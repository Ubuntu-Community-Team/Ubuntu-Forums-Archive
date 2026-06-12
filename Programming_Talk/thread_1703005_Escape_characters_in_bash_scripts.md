---
title: "Escape characters in bash scripts"
date: 2011-03-08
forum: Programming Talk
---

### Post by CaptainMark on 2011-03-08
Could some please help me figure out why this ```
#!/bin/bash

echo '\n'

rsync -vaEn --delete ~/ /media/passport/mark/;

echo -e '\nThe above folers/files will be affected.\nDo you want to continue? (y/n): ';
read choice;
yes="y"
no="n"

if [ $choice == $yes ]; then
    echo '\nUpdating'
    rsync -vaE --delete ~/ /media/passport/mark/;

elif [ $choice == $no ]; then
    echo '\nAborting'

else
    echo '\nResponse not recognised'

fi
```gives this output```
\n
..... #(lots of hidden files blah blah blah)
Desktop/
Documents/
Documents/scripts/login_scripts/
Downloads/
Music/
Pictures/
Videos/

sent 255870 bytes  received 19141 bytes  78574.57 bytes/sec
total size is 27046495629  speedup is 98346.96 (DRY RUN)

The above folers/files will be affected.
Do you want to continue? (y/n): 
n
\nAborting
```urrrm, how has it printed '\n' its ignoring an escape character and actually printing \n, but only on the aborting line, the one before 'The above files...' is printing a newline.

Okay, what blindingly obvious thing am I missing?

---

### Post by sisco311 on 2011-03-08
You have to use the -e flag:
```
echo -e "\nWhatever"
```

See:
```
man bash | less +/"[ ]+echo \["
```

---

### Post by CaptainMark on 2011-03-08
dang! thanks i knew it would be stupid, i read somewhere that that left off the newline but now reading the man thats -n, and i cant find where i read that now, its obviously rubbish

---

