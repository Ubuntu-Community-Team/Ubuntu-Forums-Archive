---
title: "[C++] sizeof(array) Changes When Passed Through Function"
date: 2010-08-24
forum: Programming Talk
---

### Post by dodle on 2010-08-24
I don't understand, would somebody mind explaining why when I test the size of the array "[color=green]info[/color]" in the main function, it evaluates to 16.  But if I test it in the "[color=green]GetName[/color]" function, it is 4?

[php]#include <iostream>
using namespace std;

char GetName(string info[])
{
	cout << sizeof(info) << endl; // info is 4bytes here
}

int main()
{
    string info[] = {"[name]", "Hello World", "[version]", "1.01"};
	cout << sizeof(info) << endl;  // info is 16bytes here (4x4)
	GetName(info);
	return 0;
}[/php]

---

### Post by dwhitney67 on 2010-08-24
That array is being converted to a pointer to an array of strings.  Since you are working on a 32-bit OS, the size of a pointer is 4-bytes. (On a 64-bit OS, it would be 8-bytes).

In C++, avoid using arrays whenever possible.  Use the STL vector.  It is a better substitute.

P.S.  Also include <string>.

---

### Post by MadCow108 on 2010-08-25
that is one of the most common beginners mistakes.
The notation *string info[]* in function declarations should never have been allowed.
It is identical to  string * info, which makes the problem clear.

also for what you seem to be wanting to do a map is the better structure
[http://www.cplusplus.com/reference/stl/map/](http://www.cplusplus.com/reference/stl/map/)

---

### Post by dodle on 2010-08-25
Okay, I guess it's time to quit being stubborn and learn something new.  :)  I probably won't get any time today, but I'll let you know how I do.  I think you have both recommended before that I use vectors.  Maps are new to me.  From a quick glance at your link, madcow, they appear to be similar to dictionaries in Python.  Maybe I'm wrong, I only took a quick glance.  

Thanks again, I'll post back later.

---

### Post by dwhitney67 on 2010-08-25
Earlier I did not pay too much attention to the context of your data, but MadCow is correct... if you plan to associate data pairs (ie key and value) together, then the STL map makes sense.

---

### Post by interval1066 on 2010-08-25
> **dodle said:**
> Okay, I guess it's time to quit being stubborn and learn something new.

You don't have to, I mean, you continue to code in plain C, and be perfectly happy, but there is just such a wealth of smart objects out there that will make your life so much easier you'll start to wonder how you got along without them. For example, learn about reverse iterators, and then come back and tell us how easy it is to reverse the characters in a string.

---

### Post by Senesence on 2010-08-31
The return type for GetName should be void, not char.

But I guess that doesn't really matter in this context. :)

---

