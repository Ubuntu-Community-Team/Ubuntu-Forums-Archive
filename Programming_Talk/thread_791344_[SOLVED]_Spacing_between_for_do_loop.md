---
title: "[SOLVED] Spacing between for do loop"
date: 2008-05-12
forum: Programming Talk
---

### Post by markbusu on 2008-05-12
Hi,

I have the following statment which is getting the values from two text files and merging them into another file:

for i in `seq -w 1 1300`;do for a in Final.txt query.txt;do cat $a | sed -n "$i p" >> Result.txt;done;done

The output into the file Result.txt is as follows:

Value in final.txt
Value in query.txt
Value in final.txt
Value in query.txt
Value in final.txt
Value in query.txt
Value in final.txt
Value in query.txt
Value in final.txt
Value in query.txt

I would like to leave a line Spacing between the Value in query.txt and final.txt to have the following output:

Value in final.txt
Value in query.txt

Value in final.txt
Value in query.txt

Value in final.txt
Value in query.txt

I have tried using the following statement, however i do not receive the desired output:

for i in `seq -w 1 1300`;do for a in Final.txt query.txt;do cat $a ;echo /n | sed -n "$i p" >> Result.txt;done;done

Any advice?? Thanks!

---

### Post by sdennie on 2008-05-12
I think you might way to change:

```

echo /n

```

to

```

echo ""

```

Edit:
You don't need the "\n" for echo.  Just ""

---

### Post by markbusu on 2008-05-12
That appears to be generating a loop.... rather then outputing the content into the results.txt, it is quickly displaying everything on screen and never ends...

Though the output on the screen is still not formatted correctly...

Any other tips m8?

Thanks!

---

### Post by sdennie on 2008-05-12
Looking at that a bit closer, I think the echo is in the wrong place (but, I'm tired and might be wrong).  Try:

```

for i in `seq -w 1 1300`;do for a in Final.txt query.txt;do cat $a | sed -n "$i p" >> Result.txt ;done echo "" >> Result.txt;done

```

Note: It's much easier to debug that stuff if you break it into multiple lines...

---

### Post by markbusu on 2008-05-12
Thanks!!

Indeed it was in the incorrect place!

---

### Post by bapoumba on 2008-05-12
Moved to PT, and marked as solved :)

---

