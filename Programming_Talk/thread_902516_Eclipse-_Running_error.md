---
title: "Eclipse- Running error"
date: 2008-08-27
forum: Programming Talk
---

### Post by Rany Albeg on 2008-08-27
Hi,

I wanted to test eclipse so i wrote a simple project which prints the word 
"hi" on the screen.

I've selected the "Managed make c++ project" option so i wont have to deal with the makefile at this time.

When i run the project i get a message: "An internal error occurred during "Launching"

need some help

thanks.

---

### Post by MarkieB on 2008-08-27
no longer participating in ubuntuforums.org

---

### Post by Rany Albeg on 2008-08-27
installation = sudo apt-get install eclipse eclipse-cdt

and the "program":

#include <iostream>
using std::cout;
int main()
{
  cout<<"hi";
  return 0;
}

the empty line after '}' is also included in the cpp file.

i'll be happy for some help.

---

### Post by mike_g on 2008-08-27
Well your code is correct. Unfortunately the error message is not very descriptive. My best guess is that you may need to link g++ to the IDE. Or, at least you have to do that with Netbeans; never used Eclipse myself.

---

### Post by mike_g on 2008-08-27
Well your code is correct. Unfortunately the error message is not very descriptive. My best guess is that you may need to link g++ to the IDE. Or, at least you have to do that with Netbeans; never used Eclipse myself.

Edit: If you havent already done it you might have to set up the headers and stuff:
```
sudo aptitude install build-essential
```

Oops double post o_O

---

### Post by Rany Albeg on 2008-08-27
Thanks markieB ,mike_b

the problem is solved :

1) open console and install build essential 
   'sudo apt-get install build-essential'

2) add the line 'Debug/project_name' as shown in the picture i added.

---

### Post by MarkieB on 2008-08-27
no longer participating in ubuntuforums.org

---

### Post by Rany Albeg on 2008-08-27
Yea , thanks again.

---

