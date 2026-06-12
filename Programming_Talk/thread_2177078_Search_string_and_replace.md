---
title: "Search string and replace"
date: 2013-09-27
forum: Programming Talk
---

### Post by neogeo1128 on 2013-09-27
Hi, 

I would like to know how can I search and replace in the following html file 
I need to find the "studentid" as search string and do the following replacement
(there are >100 studentid in the html file so I don't know how to do this)

Source : <a href="[http://www.thewebsite.abcd.com/listing.asp?studentid=K248]("http://ubuntuforums.org/view-source:http://www.hkjc.com/chinese/racing/horse.asp?horseno=K248")" border="0">Peter</a>

Target:
<a href="[http://www.thewebsite.abcd.com/listing.asp?studentid=K248]("http://ubuntuforums.org/view-source:http://www.hkjc.com/chinese/racing/horse.asp?horseno=K248")" border="0">Peter (K248)</a>


Any questions/comments are welcome
Thanks a lot!

---

### Post by ofnuts on 2013-09-27
In a terminal:
```

sed -r 's!studentid=([^"]+)" border="0">([^<]+)!studentid=\1" border="0">\2 \(\1\)!'  <yourfile

```

In slow motion:
[LIST]
[*]([^"]+) grabs the student id (everything between the "=" and the next double quote 
[*]([^<]+) grabs the student name (everything up to the next "<") 
[*]\1 and \2 in the second part are used to plug back the data extracted above 
[/LIST]

The same expression (or something very close to it) can also be used in an editor that takes regular expressions in replace commands.

---

### Post by neogeo1128 on 2013-09-27
Thanks a lot ! It worked !

---

### Post by neogeo1128 on 2013-09-27
But... one question... if the html file have no CR line feed (that is no Carriage RETURN on each line) it seems not working...... any ideas on why?

---

### Post by ofnuts on 2013-09-27
As done above it does only one change per line. Tell to do as many change as it can instead with an extra "g" at the end:
```

sed -r 's!studentid=([^"]+)" border="0">([^<]+)!studentid=\1" border="0">\2 \(\1\)!g'  <yourfile

```

---

### Post by neogeo1128 on 2013-09-27
Thanks again ... you have teached me a lot !

---

