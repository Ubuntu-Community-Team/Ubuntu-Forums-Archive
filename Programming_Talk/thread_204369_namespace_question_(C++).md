---
title: "namespace question (C++)"
date: 2006-06-26
forum: Programming Talk
---

### Post by TrendyDark on 2006-06-26
Teachers in the past have always taught me to ask any question no matter how trivial it is, so sorry if this is stupid.

I've read in a book I picked up that you can avoid writing something like:

```
std::cout << "Hi\n";
std::cout << "Hi\n";
std::cout << "Hi\n";
std::cout << "Hi\n";
std::cout << "Hi\n";
```

See *std* in front of *cout*. . I've read I can just use:

```
using std::cout;
```

or

```
usind namespace std;
```

but would it be better form just to use the namespace thing (std::) in front of *cout* every time I write it?

---

### Post by bieber on 2006-06-26
Depends.  If you're using mostly standard library functions, I'd say go ahead.  If you're using another library and you have a ton of function calls from it, you may want to set the default namespace to that.  There may be a way to change namespaces for different sections of code, but if there is, I don't know it...

---

### Post by LordHunter317 on 2006-06-26
The directive and statment are provided for a reason.  Use them, but use them correctly.  Understand the differences between the two as well.

---

### Post by TrendyDark on 2006-06-26
Thanks for the responses, I'm just starting out with this and don't want to get into a bad habbit while I'm still in programming baby-shoes.

---

### Post by thumper on 2006-06-27
It is generally considered bad form to use
```
using namespace std;
```

The reasoning behind it is that it pulls in everything in the std namespace into the local namespace.  And while most of the time it doesn't really matter, there are times when it does.

It is often better to use
```
using std::cout;
```
either at the top of the file, or at the start of the functions using it.  It gives clarity to the reader of the code.  

Personally, most of the time, I prefix with the namespace.  

Also, there is no need to call cout for each line:
```

std::cout << "Hi\n"
          << "Hi\n"
          << "Hi\n"
          << "Hi\n"
          << "Hi\n"
          << "Hi\n";
```
:)

---

### Post by Yohumbus on 2006-06-27
I would say that in header files you should write the namespace in front but in the implementation (the .c or .cpp files) then it would be fine putting a using statement after the headers. Of course this should still not conflict with what they are designed for.

---

### Post by thumper on 2006-06-27
Ah yes, I also forgot to cover the blindingly obvious.

As **Yohumbus** suggested, **NEVER** put using declarations or statements in header files.

---

### Post by ynef on 2006-06-27
You can also use a namespace in a certain function only, if you write the "using namespace std;" line there. That means that the rest of the code is protected from your use of the namespace, but you don't have to type a lot of tedious extra stuff. Then again, don't listen to me, since I'm a Java programmer (mostly).

---

### Post by TrendyDark on 2006-06-27
Thanks, I wish I knew more about C++, but I'm just learning how to make a message appear on the screen. Pretty lame at the moment, but I guess everyone starts somewhere.

So, I should use "using namespace std" if I'm only using the std namespace in that function, but not if I'll be using different namespaces in the function?

---

### Post by thumper on 2006-06-27
I'd say as a general rule don't use "using namespace std".

do this instead
```

void somefunc( /* params */ )
{
   using std::cout;
   cout << "foo bar \n";
   // ...
}

```
if you are going to use it more than once, and prefix it otherwise.

---

