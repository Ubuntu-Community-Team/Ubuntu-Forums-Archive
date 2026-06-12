---
title: "gcc compiler problem with &lt;iostream&gt;, &quot;undefined reference to 'std::cout'&quot;"
date: 2014-07-04
forum: Programming Talk
---

### Post by jweiner on 2014-07-04
I am teaching myself C++ and have been writing some simple programs; compiling them with gcc -o myprog myprog.cc
Yesterday everything was working fine.  Today the same programs that use #include <iostream> now generate a lot of error message such as

```
john@Samba:~/C++Primer/Chapter1$ gcc -o add add.cc
/tmp/ccmCygpr.o: In function `main':
add.cc.text+0x13): undefined reference to `std::cout'
add.cc.text+0x18): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
```

and lots more

Here is an example of a program that worked yesterday but not today,

```
#include <iostream>

int main()
{
    // prompt user to enter two numbers
    std::cout << "Enter two numbers:" << std::endl; 
    int v1 = 0, v2 = 0;
    std::cin >> v1 >> v2;   
    std::cout << "The sum of " << v1 << " and " << v2
              << " is " << v1 + v2 << std::endl;
    return 0;
}

```
I tried sudo apt-get purge build-essential
then sudo apt-get install build-essential

thinking that maybe the std library was corrupted, but it did not help.

Can anybody suggest a way forward?  I am at my wit's end.

---

### Post by slickymaster on 2014-07-04
Moved to the **Programming Talk** sub-forum.

@jweiner
Please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") in your posts when needed. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by jweiner on 2014-07-04
The answer is that one has to use g++ not gcc.  The #include <iostream> only makes sense to g++.

---

### Post by slickymaster on 2014-07-04
Please mark you thread as SOLVED so other people searching the forums know that it provides a working solution.

Scroll to the top of your thread and look for the Thread Tools menu item on the right of the toolbar, click on this menu item to produce a dropdown menu and then click "Mark this thread as solved".

---

