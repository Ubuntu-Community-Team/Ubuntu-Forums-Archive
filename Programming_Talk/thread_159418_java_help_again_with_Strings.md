---
title: "java help again with Strings"
date: 2006-04-12
forum: Programming Talk
---

### Post by sublime on 2006-04-12
alright so i have this string that i need to return.  however i need to return it in an amount of lines described by the user.  so if the user says that the size = 3, then i need to print 3 lines at a time. if the user says 4 i need to print it at 4 lines at a time, etc.

example:  size = 5 and string length is 24

X X X X X
X X X X X
X X X X X
X X X X X
X X X X X 

size = 4 and string length is 15

X X X X
X X X X
X X X X
X X X X


is there some sort of string break method that can make eac line in a string a certain length?  i would post the code however its part of a rather lengthy program and it doesnt really make sense without reading the entire code.

disclaimer:  this is homework.  i am not asking for someone to do it for me.  jsut a little help maybe.

---

### Post by LordHunter317 on 2006-04-12
Read the API documentation for java.lang.String.  There is a substring() or split() function (I forget the exact name) that can give you arbitrary substrings of a bigger string.

---

