---
title: "Basic C++ help"
date: 2009-07-19
forum: Programming Talk
---

### Post by sonnyxway on 2009-07-19
I've started learning c++ following along with a book. I'm up to "Employing variable arrays" and I've written out the script as it has instructed me, this is what I have ```
#include <iostream>
using namespace std ;


int main()
{
float nums[3] ;
nums[0] = 1.5 ; nums[1] = 2.75 ; nums[2] = 3.25 ;
    char name[5] = { 'm', 'i', 'k', 'e', '\0' } ;
    int coords[2] [3] = { { 1, 2, 3 } , { 4, 5, 6 } } ;
}
cout << "nums[0]: " << nums[0] << endl ;
cout << "nums[1]: " << nums[1] << endl ;
cout << "nums[2]: " << nums[2] << endl ;
cout <<    "name[0]: " << name[0] << endl ;
cout << "string: " << name << endl ;
cout << "coords[0][2]: " << coords[0][2] endl;
cout << "coords[1][2]: " << coords[1][2] endl;

return 0 ;
}

```And the error I get is, ```
arrays.cpp:12: error: expected constructor, destructor, or type conversion befor
e '<<' token
arrays.cpp:13: error: expected constructor, destructor, or type conversion befor
e '<<' token
arrays.cpp:14: error: expected constructor, destructor, or type conversion befor
e '<<' token
arrays.cpp:15: error: expected constructor, destructor, or type conversion befor
e '<<' token
arrays.cpp:16: error: expected constructor, destructor, or type conversion befor
e '<<' token
arrays.cpp:17: error: expected constructor, destructor, or type conversion befor
e '<<' token
arrays.cpp:18: error: expected constructor, destructor, or type conversion befor
e '<<' token
arrays.cpp:20: error: expected unqualified-id before "return"
arrays.cpp:21: error: expected declaration before '}' token

```I'm sure its something really simple that I'm looking over x:

---

### Post by kjohansen on 2009-07-19
You have more close "}" than you have open "{".

so you end the main function and then have more lines of code that are not in any function.  you also need "<<" before the endls



Functioning code:
```

#include <iostream>
using namespace std ;


int main()
{
float nums[3] ;
nums[0] = 1.5 ; nums[1] = 2.75 ; nums[2] = 3.25 ;
char name[5] = { 'm', 'i', 'k', 'e', '\0' } ;
int coords[2] [3] = { { 1, 2, 3 } , { 4, 5, 6 } } ;

cout << "nums[0]: " << nums[0] << endl ;
cout << "nums[1]: " << nums[1] << endl ;
cout << "nums[2]: " << nums[2] << endl ;
cout <<    "name[0]: " << name[0] << endl ;
cout << "string: " << name << endl ;
 cout << "coords[0][2]: " << coords[0][2]<<endl;
 cout << "coords[1][2]: " << coords[1][2]<<endl;

return 0 ;
}

```

---

### Post by sonnyxway on 2009-07-19
I didn't notice I missed the last two "<<" before the endls, and i knew the bracket thing in the middle of my variables and statements or whatever didn't belong but the book tells me to put it there. Meh oh well it works now so thank you.

---

### Post by Oler1s on 2009-07-19
I recommend consistently following an [Indent style (Wikipedia entry)](http://en.wikipedia.org/wiki/Indent_style). Your code isn't cleanly formatted, making the errors hard to spot. Now that you know, don't muck up formatting again. (It will just lead to a miserable time like this)

---

### Post by sonnyxway on 2009-07-19
Haha thank you, I've always noticed people doing this but never understood when and where to do it.

---

### Post by MindSz on 2009-07-20
There's many text editors out there that can do the indenting for you. I use emacs and it indents my code as I type it.

You should try to get used to indenting ... it just makes things a lot easier in the long run.

---

