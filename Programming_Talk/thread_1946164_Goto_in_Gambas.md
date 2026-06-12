---
title: "Goto in Gambas"
date: 2012-03-24
forum: Programming Talk
---

### Post by Gamer1120 on 2012-03-24
Hello everyone,
I'd like to know how to use the GOTO command (from Visual Basic) in Gambas2. My code is as following:


```
PUBLIC SUB Button1_Click()

  DIM l AS Integer = TextBox1.text
  DIM b AS Integer = TextBox2.Text
  DIM h AS Integer = TextBox3.Text
  Uitslag.text = ""
IF (b > 10 AND l > 15) THEN GOTO NIETTEKLEIN
ELSE Uitslag.text = "Te klein"
END 
NIETTEKLEIN:
IF ((l + b + h < 120) AND (l < 70)) THEN GOTO NIETTEGROOT
ELSE Uitslag.text = "Te groot"
END 
NIETTEGROOT:
Uitslag.text = "Goed"
ENDIF 
ENDIF 
END
```

I'm Dutch, so sorry for that. But 'Te klein' means too small, 'Te groot' means too big, and 'Goed' means Good. NIETTEKLEIN means Not too small, NIETTEGROOT means Not too big, and Uitslag means the result.

---

### Post by Tony Flury on 2012-03-24
I assume the code is not working ?

It could be because you are trying to GOTO to a place inside a control Structure (i.e. an IF/THEN/END IF) structure.

GOTO is a really bad idea (in any language) so best to avoid it if you can - there are rarely any good reasons to use it.

I have never written GAMBAS - but this should work : 
```

PUBLIC SUB Button1_Click()

  DIM l AS Integer = TextBox1.text
  DIM b AS Integer = TextBox2.Text
  DIM h AS Integer = TextBox3.Text
  Uitslag.text = ""
IF (b > 10 AND l > 15) THEN 
    IF ((l + b + h < 120) AND (l < 70)) THEN 
        Uitslag.text = "Goed"
    ELSE 
        Uitslag.text = "Te groot"
    ENDIF
ELSE
    Uitslag.text = "Te klein"
ENDIF
END

```

---

