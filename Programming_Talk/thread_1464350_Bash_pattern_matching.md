---
title: "Bash pattern matching"
date: 2010-04-28
forum: Programming Talk
---

### Post by Minky2k on 2010-04-28
Hi! I'm having some problems making a bash-script work with pattern matching. How do I make bash look for a variable in another variable and if the first variable contains the word in the other varible do something. Could really use the help =)

/Thx

Example:
```
Variable1:Tue
Variable2: 9d9471a7-c987-457f-bcc6-bf32e8c598d5  New       Tue
```

The code i'm currently working with looks like this:
```
Date=`date '+%a'`
while read line ;do
   if [[ "$line" == *$Date* ]]
then
    echo "Found match!"
else
    echo "No match!"
fi

done < /home/user/task_output.txt
```

---

### Post by Bachstelze on 2010-04-28
You could [font=monospace]echo[/font] the first varible and pipe the output to [font=monospace]grep[/font] to do the pattern-matching against the second one:

```
firas@itsuki ~ % cat foo.sh 
#!/bin/sh

Date=`date '+%a'`
echo "Date is $Date."

while read line ;do
   if echo "$line" | grep -q "$Date" 
then
    echo "Found match!"
else
    echo "No match!"
fi

done
firas@itsuki ~ % ./foo.sh  
Date is Wed.
foo
No match!
fooWedbar
Found match!

```

---

### Post by Minky2k on 2010-04-28
Thank you for the quick reply! However I managed to get a working solution by using: 
```
 if [[ "$line" =~ $Date ]]
```

/Regards

---

### Post by Bachstelze on 2010-04-28
> **Minky2k said:**
> Thank you for the quick reply! However I managed to get a working solution by using: 
```
 if [[ "$line" =~ $Date ]]
```

/Regards

It's not portable, though.

---

