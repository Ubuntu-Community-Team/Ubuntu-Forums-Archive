---
title: "C++ compiled files are not executing"
date: 2007-06-07
forum: Programming Talk
---

### Post by Wechuks on 2007-06-07
It happens with all compiled files, when I compile any source code all is ok, but when itry to run it , nothing happens
exaple of code 
```
#include <iostream>

int main()
{
   std::cout << "Hello World\n";
}

```
I am using Anjuta 1.2.4a
Why it is happening?

---

### Post by badactress on 2007-06-07
I'm not sure if just compiling the code in Ajunta creates an executable.. What happens if you 'build' the project (in same menu as 'compile') instead of just compiling? This should create a finished executable file that will run ok..

---

### Post by Wechuks on 2007-06-07
I Am using build and it creates executable , but it isnt working

---

### Post by slavik on 2007-06-07
how do you run the binary?

anjuta doesn't run the binaries as soon as it creates them ;)

---

### Post by Biased turkey on 2007-06-07
After you created the project with Anjuta, do the 3 following steps:
Build -> Auto Generate
Build -> Build All
Build -> Execute

---

### Post by jfinkels on 2007-06-07
You could try to compile and run it from the terminal to see if that's working:```
g++ -o outputfile source.cpp
./outputfile
```

---

