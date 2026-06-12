---
title: "C++ conditional operator confusion..."
date: 2009-02-21
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-21
Could someone please give a logical use for a conditional operator, or explain in a little more detail how it might be used cause this example has me very confused and I am not going to be able to move on till I understand it... Below is the example they give but again it just seems useless.

```
// conditional operator

#include <iostream>
using namespace std;

int main ()
{
  int a,b,c;

  a=2;
  b=7;
  c = (a>b) ? a : b;

  cout << c;

  return 0;
}

``` 

if I wanted 7 couldn't I just put: b = 7; cout << b;? I am sure there is a deeper meaning for the above example but I just can't see it. Maybe I am just not thinking like a programer yet...

---

### Post by hanniph on 2009-02-21
```
  c = (a>b) ? a : b;
```

it means that if a > b then c = a, otherwise c = b. The purpose of this example is to find greater number and assign it to c

---

### Post by geirha on 2009-02-21
It's just a shorter way of doing:
```
if ( a > b ) {
    c = a;
} else {
    c = b;
}

```

EDIT: Reading your question more carefully; it would make more sense to use something like this as an example:
```

int main ()
{
  int a,b,c;

  cout << "Input two integers: ";
  cin >> a >> b;

  c = (a>b) ? a : b;

  cout << "The largest of the two integers is: " << c << endl;

  return 0;
}

```

---

### Post by Leo Dragonheart on 2009-02-21
YES now I am enlightened....;) I understand it now and it makes perfect sense. Thank you both...

---

### Post by monkeyking on 2009-02-21
This is a classic way to confuse your boss/customer.
Just use these trinary operators, or even embed other ones in the first one.

This and some tripple pointers while using vi.
Then you are bound for a raise.

---

### Post by dwhitney67 on 2009-02-21
It's known as the ternary (or tertiary) operation.  Read [here]("http://en.wikipedia.org/wiki/Ternary_operation") for info.

---

### Post by Sockerdrickan on 2009-02-22
```

//Butterfly flies to player
static const float move_speed(0.4f);
x+=x<Player::x?move_speed:-move_speed;
y+=y<Player::y?move_speed:-move_speed;

```

---

### Post by abhilashm86 on 2009-02-22
mostly conditional operators are used in order to reduce program code,
like you can always use if else statements but there is fun in single statement like,

max=(a>big)?a:b;

---

### Post by Leo Dragonheart on 2009-02-22
> **abhilashm86 said:**
> mostly conditional operators are used in order to reduce program code,
like you can always use if else statements but there is fun in single statement like,

max=(a>big)?a:b;

I will say that is the closest I have come to a logical answer since this post thx... I can understand doing it for fun, or for the heck of it, or to confuse noobs like myself, I just don't understand the using it in an example part. It is fun, I can accept that thx again...:D

---

### Post by Npl on 2009-02-22
its also easier for a compiler to deduce possible optimizations, as the tertiary operator maps very well to conditional-move instructions.

---

### Post by Leo Dragonheart on 2009-02-22
> **Npl said:**
> its also easier for a compiler to deduce possible optimizations, as the tertiary operator maps very well to conditional-move instructions.

Thx. I was just wondering. I don't know anything about complex maths or none of that stuff. I just thought it kind of peculiar. I read a little from the link given earlier about tertiary operators but couldn't make heads or tails out of it...So I will accept that it is for compiler optimisations and leave it at that... thank you to everyone who posted a reply...

---

### Post by Reiger on 2009-02-22
Incidentally, this ternary operator is semantically equivalent to the Haskell (different language):
```

if (expr) 
  then return-expr
  else return-other-expr

```

The major benefit for a compiler, I guess, is that the number of branches (then/else) is limited to exactly 2 in all cases. This means that the compiler merely need to implement 1 conditional break (the else case) on top, and can 'line in' all code. Hence, it is a trivial statement to compile, and given the context (this fixed operation structure) also optimal.

The same cannot be said for if() statements which may have 1, 2 or depending on the language (elseif() clauses) more branches -- which requires more 'context evaluation' in order for the compiler to know how it should handle the code.

For the programmer who isn't too concerned about how easy the life of his compiler is; the benefit is mainly that this ternary operator offers a concise way to express Yes/No scenario's.

---

### Post by Leo Dragonheart on 2009-02-22
> **Reiger said:**
> Incidentally, this ternary operator is semantically equivalent to the Haskell (different language):
```

if (expr) 
  then return-expr
  else return-other-expr

```

The major benefit for a compiler, I guess, is that the number of branches (then/else) is limited to exactly 2 in all cases. This means that the compiler merely need to implement 1 conditional break (the else case) on top, and can 'line in' all code. Hence, it is a trivial statement to compile, and given the context (this fixed operation structure) also optimal.

The same cannot be said for if() statements which may have 1, 2 or depending on the language (elseif() clauses) more branches -- which requires more 'context evaluation' in order for the compiler to know how it should handle the code.

For the programmer who isn't too concerned about how easy the life of his compiler is; the benefit is mainly that this ternary operator offers a concise way to express Yes/No scenario's.

Thank you, I am understanding it more everyday now... I think I have the basic understanding of it now. I also fail to realise  that other things are involved other than just myself. The "compiler" the "computer" but I think I have the basic understanding now. Thank you for your explination. That did make my understanding even more clear...

---

### Post by Krupski on 2009-02-22
> **Leo Dragonheart said:**
> Could someone please give a logical use for a conditional operator, or explain in a little more detail how it might be used cause this example has me very confused and I am not going to be able to move on till I understand it... Below is the example they give but again it just seems useless.

```
// conditional operator

#include <iostream>
using namespace std;

int main ()
{
  int a,b,c;

  a=2;
  b=7;
  c = (a>b) ? a : b;

  cout << c;

  return 0;
}

``` 

if I wanted 7 couldn't I just put: b = 7; cout << b;? I am sure there is a deeper meaning for the above example but I just can't see it. Maybe I am just not thinking like a programer yet...

Think of it like this:

(after a test) ? (do this if it's true) : (otherwise do this)

Now, an example: Let's say you are given 2 numbers and you must return them in ascending order. That is, if I give you 5 and 3, you must give back 3 and 5. If I give you 3 and 5, just give back 3 and 5 since it's already right.

Now the (pseudo) code example:

(first number < second number) ? (return as-is) : (swap them, then return them)

You could do the same thing this way:

```

if(first < second) {
    // do nothing
} else {
    swap(first, second);
}

```

But it's more complicated.

And now here's a "real one" from a piece of code:

```

    printf("D1 is %s than D2\n", (d1 < d2) ? ("smaller") : ("larger"));

```

Make sense?

-- Roger

---

### Post by Leo Dragonheart on 2009-02-22
> **Krupski said:**
> Think of it like this:

(after a test) ? (do this if it's true) : (otherwise do this)

Now, an example: Let's say you are given 2 numbers and you must return them in ascending order. That is, if I give you 5 and 3, you must give back 3 and 5. If I give you 3 and 5, just give back 3 and 5 since it's already right.

Now the (pseudo) code example:

(first number < second number) ? (return as-is) : (swap them, then return them)

You could do the same thing this way:

```

if(first < second) {
    // do nothing
} else {
    swap(first, second);
}

```

But it's more complicated.

And now here's a "real one" from a piece of code:

```

    printf("D1 is %s than D2\n", (d1 < d2) ? ("smaller") : ("larger"));

```

Make sense?

-- Roger

Yes now I understand it thanx. I just could not think of a logical reason for such an equation. I understand the examples you gave, I just could not see it in the one the lesson gave but now I understand even their example. IMHO I think it was just the wrong example for teaching a beginer without a little more explanation. I tend to get hung up on stuff like that allot. I have a very analytical mind. I have to figure it out or die trying.lol.

---

### Post by CptPicard on 2009-02-22
The whole point of the ternary operator is that it's easier to use inside an expression to choose between values to plug into that place in the expression, based on the conditional. Nice to guard against NULL value problems for example.

If you used an if, you'd have to set a variable or define a function.

As for the benefits for compiler... the ternary operator compiles at least in my simple tests identically to an if-clause function implementation of the same, and I see no reason why it would not be just syntactic sugar for

```

type ternary(int conditional, type a, type b) {
  if (conditional)
    return a;
  else
    return b;
}

```


The only real optimization benefit I can think of is the fact that the compiler knows that the ternary operator branches are just return values from that kind of a function, and that the nesting "tree" is always complete (everything has two children). But as you can stick side-effect producing function calls into both (so you are not side-effect-less), you're still pretty close to if nesting that alters variables outside the ifs, and the if nesting structure is perfectly analyzable at compile time too, of course.

---

### Post by Krupski on 2009-02-22
> **Leo Dragonheart said:**
> Yes now I understand it thanx. I just could not think of a logical reason for such an equation. I understand the examples you gave, I just could not see it in the one the lesson gave but now I understand even their example. IMHO I think it was just the wrong example for teaching a beginer without a little more explanation. I tend to get hung up on stuff like that allot. I have a very analytical mind. I have to figure it out or die trying.lol.

If you look at the example I posted where the string "smaller" or "larger" is output depending on D1 and D2, if I couldn't use the conditional operator, I would have had to to an if() test, then copy one string or the other to a buffer, then use the buffer in the printf() statement.

It would have been much more complicated.

---

### Post by Arylon on 2009-02-23
> **CptPicard said:**
> As for the benefits for compiler... the ternary operator compiles at least in my simple tests identically to an if-clause function implementation of the same, and I see no reason why it would not be just syntactic sugar for

```

type ternary(int conditional, type a, type b) {
  if (conditional)
    return a;
  else
    return b;
}

```


Two things come to mind. One is that the ternary operator was present in C, so while the above could be written as a template function in C++, for C you would need to create many copies of that which differed only in their types (and names).

Also this is valid
```
printf("%i\n", test? 42: SomeFn() );
```
choosing between a simple value, and a function which returns a value.

---

### Post by Wybiral on 2009-02-23
> **Krupski said:**
> ```

    printf("D1 is %s than D2\n", (d1 < d2) ? ("smaller") : ("larger"));

```

Make sense?

It only makes sense if you view equal/larger as the same thing :p

Ternary operator is fun for something simple like this, but I tend to cringe when I see it nested...

((d1 < d2) ? "smaller" : ((d1 > d2) ? "larger" : "equal"))

---

### Post by CptPicard on 2009-02-23
> **Arylon said:**
> so while the above could be written as a template function in C++, for C you would need to create many copies of that which differed only in their types (and names).

That really doesn't make a difference in the compilation efficiency though.

> 
Also this is valid
```
printf("%i\n", test? 42: SomeFn() );
```
choosing between a simple value, and a function which returns a value.

And that too is going to look exactly the same compiled as the explicit function version, especially if you allow for the assumption that such a small function is going to be inline anywy :)

---

