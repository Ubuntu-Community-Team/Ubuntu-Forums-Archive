---
title: "C++ file IO exceptions"
date: 2009-08-17
forum: Programming Talk
---

### Post by Volt9000 on 2009-08-17
I come from a C# background and so I was a bit disappointed to find there aren't many "built-in" exceptions in C++, particularly for file IO. So after a bit of digging I found I have out how to handle these exceptions. However, I'm confused about the return value of of the .what() member function.

Here's a sample file:

[php]
#include <iostream>
#include <fstream>

using namespace std;

int main()
{
    char c;
    ifstream file("test.txt", ifstream::in);
    
    file.exceptions(ifstream::eofbit);
    
    try
    {
        file >> c;
        file >> c;
    }
    catch (ifstream::failure f)
    {
        cout << "Failure: " << f.what() << endl;
    }
}
[/php]

If I then create a file called "test.txt" and put one character into it, the catch block will catch the premature EOF but I will get

```

Failure: basic_ios::clear

```

Huh? Clear? I don't understand. Shouldn't what() tell me that ifstream::eofbit has been set?

---

### Post by Volt9000 on 2009-08-18
*bump*
Any help on this?

---

### Post by dwhitney67 on 2009-08-19
Perhaps you can look at the rdstate() of the file stream to determine which error you received.

Here's an (incomplete) example:
```

#include <fstream>
#include <iostream>

using namespace std;

int main()
{
   const char* TEST = "test.txt";

   try
   {
      ifstream file(TEST, ifstream::in);
      file.exceptions(ifstream::eofbit | ifstream::failbit);

      try {
         char c;
         while (file.get(c)) {
            // do something with 'c'
         }
      }
      catch (ifstream::failure& e) {
         if (file.rdstate() & ifstream::eofbit) {
            cout << "EOF reached." << endl;
      }
   }
   catch (ifstream::failure& e) {
      cout << "Error: Failure to open file " << TEST << std::endl;
   }
}

```

From personal experience, it is easier to check the state of the file at each opportunity rather than rely on exception throwing.

The code above code easily have been rewritten as:
```

#include <fstream>
#include <iostream>

using namespace std;

int main()
{
   const char* TEST = "test.txt";

   ifstream file(TEST, ifstream::in);

   if (file) {
      char c;
      while (file.get(c)) {
         // do something with 'c'
      }
      cout << "EOF reached." << endl;
   }
   else {
      cout << "Error: Failure to open file " << TEST << endl;
   }
}

```

---

### Post by Volt9000 on 2009-08-19
Ok, that seems reasonable.

But it still begs the question: when the exception is caught, why is it basic_ios::clear? AFAICT "clear" is a member function of basic_ios, not a variable.

---

### Post by Volt9000 on 2009-08-20
*bump*

---

### Post by dribeas on 2009-08-23
> **Volt9000 said:**
> Ok, that seems reasonable.

But it still begs the question: when the exception is caught, why is it basic_ios::clear? AFAICT "clear" is a member function of basic_ios, not a variable.

The exception is not the text that it contains, but the type of the instance that was thrown. You should not use the result of .what() to determine what exception was thrown, only (and if you care for it) to log the error or show to the user.

Now, the fact is that the standard does not define the error messages that should be returned in each exception. It only says that they 'should' be meaningful and provide information on the condition that triggered the error and should contain the operating system error code if it is available. 

This does not answer your question. It is probably unfortunate from the standard library implementation, but there is not much you can do (besides trying with a different compiler version)

---

### Post by Volt9000 on 2009-08-31
Ok, I understand. Thanks very much!

---

