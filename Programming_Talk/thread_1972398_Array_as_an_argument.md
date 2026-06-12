---
title: "Array as an argument"
date: 2012-05-03
forum: Programming Talk
---

### Post by echo.zyw on 2012-05-03
Hey guys, 

   I have a question about the following code. Any advice for me? Thanks in advance. :)

   Code: 
      
  2 #include <iostream>
  3 using namespace std;
  4 
  5 int printarray(int (&array)[4],n){
  6         cout << "Outputing from printarray func. " << endl;
  7         for (int i = 0; i < 4; i++){
  8                 cout << array[i] << endl;
  9         }
 10         return n;
 11 }
 12 
 13 int main(){
 14         int b[] = {1, 2, 3, 4};
 15         int *a;
 16         a = b;
 17 
 18         cout << printarray(b,5) << endl;
 19         return 0;
 20 }

    g++ -o a a.ccp error:
     
    a.cpp:5:22: error: ‘array’ was not declared in this scope
    a.cpp:5:32: error: ‘n’ was not declared in this scope
    a.cpp:5:33: error: expression list treated as compound expression in initializer [-fpermissive]
    a.cpp:5:34: error: expected ‘,’ or ‘;’ before ‘{’ token

    But if I write function printarray(int (&array)[4],n) as printarray(int (&array)[4]), then it will work well for me. Any idea why the above error happened?

---

### Post by karlson on 2012-05-03
First off use <code> tags

Second.  Why not declare function as
```
int printarray(int *array, int n)
```

---

### Post by echo.zyw on 2012-05-03
Thank you for your advice. 

Yes. That will work. But I would like to have a look at the use of reference. I just checked my code again. I find where the problem is: I didn't claim "n" as "int n" in the function...

It is working now. Thank you~~~

> **karlson said:**
> First off use <code> tags

Second.  Why not declare function as
```
int printarray(int *array, int n)
```

---

### Post by DaviesX on 2012-05-03
Actually, it works except the omitting of int :)

And except code tag should be used, please don't copy the line number too :mad:

```

#include <iostream>
using namespace std;

int printarray ( int (&array)[4],[COLOR=Red] int[/COLOR] n )    // int can't be omitted ...
{
    cout << "Outputing from printarray func. " << endl;

    for (int i = 0; i < 4; i++)
    {
        cout << array[i] << endl;
    }

    return n;
}

int main()
{
    int b[] = {1, 2, 3, 4};
    int *a;
    a = b;

    cout << printarray ( b, 5 ) << endl;
    return 0;
}

```

---

### Post by echo.zyw on 2012-05-03
Gotcha. Thank you, sir. 

> **DaviesX said:**
> Actually, it works except the omitting of int :)

And except code tag should be used, please don't copy the line number too :mad:

```

#include <iostream>
using namespace std;

int printarray ( int (&array)[4],[COLOR=Red] int[/COLOR] n )    // int can't be omitted ...
{
    cout << "Outputing from printarray func. " << endl;

    for (int i = 0; i < 4; i++)
    {
        cout << array[i] << endl;
    }

    return n;
}

int main()
{
    int b[] = {1, 2, 3, 4};
    int *a;
    a = b;

    cout << printarray ( b, 5 ) << endl;
    return 0;
}

```

---

