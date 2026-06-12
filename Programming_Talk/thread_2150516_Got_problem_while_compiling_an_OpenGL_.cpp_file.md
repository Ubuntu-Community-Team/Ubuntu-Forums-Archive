---
title: "Got problem while compiling an OpenGL .cpp file"
date: 2013-06-01
forum: Programming Talk
---

### Post by Rahul04789 on 2013-06-01
Hi freiends,

While compiling a .cpp file having code written for OpenGL by using command:
g++ -lGL -lglut tutorial14.cpp -o aaa  ,
or 
g++ -lGL -lglut -lglew -lglu tutorial14.cpp -o aaa


I got an** error message **as follows:

[B]tutorial14.cpp:25:21: fatal error: GL/glew.h: No such file or directory
compilation terminated.[/B]

My g++ version is as follows:

rahul@rahul-VPCEG28FN:~/Downloads/tutorial14$ g++ --version
g++ (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Regards,
Rahul

---

### Post by MG&amp;TL on 2013-06-01
You'll need to install *libglew-dev*, it's a separate package.

```
sudo apt-get install libglew-dev
```

---

