---
title: "[C++] Data type for 0x numbers ( Integer returns an error ) ?"
date: 2009-08-01
forum: Programming Talk
---

### Post by credobyte on 2009-08-01
I'm lost .. why I can't use 08, if 02 was already accepted ? :confused:
[B]
main.cpp[/B]
[PHP]#include <iostream>
using namespace std;

class Date
{
    public:
        int nDay;
        int nMonth;
        int nYear;
    
        void SetDate(int i_nDay, int i_nMonth, int i_nYear)
        {
            nDay = i_nDay;
            nMonth = i_nMonth;
            nYear = i_nYear;
        }
        
        void ShowDate()
        {
            cout << "Current date: " << nDay << "/" << nMonth << "/" << nYear << "\n";
        }
};

int main(int argc, char *argv[])
{
    Date date;
    
    date.SetDate(02, 08, 2009);
    date.ShowDate();
    
    return 0;    
}
[/PHP]

**Error:**
```
main.cpp:28:19: error: invalid digit "8" in octal constant
```

---

### Post by JupiterV2 on 2009-08-02
The "08" isn't a valid integer. The number '8' is a valid value. How you display the number is up to you.

[php]
#include <iostream>

using namespace std;

int main(void) {
    int num = 8;

    if (num < 10) cout << "0" << num << endl;
    else cout << num;
}[/php]

I'm sure you can come up with a much better way to implement this but I hope you get the point.

---

### Post by credobyte on 2009-08-02
> **JupiterV2 said:**
> The "08" isn't a valid integer. The number '8' is a valid value. How you display the number is up to you.

[php]
#include <iostream>

using namespace std;

int main(void) {
    int num = 8;

    if (num < 10) cout << "0" << num << endl;
    else cout << num;
}[/php]I'm sure you can come up with a much better way to implement this but I hope you get the point.

Thnx, however, I would be more interested in finding out, which data type supports this type of value. Also, why I got an error on 08 ( 08 comes after 02 .. shouldn't I receive this error on 02 ? ) ?

---

### Post by bubuzzz on 2009-08-02
it is because when you use "08", the compiler thinks that you want to use the octal numeral system; however, in this numeral system, there are only from 0 to 7. Therefore, "02" is correct but "08" is not.

---

### Post by MindSz on 2009-08-02
If you need to print out a date, there's a data type for that in C and C++, a structure called tm.

Look for it on the web and you should be able to find it. Here's a starting point [http://www.cplusplus.com/reference/clibrary/ctime/tm/](http://www.cplusplus.com/reference/clibrary/ctime/tm/)

You can also format your output so the numbers are represented by 2 digits and make the leading digits =0. I don't remember how to do this in C++ but it shouldn't be hard to find (look for the setfill() and setw() functions)

---

### Post by credobyte on 2009-08-02
> **MindSz said:**
> If you need to print out a date, there's a data type for that in C and C++, a structure called tm.

Look for it on the web and you should be able to find it. Here's a starting point [http://www.cplusplus.com/reference/clibrary/ctime/tm/](http://www.cplusplus.com/reference/clibrary/ctime/tm/)

You can also format your output so the numbers are represented by 2 digits and make the leading digits =0. I don't remember how to do this in C++ but it shouldn't be hard to find (look for the setfill() and setw() functions)

Well, no - I'm not as much interested in showing the date as to solve this problem for the future knowledge ( this was just an example ). Anyway, thank you for the link - will take a look at it :)

---

