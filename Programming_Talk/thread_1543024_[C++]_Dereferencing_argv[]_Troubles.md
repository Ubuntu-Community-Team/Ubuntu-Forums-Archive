---
title: "[C++] Dereferencing argv[] Troubles"
date: 2010-07-31
forum: Programming Talk
---

### Post by dodle on 2010-07-31
I'm trying to parse command line arguments and get the string values, but all that I get is the first character.  I can't figure out what I am doing wrong.  I have looked over the c++ pointers tutorial here: [http://cplusplus.com/doc/tutorial/pointers/](http://cplusplus.com/doc/tutorial/pointers/).  It appears to me that all I need to do to get the string value of a particular argument is to dereference the pointer using "*":

**parser.cpp**
[php]// parser
int main(int argc, char* argv[])
{
    string value;
    value = *argv[1]; // Get second argument and place it in string
    cout << value << endl;

    return 0;
}[/php]

So, if I use "hello" as the second argument:
```
:~$ parser hello
```
the desired output is the string:
> hello
but the actual output is the character:
> h

How can I get the entire string argument?

---

### Post by GeneralZod on 2010-07-31
```

argv[1]

```

is a char*, so

```

*argv[1]

```

is a single char i.e. you're de-referencing one too many times :)

---

### Post by dodle on 2010-07-31
Oh, I should have tested that first :p.  My problem started with this code:
[php]int main(int argc, char* argv[])
{
    int arg;
    string arg_o = "-o";

    if (argc > 1)
    {
        for (arg = 0; arg < argc; arg += 1)
        {
            if (argv[arg] == arg_o)
            {
                arg_o = argv[arg+1];
            }
        }
    }
    else
    {
        cout << "Usage: " << argv[0] << " [arg]" << endl;
    }

    cout << "The value for argument -o is " << arg_o << endl;

    return 0;
}[/php]

I would get a segfault when trying to print the new value of arg_o.  For some reason I had to make a new, empty, string and place the value of "argv[arg+1]" in it.  So my new code looks like this:
[php]int ParseStatus(string line, string node)
{
    cout << line << " / " << node << endl;
}

int main(int argc, char* argv[])
{
    int arg;
    string arg_o = "-o";
    string test;

    if (argc > 1)
    {
        for (arg = 0; arg < argc; arg += 1)
        {
            if (argv[arg] == arg_o)
            {
                test = argv[arg+1];
            }
        }
    }
    else
    {
        cout << "Usage: " << argv[0] << " [arg]" << endl;
    }

    cout << "The value for argument -o is " << test << endl;

    return 0;
}[/php]

Which works fine, but I still don't understand why I can't replace the value of arg_o with argv[arg+1].

---

### Post by vikas.sood on 2010-07-31
OK!!!

In the first code that you pasted in above comment, you enter the if (argv[arg] == arg_o) condition twice. For arg =1 and arg=2. Because when arg =1, you get argv[arg] == "-o" and you assign arg_o = argv[arg+1]. Again when arg = 2, you will find arg_o == argv[arg] to evaluate to true because you just assigned arg_o as argv[arg+1] from previous iteration. And when you do that, you end up derefrencing argv[2+1] which is not allocated. 

Dry run the above code and you will know it.

In the second code, it doesnt crash because it never enters if condition 2 times as assignment is done to a different variable.

Above all, if you intend to write the code to parse command line arguments, i would suggest you to use getopt_long. use man getopt_long for more details on that function. It allows you to handle short and long forms of command line arguments...ie you can handle "-o" and "--outfile" as same...."-h" and "--help" as same.

The only problem with getopt_long is portability.

Happy c++

---

