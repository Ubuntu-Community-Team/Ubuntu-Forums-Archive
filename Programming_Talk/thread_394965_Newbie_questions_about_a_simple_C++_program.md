---
title: "Newbie questions about a simple C++ program"
date: 2007-03-27
forum: Programming Talk
---

### Post by ppl on 2007-03-27
Hi, as a newbie in C++ , I was trying to write a simple exercise program(question 8 ,C 02 in Thinking in C++). Here is my program:

```
//: creat a vector<float> and put 25 float point numbers into it using for loop and display the vector
#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<float> f_vector;
    float number;
    for(int i = 0; i < 5; i++){
	cout << "Pleas input a float point number: ";
	cin >> number;
	f_vector.push_back(number);
    }
    for(int j = 0; j < f_vector.size(); j++) 
	cout << "The number :" << j << " is " << f_vector[j] << endl;
}
```
    


However, the program didn't work as I expect. It works when I input float numbers, but when I input things other than float points numbers, it will output something like this:

> Pleas input a float point number: p
Pleas input a float point number: Pleas input a float point number: Pleas input a float point number: Pleas input a float point number: The number :0 is -
2.96384e-05
The number :1 is -2.96384e-05
The number :2 is -2.96384e-05
The number :3 is -2.96384e-05
The number :4 is -2.96384e-05

As you could see , the program will finish when I input any one character other than 5 float point numbers. Don't understand the reasons of that kind behavior of my program. As I read from Thinking in C++:

"The iostreams operator used with cin is >>. This operator waits for the same kind of input as its argument. For example, if you give it an integer argument, it waits for an integer from the console."

Shouldn't my program wait for a float point number to process, and how comes it finish the for loop when I only input once? How could I avoid that?

And another question I was curious when I writing C++ program is when I write something like :" int intNum;" or "float floatInput;" Is that variable initialize automatically by C++ itself, or it is something you can not depend on, you'd better manually do it by yourself?  

Please help, thanks in advance.

---

### Post by kpatz on 2007-03-27
The program will ask you for 5 floating point numbers, no more, no less, because of the for loop.

To make it accept an arbitrary number of numbers, change the for loop to this:

```
    cout << "Please input a float point number (Ctrl-D to exit): ";
    while (cin >> number) {
        f_vector.push_back(number);
        cout << "Please input another float point number (Ctrl-D to exit): ";
    }
```
This causes the loop to execute for any number of inputted numbers.  Hit Ctrl-D, or enter something other than a number to exit the loop (this causes cin to return false, and the while loop exits).> And another question I was curious when I writing C++ program is when I write something like :" int intNum;" or "float floatInput;" Is that variable initialize automatically by C++ itself, or it is something you can not depend on, you'd better manually do it by yourself?You should initialize it yourself.  If you don't, the initial value is unpredictable.  You can declare and initialize in one step, such as "int intNum = 0;".

---

### Post by hod139 on 2007-03-27
Your problem is that you are not handling the error cases of cin correctly.  If cin cannot handle the input it goes into a fail state, and the bad input is left on the stream until you clear it.

You need to change your cin line to
```

while(!(std::cin >> number))
{
  std::cin.clear();
  std::cin.ignore(std::numeric_limits<streamsize>::max(),'\n');
}

```

This code checks for a failure, if it is a failure it 
1) clears the failure
2) uses cin.ignore to remove the input that caused the failure.  The ignore function is saying, ignore the maximum number of input characters allowed on a stream, or a newline, whichever comes first.

---

### Post by silas_irl on 2007-03-27
Ok here's a solution that should work
```

....
  std::cout << "Please input a float point number: "
  std::cin >> number;

  // Was there illegal input, if so cins fail bit will be set
  if (std::cin.fail())
  {
    std::cin.clear(); //clear the failed bit
    // ignore the input we got
    while (std::cin.peek() != '\n')
      std::cin.ignore();

     // ask for the input again
     std::cout << "Invalid input, please input a float point number: "
     std::cin >> number;
  }

  f_vector.push_back(number);
 ...

```

> And another question I was curious when I writing C++ program is when I write something like :" int intNum;" or "float floatInput;" Is that variable initialize automatically by C++ itself, or it is something you can not depend on, you'd better manually do it by yourself? If it's a global variable then its initialised, however if its a local variable then it's not.  Its always best practice to initialise all variables prior to using them

---

### Post by ppl on 2007-03-27
Thanks guys, really appreciate your input!

But when I tried to plug those solutions into my code, things didn't work out as I expected.  Seems like hod139's code will ignore the first correct input after ignore incorrect input previously, and silas_irl's code looks like a better solution, but have problems's as well ,and looks like it will store the incorrect input anyway. 

I probably did something wrong as well, as I am a little bit in hurry. But things are getting more interesting now. Unfortunately I need go University now, do some VHDL coding and Signal processing problems. I'll come back check the code after school.

---

### Post by hod139 on 2007-03-27
> **ppl said:**
> 
But when I tried to plug those solutions into my code, things didn't work out as I expected.  Seems like hod139's code will ignore the first correct input after ignore incorrect input previously

Strange, works fine for me.  Here is the full code, with an added cout to maybe make it clearer:

```

#include <iostream>
#include <vector>

using namespace std;

int main() {
    vector<float> f_vector;
    float number;
    for(int i = 0; i < 5; i++){
    cout << "Pleas input a float point number: ";
    //cin >> number;
     while(!(std::cin >> number))
     {
       cout << "Illegal input, please input a float point number: ";
       std::cin.clear();
       std::cin.ignore(std::numeric_limits<streamsize>::max(),'\n');
     }
    f_vector.push_back(number);
    }
    for(int j = 0; j < f_vector.size(); j++) 
    cout << "The number :" << j << " is " << f_vector[j] << endl;
}

``````

./a.out 
Pleas input a float point number: 1
Pleas input a float point number: a
Illegal input, please input a float point number: 2
Pleas input a float point number: 3
Pleas input a float point number: a
Illegal input, please input a float point number: b
Illegal input, please input a float point number: c
Illegal input, please input a float point number: d
Illegal input, please input a float point number: 4
Pleas input a float point number: 5
The number :0 is 1
The number :1 is 2
The number :2 is 3
The number :3 is 4
The number :4 is 5

```


Edit:  By the way, you probably should be using double.  There is no reason to use float over double.

---

### Post by ewtesterman@cox.net on 2007-03-27
You may want to read [here]("http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3") for a better explanation of the code above. I would also recommend reading about try catch and throw (however in this instance I don't think they would be of much use)

---

### Post by ppl on 2007-03-28
Hi hod139, the program works now ,thanks again.

thanks ewtesterman for the link, lots of other stuff could be a good reference for later. That program is just an exercise from a book about C++ I am reading.

---

