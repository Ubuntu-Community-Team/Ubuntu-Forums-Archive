---
title: "Missing header files"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by tuxia on 2011-09-30
Hello,
I installed tesseract-ocr software by downloading from svn and compiling and making and installing.
Now i am looking at /usr/include directory and can not see tesseract related headers.
 
Also when i try to compile a source file of mine which includes headers of tesseract, i get lotd of "undefined reference to" errors.
 
Should i install tesseract-ocr-dev, but in repos it is old, and i want the last version.
 
Edit:
My question is should not the installation distribute headers into usr/include directory???
 
Thanks for any idea.

---

### Post by acrazyplayer on 2011-09-30
Hello, you may just have to add it to the build commands, for example I use sfml and to make it compile or build I have to use the commands "g++ -Wall -o "%e" "%f" -lsfml-graphics" If I dont include the -lsfml-graphics then I have the same problems you do.

---

