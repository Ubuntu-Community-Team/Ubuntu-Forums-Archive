---
title: "My First Program..."
date: 2009-02-25
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-25
This is the first program I wrote in C++ with no outside help from anyone except I did have to go back and look at the stringstream lesson...

```


#include <iostream>				// Leo M. Dragonheart...
#include <string>				// Tue 24 Feb 2009 11:32:40 PM CST...
#include <sstream>				// My very 1st unassisted working program...!
using namespace std;

int main()
{
    string mystr;
    bool ispasscode=false;
    int passcode;

    while (!ispasscode)
    {
        cout << "Please enter your passcode: ";
        getline (cin,mystr);
        stringstream(mystr) >> passcode;

        if (passcode == 64) {
            ispasscode = true;
            cout << "You have entered the correct passcode: Have a nice day! " << endl;
        }
        else {
            cout << "This is not your passcode!...Please try again! " << endl;
        }
    }
    cin.get();
    return 0;
}
  

```

---

### Post by soltanis on 2009-02-25
I think mine was something similar to yours. It was a C program that just scanned input lines and compared it to this really long string, and would just loop forever until you got the string right. I used to to lock my friend's little sister out of my computer while I was away.

(I could've used slock, but hey, she was more entertained with the letter's appearing on the screen)

---

### Post by shadow_code on 2009-02-25
It wasn't my first. But I remember being excited after making a play button change to pause when it's clicked (in Flash) :P

---

### Post by Zugzwang on 2009-02-25
Dear op, you can use the tool "astyle" to get correct indentation of your code automatically. This way it looks far nicer and easier to read!

If you are using KDevelop, you can also use the built-in code formatter. Some other IDEs have similar tools as well.

```

sudo apt-get install astyle
astyle my_code.cpp

```

---

### Post by Leo Dragonheart on 2009-02-25
> **Zugzwang said:**
> Dear op, you can use the tool "astyle" to get correct indentation of your code automatically. This way it looks far nicer and easier to read!

If you are using KDevelop, you can also use the built-in code formatter. Some other IDEs have similar tools as well.

```

sudo apt-get install astyle
astyle my_code.cpp

```

Thanx for the tip... I used KDevelope Edited in original post...

---

