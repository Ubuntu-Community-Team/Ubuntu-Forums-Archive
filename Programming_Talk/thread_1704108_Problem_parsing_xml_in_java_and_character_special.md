---
title: "Problem parsing xml in java and character special"
date: 2011-03-10
forum: Programming Talk
---

### Post by alexlfe on 2011-03-10
I have a problem in Ubuntu...
with special character, because i have developer a program in windows and work fine but in ubuntu no, why? 

In this code...

DocumentBuilder db;
db = dbf.newDocumentBuilder();
Document document;
document = db.parse(pathFileXML);
document.getDocumentElement().normalize();
System.out.println("Result:" + this.getAsString(document));

I have the output with fine special chacter, for example:
èàéò

while the same program in ubuntu don't work...
like ƒÂ¨ÃƒÂ¨ÃƒÂ¨ ÃƒÂ

why...
the code is the same...

---

### Post by PaulM1985 on 2011-03-10
Are you using the same runtime environment?

What happens if you type:
```

java -version

```
in Windows and then in Ubuntu?

I think OpenJDK Runtime is the default on Ubuntu whereas I am assuming you are using Sun Java Runtime on Windows.

Paul

---

### Post by alexlfe on 2011-03-10
I solved ...

---

### Post by alexlfe on 2011-03-10
I have solved alone, because java encode each uses the operating system and therefore you must always set the encode if you do not want to have problems changing platforms. :-)))))

---

