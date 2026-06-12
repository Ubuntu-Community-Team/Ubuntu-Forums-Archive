---
title: "How to disable HTML button ( via JavaScript ) ?"
date: 2009-09-06
forum: Programming Talk
---

### Post by defacto on 2009-09-06
Here's the button, outside of my form:
```
<button name="send" onClick="submitForm()">&#1054;&#1090;&#1087;&#1088;&#1072;&#1074;&#1083;&#1103;&#1090;&#1100;</button>

```

Keep in mind that, this one doesn't work right ( doesn't disable my button ):
```
document.getElementById("send").disabled = true;
```

Any ideas ? Is there a way to disable button which doesn't belong to a form ?

---

### Post by Linteg on 2009-09-06
Perhaps you should let your button's id and not name be send ;)

---

### Post by defacto on 2009-09-06
> **Linteg said:**
> Perhaps you should let your button's id and not name be send ;)

Ty :)

---

