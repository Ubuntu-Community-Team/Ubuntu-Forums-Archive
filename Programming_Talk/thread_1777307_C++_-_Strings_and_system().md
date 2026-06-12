---
title: "C++ - Strings and system()"
date: 2011-06-07
forum: Programming Talk
---

### Post by philpot345 on 2011-06-07
Playing around with ubuntu 11.04, kernel 2.6.38-9-generic-pae and gcc  4.5.2, tinkering with c++ in general. Anyways trying to open a webpage in firefox, then add an int value to the end of the string that contains the address and open a new tab with the new link in it as well.

```


#include <iostream>
#include <cstdlib>
#include <string>
#include <stringstream>

int main()
{
string website = "firefox www.google.com/";
stringstream test;
int var = 3;
test.str(website);
test << var;
system(test);
}


```The places that goole brought up all talked about using stringsteam to do the job, but the compiler doesn't like anything I have been trying.
Read up a bit about stringstream at [http://www.cplusplus.com/reference/iostream/stringstream/stringstream/](http://www.cplusplus.com/reference/iostream/stringstream/stringstream/) but just not sure how to implement it.

To recap:

Problem 1:
Adding an int var to the end of a string.

Problem 2:
Sending the appended string through the system() command.

Any insight or info that could lead me to understanding this a little better would be very much appreciated, thanks.

---

### Post by dwhitney67 on 2011-06-07
This should work, with whatever you are attempting to accomplish:
```

#include <string>
#include <sstream>
#include <iostream>
#include <cstdlib>

int main()
{
   std::string       website = "firefox www.google.com/";
   int               var = 3;
   std::stringstream test;

   test << website << var;

   system(test.str().c_str());
}

```

---

### Post by Simian Man on 2011-06-07
dwhitney67 is correct.  C++ is a horrible language for this kind of thing though.

---

### Post by hakermania on 2011-06-07
by the way, the correct way to open a webpage is to call
'xdg-open' so as to open with the default browser, which may not be firefox

---

### Post by philpot345 on 2011-06-07
Awsome Dwhitney67, works like a charm! Thanks. Quick question though, I noticed at this snipit of code:

```


system(test.str().c_str());


```what is the .c_str() for? is it included any time stringstream is used?

Also Hackermania, is 'xdg-open' used on all versions of linux? As in should I be able to use it from gnome to kde or evern fxce? and on a side note would you recommend a place or two to read up on this? For example is it related to gnome in general or x.org?
[]("http://ubuntuforums.org/member.php?u=895189")

---

### Post by hakermania on 2011-06-07
I don't know, I was unaware that you needed a cross-platform application :/
I don't have any other Desktop than GNOME (even Backtrack with GNOME lol)

---

### Post by dwhitney67 on 2011-06-07
> **philpot345 said:**
>  Thanks. Quick question though, I noticed at this snipit of code:

```

system(test.str().c_str());

```
what is the .c_str() for? is it included any time stringstream is used?

The stringstring encapsulates an std::string; to retrieve this string, use the str() method.  Once the std::string is in "hand", then use the c_str() method (of std::string) to obtain the const char*, or C-style string as some folks call it, to pass to system().  After all, that is the type of data that the system() call requires.

Google for "C++ function chaining" for more details.

---

### Post by JupiterV2 on 2011-06-07
For what its worth, function chaining is common practice in Java, too.

Just felt the need to share.

---

### Post by cgroza on 2011-06-07
Toolkits like wxWidgets have a very elegant way of opening links into the default browser.
I use wxLaunchDefaultBrowser(wxString).

---

