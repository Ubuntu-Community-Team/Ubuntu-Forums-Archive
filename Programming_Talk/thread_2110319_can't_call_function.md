---
title: "can't call function"
date: 2013-01-29
forum: Programming Talk
---

### Post by sanda199 on 2013-01-29
Hi everyone, Let me ask you questions. I wanna call function from another program to my program. I had put header file of another program in my program. But i still can't call. The program is like 

LinuxCamera.h

class LinuxCamera
{
       private:
       LinuxCamera();
}

I wanna call that LinuxCamera function to my program. And inside my program, I wrote like 


#include "LinuxCamera.h"
int main()
{
      LinuxCamera cam;
      cam.LinuxCamera();
}

I declared one variable under same class. But I still got error like "LinuxCamerawas not declared". Why? Please kindly let me know.

---

### Post by ju2wheels on 2013-01-29
Thats what is supposed to happen because you marked the function as private in your class. A private function is not accessible outside of your class, it is only accessible to objects of the class internally. Change private to public if you want the function to be accessible from outside the class.

---

### Post by muteXe on 2013-01-30
You shouldn't have a function in your class the same name as the class. You've instantiated an object, and then you effectively call the constructor again.

You need (i think) something like this:
```


class LinuxCamera
{
public:
  LinuxCamera();
  MyMethod1();
  MyMethod2();
  ....

private:
  // your private data members
};




#include "LinuxCamera.h"
int main()
{
  LinuxCamera cam;     // calls your LinuxCamera() constructor 
  cam.MyMethod1()();   // calls your method
}


```

---

### Post by spjackson on 2013-01-30
When I try to compile your code, the errors I get are these:
```

g++     cam.cpp   -o cam
In file included from cam.cpp:1:0:
LinuxCamera.h:5:1: error: expected ‘;’ after class definition
LinuxCamera.h: In function ‘int main()’:
LinuxCamera.h:4:1: error: ‘LinuxCamera::LinuxCamera()’ is private
cam.cpp:4:13: error: within this context
cam.cpp:5:5: error: invalid use of ‘LinuxCamera::LinuxCamera’

```
which isn't anything like "LinuxCamera was not declared". So that's rather puzzling. Are you using g++ or some other compiler?

Your class definition in LinuxCamera.h needs a semi-colon after the closing brace. Perhaps that's a copy and paste issue, it is a mistake I've seen a few times when Java programmers move to C++.

Your function isn't an ordinary function. It has the same name as the class and is therefore a constructor. A constructor is called automatically when an object is declared, i.e. on the first line of main's body. However, you cannot declare this object because the constructor is private. The most common case is to declare a constructor public; the circumstances under which you really want to delare it private are rare.

Because it is a constructor, you can't call it on an already constructed object as you try to do on the second line of main's body.

Finally, when you come to link your program, you will need to include your implementation of your declared function in the link.

---

