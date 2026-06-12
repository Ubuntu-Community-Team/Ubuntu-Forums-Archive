---
title: "to_string compilation error"
date: 2015-10-28
forum: Programming Talk
---

### Post by EricDallal on 2015-10-28
I am using the to_string function in a c++ program I wrote, but when I try to compile, I get

error: ‘to_string’ was not declared in this scope.

I have #include <string> in the file, as well as using namespace std;. I compiled the program with g++ and used the -std=c++11 flag, and it says the version is gcc 4.8.4. Why is this not compiling?

---

### Post by mfvpcrec on 2015-10-28
Did you try a small program with  to_string() only?
Maybe you  forgot something in the code...an ambit declaration maybe? 
Bye!

---

### Post by EricDallal on 2015-10-28
It worked with small program, at which point I realized that when I compiled the small program, I had done so with only the -std=c++11 flag, and not with any of the other flags I had used. I believe the problem is that I couldn't use -ansi. Thanks for your help!

---

### Post by mfvpcrec on 2015-10-28
I do not have that version of g++ , i have the 5.2.1 version , but 

```

#include <iostream>
#include <string>

using namespace std;

int main (void)
{
        int a=77;
        
        cout<<to_string(a)+" Is a good number"<<endl;

        return 0;
}

```

works fine to me ...

---

