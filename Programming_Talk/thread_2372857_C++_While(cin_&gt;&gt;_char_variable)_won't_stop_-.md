---
title: "C++: While(cin &gt;&gt; char_variable) won't stop - Help is appreciated"
date: 2017-09-29
forum: Programming Talk
---

### Post by grann.mora on 2017-09-29
Hello to the community. I am posting this hoping that i will finally have my answer and that i will understand what the issue here is. First off, i am not just looking for a solution, but mostly i am trying to understand why i have been having this issue. 
The code i am about to show you is from the famous Stroustup's book "Programming: Principles and Practice using C++". So it should be working. However , it doesn't. 
I have checked my code line by line and it is exactly as the book's code. However, there is some logical error i am unable to understand. 


Please note that my issue is similar to this guys issue:*** ubuntuforums.org/showthread.php?t=1057302***
I read the whole thread and didn't understand or solve my problem. So i decided to make another thread, more appropriate to my issue.


A few words about the code before posting it. The code is from page 177, paragraph 6.3.1 (keep in mind that i have the Greek version of the book, so pages or even paragraphs might differ). The code is supposed to implement a simple computational machine. For example, it should be able to add, subtract, multiply and divide. Here is the code:


```
#include "stdafx.h"
#include "../ProjectVectors/std_lib_facilities.h" //this is the header file created by Stroustup and used throughout the book.


int main()
{
    int lval = 0; //left variable
    int rval;      //right variable
    char op;


    cout << "Please, write a computation with +, - , * or / : " << endl; //e.x. 1+2*3
    cin >> lval;


    if (!cin) error("There is no first value.");


    while (cin>>op) //**here is the problem.**
    {
        cin.clear();
        cin >> rval;
        if (!cin)error("Value Missing.");
        switch (op)
        {
        case '+':
            lval += rval;
            break;
        case '-':
            lval -= rval;
            break;
        case '*':
            lval *= rval;
            break;
        case '/':
            lval /= rval;
            break;
        default:
            cout << "Result is: " << lval << endl;
            keep_window_open();
            return 0;
        }
    }
    error("Wrong Computation");
}

```

_My issue: _

Stroustrup runs this program with input " **1+2*3** " and get's a result of **9 **(which is wrong by the way, but that is not the point). When i run the program, i type "**1+2*3**" (without the quotations), then i hit **ENTER **and nothing happens. Shouldn't the program end? Shouldn't the **SWITCH **go to **DEFAULT **and end the program?

I am a bit confused and i have been trying to understand this for quite sometime. If anyone has any idea, i would be grateful. 

Be well :D

---

### Post by spjackson on 2017-09-30
I don't have the book so I don't know whether there are any differences between your code and the book. However, I can see that after it has read the 3, cin>>op is hanging waiting for input. In order to reach the default branch of the switch, you need an operator that isn't one of the 4 specified and then you need another rval or it will hang waiting for one. Hence: "1+2*3!4" followed by return does print the result of 9.

---

### Post by grann.mora on 2017-10-02
@spjackson
I see. When I type in 1+2*3, I press enter. Isn't the character '\0' enough to enter the DEFAULT and exit the while loop?
Could you please elaborate a little more? Why should I add '!' and '4' and not just ENTER or just '!' ?
Thank you for your answer.

EDIT:
I run the program again with '**1+2*3!4**' as input. It runs fine. Could you explain why the '**!4**' stops the while loop, please? 
Thanks!

---

### Post by norobro on 2017-10-02
std::cin ignores preceding whitespace. Give this a read: [http://www.cplusplus.com/reference/ios/skipws/?kw=skipws](http://www.cplusplus.com/reference/ios/skipws/?kw=skipws)

"cin >> op" is expecting a char so you can enter anything that is not a digit, because a digit will be read by the previous cin (cin >> rval) or an operator processed by the switch statement. After processing the char execution continues to "cin >> rval" so it is necessary to enter an int in order to continue to the switch statement.

---

### Post by grann.mora on 2017-10-03
@norobro
I think I understand. So, '**1**' is grabbed by the first '  cin >> lval  ',  then '**+**', is grabbed by the '**cin>>op**', and so on. 
So, when 3 is grabbed by the last '**cin>>rval**', then there is nothing for  '**cin>>op**' to grab. I type in '** !' ** in order for the cin >> op to take it and exit the loop. I also add the number 4 so that i don't get an error. 

I think i understand, thanks to your explanations guys. 
One last thing. If i want to run it and END when i type ENTER, what should i do? I have a couple of ideas but i am interested to read what you have to say!

Thanks for your time, it was very helpful.

---

### Post by norobro on 2017-10-03
You could use std::stringstream. Not sure the error checking in the following will catch everything though.```
#include <string>
#include <sstream>
#include <iostream>

int main () {
    char op;
    int lval = 0;
    int rval;
    std::string str;
    std::cout << "Please, write a computation with +, - , * or / : \n"; //e.x. 1+2*3
    std::getline(std::cin, str);
    std::stringstream ss;
    ss << str;
    ss >> lval;
    if(lval == 0) {
        std::cout << "There is no first value\n";
        return 0;
    }
    while(!ss.eof()) {
        ss >> op;
        ss >> rval;
        if(rval == 0) {
            std::cout << "Value Missing\n";
            return 0;
        }
        switch (op) {
                case '+':
                    lval += rval;
                    break;
                case '-':
                    lval -= rval;
                    break;
                case '*':
                    lval *= rval;
                    break;
                case '/':
                    lval /= rval;
                    break;
                default:
                    std::cout << "Invalid Operator\n";
                    return 0;
        }
   }
   std::cout << "result is: " << lval << "\n";
   return 0;
}
```

---

