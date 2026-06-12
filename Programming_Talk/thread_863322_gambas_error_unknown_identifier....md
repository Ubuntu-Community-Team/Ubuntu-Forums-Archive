---
title: "gambas error unknown identifier..."
date: 2008-07-18
forum: Programming Talk
---

### Post by Existance0 on 2008-07-18
When i run this code i get an unknown identifier: fmain.class error
```
PUBLIC SUB Form_Open()
DIM number AS Integer
DIM solution AS Integer
solution = 0
number = 3
END

PUBLIC SUB Button1_Click()

DO WHILE number < 999
IF number MOD 3 == 0 THEN
{
  solution = solution + number
}
ELSE number MOD 5 == 0 THEN
{
  solution = solution + number
}
END IF
INC number
LOOP
label1.text = solution

END
```

anyone know why?

---

### Post by themusicwave on 2008-07-18
I have never used Gambas, but from looking at the code I think the issue is that you define number and solution inside of Form_Open.  They are local to that function in scope.  Meaning they don't exist in your Button1_Click() function.  That is why it is saying unknown identifier.  Variables and function names are identifiers, it is telling you it doesn't know what number and solution refer to.

You need to either define them globally or pass them to the button click function somehow.

Try this:
```

DIM number AS Integer
DIM solution AS Integer
solution = 0
number = 3

PUBLIC SUB Button1_Click()

DO WHILE number < 999
IF number MOD 3 == 0 THEN
{
  solution = solution + number
}
ELSE number MOD 5 == 0 THEN
{
  solution = solution + number
}
END IF
INC number
LOOP
label1.text = solution

END


```

---

### Post by Existance0 on 2008-07-18
nope now i get unexpected dim error
[img]http://img244.imageshack.us/img244/7286/screenshotwz1.png[/img]

---

### Post by Existance0 on 2008-07-18
lol i fixed it the problem was that you cant use { or }

---

### Post by kva on 2008-07-20
How do you global variable in gambas ? I got UNEXPECTED DIM when DIM I AS INTEGER in top line of the code.

---

