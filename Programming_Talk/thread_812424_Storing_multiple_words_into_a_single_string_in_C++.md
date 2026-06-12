---
title: "Storing multiple words into a single string in C++"
date: 2008-05-29
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-05-29
Hey All

How do I store multiple words into a single variable in C++?  Say I'm writing a program that takes a user's first and last names and stores them both into a single string.  How would I do that?  I asked someone this question before and seem to remember them saying something about getline or something like that...
Thanks.

---

### Post by LaRoza on 2008-05-29
> **the_real_fourthdimension said:**
> Hey All

How do I store multiple words into a single variable in C++?  Say I'm writing a program that takes a user's first and last names and stores them both into a single string.  How would I do that?  I asked someone this question before and seem to remember them saying something about getline or something like that...
Thanks.
[php]
#include <iostream>
int main(int argc, char** argv)
{
    std::string name;
    std::cout << "What is your name? \n" << std::endl;
    std::getline(std::cin,name);
    std::cout << "You are " <<  name << std::endl;
    return 0;
}
[/php]

---

### Post by dempl_dempl on 2008-05-29
Before we start:

[http://www.cplusplus.com/reference/string/getline.html](http://www.cplusplus.com/reference/string/getline.html)

I use [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)  site all the time when I program. 

Here's an example I've copy+pasted from that link


```

// getline with strings
#include <iostream>
#include <string>
using namespace std;

int main () {
  string str;
  cout << "Please enter full name: ";
  getline (cin,str);
  cout << "Thank you, " << str << ".\n";
}

```

Cheers!

LaRoza: It seems that you were 2 secs faster than me :)

---

### Post by the_real_fourthdimension on 2008-05-29
Thank you both very much! :)

---

### Post by LaRoza on 2008-05-29
> **the_real_fourthdimension said:**
> Thank you both very much! :)

Mine is better though.

---

### Post by dempl_dempl on 2008-05-29
No, I have a "Thank you " in my code  , which makes it more user-friendly  :P

---

### Post by LaRoza on 2008-05-29
> **dempl_dempl said:**
> No, I have a "Thank you " in my code  , which makes it more user-friendly  :P

I don't take the weasel way and use "using namespace std;", making the code more explicit, more programmer friendly.

---

