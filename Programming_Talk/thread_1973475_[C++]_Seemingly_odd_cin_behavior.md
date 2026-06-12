---
title: "[C++] Seemingly odd cin behavior"
date: 2012-05-04
forum: Programming Talk
---

### Post by catlover2 on 2012-05-04
Hello world!

If I compile the following code,
[php]
#include <iostream>
#include <string>
using namespace std;
#define NEWLINE "\n"

int main ()
{
  string w_string;
  cout << "Please enter some combination of characters that DOES include some whitespace: ";
  getline (cin,w_string);
  cout << NEWLINE << "You just entered the string '" << w_string << "'" << NEWLINE;
  return 0;
}
[/php]
it runs as expected:
```

$ ./a.out 
Please enter some combination of characters that DOES include some whitespace: Hi there!

You just entered the string 'Hi there!'

```


BUT, if I add more to it as follows,
[php]
include <iostream>
#include <string>
using namespace std;
#define NEWLINE "\n"
#define TWOLINE "\n \n"

int main ()
{
  cout << "Please enter a number: ";
  int a_number;
  cin >> a_number;
  cout << NEWLINE;
  cout << "You just entered the number " << a_number << ", and you get " << a_number+1 << " if you add 1 to it." << TWOLINE;

  string w_string;
  cout << "Please enter some combination of characters that DOES include some whitespace: ";
  getline (cin,w_string);
  cout << NEWLINE << "You just entered the string '" << w_string << "'" << NEWLINE;
  return 0;
}

[/php]
then it still compiles but outputs this
```

$ ./a.out 
Please enter a number: 7

You just entered the number 7, and you get 8 if you add 1 to it.
 
Please enter some combination of characters that DOES include some whitespace: 
You just entered the string ''

```
without waiting for my input.

What am I missing?

-catlover

---

### Post by Vaphell on 2012-05-04
you are missing the newline char waiting in the buffer. It gets eaten by getline() right off the bat, producing empty string, so you don't get to type anything.
after cin >> var; use cin.ignore() to purge the buffer.

[http://www.augustcouncil.com/~tgibson/tutorial/iotips.html](http://www.augustcouncil.com/~tgibson/tutorial/iotips.html)

btw why do you use defined NEWLINE istead of std::endl ?

---

### Post by catlover2 on 2012-05-04
Thanks for the link. I see what I did there now.

As for using a defined NEWLINE, does it matter? If I use NEWLINE, then I can also define TWOLINE, THREELINE, etc without having to type endl multiple times.

---

