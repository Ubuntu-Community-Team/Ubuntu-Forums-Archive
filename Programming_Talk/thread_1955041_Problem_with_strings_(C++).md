---
title: "Problem with strings (C++)"
date: 2012-04-09
forum: Programming Talk
---

### Post by flurospar on 2012-04-09
I required a quick solution for comparing dates, and wrote this small thing which does the job perfectly:

```

#include <iostream>
#include <string>
#include <fstream>
#include <ctime>
using namespace std;

bool checkdate(string input_date)
{
    bool date_check_result = false;
    time_t date_temp;
    struct tm *date_format; 
    char date_[11];
    time(&date_temp);
    date_format = localtime(&date_temp);
    strftime(date_out, 11, "%d-%m-%Y", date_format);
    if(input_date == date_out)
    {
        date_check_result = true;
    }
    return (date_check_result);
}

int main()
{
    string date_in_the_file;
    ifstream datefile("date");
    if (datefile.is_open())
    {
        getline(datefile, date_in_the_file);
        datefile.close();
    }
    cout << "date in the file = " << date_in_the_file << endl;
    if (checkdate(date_in_the_file.c_str()))
    {
        cout << "the dates matched!" << endl;
        return 0;
    }
    else
    {
        cout << "the dates didn't match!" << endl;
        return -1;
    }
}

```I had completely forgotten about this thing for months, and now, unfortunately, I can't understand my own code. I am at a loss to understand a few things:

1. How does a string and a char[] become comparable? It isn't comparable if I did " checkdate(date_in_the_file) " (causes errors while compiling) but becomes magically comparable when I use " checkdate(date_in_the_file.c_str()) ".

2. Even if I use " bool checkdate (char *input_date) " with " checkdate(date_in_the_file.c_str()) " , the dates do not match, whether I use " if(input_date == date_out) " or " strcmp(input_date, date_out") ". Why?


Any help is appreciated.

---

### Post by dwhitney67 on 2012-04-09
> **flurospar said:**
> 
1. How does a string and a char[] become comparable?

The STL string class has a method associated with it that allows for comparisons with another string object, or with const char* arrays.

> **flurospar said:**
> 
It isn't comparable if I did " checkdate(date_in_the_file) " (causes errors while compiling) ...

I doubt this; another error must have confused you into believing that calling checkdata with a bonafide std::string was causing a compile error.

> **flurospar said:**
> 
2. Even if I use " bool checkdate (char *input_date) " with " checkdate(date_in_the_file.c_str()) " , the dates do not match, whether I use " if(input_date == date_out) " or " strcmp(input_date, date_out") ". Why?

This strings don't match because they are not the same.  Without having the privilege of seeing the data within your file, I cannot comment further.

> **flurospar said:**
> 
Any help is appreciated.
Since you have no intentions of modififying the string passed to checkdate(), I would recommend that a) you declare the variable as const, and b) that you pass the string by reference.
```

bool checkdate(**const std::string&** date)
{
    ...
}

```

---

### Post by flurospar on 2012-04-09
If I use bool checkdate(char* input_date) and if (checkdate(date_in_the_file.c_str())) , I get an error like this:

```
test.cpp:33:40: error: invalid conversion from 'const char*' to 'char*' [-fpermissive]
test.cpp:7:6: error:   initializing argument 1 of 'bool checkdate(char*)' [-fpermissive]

```

I was wrong about  checkdate(date_in_the_file) causing compile errors, but this one sure does cause compile errors. (I was wrong about not getting a match, it doesn't compile).

BTW, is the memory associated with the variables in checkdate() erased after the function ends? I am using this in a larger program and see the memory usage rising drastically after a few hours. Also, can we delete strings like dynamically assigned C-style strings?

---

### Post by GeneralZod on 2012-04-09
Use 

```

 bool checkdate(const char* input_date) 

```

instead.

Edit:

Or rather, do what dwhitney67 said :)

---

### Post by flurospar on 2012-04-09
With bool checkdate(const char* input_date), the following happens:

```

$ g++ test.cpp -o test
$ date +%d-%m-%Y > date
$ ./test
date in the file = 09-04-2012
the dates didn't match!
$ date +%d-%m-%Y
09-04-2012


```

Why should this occur?

---

### Post by dwhitney67 on 2012-04-09
> **flurospar said:**
> With bool checkdate(const char* input_date), the following happens:

```

$ g++ test.cpp -o test
$ date +%d-%m-%Y > date
$ ./test
date in the file = 09-04-2012
the dates didn't match!
$ date +%d-%m-%Y
09-04-2012


```

Why should this occur?
If you examine the code you originally posted, the following statement is legal, yet it does not do what you want.
```

if(input_date == date_out)

```
That statement merely compares two pointers (to strings).  If you want to program in C, you need to use strcmp() or strncmp().  If you want to program in C++, then something like this would be more appropriate:
```

bool checkdate(**const std::string&** input_date)
{
    time_t     date_temp;
    struct tm* date_format;
    char       date_out[11];

    time(&date_temp);

    date_format = localtime(&date_temp);

    strftime(date_out, 11, "%d-%m-%Y", date_format);

    **return input_date == date_out;**
}

...

```
There's no need to maintain a bool "flag" to return when returning the result of the comparison will suffice.  However, some programmers tend to like keeping a flag that can be analyzed using a debugger.  The choice is yours.

---

