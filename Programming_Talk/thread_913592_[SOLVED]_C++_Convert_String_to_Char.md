---
title: "[SOLVED] C++ Convert String to Char"
date: 2008-09-07
forum: Programming Talk
---

### Post by DGortze380 on 2008-09-07
Hey all,

Trying to find a way to convert a String of text to an array of Characters.

I've found a number of solutions to convert a string to an array of words, but all of them need a delimiter to break up the tolkens. 

Thanks in advance, back to trying to figure out the logic of this.

-Dan

---

### Post by nrs on 2008-09-07
I'm not sure I understand what you're asking, you mean like a plain C "string"? string.c_str()

---

### Post by nitro_n2o on 2008-09-07
you could just use the c_str() function, which gives you an array of char 

```

string hello = "hello"; 
char *s = hello.c_str();
int i; 
for(i=0; i<hello.length(); i++) 
  printf("%c\n", s[i]);

```

---

### Post by DGortze380 on 2008-09-07
Thanks for the suggestions. I'll look into c_str() because is looks cleaner, but this is what I ended up coming up with.

EDIT: edited the code to fix a declaration issue and make the purpose clearer. See below.

```

#include <iostream>
#include <string>

using namespace std;

int main()
{

string str;
int lengthOfString;

     cout << "Enter a string: " << endl;
     getline ( cin, str);
     lengthOfString=str.length();

char characters[lengthOfString];

     str.copy( characters, lengthOfString );

     cout << "The third character is: " << characters[2] << endl;

return 0;
}


```

---

### Post by rnodal on 2008-09-08
> **DGortze380 said:**
> Thanks for the suggestions. I'll look into c_str() because is looks cleaner, but this is what I ended up coming up with.

```

#include <iostream>
#include <string>

using namespace std;

int main()
{

string str;
int lengthOfString;
char characters[lengthOfString];

getline ( cin, str);
lengthOfString=str.length();
str.copy( characters, lengthOfString );

return 0;
}


```

Are you sure that works? I have not tested it but if I *remember* well when you declare an array the compiler needs to know the size of the array. And from your code lengthOfString is not initialized to anything. Am I missing something?

-r

---

### Post by Sneaky07 on 2008-09-08
I agree with rnodal.  You must initialize your array with either a global constant or directly i.e. 
```
lengthOfString [200];
```

Also I'm not sure about this syntax:
```
lengthOfString=str.length();
```
I'm not sure what your declaring here but just a reminder that you can't just make an array equal something else.  You have to put it in a loop so every element of the array equals something else.

---

### Post by DGortze380 on 2008-09-08
> **rnodal said:**
> Are you sure that works? I have not tested it but if I *remember* well when you declare an array the compiler needs to know the size of the array. And from your code lengthOfString is not initialized to anything. Am I missing something?

-r

EDIT: See original post for complete corrected code.

my mistake, you're right. I cut out a lot of text and cout commands, things got moved around, it should look like this. Yes it does definitely work.

```

string str;         //holds a string
int lengthOfString; //hold the number of characters in the string

getline ( cin, str);  //read in the string
lengthOfString=str.length();  //find the number of characters in the string and save it in length of string
char characters[lengthOfString];  //initialize array 
str.copy( characters, lengthOfString ); //fills array in order with characters from the string

return 0;

```

---

### Post by DGortze380 on 2008-09-08
> **Sneaky07 said:**
> I agree with rnodal.  You must initialize your array with either a global constant or directly i.e. 
```
lengthOfString [200];
```

Also I'm not sure about this syntax:
```
lengthOfString=str.length();
```
I'm not sure what your declaring here but just a reminder that you can't just make an array equal something else.  You have to put it in a loop so every element of the array equals something else.

lengthOfString is not an array, it's an integer equal to the number of characters in the string.

---

### Post by rnodal on 2008-09-08
> **DGortze380 said:**
> my mistake, you're right. I cut out a lot of text and cout commands, things got moved around, it should look like this. Yes it does definitely work.

```

string str;
int lengthOfString;

getline ( cin, str);
lengthOfString=str.length();
char characters[lengthOfString];
str.copy( characters, lengthOfString );

return 0;

```

I'm sorry for making you give me an explanation I should have assumed that you just took things out for simplicity. One more time I apologize.

-r

---

### Post by DGortze380 on 2008-09-08
> **rnodal said:**
> I'm sorry for making you give me an explanation I should have assumed that you just took things out for simplicity. One more time I apologize.

-r

Not a problem. The point of posting it is so other people can refer to it. Always go ahead and point out a potential issue.

---

