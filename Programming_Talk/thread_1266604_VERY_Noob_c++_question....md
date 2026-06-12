---
title: "VERY Noob c++ question..."
date: 2009-09-14
forum: Programming Talk
---

### Post by conorsulli on 2009-09-14
hi, was just wondering anyone could justify what the hell I've done wrong in the following piece of cpp, If the program looks a little random it's because I was literally banging random commands into a text editor to see if I would be able to code anything at all up..... Then this happened :-(

*cpp source attached, I had to add a .txt to the extension so ubuntuforums would let me upload the .cpp

Thank You.

---

### Post by &#32 Greg on 2009-09-14
Two things: You never declared name or team, and from what I remember of C++, isn't it normally cin >> name?

EDIT: OK, you did declare them (duh, I missed it on an indent)

EDIT2: Worked for me with using cin >> name

---

### Post by no1wantdthisname on 2009-09-14
[http://augustcouncil.com/~tgibson/tutorial/iotips.html](http://augustcouncil.com/~tgibson/tutorial/iotips.html)

Looks like this problem:
```

std::cin.getline() can run into problems when used with std::cin >> var.

```

---

### Post by conorsulli on 2009-09-17
Hi, thanks for the replies...

I would use just regular cin however that would ignore spaces... i.e

enter name : Harry Bo

would return : Hello harry

a simple cin >> name , would only read as far as the space line then cut off.

so I need to try import a string into it.... :-(


edit: To no1wantdthisname : Link seems to have died or is overloaded :-(

---

### Post by dwhitney67 on 2009-09-17
If you need to read a string in its entirety, use getline().

For example:
```

#include <iostream>
#include <string>

int main()
{
   std::string name;
   std::cout << "Enter your name: ";
   std::getline(std::cin, name);

   std::cout << "Hello " << name << std::endl;
}

```

With respect to the issue you are having with your code, you need the app to consume the trailing newline character that is left over after the decimal values are read in.
```

...

  int c;
  cin >> c;

...

  // consume trailing newline
  cin.ignore(10, '\n');  // gobble 10 characters from the cin stream, until a newline is found; 10 was arbitrarily chosen.

```

P.S.  Please, in the future when posting code, please post it in CODE tags similar to what I have done above.  It is annoying to have to reference an attached file or external link.

---

### Post by TheBuzzSaw on 2009-09-17
You really ought to compact several of your output lines as well. You have this:
```
cout << "a is the value: ";
cout << a << endl;
```

Try this instead:
```
cout << "a is the value: " << a << endl;
```

---

### Post by sunchiqua on 2009-09-17
You should take a look at [namespaces]("http://www.cplusplus.com/doc/tutorial/namespaces/"). Instead of using [COLOR=Blue]std::<method>[/COLOR], use [COLOR=Blue]<method>[/COLOR] ( saves your time, code looks cleaner, etc. ).

---

### Post by conorsulli on 2009-09-18
Thanks ever so much guys! I felt like a real clown!.. oh I think I was using namespaces btw.
:P

---

### Post by c0mput3r_n3rD on 2009-09-18
just a tip: declare all variables at the top of the program, always, every single one, and always initialize the variables to something, even if it's 0, or null.
ex:
```

int a = 0;
string myStr = "";
int* num1 = NULL;
bool myBool = FALSE;
int array[10] = 0;
/* etc. */

```

---

### Post by conorsulli on 2010-04-14
Thanks guys... haha this thread is so OLD!! gotten a lot better since then :-)

---

