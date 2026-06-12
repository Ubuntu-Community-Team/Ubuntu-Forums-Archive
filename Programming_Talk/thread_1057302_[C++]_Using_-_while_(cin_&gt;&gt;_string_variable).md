---
title: "[C++] Using - while (cin &gt;&gt; string_variable) help"
date: 2009-02-01
forum: Programming Talk
---

### Post by Nexusx6 on 2009-02-01
Hello,

I'm a python coder taking a C++ class (don't worry, I've read the rules before, its not a 'do my homework for me post'). The homework was a simple Mad Libs style program and I have nearly the whole thing done, but in an effort to keep my code clean I'm getting caught up at a point in a while statement that I have in a function. 

```
void getLib(string prompt, string& var)
//This function takes 2 string arguments, a prompt and a global variable defined in main()
//and checks "var" for a real value and not a blank caused by hitting "Enter"
{
    using namespace std;
    cout << prompt;
    while (cin >> var && var == "") //If user try's to leave field blank, stop and request until they enter something
    {
        cout << "Hey! Don't be passing blanks! I need something to work with here!\n"
             << prompt;
    }
}

```

The point of the while loop is to get input for the variable and make sure the user didn't simply hit the Enter key -- if they do, prompt them again for input. What's happening instead is this: 

```
Hola! What's your name?      //Carriage return
                            //Carriage return
Foo
Hi Foo!
```
Though its not letting the code continue until data is put in, it's also not displaying the 'cout <<' or 'prompt' parts. I know I could use If statements in the while loop, but it wouldn't be as clean. So, what is it I am doing wrong here?

---

### Post by norcim on 2009-02-01
you could try moving the  "cin>>var" inside the loop. be sure to initialize var to "" first


this expression "cin>>var" returns "cin" . this is because the overloaded ">>" is set to return "cin" to allow for expressions like "cin>>a>>b>>c". This allows "cin>>a" to be evaluated, then "cin>>b" is evaluated then "cin>>c"....

When you use "while(cin>>a)" it will be an endless loop asking for input until one is given. So when you add "while(cin>>a && a=="") the body of the loop is never executed. 


read more here.. [http://www.fredosaurus.com/notes-cpp/io/io-operators.html](http://www.fredosaurus.com/notes-cpp/io/io-operators.html)

---

### Post by SledgeHammer_999 on 2009-02-01
Maybe something like this:
```
void getLib(string prompt, string& var)
//This function takes 2 string arguments, a prompt and a global variable defined in main()
//and checks "var" for a real value and not a blank caused by hitting "Enter"
{
    using namespace std;
    cout << prompt;
    while (var == "") //If user try's to leave field blank, stop and request until they enter something
    {
        cout << "Hey! Don't be passing blanks! I need something to work with here!\n"
             << prompt;
        cin >> var;
    }
}
```

I **think** the problem here is that "cin >> var" cannot be evaluated as TRUE or FALSE.
And maybe instead of "var == """ use "var.empty()". link-->[http://www.cplusplus.com/reference/string/string/empty.html](http://www.cplusplus.com/reference/string/string/empty.html)

---

### Post by Nexusx6 on 2009-02-01
> **norcim said:**
> you could try moving the  "cin>>var" inside the loop. be sure to initialize var to "" first

Yeah, I have initialized var as an empty string in the main() function.

Thought I could do that, I would have to repeat cin >> var twice, to get it working right, ie.

```

cout << prompt;
cin >> var;
while (var == "")
{
     cout << "Please enter a real value";
     cin >> var;
}

```

Which yeah defiantly works, but isn't there a way without having to write cin >> var twice like that? Though it is nit-picky of me, I don't want to develop bad habits this early in the semester :redface:

---

### Post by Nexusx6 on 2009-02-01
> **SledgeHammer_999 said:**
> Maybe something like this:
```
void getLib(string prompt, string& var)
//This function takes 2 string arguments, a prompt and a global variable defined in main()
//and checks "var" for a real value and not a blank caused by hitting "Enter"
{
    using namespace std;
    cout << prompt;
    while (var == "") //If user try's to leave field blank, stop and request until they enter something
    {
        cout << "Hey! Don't be passing blanks! I need something to work with here!\n"
             << prompt;
        cin >> var;
    }
}
```

I **think** the problem here is that "cin >> var" cannot be evaluated as TRUE or FALSE.
And maybe instead of "var == """ use "var.empty()". link-->[http://www.cplusplus.com/reference/string/string/empty.html](http://www.cplusplus.com/reference/string/string/empty.html)

Hmm, problem is; if I do it that way, the "error" gets printed before the user gets a chance to put a variable in. If I flip it so that cin >> var comes before cout << such as:

```

while (var == "") //If blank request until something is entered
    {

        cin >> var;
        cout << "Hey! Don't be passing blanks! I need something to work with here!\n"
             << prompt;

    }

```

It gets even more strange:
```

Hola! What's your name?    //<enter key>
                    //<enter key>

Foo
Hey! Don't be passing blanks! I need something to work with here! //An error got spit out even though user put in a value
Hola! What's your name? Hello Foo! //the prompt got repeated for some reason

```

Weird. Should I post my whole code?

> 
I **think** the problem here is that "cin >> var" cannot be evaluated as TRUE or FALSE.
You might be on to something

---

### Post by dwhitney67 on 2009-02-01
Consider this alternative:
[php]
#include <string>
#include <iostream>

int main()
{
  std::string name;

  do
  {
    std::cout << "Enter your name: ";
    getline(std::cin, name);

    /* optional code in case operator enters ctrl-d */
    if (!std::cin)
    {
      std::cin.clear();
      std::cout << std::endl;
    }
    /* end optional code */

  } while (name.empty() || !isalpha(name[0]));

  std::cout << "name = " << name << std::endl;
}
[/php]

---

### Post by Nexusx6 on 2009-02-01
Since I think Sledgehammer is right and that "cin >> var" can't be evaluated for a boolean value I've settled on a mix of the suggestions posted here:
```
    do {
        cout << prompt;
        getline(cin, var);
        if (var.empty()) cout << "Please put something in the field";
    } while (var.empty());
```

Thanks everyone for all the help and tips!

---

### Post by dribeas on 2009-02-01
> **norcim said:**
> you could try moving the  "cin>>var" inside the loop.

> **SledgeHammer_999 said:**
> I **think** the problem here is that "cin >> var" cannot be evaluated as TRUE or FALSE.
And maybe instead of "var == """ use "var.empty()". link-->[http://www.cplusplus.com/reference/string/string/empty.html](http://www.cplusplus.com/reference/string/string/empty.html)

First, to make things clearer, there is no problem with the std::cin >> var code being inside the parenthesis of the while. Input streams have a conversion to bool implemented similar to:

```

// Equivalent, the real code is more complex (string is a instantiation of a template)
class string
{
public:
   operator bool() {
      return !fail();
   }
};

```

Now back to the real deal. The problem is that the >> operator will skip blank spaces until it finds a non-blank character. When your code calls std::cin >> var the system will start reading and will skip any blank space, including your enters. By the time it returns, either var is non-empty or the operation has failed (error or EOF), so the condition of the while will never be true and thus you will get no feedback.

If you really want to work on that input problem, you can either go for dwhitney67 solution of using getline --which will return once the first eol is found. Or you can go into a harder input mechanism where you read each char and compose the string yourself. I would not consider it worth the effort.

---

### Post by Nexusx6 on 2009-02-01
> Now back to the real deal. The problem is that the >> operator will skip blank spaces until it finds a non-blank character. When your code calls std::cin >> var the system will start reading and will skip any blank space, including your enters. By the time it returns, either var is non-empty or the operation has failed (error or EOF), so the condition of the while will never be true and thus you will get no feedback.

If you really want to work on that input problem, you can either go for dwhitney67 solution of using getline ...

**Oooh!** Thats why the program wasn't responding the way I wanted it to when I was using cin. That makes sense, I didn't know cin skips blank characters.

```
    cout << prompt;
    while (getline(cin,var) && var.empty()) {
        cout << "\nPlease enter something into the field"
             << prompt;
        }
```
Well look at that, it works :D Thank you!

---

### Post by norcim on 2009-02-01
hope you got the underlying lesson in that :)

---

