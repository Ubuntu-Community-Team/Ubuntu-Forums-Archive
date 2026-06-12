---
title: "Weird output when executing .cpp"
date: 2013-07-18
forum: Programming Talk
---

### Post by c beginner on 2013-07-18
I'm an absolute beginner to C++.  The output I am having from executing the program is completely different on my Ubuntu terminal and online C++ compilers.

Please spare a moment to refer to my simple code: [http://codepad.org/EPmtzMqK](http://codepad.org/EPmtzMqK)

[IMG]http://i39.tinypic.com/rk0co0.png[/IMG]

I've no idea why it's showing '8s' insted of '8 is'. Btw i'm using gedit as the text editor.

---

### Post by c beginner on 2013-07-18
Err my bad, I confused << with + in my head for some reason. Now all is working fine.

---

### Post by Warren Hill on 2013-07-18
Error is in line 26 of your code 

change this```

cout << "Cube root of " << cube << " is " + cubeRoot << endl;
```

to this```

cout << "Cube root of " << cube << " is " << cubeRoot << endl;
```


That is you had a **+ **where you should of had **<< **

Not sure why it printed what it did but it's clear why it didn't print what you wanted.

Tested on Ubuntu 12.04 32-bit same results as you for unmodified code.  Works correctly with this change.

---

### Post by oldos2er on 2013-07-18
Moved to Programming Talk.

---

