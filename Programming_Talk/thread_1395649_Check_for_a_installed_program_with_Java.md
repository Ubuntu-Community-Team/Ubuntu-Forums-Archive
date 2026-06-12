---
title: "Check for a installed program with Java"
date: 2010-02-01
forum: Programming Talk
---

### Post by Ferrat on 2010-02-01
I've started working on a Java front-end for easy DVD creation from different sources using other programs like mencoder and tovid etc however I was wondering if there is a way to check to see if for ex. mencoder is installed?

I guess I could use Java to shell code which I will be using a lot probably but just checking before if there is another way?

---

### Post by SemiBuz on 2010-02-01
```
File file = new File("/usr/bin/mencoder");

if (file.exists()) {
    System.out.println("mencoder - OK!");
} else {
    System.out.println("Couldn't find mencoder ..");
}

```

---

### Post by Ferrat on 2010-02-01
Ah great :) thanks a lot that was exactly what I was looking for, so obvious I shouldn't really have had to ask ^^

---

### Post by Zugzwang on 2010-02-01
May I suggest that you rather try to call "mencoder -v" or something like that and check if you get a version number back (can be done using the Process class) as it is not guaranteed that "mencoder" will actually reside in "/usr/bin". For example if you compile it yourself, then it will rather be in "/usr/local/bin".

---

### Post by Ferrat on 2010-02-03
Ah even better :) 
then I can check version and if then if present try to find it at the "normal" places and if not ask the user to tell the program where it is :)

---

