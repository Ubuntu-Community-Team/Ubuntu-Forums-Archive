---
title: "Neec help with  syntax error within g++ compiler"
date: 2012-09-17
forum: Programming Talk
---

### Post by Harryviu on 2012-09-17
#include <iostream>

using namespace std;

//PROTOTYPES
void decimal2Base(int num, int base, char *result, int offset = 0);

int main()
{
** //LOCAL DECLARATIONS
** int num;
** int base;
** char result[20];

** while (true)
** {
***** cout << "Enter number: ";
***** cin >> num;
***** if (num < 0) break;
***** cout << "Enter base: ";
***** cin >> base;
***** if (base > 36 || base < 2) break;

***** decimal2Base(num, base, result);
***** cout << result << endl;

***** cout << endl;
** }

** cout << "\nEnd - Press enter to exit . . . ";
** cin.sync();
** cin.get();
** return 0;
}

//---------------------------------------------------------
// FUNCTION DEFINITIONS
//---------------------------------------------------------
void decimal2Base(int num, int base, char * result, int offset)
{
** if (base > 36 || base < 2)
***** result = "NaN";
** else
** {
***** int digitVal = num % base;
***** *result = (digitVal < 10 ? digitVal + '0' : digitVal - 10 + 'A');

***** if (num >= base)
******** decimal2Base(num / base, base, result + 1, offset + 1);
***** else
***** {
******** result[1] = '\0';
******** result -= offset;
******** //get result's length
******** int len = 0;
******** for (char *ptr = result; *ptr; ptr++)
*********** len++;
******** //copy result to a temporary string
******** char *temp = new char[len + 1];
******** for (char *ptr = result, *tempPtr = temp; *ptr; ptr++, tempPtr++)
*********** *tempPtr = *ptr;
******** //copy back to result in reversed order
******** for (int i = len - 1; i >= 0; i--)
*********** result[len - 1 - i] = temp[i];
******** //free memory of the temporary string
******** delete [] temp;
***** }
** }
}

---

### Post by trent.josephsen on 2012-09-17
No wonder. You've got tons of asterisks in front of all your indented lines.

---

### Post by Odexios on 2012-09-17
You can use the [php] or ```
 tags to post code and preserve indentation.

Don't know about the rest, this is the only line I read, but (assuming functions work the same way in C and C++) that

[code]result = "NaN";
```

line, though not syntactically wrong, doesn't change anything in the original string.

---

### Post by dwhitney67 on 2012-09-17
Here... this works:
```

#include <string>
#include <limits>
#include <iostream>

using namespace std;

void decimal2Base(int num, int base, string& result);
template <typename T> T getInput(const char* prompt);

int main()
{
    while (true)
    {
        string result;

        int num  = getInput<int>("Enter number: ");
        int base = getInput<int>("Enter base: ");

        decimal2Base(num, base, result);

        cout << "Converted number is: " << result << endl << endl;
    }

    cout << "\nEnd - Press enter to exit . . . ";
    cin.get();
}

void decimal2Base(int num, int base, string& result)
{
    if (base < 2 || base > 36)
    {
        result = "NaN";
    }
    else
    {
        int digitVal = num % base;

        result += (digitVal < 10 ? digitVal + '0' : digitVal - 10 + 'A');

        if (num >= base)
        {
            decimal2Base(num / base, base, result);
        }
        else
        {
            result = string(result.rbegin(), result.rend());
        }
    }
}

template <typename T> T getInput(const char* prompt)
{
    using namespace std;

    T    input;
    bool done = false;

    while (!done)
    {
        // prompt user and attempt to read input
        cout << prompt;
        cin  >> input;

        // check if valid input given; break from loop if so.
        if (cin.peek() == '\n' && cin.good())
        {
            done = true;
        }
        else
        {
            // user gave bad input; let them know about it.
            cout << "Invalid input!  Try again...\n" << endl;
            cin.clear();
        }

        do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);
    }

    return input;
}

```

If you have questions, Google.


P.S.  In C++, avoid char arrays; use the STL string class instead.  It will make your life a lot easier.

---

