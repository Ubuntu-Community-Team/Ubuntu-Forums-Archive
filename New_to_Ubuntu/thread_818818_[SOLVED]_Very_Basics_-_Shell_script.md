---
title: "[SOLVED] Very Basics - Shell script"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Phoenixzeus on 2008-06-04
Hello,
As the title suggests, I have having problems with the very basics of shell scripting.

I have looked around for quite awhile and I couldn't find much on this topic. I am looking for the shell command to open a file with a particular problem. In this case, I want to open a file called test.swf with Mozilla firefox (I have all the swf addins working and it will play if I open it manually). Mozilla firefox is NOT the default player for this type of file.

Any help is appreaciated :)
-Phoenixzeus

---

### Post by Joeb454 on 2008-06-04
If you want to do it manually every time, then you would run ```
firefox /path/to/swf
``` which should work just fine :)

If you want a terminal app that asks you where the file is located, then I should be able to make one :)

---

### Post by Phoenixzeus on 2008-06-04
Thank you, that is all I needed. On the off chance that you might know, I made another script and tried to run it by ./<filename> however, it gives me a permission denied message. It has been made an executable and I have sudo'd it. I have checked and everyone has write/read permissions. Is there anything obvious I am missing?

---

### Post by beanhead on 2008-06-04
Well bash is the default shell, here is a link to the manual it should help you understand whats happening when you use it,

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

It takes some time to get used to it ! Hope it helps :D

---

### Post by Joeb454 on 2008-06-04
It's because a .swf file is a binary file :)

I just tried running a .swf I have, and that was the error I got ("Cannot execute binary file")

---

### Post by rampageoberon on 2008-06-04
> **Phoenixzeus said:**
> Thank you, that is all I needed. On the off chance that you might know, I made another script and tried to run it by ./<filename> however, it gives me a permission denied message. It has been made an executable and I have sudo'd it. I have checked and everyone has write/read permissions. Is there anything obvious I am missing?


Umm, sounds like it doesn't have execute permissions

chmod it to 755

```
chmod 755 file
```

hope that helps

---

### Post by Phoenixzeus on 2008-06-04
Thank you everyone, it was Joeb454 said, its because SWF is a binary file and I wasn't telling it to open with any particular program. Thanks again, you were all helpful :)

---

### Post by Joeb454 on 2008-06-04
No problem - and glad to see you marked the thread solved :D

---

### Post by Phoenixzeus on 2008-06-04
Lol :) I know its something that is very rarely done :)
Thanks again mate.

---

