---
title: "Cout library - QtCreator programming question"
date: 2010-04-10
forum: Programming Talk
---

### Post by hakermania on 2010-04-10
Hi, i am (still ;) ) a beginner in C++
I need the library in which i can found the "cout"
The tutorial I follow uses iostrem.h, however Qtcreator gives error "Library not found"
Qt finds the library iostream (without the extension .h)
but cout doesn't seem to be there - it gives error "`cout` was not declared in this scope"

Any help?

---

### Post by MadCow108 on 2010-04-10
cout is part of the c++ standard library, it represents the standard output stream
it is defined in the header iostream. iostream.h is deprecated, this means your tutorial is outdated!
[http://www.cplusplus.com/reference/iostream/cout/](http://www.cplusplus.com/reference/iostream/cout/)

it lies in the namespace std as all other standard stuff
so you have to call std::cout or put a using namespace std on top of your source file or a using std::cout in the scope where it is used

---

### Post by hakermania on 2010-04-11
hmm all seem to be alright but   p, li { white-space: pre-wrap; }  endl;
 is not recognized as it was with simple cout :(

---

### Post by DiegoTc on 2010-04-11
I know your mistake.
If you are using QT4c++ and want to develop console appli

cations, you have to create a new Console Project. Thats the only way you can do it.
And you have to execute it on the terminal. I don't why it doesn't works :(
You have to compile in QT, after that go to terminal. In terminal go to the directory where the project is and do the following commands.
```

qmake name of the project.pro

```

the do this one
```

./name of the project

```

---

### Post by phrostbyte on 2010-04-12
#include <iostream>
using namespace std;
int main()
{
   cout << "blah blah" << endl;
   return 0;
}

- or -

#include <iostream>

int main()
{
   std::cout << "blah blah" << std::endl;
   return 0;
}

---

