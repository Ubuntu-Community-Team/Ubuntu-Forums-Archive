---
title: "C Dynamic Variable Creation"
date: 2009-12-30
forum: Programming Talk
---

### Post by lewisforlife on 2009-12-30
I would like to dynamically create variables on the fly in a C program.  For instance, if I have a loop that loops 3 times, I want it to create:

[LIST]
[*]int var1 = somenumber
[*]int var2 = somenumber
[*]int var3 = somenumber
[/LIST]

Is this possible in C, and if so, how would I go about doing this.

---

### Post by dwhitney67 on 2009-12-30
No, dynamic variable creation is not possible in C.

Can you please elaborate on what you require?  You can allocate an array, of whatever size you require, during runtime, and assign values to the array.

Something like:
```

int* array = malloc(numValues * sizeof(int));

if (array)
{
   for (int i = 0; i < numValues; ++i)
   {
      array[i] = someNumber;
   }
}
else
{
   /* failure to allocate */
}

```

---

### Post by CptPicard on 2009-12-30
Has to be done by usage of an appropriate data structure... array, a hash, tree... keyed property list...

---

### Post by nvteighen on 2009-12-30
> **lewisforlife said:**
> I would like to dynamically create variables on the fly in a C program.  For instance, if I have a loop that loops 3 times, I want it to create:

[LIST]
[*]int var1 = somenumber
[*]int var2 = somenumber
[*]int var3 = somenumber
[/LIST]

Is this possible in C, and if so, how would I go about doing this.

You can't. The only two languages I am aware of being able to do this are Python and Lisp. Maybe Perl and Ruby can do it too, but I don't remember.

---

### Post by Can+~ on 2009-12-30
The closest thing to assigning names and values in runtime is with a Hash. Although, I assume that the OP is a beginner, so stick to arrays (which, in theory, are a particular type of hash where f(i) = i*size).

---

### Post by CptPicard on 2009-12-30
> **Can+~ said:**
> Although, I assume that the OP is a beginner, so stick to arrays (which, in theory, are a particular type of hash where f(i) = i*size).

Which are all just mappings (functions) from keys to values, and particularly in this case in Lisp terms we're looking at the *environment* keys-to-values mapping, which the expression is evaluated in terms of... :)

*Sigh*... it's all Lisp and so few know it ;)

---

### Post by MaxIBoy on 2009-12-30
You can't create a variable on the fly. You can create an array of variables of any length (and use realloc to resize the array dynamically,) but then you have to use numbers instead of names.

You can also use a hash table or associative array to associate names with values, but this has a performance penalty and it's kind of a pain besides. (You can't treat the values as variables, but as the output of a function.)


Try an interpreted language. Lua, shell, and Python (in order from most to least) have the ability to do this kind of thing effortlessly. Apparently Lisp is the champion for this kind of stuff, but I've never used it. Can't say I've really tried any interpreted language besides those three, actually.

---

### Post by nvteighen on 2009-12-31
An example on how to do this in Common Lisp :)

```

(defmacro dyn (basename &rest maps)
  `(progn
     ,@(loop for pair in maps
          collect
            `(defvar ,(intern (string-upcase (format nil 
                                                     "~a~a" 
                                                     basename
                                                     (car pair))))
               ,(cadr pair)))))

; SLIME 2009-07-02
CL-USER> (dyn "abc" (7 8) (77 'u))
ABC77
CL-USER> abc7
8
CL-USER> abc77
U

```

EDIT: Improved it a bit.

---

### Post by worseisworser on 2009-12-31
> **nvteighen said:**
> An example on how to do this in Common Lisp :)

```

(defmacro dyn (basename &rest maps)
  `(progn
     ,@(loop for pair in maps
          collect
            `(defvar ,(intern (string-upcase (format nil 
                                                     "~a~a" 
                                                     basename
                                                     (car pair))))
               ,(cadr pair)))))

; SLIME 2009-07-02
CL-USER> (dyn "abc" (7 8) (77 'u))
ABC77
CL-USER> abc7
8
CL-USER> abc77
U

```

EDIT: Improved it a bit.


Or one could use PROGV which will generate *dynamic* bindings 100% at run-time:

```

CL-USER> (flet ((test ()
                  (format t "test A: ~A~%" a)
                  (format t "test B: ~A~%" b)))
           (progv (list 'a 'b) (list 1 2)
             (test)
             (format t "A: ~A~%" a)
             (format t "B: ~A~%" b)))
test A: 1
test B: 2
A: 1
B: 2
NIL

```

Quite cool. :) Note that the two calls to LIST really are evaluated at *run-time*, which means that they could be passed in as arguments or variables.

Just to show more clearly that the TEST function and the PROGV things really are 100% separate:

```

CL-USER> (defun test () 
           (format t "test A: ~A~%" a)
           (format t "test B: ~A~%" b))
TEST

CL-USER> (progv (list 'a 'b) (list 1 2)
           (test)
           (format t "A: ~A~%" a)
           (format t "B: ~A~%" b))
test A: 1
test B: 2
A: 1
B: 2
NIL
CL-USER> 

```


Wrt. the OP I would use STD:MAP or STD:HASH (C++0x; GCC supports this via the -std=gnu++0x option) or using C I'd go for the GLib library: [http://library.gnome.org/devel/glib/stable/glib-Hash-Tables.html](http://library.gnome.org/devel/glib/stable/glib-Hash-Tables.html) .. which pretty much is available "everywhere".

---

### Post by MaxIBoy on 2009-12-31
Here's how you create new globals in Lua:
```
max@server:~$ lua
Lua 5.1.2  Copyright (C) 1994-2007 Lua.org, PUC-Rio
> _G["foo"] = "bar"
> print (foo)
bar
> varname = "spam"
> _G[varname] = "eggs"
> print (varname)
spam
> print (spam)
eggs
> print (_G["varname"])
spam
> print(_G[_G["varname"]])
eggs
>

```_G is a special table that points to the global scope. I suppose the language is sort of "cheating" by doing it this way, but it works well.

You can also use the dot "." if you don't want to use strings as names, but this has its limits:
```
> print(_G.varname)
spam
> print(_G._G.varname) -- _G contains itself because _G is a global, so this doesn't quite work.
spam
> print(_G.(_G.varname)) -- This doesn't work either
stdin:1: '<name>' expected near '('
> print (_G[_G.varname]) --this does work
eggs
>

```Also, heck, why not? Let me show you what some of this stuff is good for:
```
> _G["print"]("hello") -- functions are part of _G as well
hello
> _G["PRINT"]=function(str) print ( string.upper(str) ) end -- create a wrapper around "print"
> PRINT ("hello")
HELLO
> _G["_print"]=_G["print"]
> _G["print"] = function(str) _print (string.upper (str)) end -- completely replace "print"
> print "hi"
HI
>

```

---

### Post by nvteighen on 2009-12-31
> **MaxIBoy said:**
> _G is a special table that points to the global scope. I suppose the language is sort of "cheating" by doing it this way, but it works well.


It's almost like what my Common Lisp is actually doing: The key part in my code is (intern ...), which takes a string and includes a symbol using that string into the current "package" (= sort of a namespace... well, you can choose the package...)... in other words (and in other language :D), the same as you're doing in Lua. The whole rest is part of the macro to make this more usable.

---

### Post by MaxIBoy on 2009-12-31
You know, this kinda explains the lambda in your avatar...


Here's the Python:
```
>>> globals()["spam"] = "eggs"
>>> print (spam) #this works but...
eggs
>>> def foo (bar):
...     locals()["baz"] = locals()["bar"]
...     print ( locals()["baz"] )
...     print ( baz ) #this doesn't work
...
>>> foo ("hi")
hi
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 4, in foo
NameError: global name 'baz' is not defined
>>>

```

---

### Post by Hellkeepa on 2009-12-31
HELLo!

Thought this was a question about C, but what the heck... Here's how it's done in PHP:
[php]$Name = "test";
$$Name = "Value";
echo $test;
[/php]
Or using array values as names:
[php]$Array = array ('test');
${$Array[0]} = "Value";
echo $test;
[/php]
Or use the "$_GLOBALS" array, which doesn't work inside of functions (naturally enough):
[php]$_GLOBALS['test'] = "Value";
echo $test;[/php]
That said, it is my experience that if you encounter a situation where you think you need variable variables, then it is extremely likely that you've done something wrong in the design of the system.

Happy codin'!

---

### Post by nvteighen on 2010-01-01
> **MaxIBoy said:**
> You know, this kinda explains the lambda in your avatar...


Here's the Python:
```
>>> globals()["spam"] = "eggs"
>>> print (spam) #this works but...
eggs
>>> def foo (bar):
...     locals()["baz"] = locals()["bar"]
...     print ( locals()["baz"] )
...     print ( baz ) #this doesn't work
...
>>> foo ("hi")
hi
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 4, in foo
NameError: global name 'baz' is not defined
>>>

```

Easier :):
```

>>> base = "abc"
>>> for x in xrange(10):
...     exec "%s%d = %d" % (base, x, x)
... 
>>> abc0
0
>>> abc1
1
>>> abc2
2
>>> abc8
8
>>> abc9
9
>>> 

```

---

### Post by 10nitro on 2010-01-02
In C you must use pointers for dynamic allocation.

Something like this:
```

struct linked_list {
    int val;
    struct linked_list *next;
};

int main()
{
    struct linked_list *next=NULL;
    struct linked_list *current=NULL;
    
    /* the loop */
    while ( test() ) {
        current=malloc(sizeof(struct linked_list));
        current->next=next;
        next=current;

        current->val=3;/* or whatever */
    }

    return 0;
}

```

---

### Post by Shippou on 2010-01-02
> **10nitro said:**
> In C you must use pointers for dynamic allocation.

Something like this:
```

struct linked_list {
    int val;
    struct linked_list *next;
};

int main()
{
    struct linked_list *next=NULL;
    struct linked_list *current=NULL;
    
    /* the loop */
    while ( test() ) {
        current=malloc(sizeof(struct linked_list));
        current->next=next;
        next=current;

        current->val=3;/* or whatever */
    }

    return 0;
}

```

Actually, this is what I will suggest. :)

Just put all the things you want there inside the structure.

Or alternatively, you can do something like this:

```

typedef struct linked_list {
    int val;
    struct linked_list *next;
}dyn_val;

int main()
{
    dyn_val *next=NULL;
    dyn_val *current=NULL;
    
    /* the loop */
    while ( test() ) {
        current=malloc(sizeof(dyn_val));
        current->next=next;
        next=current;

        current->val=3;/* or whatever */
    }

    return 0;
}

```

Does the same thing, but is neater with the typedefs (IMHO).

The Java way is this:
```

public class Something {
    public static void main (String[] args) {
          LinkedList list = new LinkedList();
          list.add(/*things...*/);
          /*Keep doing the above n times. It is up to you. Insert in a loop or something.*/
    }
} 

```

Of course this is cheating, because I am using the LinkedList class (in jav.util.*).

I think dynamic variable creation can also be done in Assembly, but that is beyond my domain.

NOTE: I like the LISP code (although I cannot understand it at the moment).

Could someone try this using APL? I'm interested. :)

---

### Post by Reiger on 2010-01-02
> **nvteighen said:**
> You can't. The only two languages I am aware of being able to do this are Python and Lisp. Maybe Perl and Ruby can do it too, but I don't remember.

Anything with eval() type functions can do this. Actually, anything with proper support for reflection can do that too; e.g. in Java it is possible to define for instance Enums at run time.

Similarly if dynamically allocated arrays are all you want -in Java at least- Object... type will work.

---

### Post by nvteighen on 2010-01-02
> **Shippou said:**
> 
NOTE: I like the LISP code (although I cannot understand it at the moment).


The Common Lisp code [I posted]("http://ubuntuforums.org/showpost.php?p=8587071&postcount=8") does this:
1. Gets a base string and then a list of pairs each of those has the suffix as first element and the initial value for the created variable. The base string is stored in the 'basename' variable and the list of pairs in 'maps'.
2. Loops all stuff in 'maps' and creates a list of 'defvar' calls generating the symbol for that variable by concatenating (via format, which is like C's sprintf in this case) the basename string with the "suffix" (which is conveniently converted into its string representation by format) to form that new variable name. Then, it closes the defvar by grabbing the value we wanted to bind the variable to.
3. The loop returns a list of all generated defvar clauses. This list is destructured by ,@ (this means: ,@(1 2 3) -> 1 2 3) but immediately enclosed by 'progn', which is a way to group several instructions into a same block of execution.
4. This is a **macro**, not a function. So, what this returns is not data, but **code**. This is processed at compile-time, so the actual binding of the variables will happen later at runtime.

:)

---

### Post by CptPicard on 2010-01-02
> **nvteighen said:**
> 4. This is a **macro**, not a function. So, what this returns is not data, but **code**.

It does return data, which in this case is the data for valid code. Which is then executed at runtime... :p

---

### Post by Shippou on 2010-01-03
> **nvteighen said:**
> The Common Lisp code [I posted]("http://ubuntuforums.org/showpost.php?p=8587071&postcount=8") does this:
1. Gets a base string and then a list of pairs each of those has the suffix as first element and the initial value for the created variable. The base string is stored in the 'basename' variable and the list of pairs in 'maps'.
2. Loops all stuff in 'maps' and creates a list of 'defvar' calls generating the symbol for that variable by concatenating (via format, which is like C's sprintf in this case) the basename string with the "suffix" (which is conveniently converted into its string representation by format) to form that new variable name. Then, it closes the defvar by grabbing the value we wanted to bind the variable to.
3. The loop returns a list of all generated defvar clauses. This list is destructured by ,@ (this means: ,@(1 2 3) -> 1 2 3) but immediately enclosed by 'progn', which is a way to group several instructions into a same block of execution.
4. This is a **macro**, not a function. So, what this returns is not data, but **code**. This is processed at compile-time, so the actual binding of the variables will happen later at runtime.

:)

Hmmnn. Somewhat like a cheat. :)

Oh well. I think I have to study LISP first. I do appreciate the explanation, though. :)

---

### Post by mmix on 2010-01-03
then it could be done with melt & gcc.

[http://gcc.gnu.org/wiki/MiddleEndLispTranslator](http://gcc.gnu.org/wiki/MiddleEndLispTranslator)

---

