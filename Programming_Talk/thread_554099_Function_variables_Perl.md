---
title: "Function variables Perl"
date: 2007-09-18
forum: Programming Talk
---

### Post by Dylock on 2007-09-18
Howdy, anyone know of a way to retain a variable inside a function without declaring the variable outside the function

ex


&foo;
&foo;

sub foo
{
   $x++;
}
assume that $x has an initial value
I want the second function call to have the value of $x from the previous function call

Suggestions?

---

### Post by mssever on 2007-09-19
I'm not a Perl programmer, so I might be off a bit, but why not just return x in your function?

(You might like Ruby's blocks, which don't have this problem.)

---

### Post by bunker on 2007-09-19
You're looking for a static type, but perl doesn't have it.  Here is a way of getting the same effect:

```

BEGIN {
  my $x = 1;
  sub function {
    return $x++;
  }
}

```

Who said perl doesn't make sense!

---

### Post by Dylock on 2007-09-19
yea i still haven't understood blocks yet in perl, do you count the BEGIN block as a function, or how is it invoked? Automatically when you call the function ?

---

### Post by bunker on 2007-09-19
The blocks just denote a scope.  The 'my' keyword says that a variable is part of that scope.  By nesting the function in that way, you get access to the stuff in the parent scope.  A lot of languages have ways of denoting scope other than functions and control constructs, but they're not used very often - and I don't know of any that you use like this other than perl ;).

Here's an example of using scopes with C - it might make things clearer for you:

```

#include <stdio.h>

int main() {
  int a = 1;
  { /* start  a scope */
    int b = 2;
    printf("A is: %d\n", a); // works - a is declared in the parent scope
    printf("B is: %d\n", b); // works
  } /* .. and then end it */
  // printf("A is: %d\n", b); // Won't compile; complains b is not declared
  return 0;
}

```

---

### Post by Dylock on 2007-09-19
oh alright i get it now, so by declaring a function inside a block it can access any variables inside the block.

thats pretty cool, exactly what i want to happen.

thanks

---

### Post by skeeterbug on 2007-09-19
> **bunker said:**
> You're looking for a static type, but perl doesn't have it.  Here is a way of getting the same effect:

```

BEGIN {
  my $x = 1;
  sub function {
    return $x++;
  }
}

```

Who said perl doesn't make sense!


Actually it sort of does have a static type.

[http://perldoc.perl.org/perltoot.html#Class-Data](http://perldoc.perl.org/perltoot.html#Class-Data)

> 
But more often than not, you just want to make your class data a file-scoped lexical. To do so, simply put this at the top of the file:

    my $Census = 0;

Even though the scope of a my() normally expires when the block in which it was declared is done (in this case the whole file being required or used), Perl's deep binding of lexical variables guarantees that the variable will not be deallocated, remaining accessible to functions declared within that scope. This doesn't work with global variables given temporary values via local(), though.

---

