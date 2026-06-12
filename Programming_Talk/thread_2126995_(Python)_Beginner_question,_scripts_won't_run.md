---
title: "(Python) Beginner question, scripts won't run?"
date: 2013-03-18
forum: Programming Talk
---

### Post by KamonB on 2013-03-18
This is a extremely basic question and I feel awful just asking it but:


I'm trying to teach myself Python and I've been reading the stickies.. However when I start saving strings of codes into gedit, the site I'm learning off of tells me to "run the script" 

How do I "run the script" through just gedit so it'll pop up in the Python3 terminal in Ubuntu?

I save it as test1.py but I have no idea what to do with it.

---

### Post by Mr. Shannon on 2013-03-18
You run most python scripts from the command line.  So open a terminal with ctrl+alt+t and then cd to the directory your script is and run the script with:
```
./<your script>
```

However, your script is probably not marked as executable yet, so you will first have to do:
```
chmod +x <your script>
```

---

### Post by schragge on 2013-03-18
From the terminal (**Ctrl**+**Alt**+**t**) ```
python test1.py
``` or ```
python3 test1.py
```

---

### Post by KamonB on 2013-03-18
I feel so dumb, thank you guys so much!

---

