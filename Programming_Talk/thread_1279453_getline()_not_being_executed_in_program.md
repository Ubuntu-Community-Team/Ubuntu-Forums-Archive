---
title: "getline() not being executed in program"
date: 2009-09-30
forum: Programming Talk
---

### Post by kcode on 2009-09-30
getline is just being ignored in the code! After first input 'yes' is displayed.
```

int main()
{
    int t,i, len=0, k, T;
    string pattern;
    while ( cin >> T ){
        for (i=0; i<T; i++){
            getline( cin, pattern );
            len = pattern.length();
            if ( len == 0 ){
                cout << "Yes" << endl;
                continue;
            }
            if ( len%2 != 0 ){
                cout << "No" << endl;
                continue;
            }
            if ( valid( pattern, len ) ) cout << "Yes" << endl;
            else cout << "No" << endl;
        }
        pattern.clear();
    }
    return 0;
}

```

---

### Post by lisati on 2009-09-30
<never mind, code as posted won't even compile for me.....>

---

### Post by kcode on 2009-09-30
Its is already included.

---

### Post by dwhitney67 on 2009-09-30
```

...
    while ( cin >> T ){
        cin.ignore(100, '\n'); // 100 was arbitrarily chosen.

        ...

```
Read here for more info:  [http://www.cplusplus.com/reference/iostream/istream/ignore/](http://www.cplusplus.com/reference/iostream/istream/ignore/)

---

### Post by kcode on 2009-10-03
> **dwhitney67 said:**
> ```

...
    while ( cin >> T ){
        cin.ignore(100, '\n'); // 100 was arbitrarily chosen.

        ...

```
Read here for more info:  [http://www.cplusplus.com/reference/iostream/istream/ignore/](http://www.cplusplus.com/reference/iostream/istream/ignore/)

I got that but I dont see how it solves my problem. getline() fucntion is skipped for no reason.

Thanks

---

### Post by MadCow108 on 2009-10-03
maybe your logic is wrong
if you input according to what is expected by that code it does not get skipped:
a number followed by N strings followed by newline e.g.
3 fgdf
fg
fg

---

### Post by dwhitney67 on 2009-10-03
> **kcode said:**
> I got that but I dont see how it solves my problem. getline() fucntion is skipped for no reason.

Thanks

It is not skipped; seriously, did you step through your code using the debugger?  Or at a minimum, place trace print out statements in your code?

The getline() _is_ being called, and it is cheerfully gobbling up the newline character that you left behind in the input stream (cin) after you prompted the user to enter a numeric value.

cin will fulfill parsing the int-value that is entered, and will consider the input up to, but not including, the newline that is entered.  So even if you enter 123abc<enter>, cin will return 123.  The rest of the "crap" is still sitting in the input stream.

If you still have your doubts, try this test program, and when running it, enter "123abc<enter>" at the prompt.

```

#include <iostream>
#include <string>

int main()
{
   using std::cout;
   using std::cin;
   using std::endl;

   int         number;
   std::string crap;

   cout << "Enter a number: ";
   cin  >> number;

   getline(cin, crap);

   cout << "Number entered: " << number << endl;
   cout << "Add't crap    : " << crap   << endl;
}

```

Now with respect to the cin.ignore(), it will discard the "crap" by flushing the input stream up to _and_ including the delimiter character specified.  In the example I provided in the earlier post, I specified the '\n' as the delimiter, and I told it to flush up to 100 characters.

P.S.  If when running your app, you do not enter a numeric value when prompted, the while loop will never be traversed because cin will convert its state to a boolean, which will be false.

---

### Post by kcode on 2009-10-03
Thanks, got it.

---

