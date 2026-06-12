---
title: "Moving insertion point in a file"
date: 2012-06-18
forum: Programming Talk
---

### Post by squirrelplayingtag on 2012-06-18
I'm attempting to create a simple script that searches for a string and removes the entire line. Right now I'm using sed to remove the required line but the insertion point returns to the beginning of the file. I need the insertion point to be the last line of the file. How can I do that using a bash script?

---

### Post by trent.josephsen on 2012-06-18
What insertion point? Are you trying to script an editor of some variety?

What you want to do is not very clear. Can you post what you did with sed and describe how the result is not what you want?

---

### Post by squirrelplayingtag on 2012-06-18
I have a file called uuid which has lines as such:

```

aaaa:bbbb:cccc:dddd
1111:2222:3333:4444
eeee:ffff:gggg:hhhh
5555:6666:7777:8888

```

Right now if I open up the file in any text editor and start typing, the insertion point is after the 8888. Once I run 

```

sed -i '/eeee:ffff:gggg:hhhh/d' /home/sqt/uuid

```

I correctly get a file that looks like:

```

aaaa:bbbb:cccc:dddd
1111:2222:3333:4444
5555:6666:7777:8888

```

but if I open the uuid file in a text editor and start typing the insertion point is now before aaaa. I need for text to be entered after 8888 if I simply open the file in a text editor.

---

### Post by Barrucadu on 2012-06-18
`sed` doesn't alter where the editor places its cursor.

---

### Post by Bachstelze on 2012-06-18
You Can't Do That&#8482;

It's up to the editor to determine where it places its cursor at startup. What you refer to as "insertion point" simply does not exist.

---

### Post by codemaniac on 2012-06-18
Do you want to instruct your editor to open up and position its cursor at the last line ?

We can instruct vim where we want to place the cursor at startup .

In vim i would do a ,

```
vim +$ file_name
```

to place the cursor at the last line .

---

### Post by pbrane on 2012-06-18
It may be that the editor saves the last edit point. When you re-open the file it places the cursor at that point. Gedit does this.

But when you run sed it deletes a line and the last saved edit point is no longer valid. It is beyond the end of the file.

---

