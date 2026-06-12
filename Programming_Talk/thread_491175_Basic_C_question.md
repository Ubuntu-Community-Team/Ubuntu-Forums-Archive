---
title: "Basic C question"
date: 2007-07-03
forum: Programming Talk
---

### Post by LaRoza on 2007-07-03
I have already studied C++ among other languages and am now learn C, and I have a few questions.

*Does main() return a value?
*What namespace is "printf()" in?
*Do you know of any good references to C for C++ programmers?

Thanks.

---

### Post by runningwithscissors on 2007-07-03
> **LaRoza said:**
> *Does main() return a value?It should. You can declare main as returning void but it's good practice to return EXIT_SUCCESS or EXIT_FAILURE depending upon what went on during the execution of your program.
> **LaRoza said:**
> *What namespace is "printf()" in?There are no namespaces. So watch out for collisions.
> **LaRoza said:**
> *Do you know of any good references to C for C++ programmers?The GNU C library documentation or associated manpages are easily available and quite useful. Most C libraries in wide use on Linux are well documented.

---

### Post by LaRoza on 2007-07-03
Thanks, I am reading a tutorial on C now, [http://www.iu.hio.no/~mark/CTutorial/CTutorial.html#Operating%20systems](http://www.iu.hio.no/~mark/CTutorial/CTutorial.html#Operating%20systems), and am mostly scanning for non-C++ things to watch out for. 

(Function prototypes are missing, learning C++ first has made me try to declare functions in every language before using them, even in Python)

---

### Post by gborzi on 2007-07-03
I'm not an expert in C, I have used it sometimes, so these are just my 2 cents:
1) main returns an int, it is generally declared as > int main(...) ...
note that main can have argc and argv as arguments;
2) there are no namespaces in C;
3) I don't know of any reference for C++ programmers that wants to learn C. Perhaps a good C introduction is enough.

Regards.

---

### Post by ankursethi on 2007-07-03
"The C Programming Language" by Ritchie and Kerninghan is the book you are looking for. It's concise, to the point and contains everything you need to know about C. As you already know C++, it'll take you maximum 2-3 days to read and understand that book.

---

### Post by LaRoza on 2007-07-03
> **ankursethi said:**
> "The C Programming Language" by Ritchie and Kerninghan is the book you are looking for. It's concise, to the point and contains everything you need to know about C. As you already know C++, it'll take you maximum 2-3 days to read and understand that book.

Thanks, right now I have a tutorial and a downloaded book.

To the gborz and runningwithscissors, thanks for the answers. To gborz, the names of the parameters is insignificant, the types, int and char* are what are important, unless it differs from C++.

---

### Post by runningwithscissors on 2007-07-03
> **LaRoza said:**
> Function prototypes are missing...
Nope. They're available.

---

### Post by LaRoza on 2007-07-03
> **runningwithscissors said:**
> Nope. They're available.

The tutorial didn't have them, are they new to C? (relatively, I mean)

---

### Post by runningwithscissors on 2007-07-03
> **LaRoza said:**
> The tutorial didn't have them, are they new to C? (relatively, I mean)They were introduced in C89.

---

### Post by LaRoza on 2007-07-03
> **runningwithscissors said:**
> They were introduced in C89.

Thanks. C y'all later!

---

