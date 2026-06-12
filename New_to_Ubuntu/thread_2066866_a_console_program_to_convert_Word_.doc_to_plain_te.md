---
title: "a console program to convert Word *.doc to plain text *.txt?"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by honeybear on 2012-10-05
Hi,

Without using Wine, I would search a program in the repositories that can using the console (eg. xterm) to convert Word *.doc to plain text *.txt? 

thank you

---

### Post by critin on 2012-10-05
> **honeybear said:**
> Hi,

Without using Wine, I would search a program in the repositories that can using the console (eg. xterm) to convert Word *.doc to plain text *.txt? 

thank you

I did a quick Google for this and all seemed to have at least one problem each.  It can be done if the issue is acceptable and you're knowledgeable with commands.  I believe the issues were different from app to app.

If it doesn't have to be commandline, there is abiword, libre, etc that work great.

---

### Post by Cheesemill on 2012-10-05
You can use LibreOffice:
```
soffice --headless --convert-to txt:text file_to_convert.doc
```

---

### Post by dodo3773 on 2012-10-05
Just use the catdoc program. 
```

catdoc file.doc > newfile.txt

```

---

### Post by honeybear on 2012-10-07
catdoc is nice one

Thank you soooo much !!

---

### Post by dodo3773 on 2012-10-07
> **honeybear said:**
> catdoc is nice one

Thank you soooo much !!

You're welcome. Happy to help.

---

### Post by honeybear on 2012-10-08
> **dodo3773 said:**
> You're welcome. Happy to help.

Nice to hear you. I am glad you did.

---

