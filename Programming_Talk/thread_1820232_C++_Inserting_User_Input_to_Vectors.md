---
title: "C++: Inserting User Input to Vectors"
date: 2011-08-07
forum: Programming Talk
---

### Post by benedictusk on 2011-08-07
Hi.

I started learning C++ about a month ago, and I recently ran into a small problem concerning vectors. I found a workaround, but it's not as elegant as I would like.

What I'm trying to do is have the user input an integer that will be inserted into a vector.

Here is my code:
```

#include<iostream>
#include<vector>

using namespace std;

int main()
{
    vector <int> integers;
    
    int tempInt;

    cout << "Input an integer to put into a vector." << endl;
    cin >> tempInt;
    integers.push_back(tempInt);

    vector<int>::iterator elementLocation = integers.begin();
    while(elementLocation != integers.end())
    {
        cout << *elementLocation << endl;
        
        elementLocation ++;
    }

    return 0;
}

```This code is just practice so I can get better with vectors, which will be a key part of the code of a more practical program I am writing. All this does is get an int from the user and display it using an iterator. 
I was wondering if there's a nicer way to get user input into the vector; preferably something that only requires one line of code, and can work without temporary variables. I was thinking something along the lines of integers.push_back(cin), but this, as well as other variations I have tried, gives me lots of errors.

Thanks for the help!

---

### Post by GeneralZod on 2011-08-07
Check out e.g.

[http://www.java2s.com/Code/Cpp/Data-Structure/Useistreamiteratorwiththecopyalgorithm.htm](http://www.java2s.com/Code/Cpp/Data-Structure/Useistreamiteratorwiththecopyalgorithm.htm)

although be aware that terse code can be cryptic code (and also this example will lead to undefined behaviour if the user enters more than 5 numbers! :o)

---

### Post by karlson on 2011-08-07
> **benedictusk said:**
> Hi.

I started learning C++ about a month ago, and I recently ran into a small problem concerning vectors. I found a workaround, but it's not as elegant as I would like.

What I'm trying to do is have the user input an integer that will be inserted into a vector.

[snipped]
 
I was wondering if there's a nicer way to get user input into the vector; preferably something that only requires one line of code, and can work without temporary variables. I was thinking something along the lines of integers.push_back(cin), but this, as well as other variations I have tried, gives me lots of errors.

Thanks for the help!

Just as an advice:

Unless you are sure of who will be reading your code you should make it as readable as possible.  The fact that you write 3 lines of code is irrelevant since a compiler optimizer would probably give you the simplest and fastest solution possible.  Also, if you're just learning vectors and as I gather C++ in general don't try to combine statements...

If you want a single line implementation you should consider that whatever argument you pass to a function should be constructable into the class required to be passed to the function.  In this case the push_back() function takes an integer, which means that you should be able to construct an integer from std::istream&

---

### Post by exohuman on 2011-08-07
I think you may run into problems with that approach. It may be better to assume the input from the user is a string and then get the int from the string after you checked to see if the input is a number and not some other character. Otherwise, you'll run into problems with type and possibly the newline character.

---

### Post by benedictusk on 2011-08-07
Thanks for the replies!

Honestly though, I'm not trying to get from three lines to one because I think it will be more efficient, but because if I'm going to be using vectors often, I don't want to have to spend time writing more code each time if there's a shorter way to do it. I guess I wrongly assumed that there was a way to use cin as a variable and use that as a parameter for push_back(). To me, push_back(cin) is more readable than something with temporary variables whose purposes might be difficult to see, but if there's no legal statement similar to that, I'll just keep doing what I've been doing until now.
@exohuman: Actually, in the bigger program I'm writing, I will be using a char vector. This int vector is just to get myself used to the syntax and manipulation of vectors in general.

---

### Post by cgroza on 2011-08-08
According to the documentation: [http://www.cplusplus.com/reference/iostream/istream/get/](http://www.cplusplus.com/reference/iostream/istream/get/)

You should be able to use cin.get() to achieve what you asked for in the original post.
```

your_int_vector.push_back(cin.get());

```I am not aware about the draw backs and reliability so please do some research about it first.

---

### Post by dwhitney67 on 2011-08-08
> **cgroza said:**
> I am not aware about the draw backs and reliability so please do some research about it first.
One major drawback is that the get() function (w/ no params) returns only one character at a time, and the ASCII value (as int) of such.  Thus if the user enters 10<enter>, only the first character '1', represented by int 49, is returned.  A subsequent call to get() would return 48 (for the '0'), and finally 10 for the newline.  This is not what the OP requires.

---

### Post by psusi on 2011-08-08
It won't be more efficient; the compiler does a very good job generating optimized assembly.

---

### Post by unknownPoster on 2011-08-08
With a one-liner, you also don't have a chance to "sanitize" input if you need to do so, not sure if that's important in your case.

---

### Post by dwhitney67 on 2011-08-08
> **unknownPoster said:**
> With a one-liner, you also don't have a chance to "sanitize" input if you need to do so, not sure if that's important in your case.

It should always be important.

Here's my cheat with inserting an inputed value into a vector using a "one liner":
```

#include <iostream>
#include <limits>

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T    input;
   bool done = false;

   while (!done) {
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

#include <vector>
#include <iterator>

int main(void)
{
   std::vector<int> integers;

   for (int i = 0; i < 5; ++i)
   {
      **integers.push_back(getInput<int>("Enter a number: "));**
   }

   std::copy(integers.begin(), integers.end(), std::ostream_iterator<int>(std::cout));
   std::cout << std::endl;
}

```

---

