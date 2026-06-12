---
title: "[C++] String ptr with c_str"
date: 2010-09-16
forum: Programming Talk
---

### Post by xnerdx on 2010-09-16
I'm having an issue with a function I built to make the string all lower case. I have the fucntion taking an argument of (string* uInput) and the function is called by (&tempInput). In the function being called I'm trying to run uInput.c_str() (I've also tried c_str(uInput) but I get an error about c_str() being undeclared (first use in function). Here is the class function I'm attempting to build:
```

void FCard::makeAllLower(string* uInput)
{
     for(int i = 0; i < strlen(c_str(uInput)); i++)
     {
         uInput[i] = tolower(uInput[i]);
     }
}

```
I use c_str in other instances of the program and have no problem. Is it because I'm using a string*?

---

### Post by dwhitney67 on 2010-09-16
Use uInput.size() or uInput.length() to acquire the size of the string.

Or do something like:
```

void FCard::makeAllLower(**std::string&** uInput)
{
   for (std::string::iterator it = uInput.begin(); it != uInput.end(); ++it)
   {
      *it = tolower(*it);
   }
}

```
I recommend that you pass class objects by reference, not by pointer.  This is typically what is done; but do what you want.


P.S.  Another alternative:
```

void myToLower(char& ch)
{
   ch = tolower(ch);
}

void FCard::makeAllLower(**std::string&** uInput)
{
   std::for_each(uInput.begin(), uInput.end(), myToLower);
}

```

---

### Post by xnerdx on 2010-09-16
I made the mistake of thinking that to pass by reference I had to pass the arguements to (string& uInput) with (*tempInput). Simply changed it to (tempInput) and compiled fine :D

---

