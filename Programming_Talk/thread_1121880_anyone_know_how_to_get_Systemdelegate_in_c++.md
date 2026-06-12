---
title: "anyone know how to get System::delegate in c++"
date: 2009-04-10
forum: Programming Talk
---

### Post by beattyml1 on 2009-04-10
So I'm doing my first ever real world programming project and I've run into a bit of a problem: I can't seem to find System::delegate, any idea what #include I would need to get at, also is this going to work differently between windows and linux

(right now I am using windows/VS2008 to try to figure out how to find/use it, but the final project will be done in linux with which ever program I decide works best, which as of right now looks to be geany with which I am comfortable or eclipse which I hear wonderful things about)

---

### Post by beattyml1 on 2009-04-10
actually I should mention that the main goal is simply to return a pointer to a function and if there is an easier (or more universal) way to do this than delegates that would be good/better

---

### Post by johnl on 2009-04-10
System::delegate is party of "Managed" C++, or C++.NET (or whatever they're calling it these days).   "Managed" C++ refers to C++ compiled as part of the .NET CLR.  

Generally it's used to build quick .NET wrappers to existing C++ code.  It's almost never used to build new applications.  

I don't know what, if any, support the Mono project has for C++.NET, but it's pretty likely that you will not be able to easily compile your code under Linux.

---

### Post by johnl on 2009-04-10
> **beattyml1 said:**
> actually I should mention that the main goal is simply to return a pointer to a function and if there is an easier (or more universal) way to do this than delegates that would be good/better

Here's a quick example.


```

/* we have two functions, add and sub */

int add(int x, int y) 
{
   return x + y;
}

int sub(int x, int y) 
{
   return x - y;
}

/* this declares a type 'math_func_ptr' which represents 
 * a pointer to a function that takes the arguments (int, int)
 * and returns an int.
 */
typedef int(*math_func_ptr)(int,int);

int main() {
  /* our function pointer points to nothing */
  math_func_ptr p = NULL;
  int result;

  /* but we can change that */
  p = add;
  /* and call it just like a regular function */
  result = p(4, 5); /* 4 + 5 */
  p = sub;
  result = p(4, 5); /* 4 - 5 */

}

```

Hope this helps.

---

### Post by directhex on 2009-04-10
> **johnl said:**
> System::delegate is party of "Managed" C++, or C++.NET (or whatever they're calling it these days).   "Managed" C++ refers to C++ compiled as part of the .NET CLR.  

Generally it's used to build quick .NET wrappers to existing C++ code.  It's almost never used to build new applications.  

I don't know what, if any, support the Mono project has for C++.NET, but it's pretty likely that you will not be able to easily compile your code under Linux.

Most Managed C++ uses "mixed-mode assemblies" (a mix of cross-platform .NET code, and system-specific C++ code) and Mono doesn't support it.

System.Delegate is fully functional in C# though

---

### Post by beattyml1 on 2009-04-10
thanks this was very helpful

---

