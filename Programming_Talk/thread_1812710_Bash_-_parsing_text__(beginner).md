---
title: "Bash - parsing text ? (beginner)"
date: 2011-07-26
forum: Programming Talk
---

### Post by bubbaspam on 2011-07-26
Sorry, but I am very new to this and haven't been able to figure out how to parse  a simple text file (dummy.txt). 

Example:
    email - header gibberish
    http:/www.somewhere.com/xyzdir/**XXXXXXXXX**/?mode=desktop
    other random text

I need to set a variable ($id) to [B]XXXXXXXXXX

Thanks for any help!
[/B]

---

### Post by mikejonesey on 2011-07-26
start;

cat moomoo.txt

email - header gibberish
    http:/www.somewhere.com/xyzdir/**XXXXXXXXX**/?mode=desktop
    other random text

grep [www.somewhere.com](www.somewhere.com)

http:/www.somewhere.com/xyzdir/**XXXXXXXXX**/?mode=desktop
     
sed 's/\//g'

http: [www.somewhere.com](www.somewhere.com) xyzdir** ****XXXXXXXXX** ?mode=desktop
      
awk '{print $4}'

****[B]XXXXXXXXX

[/B]would need more data to properly tell you though... (don't know what to filter for or on...)

---

### Post by mikejonesey on 2011-07-26
or;

```
cat blabla.txt | grep ^http | cut -d "/" -f 4
```

ps... would still need more data to confirm... :)

---

