---
title: "Bash text file merging question"
date: 2011-03-08
forum: Programming Talk
---

### Post by Andrew_Balls on 2011-03-08
Hello everyone, I have three text files called the following:

names.txt
emails.txt
numbers.txt

the names.txt file includes names in the following format:

steve
bob
harry

and the emails.txt file has the same format, one entry per line:

[email]steve@yahoo.com[/email]
[email]bob@hotmail.com[/email]
[email]harry@aol.com[/email]

The numbers.txt file includes the same format.

My ultimate goal is to have one file with the following format:

name:email:number
or
steve:steve@yahoo.com:555-555-5555
bob:bob@hotmail.com:555-555-5556

so on. My question is this, how do I read the first line of each file, append a value, echo back all the values, the do the same for the second line from each file, then the third. etc etc.

Thanks! Please let me know if you need anymore information to help.

-Andrew

---

### Post by sisco311 on 2011-03-08
Hi and welcome to the forums!

You can use the **paste** command. For details check out its man page:
```
man paste
```

---

### Post by amauk on 2011-03-08
untested, but this should do it

```
#!/bin/bash

FILE_NAMES="names.txt"
FILE_EMAILS="emails.txt"
FILE_PHONES="numbers.txt"

MAX_LINE_NUM=$(cat "$FILE_NAMES" | wc -l)
LINE_NUM=1

while [ "$LINE_NUM" -le "$MAX_LINE_NUM" ]; do
	LINE_NAME=$(sed "${LINE_NUM}q;d" "$FILE_NAMES")
	LINE_EMAIL=$(sed "${LINE_NUM}q;d" "$FILE_EMAILS")
	LINE_PHONE=$(sed "${LINE_NUM}q;d" "$FILE_PHONES")

	echo "${LINE_NAME}:${LINE_EMAIL}:${LINE_PHONE}"
	LINE_NUM=$(expr "$LINE_NUM" + 1)
done
```

---

### Post by sisco311 on 2011-03-08
In (`pure') bash I would do something like:
```

while read -r l1; read -r l2 <&6; read -r l3 <&7; do 
  echo "${l1}:${l2}:${l3}"
done < names 6< emails 7< numbers > newfile

```

---

### Post by Andrew_Balls on 2011-03-08
Thanks guys! I read through all three responses and I'll modify my code accordingly.

Thanks again!
-Andrew

---

