---
title: "[C++]error: called object type 'bool' is not a function or function pointer"
date: 2015-09-07
forum: Programming Talk
---

### Post by benrob0329 on 2015-09-07
Ok, so I have finally found time to work on learning C++, so what better way of learning than writing a simple calculator, right?

I'm afraid I can't quite figure out this error Clang is throwing at me:

```
/home/ben/C++/Calculator/main.cpp|76|error: called object type 'bool' is not a function or function pointer|
```

Here is main.cpp:

```
/*
Copyright (c) 2015 INNOVATION-Plex

This software is provided 'as-is', without any express or implied
warranty. In no event will the authors be held liable for any damages
arising from the use of this software.

Permission is granted to anyone to use this software for any purpose,
including commercial applications, and to alter it and redistribute it
freely, subject to the following restrictions:

1. The origin of this software must not be misrepresented; you must not
   claim that you wrote the original software. If you use this software
   in a product, an acknowledgement in the product documentation would be
   appreciated but is not required.
2. Altered source versions must be plainly marked as such, and must not be
   misrepresented as being the original software.
3. This notice may not be removed or altered from any source distribution.
*/


#include <iostream>
#include <string>
#include <sstream>

using namespace std;

float math (float a, char b, float c)
{
    if (b == '+')
    {
        return a + c;
    }

    else if (b == '-')
    {
        return a - c;
    }

    else if (b == '*')
    {
        return a * c;
    }

    else if (b == 'x')
    {
        return a * c;
    }

    else if (b == '/')
    {
        return a / c;
    }

    else
    {
        cerr << "Invaled Equation Type.";
    }
}

float strEquation (string equation)
{
    bool equationNumIs2 = false;
    char equationChar;
    string equationTmpStr = "";
    string equationTmpStr2 = "";

    for (char equationChar : equation)
    {
        if ((equationChar == '1') || (equationChar == '2') || (equationChar == '3') || (equationChar == '4') || (equationChar == '5') || (equationChar == '6') || (equationChar == '7') || (equationChar == '8') || (equationChar == '9') || (equationChar == '0') || (equationChar == '.'))
        {
            if (equationNumIs2 != true) equationTmpStr.append (1,equationChar);
            else equationTmpStr2.append (1, equationChar);
        }

        else if (equationChar == '+') || (equationChar == '-') || (equationChar == '*') || (equationChar == 'x') (equationChar == '/') (equationChar == '%'))
        {
            char b = equationChar;
            equationNumIs2 = true;
        }
        else if (equationChar == " ") equationNumIs2 = true;
    }

    stringstream (equationChar2) >> float a
    stringstream (equationChar3) >> float c

    return math(a, b, c)

int main()
{

//Variable definitions
    string type;
    float num1, num2;

//License, Copyright, and Vertion
    cout << "\
    Calculator Vetion 0.1.2\n\
    \n\
    Copyright (c) 2015 INNOVATION-Plex\n\
    \n\
    This software is provided 'as-is', without any express or implied\n\
    warranty. In no event will the authors be held liable for any damages\n\
    arising from the use of this software.\n\
    \n\
    Permission is granted to anyone to use this software for any purpose,\n\
    including commercial applications, and to alter it and redistribute it\n\
    freely, subject to the following restrictions:\n\
    \n\
    1. The origin of this software must not be misrepresented; you must not\n\
    claim that you wrote the original software. If you use this software\n\
    in a product, an acknowledgement in the product documentation would be\n\
    appreciated but is not required.\n\
    2. Altered source versions must be plainly marked as such, and must not be\n\
    misrepresented as being the original software.\n\
    3. This notice may not be removed or altered from any source distribution.\n\
    " << endl;

//Todo and Help
    cout << endl << "\
TODO:\n\
    Make the syntax faster to type, eg: [5+5]\n\
    Make a cleaner way to exit\n\
    Add the appility to be able to do Algabraic things (Variables, ect)\n\
    \n\
Help:\n\
    Enter the equation you would like to have computed.\n\
    E.G. [5 + 5]\n\
    Press CTRL+C to exit." << endl;


//Infanint input loop and math checks
    while (true)
    {

//Terminal Identification (For Looks)
    cout << endl << "(Calculator)";

//Equation input
    cin >> equationInput;


//Computing of the Equation
    cout << strEquation(equationInput);


//Add a line break to clean things up.
    cout << endl;
    }

//End the program.
    return 0;
}


```

I'm afraid I haven't gotten around to fully commenting my code quite yet, and the code wont compile at all (for multiple errors, but I can probably figure those out).

---

### Post by spjackson on 2015-09-07
> 
```

        else if (equationChar == '+') || (equationChar == '-') || (equationChar == '*') || (equationChar == 'x') (equationChar == '/') (equationChar == '%'))

```

Your last 3 expressions are missing || operators between them.

---

### Post by benrob0329 on 2015-09-07
Oh, dirp. Thanks!

There is probably a better way to do it, like a switch controll, but I have the idea now.

---

