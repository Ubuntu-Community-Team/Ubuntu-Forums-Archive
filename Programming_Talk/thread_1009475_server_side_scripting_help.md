---
title: "server side scripting help"
date: 2008-12-12
forum: Programming Talk
---

### Post by agdurrette on 2008-12-12
How posable is it to make a server server side scripting language like php and a data base like mysql. i want to make my own simple data base that information can be put in and a web page read it.
How can i do that.
Thanks for any help.
Andrew

---

### Post by mssever on 2008-12-12
> **agdurrette said:**
> How posable is it to make a server server side scripting language like php As possible as it is to design any language.

---

### Post by slavik on 2008-12-12
Could you rephrase what you want to do?

I am understanding 2 possible things:
1. Create a web page in PHP and have it add things to a database.
2. Write your own PHP that would be run by apache that will have it's own db and such.

Are you trying to do #1 or #2?

---

### Post by agdurrette on 2008-12-12
> **slavik said:**
> Could you rephrase what you want to do?

I am understanding 2 possible things:
1. Create a web page in PHP and have it add things to a database.
2. Write your own PHP that would be run by apache that will have it's own db and such.

Are you trying to do #1 or #2?
Well i want to make my own language and a data base. somthing like php scrript that i can put in a web page and it will display somthing from my own database. like ```
<!mydb id="name1" !>
``` will read a file (somthing.mydb) ```

//comment//
<db title="name">
<dbc id="name1">somtin1</dbc>
<dbc id="name2">somtin2</dbc>
<dbc id="name3">somtin3</dbc>
</db>

``` and display somtin1

---

### Post by slavik on 2008-12-12
so you want to reinvent php and mysql.

unfortunately, I do not have an advice for such task ...

---

### Post by drubin on 2008-12-13
> **agdurrette said:**
> Well i want to make my own language and a data base. somthing like php scrript that i can put in a web page and it will display somthing from my own database. like ```
<!mydb id="name1" !>
``` will read a file (somthing.mydb) ```

//comment//
<db title="name">
<dbc id="name1">somtin1</dbc>
<dbc id="name2">somtin2</dbc>
<dbc id="name3">somtin3</dbc>
</db>

``` and display somtin1

that looks like jsp.

---

