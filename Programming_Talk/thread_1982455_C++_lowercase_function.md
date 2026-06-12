---
title: "C++ lowercase function"
date: 2012-05-18
forum: Programming Talk
---

### Post by bobman321123 on 2012-05-18
I need a function or a tool or something that would accept string input and convert it to lowercase. 

Any ideas?

```

#include <iostream>
#include <string>
using namespace std;
int main(){
string testing;
cin >> testing;
//How do I make ^this all lowercase regardless of input?
}

```

---

### Post by kingtaurus on 2012-05-18
> **bobman321123 said:**
> I need a function or a tool or something that would accept string input and convert it to lowercase. 

Any ideas?

```

#include <iostream>
#include <string>
using namespace std;
int main(){
string testing;
cin >> testing;
//How do I make ^this all lowercase regardless of input?
}

```

Within the C standard library there is a function called:
```

tolower

```

Its probably best if you investigate these options and come up with a solution for yourself.

Cheers

---

### Post by MiXor on 2012-05-18
Would that sort of thing do the trick?

[http://www.cplusplus.com/reference/clibrary/cctype/tolower/](http://www.cplusplus.com/reference/clibrary/cctype/tolower/)

---

### Post by bobman321123 on 2012-05-18
> **MiXor said:**
> Would that sort of thing do the trick?

[http://www.cplusplus.com/reference/clibrary/cctype/tolower/](http://www.cplusplus.com/reference/clibrary/cctype/tolower/)

I tried that, but I couldn't make it work, it might only work for C, not C++.

---

### Post by MiXor on 2012-05-18
Apologies! :)

[http://www.cplusplus.com/reference/std/locale/ctype/](http://www.cplusplus.com/reference/std/locale/ctype/)
This looks interesting, not sure if it's any help to you...

---

### Post by dwhitney67 on 2012-05-19
> **bobman321123 said:**
> I tried that, but I couldn't make it work, it might only work for C, not C++.

You tried tolower(), and it doesn't work for C++?  I have doubts that you tried anything.

Why don't you show your coding attempt of using tolower().

---

### Post by roelforg on 2012-05-19
```

#include <iostream>
#include <string>

using namespace std;

int main()
{
string a="HellO WORLD!";
for (unsigned i = 0; i < a.size(); i++)
{
 char b=a[i];
 if ((b>='A')&&(b<='Z'))
  a[i]=b-'A'+'a';
}
cout << a << endl;
}

```
Isn't so hard, is it?

---

### Post by bobman321123 on 2012-05-19
> **roelforg said:**
> ```

#include <iostream>
#include <string>

using namespace std;

int main()
{
string a="HellO WORLD!";
for (unsigned i = 0; i < a.size(); i++)
{
 char b=a[i];
 if ((b>='A')&&(b<='Z'))
  a[i]=b-'A'+'a';
}
cout << a << endl;
}

```Isn't so hard, is it?
But do I have to go into the chars to convert it?
There's something in Java where you can do: 
```

.toLowerCase()

```
to convert entire strings to lowercase.

If I have to go into the chars, I'll do that, but I'm just curious if there's a string level way to do that.

---

### Post by dwhitney67 on 2012-05-19
> **bobman321123 said:**
> 
... but I'm just curious if there's a string level way to do that.

No there is not.  The methods associated with std::string are described here:  [http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

As for an example using tolower(), here it is:
```

#include <string>
#include <iostream>
#include <algorithm>    // for std::transform
#include <ctype.h>      // for tolower

int main()
{
    std::string input;

    std::cout << "Enter a phrase: ";
    std::cin  >> input;

    std::transform(input.begin(), input.end(), input.begin(), tolower);

    std::cout << "Input is: " << input << std::endl;
}

```

---

### Post by bobman321123 on 2012-05-20
> **dwhitney67 said:**
> No there is not.  The methods associated with std::string are described here:  [http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)

As for an example using tolower(), here it is:
```

#include <string>
#include <iostream>
#include <algorithm>    // for std::transform
#include <ctype.h>      // for tolower

int main()
{
    std::string input;

    std::cout << "Enter a phrase: ";
    std::cin  >> input;

    std::transform(input.begin(), input.end(), input.begin(), tolower);

    std::cout << "Input is: " << input << std::endl;
}

```
Your answer reminds me of a question I had.
Twofold question actually...

First of all, what exactly is the function of a namespace?

Secondly, does std::cin have any advantage over simply adding "using namespace std;" to the beginning?

---

### Post by dwhitney67 on 2012-05-20
> **bobman321123 said:**
> Your answer reminds me of a question I had.
Twofold question actually...

First of all, what exactly is the function of a namespace?

Secondly, does std::cin have any advantage over simply adding "using namespace std;" to the beginning?

When you start to work with larger projects, where there are many namespaces, it saves a headache or two when attempting to discern where a function is located at.  By using the namespace scope operator when needed, it also frees your mind from having to worry, if by chance, you name a function with a similar name that appears in the std namespace.

For a trivial application, adding "using namespace std;" saves for a lot of typing -- so I supposed one could argue that it is advantageous.  For me, however, I didn't lose a drop of sweat with the extra typing.


P.S.  A C++ namespace is synonymous with a Java package.  Both are used to collect related classes and functions in a "box".

---

### Post by highspider on 2012-05-20
I know its like beating a dead horse because its been answered; but, I think this way is the easiest for a beginner because it uses the the lolower() function.

```

#include <iostream> 
#include <string> 
 
using std::cin; 
using std::cout; 
using std::string; 
 
int main(){ 
 
    cout << "Enter a String: "; 
    string testing; 
    cin >> testing; 
 
[COLOR=SeaGreen]    //loop through each character of the string until '\0' the end of  
    //of the string and make it lower-case [/COLOR]
    for(int i = 0; testing[i] != '\0'; i++){ 
        testing[i] = tolower(testing[i]); 
    } 
 
    cout << testing; 
 
    return 0; 
}

```TEST with g++ (gcc version 4.4.5)
```

Enter a String:  ThIsISA-12341234-TEST-! 
thisisa-12341234-test-!

```

---

### Post by markbl on 2012-05-20
C string, in place conversion:
```

#include <ctype.h>

// Function to convert argument string to lower case
char *strlower(char *string)
{
    char *p = string;

    if (p) {
        while (*p) {
            *p = tolower(*p);
            p++;
        }
    }

    return string;
}

```

---

### Post by dwhitney67 on 2012-05-21
> **highspider said:**
> ... I think this way is the easiest for a beginner because it uses the the lolower() function.

That's the same function I specified as the unary operator when I used std::transform().  :-)

---

### Post by Zugzwang on 2012-05-21
Actually, one *could* present to the OP a solution that uses Boost's function to convert a std::string to lowercase, which in a sense would be simpler than every solution so far, but I don't want to spoil dwhitney67's teaching concept here.

---

### Post by dwhitney67 on 2012-05-21
> **Zugzwang said:**
> Actually, one *could* present to the OP a solution that uses Boost's function to convert a std::string to lowercase, which in a sense would be simpler than every solution so far, but I don't want to spoil dwhitney67's teaching concept here.

Not all systems have Boost, including my work system.  But you are correct... one should offer an example...

```

#include <boost/algorithm/string/case_conv.hpp>
#include <string>
#include <iostream>

int main()
{
    std::string str = "AbCdEFghijKLMNOPqrstuVWxyZ";

    boost::algorithm::to_lower(str);

    std::cout << str << std::endl;
}

```

---

### Post by bobman321123 on 2012-05-21
Thanks for all the help guys, it's proving really educational. :)

dwhitney67, how would I do that under namespade std without adding "std::" to the beginning of every command?

That or, how would I tell how to apply "std::"?

---

### Post by AnotherTest on 2012-05-21
Sorry, accidental double post. Please remove.

---

### Post by AnotherTest on 2012-05-21
> **bobman321123 said:**
> Thanks for all the help guys, it's proving really educational. :)
 
dwhitney67, how would I do that under namespade std without adding "std::" to the beginning of every command?
 
That or, how would I tell how to apply "std::"?
You could use using declarations for notational convenience, such as.
 
using std::string;
 
The above will allow use of string withough explicitly prefixing it with the std namespace.
 
If you did not import a name from a namespace, you must prefix it with the name of the given namespace followed by the scope operator(::). Thus, every variable, function, class, struct, enum, union... declared in std must be prefixed with std. Notice how you do not have to prefix member function names. Nor do you have to prefix operators(thanks to a hack).

---

### Post by bobman321123 on 2012-05-21
> **AnotherTest said:**
> You could use using declarations for notational convenience, such as.
 
using std::string;
 
The above will allow use of string withough explicitly prefixing it with the std namespace.
 
If you did not import a name from a namespace, you must prefix it with the name of the given namespace followed by the scope operator(::). Thus, every variable, function, class, struct, enum, union... declared in std must be prefixed with std. Notice how you do not have to prefix member function names. Nor do you have to prefix operators(thanks to a hack).

Are there namespaces other than std?

---

### Post by dwhitney67 on 2012-05-21
> **bobman321123 said:**
> Are there namespaces other than std?

Sure.  For example, boost is a namespace, and within it are other namespaces, such as algorithm.  That's why earlier I posted code that had this statement:
```

**boost::algorithm::**to_lower(str);

```
The code in bold text is referencing the namespace where to_lower() exists.

You can also define your own namespace; for example:
```

namespace foo
{
    void function() {}
}

int main()
{
    foo::function();
}

```

---

### Post by bobman321123 on 2012-05-21
> **dwhitney67 said:**
> Sure.  For example, boost is a namespace, and within it are other namespaces, such as algorithm.  That's why earlier I posted code that had this statement:
```

**boost::algorithm::**to_lower(str);

```The code in bold text is referencing the namespace where to_lower() exists.

You can also define your own namespace; for example:
```

namespace foo
{
    void function() {}
}

int main()
{
    foo::function();
}

```
Ohhhhhhhhhhhhhhhhhh!
So a namespace is just a subsection of C(++) that has a group of usable commands in it?

Like, "cin" would be defined in "namespace std" as to how it worked?

---

### Post by dwhitney67 on 2012-05-21
> **bobman321123 said:**
> Ohhhhhhhhhhhhhhhhhh!
So a namespace is just a subsection of C(++) that has a group of usable commands in it?

Like, "cin" would be defined in "namespace std" as to how it worked?

You mentioned earlier that you come from a Java background; I also mentioned earlier that C++ namespaces are comparable to Java packages.

PS.  If you had to translate Java to C++, something like this would be the result:

In Java:
```

package foo;

public class FooBar
{
    public static void function()
    {
    }
}

```

In C++:
```

namespace foo
{
    class FooBar
    {
    public:
        static void function()
        {
        }
    };
}

```

---

### Post by bobman321123 on 2012-05-21
> **dwhitney67 said:**
> You mentioned earlier that you come from a Java background; I also mentioned earlier that C++ namespaces are comparable to Java packages.

PS.  If you had to translate Java to C++, something like this would be the result:

In Java:
```

package foo;

public class FooBar
{
    public static void function()
    {
    }
}

```In C++:
```

namespace foo
{
    class FooBar
    {
    public:
        static void function()
        {
        }
    };
}

```

:P My "Java Background" was a computer science course in Java.
So yes, it laid the foundation of my programming knowledge, but I didn't get quite that far in it. 
I got to the point of resizable arrays.

---

