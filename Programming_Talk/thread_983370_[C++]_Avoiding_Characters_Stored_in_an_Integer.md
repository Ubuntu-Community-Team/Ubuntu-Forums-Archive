---
title: "[C++] Avoiding Characters Stored in an Integer"
date: 2008-11-15
forum: Programming Talk
---

### Post by sillyrabbit on 2008-11-15
First off, I did Google this with no good results...

I have a console program and it takes integers as options. However, when I put in a letter as an answer the program messes up. **How do I prevent character(s) from being stored in an integer?**

int option;
cin >> option;

---

### Post by dwhitney67 on 2008-11-15
cin will not store characters in an integer.

If you query for an integer using cin, and the user enters one or more characters (followed by 'enter'), then cin will fail.  You can verify this by calling cin.fail().

To clear cin's error state, you need to call cin.clear(), followed by a call to cin.ignore() remove unwanted characters from the data stream.

For example:
[php]
...
int value = 0;

while (true)
{
  std::cout << "Enter a number: ";
  std::cin  >> value;

  if (std::cin.fail())
  {
    std::cin.clear();
    std::cin.ignore(1024, '\n');  // ignore at most 1024 characters until '\n' found
  }
  else
    break;  // all good; we got a value
}
...
[/php]

---

### Post by WW on 2008-11-15
*Nevermind... I should test more before posting code.*

---

