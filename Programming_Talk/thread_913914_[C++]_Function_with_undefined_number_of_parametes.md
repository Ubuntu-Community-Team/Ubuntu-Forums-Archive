---
title: "[C++] Function with undefined number of parametes?"
date: 2008-09-08
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-09-08
While experimenting with gstreamer(written in C) I saw many functions taking many parameters, without having a fixed number of them, and the last is a NULL parameter. 
1.How do I implement this kind of function in C++? 
2.How do I know how many parameters where passed?
example pseudo code:
```
my_custom_function(int parm1, int parm2, int parm3 ... int parmN, NULL)
```

---

### Post by LaRoza on 2008-09-08
> **SledgeHammer_999 said:**
> While experimenting with gstreamer(written in C) I saw many functions taking many parameters, without having a fixed number of them, and the last is a NULL parameter. 
1.How do I implement this kind of function in C++? 
2.How do I know how many parameters where passed?
example pseudo code:
```
my_custom_function(int parm1, int parm2, int parm3 ... int parmN, NULL)
```
[http://www.codersource.net/c++_variable_argument_functions.html](http://www.codersource.net/c++_variable_argument_functions.html)

[http://www.cppreference.com/stdother/va_arg.html](http://www.cppreference.com/stdother/va_arg.html)

It should explain it.

---

### Post by nvteighen on 2008-09-08
For you to know, in **C** (examples taken from a real piece of code by me I hope to release soon):

0. **#include <stdarg.h>** It's a Standard Library's header, so you don't need to install anything special.

1. You declare the function as:
```
[color=#B00040]char[/color] list_set(list_t [color=#666666]*[/color]list, [color=#B00040]void[/color] [color=#666666]*[/color]data, ...)

```

The ellipsis (...) tells the compiler the function will have an undefined amount of parameters. Note that functions have to have at least one required argument.

2. Look at this code (which is from a real program I'm developing, to show what's the usual way to use this). Don't try to understand what it does, but rather read the comments. 
```
[color=#B00040]char[/color] [color=#0000FF]list_set[/color](list_t [color=#666666]*[/color]list, [color=#B00040]void[/color] [color=#666666]*[/color]data, ...)
{
    [color=#B00040]char[/color] exit_code [color=#666666]=[/color] [color=#666666]0[/color];
    va_list ap; [color=#408080]*/* Variable parameters list declared */*[/color]
    va_start(ap, data); [color=#408080][i]/* Initializing 'ap' to take parameters up from 
                           argument 'data'. */[/i][/color]
   
    [color=#408080]*/* Parse arguments */*[/color]
    [color=#B00040]void[/color] [color=#666666]*[/color]i [color=#666666]=[/color] [color=#008000]NULL[/color]; [color=#408080][i]/* Now, we have to iterate through 'ap', but the counter has
                       to be (void *) because that's the type I need. But it 
                       should be of the data type you expect from arguments. */[/i][/color]
    size_t j;
    [color=#008000]**for**[/color](i [color=#666666]=[/color] data, j [color=#666666]=[/color] [color=#666666]0[/color]; i [color=#666666]!=[/color] [color=#008000]NULL[/color]; i [color=#666666]=[/color] va_arg(ap, [color=#B00040]void[/color] [color=#666666]*[/color]), j[color=#666666]++[/color])
        [color=#408080][i]/* va_arg() returns the next argument from 'ap' that corresponds to the 
           data type I request it to be (void *) in this case. As you see, if 
           the parameter is NULL, the for-loop stops. */[/i][/color]
    {
        node_t [color=#666666]*[/color]curr [color=#666666]=[/color] LIST_NODE(list, j);
		
        [color=#008000]**if**[/color](curr [color=#666666]==[/color] [color=#008000]NULL[/color])
        {
            exit_code [color=#666666]=[/color] list_append_data(list, j [color=#666666]-[/color] [color=#666666]1[/color], i);
            [color=#008000]**if**[/color](exit_code [color=#666666]==[/color] [color=#666666]1[/color])
                [color=#008000]**break**[/color];
        }
        [color=#008000]**else**[/color]
            node_set_data(curr, i); [color=#408080]*/* Here I used the parameter I've taken. */*[/color]
    }
    
    va_end(ap); [color=#408080]*/* You ALWAYS have to "close" the arguments list. */*[/color]

    [color=#008000]**return**[/color] exit_code;    
}

```

3. So, basically, you create a va_arg variable, initialize it with va_start() and then, you request the next argument with va_arg(). And when you're done, you close it with va_end()

---

### Post by dribeas on 2008-09-08
> **SledgeHammer_999 said:**
> While experimenting with gstreamer(written in C) I saw many functions taking many parameters, without having a fixed number of them, and the last is a NULL parameter. 
1.How do I implement this kind of function in C++? 
2.How do I know how many parameters where passed?
example pseudo code:
```
my_custom_function(int parm1, int parm2, int parm3 ... int parmN, NULL)
```

In general I would advice against variable argument methods (with varargs) as it is harder to use generic code on that kind of methods (some libraries don't even support it). In some cases (as gstreamer) where they must provide for a completely general unknown at library-compile time interface, it may be the only option, but in general if you can make it with just default values for your methods, that plays better with the rest of the language.

```

void f( int a = 0, double b = 0.0, std::string value = "" ); 

f(); // calls f(0,0.0,"")
f(1); // calls f(1,0.0,"")
f(2,3.0); // calls f(2,3.0,"")
f(4,5.0,"Hi");

```

Limitations are: you can only omit parameters from the right (you cannot provide just the string value) and you must have a predefined set of maximum parameters (and order).

Not as flexible as varargs, but easier to use with generic code (boost::bind, boost::lambda, boost::signal, boost::function...)

   David

---

### Post by SledgeHammer_999 on 2008-09-08
I think I understand now :D Ehm just one question: from the examples I read: When I call the function I don't need to pass NULL as the final parameter, right?

@dribeas I don't like to use variable argument methods but in case of my program I need to pass to a pipeline a variety of elements(plugins/decoders/filters). I can't know from the beginning how many elements I'll need to decode a certain media type.

---

### Post by nvteighen on 2008-09-08
> **SledgeHammer_999 said:**
> I think I understand now :D Ehm just one question: from the examples I read: When I call the function I don't need to pass NULL as the final parameter, right?


At least in my C example, yes. Because the for-loop that processes arguments is told to stop when the argument is NULL; surely gstreamer does the same (and GTK+ also uses the same idiom).

If you don't pass NULL, the result is undefined... usually it works (for me), but you aren't safe from possible weirdnesses because of that, so better don't do that and follow the API! :)

---

### Post by SledgeHammer_999 on 2008-09-08
yeah I figured that I 'need' to pass NULL so I'll know where to stop(my code). But I have another question. Which is the correct header for C++ _stdargs.h_ or _cstdarg_?

---

### Post by dribeas on 2008-09-08
> **SledgeHammer_999 said:**
> yeah I figured that I 'need' to pass NULL so I'll know where to stop(my code). But I have another question. Which is the correct header for C++ _stdargs.h_ or _cstdarg_?

Ending your parameter sequence with NULL (in C, 0 in C++) is optional, as long as you can figure the parameter list size. printf and all its variants don't require the size of the argument list, it can be inferred from the first char* parameter.

In general, for all C standard header xxx.h there is a related cxxx C++ header. In most cases it is just a wrapper that places the functions inside the std namespace. In some cases it also undefines macros and implements them as inline functions. You should go for the cxxx version whenever available (if you code C++).

---

### Post by kjohansen on 2008-09-08
maybe it is just me but I have always hated this construct.

You could just as easily make the parameter a single argument of type vector and get the same functionality with a cleaner construct.

---

