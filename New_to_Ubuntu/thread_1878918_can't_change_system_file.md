---
title: "can't change system file"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by tomgnu on 2011-11-10
I'm trying to add another library to my Arduino Library but with no luck...
I have opened file system...usr...share Arduino and tried to drag my library into the Arduino library but it won't stay over..
Tried as root.
Anything else I can try?
Thank you

---

### Post by MG&amp;TL on 2011-11-10
Press Alt-f2 and type:

```
gksu nautilus
```

enter your password, then drag and drop the files. If it still won't work, you have a very fundamental problem.

Be careful with root, as always. :)

When you say tried as root, how?

---

### Post by MG&amp;TL on 2011-11-10
Or:

```
sudo cp arduinofiles /usr/where_the_arduino_stuff_goes
```

---

### Post by tomgnu on 2011-11-10
I seem to have a fundamental problem.
Thanks for your help anyway.

---

### Post by MG&amp;TL on 2011-11-10
What error do you get? Are you root on your system?

---

