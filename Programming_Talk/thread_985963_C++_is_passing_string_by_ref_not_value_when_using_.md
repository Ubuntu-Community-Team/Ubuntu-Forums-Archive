---
title: "C++ is passing string by ref not value when using namespacees"
date: 2008-11-18
forum: Programming Talk
---

### Post by bluedalmatian on 2008-11-18
ive got a file called main.cpp

which declares some global string variables in a namesapce e.g

myNamesapce
{
    std::string myString;


}

main()
{
   myString = "XYZ";
   ....
   someFunction(myNamespace::myString);
}

If we imagine someFunction has been declared so:

someFunction(std::string s)
{
....
}

then my use of it would be correct?  Yet when I compile it complains that I'm passing by reference and that the function
someFunction(std::string&) doesnt exist.

I can only assume this is sometihng to do with the namespaces because I cant see any other reason for this to fail?

Any ideas please?

Thanks

---

### Post by Tony Flury on 2008-11-18
sure in C++ a string is just a pointer to a memory block - in which case they are always passed by reference. Your function would not get a unique version of the string.

---

### Post by scourge on 2008-11-18
> **Tony Flury said:**
> sure in C++ a string is just a pointer to a memory block - in which case they are always passed by reference. Your function would not get a unique version of the string.

A C programmer coming to the rescue? std::string is not a pointer, and it can be passed by value just like structs in C. Here's how to get one by reference:

```

void func(std::string& str);

```

---

### Post by bluedalmatian on 2008-11-18
I know how to pass by reference but the function im calling expects it by value, which im sure is what ive typed - yet the compiler is complaining im doing it by reference

---

### Post by Tony Flury on 2008-11-18
more like a c++ programmer who thought he understood the stl but clearly doesn't :-) Thanks for the correction.

i must admit i now avoid C++ where ever possible - I like my sanity intact.

---

### Post by hod139 on 2008-11-18
Why would you ever want to pass a string by value?  In any case, this code compiles fine for me
```

namespace myNamespace
{
   std::string myString;
}


void someFunction(std::string s)
{
  std::cout << s << "\n\n";
}


int main(void){
   myNamespace::myString = "XYZ";
   
   someFunction(myNamespace::myString);
   
   return 0;
}

```

But back to my first question, why would you ever want to pass the string by value?  If you do not want the function to be able to modify the string, pass it by const reference
```

void someFunction(const std::string &s);

```

---

### Post by samjh on 2008-11-18
> **bluedalmatian said:**
> ive got a file called main.cpp

which declares some global string variables in a namesapce e.g

myNamesapce
{
    std::string myString;


}

main()
{
   myString = "XYZ";
   ....
   someFunction(myNamespace::myString);
}

If we imagine someFunction has been declared so:

someFunction(std::string s)
{
....
}

then my use of it would be correct?  Yet when I compile it complains that I'm passing by reference and that the function
someFunction(std::string&) doesnt exist.

I can only assume this is sometihng to do with the namespaces because I cant see any other reason for this to fail?

Any ideas please?

Thanks

Well, simple stuff first...

You need to define the function someFunction(std::string s) prior to the code that calls it: ie. prior to main().   Alternatively, you can place the function prototype prior to main() and define the function after main().

Now for the passing-by-reference vs passing-by-value...

You caught yourself out when you said:
*Yet when I compile it complains that I'm passing by reference and that the function **someFunction(std::string&)** doesnt exist*.

So what is it?  someFunction(std::string& s), or someFunction(std::string s)???  Which one is the declaration you REALLY used? ;)

C++ will pass the string by value if someFunction(std::string s), and pass by reference if someFunction(std::string& s).

---

### Post by scourge on 2008-11-18
> **hod139 said:**
> Why would you ever want to pass a string by value?

When one needs a local non-const copy of the string. Example:
```

void func(std::string str) {
    // modify str
}

```

Of course you can also do it with a const reference, but with more code
```

void func(const std::string& str) {
    std::string local_str = str;
    // modify local_str
}

```

---

