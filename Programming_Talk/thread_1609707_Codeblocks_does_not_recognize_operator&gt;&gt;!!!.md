---
title: "Code::blocks does not recognize operator&gt;&gt;!!!"
date: 2010-10-30
forum: Programming Talk
---

### Post by kdizil on 2010-10-30
Ok i just switched from the netbeans IDE to code::blocks and it was working well till i tested it with "cin>>" and it gave me the error
no match for 'operator>>'. If anybody knows how to fix this please help 

the code was
```
#include <iostream>

using namespace std;

int main(){
    int test;
cin>>test>>endl;
cout<<test<<endl;
return 0;}

```

---

### Post by spjackson on 2010-10-30
> **kdizil said:**
> Ok i just switched from the netbeans IDE to code::blocks and it was working well till i tested it with "cin>>" and it gave me the error
no match for 'operator>>'. If anybody knows how to fix this please help 

the code was
```
#include <iostream>

using namespace std;

int main(){
    int test;
cin>>test>>endl;
cout<<test<<endl;
return 0;}

```
You shouldn't be able to compile that with netbeans either. You cannot read into std::endl .

---

### Post by kdizil on 2010-10-30
It works on Visual studios when i write a c++ program why doesnt it work on code::blocks im new to programming and could really use some help solving this problem

---

### Post by kdizil on 2010-10-30
Never mind LOL programming error im a newb and i appreciate the help!!

---

### Post by spjackson on 2010-10-30
> **kdizil said:**
> It works on Visual studios when i write a c++ program why doesnt it work on code::blocks im new to programming and could really use some help solving this problem
Your code does not compile with Visual C++ 2008. It should not compile with any C++ compiler because it is not valid C++. If you find a C++ compiler that will compile it, then report it as a bug to the compiler vendor or maintainer. When I said that you cannot read into std::endl, I meant precisely that.
```

cin>>test>>endl;

```That line is invalid. Try changing it to something valid like
```

cin>>test;

```

---

