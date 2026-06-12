---
title: "[SOLVED] cpp"
date: 2008-01-28
forum: Programming Talk
---

### Post by chris200x9 on 2008-01-28
Hi, what is wrong with this :confused::confused::confused:

```


// polandrom.cpp : Defines the entry point for the console application.

//





#include <iostream>

#include <string>

#include <cstdlib>



using namespace std;

int main()

{

    int counter2;

    string word2;

    string word;

    int counter = 0;

    cout << "input a word you think is a pallindrome" << endl;

    cin >> word;

    

    counter2 = word.length();

    counter2 = counter2 - 1;



    while (counter2 != -1 )

    {

        word2[counter] = word[counter2];





       counter++;

counter2--;

    }         

  

    word2[counter] = '\0';

    if ( strcmp(word.c_str(), word2.c_str()) == 0)

    {

        cout << "you got yourself a pallindrome there, buddy"; << endl;



    }



    else

        cout << "no pallindrome for you!"; << endl;





	return 0;

}




```



help it compiled fine in windows but now I am getting an error about both cout statements  in the if/else statement.

---

### Post by aks44 on 2008-01-28
I seriously doubt that it compiled fine in Windows as it is.

Hint: semicolons... ;-)


EDIT: Oh and BTW... you've got a buffer overrun problem here (word2 is not initialized to hold anything) which will probably segfault. Which makes me doubt even more that it worked at all, even on Windows.
Also, strcmp is not C++, better use std::string::operator==().

---

### Post by chris200x9 on 2008-01-28
thanks for the hint, but I am serious it compiled fine.

edit: yea noticed the semicolons I just added the endl and forgot to take out the other semicolons

---

### Post by aks44 on 2008-01-28
> **chris200x9 said:**
> thanks for the hint, but I am serious it compiled fine.

Then I'm sorry to be so blunt, but the compiler you were using on Windows is plain crap. The code you posted is *not* compilable by any means, operator<<() needs to have a left-handside operand as well as a right-handside one.


EDIT:
> **chris200x9 said:**
> edit: yea noticed the semicolons I just added the endl and forgot to take out the other semicolons
Ok, that explains everything. :)

---

