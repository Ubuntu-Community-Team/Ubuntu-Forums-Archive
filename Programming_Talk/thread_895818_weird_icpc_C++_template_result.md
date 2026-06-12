---
title: "weird icpc C++ template result"
date: 2008-08-20
forum: Programming Talk
---

### Post by arkangel on 2008-08-20
```

#include  <iostream>        

typedef int (*functionpointer)();

template<typename T>
int print(){

  T a=(T) 3.14159;
  std::cout << "print() called, a=" << a << "\n";
  return 0;
}




template<functionpointer f>
int runfunction(){

   return f();

}


template<typename T> 
void program(const T &pi)
{

  std::cout << "program called: pi=" << pi <<"\n";

  // OK with gcc + icc
  //runfunction< &print<double> >();  

   // only OK for gcc
   runfunction< &print<T> >();  

}


main(){
  program<double>(3.14159);

}


```

I compiled this with gcc and  works well , with icpc (INTEL C++)  i got ": error: no instance of function template "runfunction" matches the argument list"   which is weird .  In my opinion  there is no difference  calling  &print<T>  or &print<double>  the compiler should understand both,  in any case   how can I rewrite  to get what i want in a simpler way[PHP][/PHP]

---

### Post by dribeas on 2008-08-20
> **arkangel said:**
> ```
template<functionpointer f>
int runfunction(){

   return f();

}
```

Why are you making this a template? You could just as well get rid of the template and use:
```
int runfunction( functionpointer f ) {
   return f();
}
```

I have tried it with [Comeau C++ compiler]("http://www.comeaucomputing.com/tryitout") with the same error (and Comeau is as of now the most standard compiler available), so it must be an error :)

I assume that the error is generated during first pass of the template validation, when T is not yet substituted by the instantiation type. At that point print<T>, T being still generic, is undefined for the compiler. Note that even if at this point is might be clear to you that print<double> will have int (*)() signature it might not always be like that as you could specialize the template later on with a different signature:

```
template<> double print<double>() { ... }
```

Now, if instead of print<T> you explicit print<double> then the compiler must instantiate the template there with whatever definition is known, and that has int (*)() signature as is expected.

   David

P.S. What were you trying to achieve? The code seems as a simplification of some other more complex code. Else you can get rid of runfunction alltogether.

P.S.2 Standard C++ requires return types in all functions, valid main signatures are: int main() and int main( int argc, char** argv ), but you cannot omit the int.

**EDIT:**
I have just tried substituting the function template with a class template with success:
```

template <functionpointer f>
struct functionrunner 
{
   int operator()() { return f(); }
};
template<typename T> 
void program(const T &pi)
{
  std::cout << "program called: pi=" << pi <<"\n";
  functionrunner< &print<T> > f;
  f();
}
int main(){
  program<double>(3.14159);
}
```

Which might be a solution for you, but leaves me wondering why or how... I am not sure that the above reasoning holds.

---

