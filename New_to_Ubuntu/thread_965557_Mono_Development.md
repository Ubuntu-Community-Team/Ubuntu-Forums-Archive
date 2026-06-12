---
title: "Mono Development"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by xnerdx on 2008-10-31
Hello! I am absolutely in love with linux :). I have been using it for about 5 months now. (Unimportant) Anyways, I recently have steped into the programing world. I installed Mono Development from the Add/Remove... section of the Applications panel on ubuntu 8.10. I installed it and it loads and runs pretty much like it should, only some slight problems? I was trying to compile a program and I seem to always get outputs that contain errors or I get a debuging problem. Here is the code I am testing due to the fact that I couldn't make my code compile I decided to attempt to copy and paste the code used by the book in which I am reading ([http://www.programmersheaven.com/2/CSharpBook](http://www.programmersheaven.com/2/CSharpBook)). This is the code:
```
using System;
// To execute the program write "SwitchCaseExample 2" or
// any other number at command line,
// if the name of .exe file is "SwitchCaseExample.exe"
namespace CSharpSchool
{
    class SwitchCaseExample
    {
        // Demonstrates the use of switch...case statement along with
        // the use of command line argument
        static void Main(string [] userInput)
        {
            int input = int.Parse(userInput[0]);
            // convert the string input to integer.
            // Will throw a run-time exception if there is no input at run-time or if
            // the input is not castable to integer.
            switch(input)      // what is input?
            {
                case 1:        // if it is 1
                    Console.WriteLine("You typed 1 (one) as the first command line argument");
                    break;     // get out of switch block
                case 2:        // if it is 2
                    Console.WriteLine("You typed 2 (two) as the first command line argument");
                    break;     // get out of switch block
                case 3:        // if it is 3
                    Console.WriteLine("You typed 3 (three) as the first command line argument");
                    break;     // get out of switch block
                default:       // if it is not any of the above
                    Console.WriteLine("You typed a number other than 1, 2 and 3");
                    break;     // get out of switch block
            }
        }
    }
}

```
It doesn't give me any debuging errors but when I chose the Run command it gives me this as my application output:
```
Unhandled Exception: System.IndexOutOfRangeException: Array index is out of range.
  at CSharpSchool.SwitchCaseExample.Main (System.String[] userInput) [0x00000] in /home/michael/meow/meow/cat.cs:13 
```

---

### Post by directhex on 2008-10-31
> **xnerdx said:**
> Hello! I am absolutely in love with linux :). I have been using it for about 5 months now. (Unimportant) Anyways, I recently have steped into the programing world. I installed Mono Development from the Add/Remove... section of the Applications panel on ubuntu 8.10. I installed it and it loads and runs pretty much like it should, only some slight problems? I was trying to compile a program and I seem to always get outputs that contain errors or I get a debuging problem. Here is the code I am testing due to the fact that I couldn't make my code compile I decided to attempt to copy and paste the code used by the book in which I am reading ([http://www.programmersheaven.com/2/CSharpBook](http://www.programmersheaven.com/2/CSharpBook)). This is the code:
```
using System;
// To execute the program write "SwitchCaseExample 2" or
// any other number at command line,
// if the name of .exe file is "SwitchCaseExample.exe"
namespace CSharpSchool
{
    class SwitchCaseExample
    {
        // Demonstrates the use of switch...case statement along with
        // the use of command line argument
        static void Main(string [] userInput)
        {
            int input = int.Parse(userInput[0]);
            // convert the string input to integer.
            // Will throw a run-time exception if there is no input at run-time or if
            // the input is not castable to integer.
            switch(input)      // what is input?
            {
                case 1:        // if it is 1
                    Console.WriteLine("You typed 1 (one) as the first command line argument");
                    break;     // get out of switch block
                case 2:        // if it is 2
                    Console.WriteLine("You typed 2 (two) as the first command line argument");
                    break;     // get out of switch block
                case 3:        // if it is 3
                    Console.WriteLine("You typed 3 (three) as the first command line argument");
                    break;     // get out of switch block
                default:       // if it is not any of the above
                    Console.WriteLine("You typed a number other than 1, 2 and 3");
                    break;     // get out of switch block
            }
        }
    }
}

```
It doesn't give me any debuging errors but when I chose the Run command it gives me this as my application output:
```
Unhandled Exception: System.IndexOutOfRangeException: Array index is out of range.
  at CSharpSchool.SwitchCaseExample.Main (System.String[] userInput) [0x00000] in /home/michael/meow/meow/cat.cs:13 
```

Technically you haven't got any errors in your code, it's behaving correctly. You see this line:
```
            int input = int.Parse(userInput[0]);
```

Well, userInput is an array of all the parameters given to your program when you ran it (e.g. "mono SwitchCaseExample.exe panda bears are cute" would provide an array with 4 entries - "panda", "bears", "are" and "cute", indexed from 0-3)

If you run your app with no command-line parameters, then you're trying to access the first value of an array with zero entries - obviously not possible

Try running from a command line to see how it should go:
```
directhex@mortos:/tmp$ mono foom.exe

Unhandled Exception: System.IndexOutOfRangeException: Array index is out of range.
  at CSharpSchool.SwitchCaseExample.Main (System.String[] userInput) [0x00000] 
directhex@mortos:/tmp$ mono foom.exe 1
You typed 1 (one) as the first command line argument
directhex@mortos:/tmp$ mono foom.exe 3 is a big number
You typed 3 (three) as the first command line argument
```

---

### Post by directhex on 2008-10-31
> **directhex said:**
> Technically you haven't got any errors in your code, it's behaving correctly. You see this line:
```
            int input = int.Parse(userInput[0]);
```

Well, userInput is an array of all the parameters given to your program when you ran it (e.g. "mono SwitchCaseExample.exe panda bears are cute" would provide an array with 4 entries - "panda", "bears", "are" and "cute", indexed from 0-3)

If you run your app with no command-line parameters, then you're trying to access the first value of an array with zero entries - obviously not possible

Try running from a command line to see how it should go:
```
directhex@mortos:/tmp$ mono foom.exe

Unhandled Exception: System.IndexOutOfRangeException: Array index is out of range.
  at CSharpSchool.SwitchCaseExample.Main (System.String[] userInput) [0x00000] 
directhex@mortos:/tmp$ mono foom.exe 1
You typed 1 (one) as the first command line argument
directhex@mortos:/tmp$ mono foom.exe 3 is a big number
You typed 3 (three) as the first command line argument
```

Oh, and the code also fails on non-numeric values:
```
directhex@mortos:/tmp$ mono foom.exe badger

Unhandled Exception: System.FormatException: Input string was not in the correct format
  at System.Int32.Parse (System.String s) [0x00000] 
  at CSharpSchool.SwitchCaseExample.Main (System.String[] userInput) [0x00000] 
```

This is because Int.Parse() throws an exception if it fails to do as expected. You can switch to using Int.TryParse() instead, which does not throw an exception. Switch the Int.Parse line for:
```
            int input = 0;
            int.TryParse(userInput[0], out input);
```
which then means:
```
directhex@mortos:/tmp$ mono foom.exe snake
You typed a number other than 1, 2 and 3
```

Or, even better, get rid of the exception from earlier:
```
            int input = 0;
            if(userInput.Length > 0)
                int.TryParse(userInput[0], out input);
```
->
```
directhex@mortos:/tmp$ mono foom.exe 
You typed a number other than 1, 2 and 3
```

---

### Post by directhex on 2008-10-31
(If memory serves, TryParse requires you compile for .NET 2.0 using mono-gmcs, not .NET 1.1 with mono-mcs. You can change profile somewhere in the project settings in MonoDevelop, try right-clicking on things ni the solution pane & looking through Properties windows)

---

### Post by xnerdx on 2008-10-31
Wait I am extremely confused! Lol :) Okay, first off what .net framework is Mono Development based on? I think that the book I am reading is writing programs on a 2.0 framework. If it doesn't compile in 2.0 is there a way to make it? Can someone maybe quickly review the ebook in the link I posted to maybe tell me what may be wrong?
Thank you

---

### Post by directhex on 2008-10-31
> **xnerdx said:**
> Wait I am extremely confused! Lol :) Okay, first off what .net framework is Mono Development based on? I think that the book I am reading is writing programs on a 2.0 framework. If it doesn't compile in 2.0 is there a way to make it? Can someone maybe quickly review the ebook in the link I posted to maybe tell me what may be wrong?
Thank you

"mcs" compiles for the 1.0 class library. "gmcs" compiles for the 2.0 class library. Monodevelop compiles for whatever you configured your project to compile against (there's some setting somewhere for runtime version, like I said it's in the project options or solution options)

---

