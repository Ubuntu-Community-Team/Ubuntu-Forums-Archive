---
title: "Array of char problem. c++"
date: 2013-04-01
forum: Programming Talk
---

### Post by hatsoff on 2013-04-01
I'm wondering why i'm not allowed to declare and initialize array of char with alphabets?
This is code for vegenere cipher.

```
#include <stdio>  
#include <string>
#include <ctype>
#include <iostream>
using namespace std;

int main()
{
    char predefine[5] = {`a`,`b`,`c`,`d`}; //predefine array
    string plaintext;
    string key;
    cout <<"enter plaintext"; //taking input
    cin >> plaintext;
    cout <<"enter key"; 
    cin >> key;
    for(int i = 0; i < strlen(plaintext.c_str()) ; i++) //running loop
    {
            char character = plaintext[i] ; // each time a key takeout &store inna var
            cout << character << endl;
            char keytake = key[i];   //each time a key takeout & store inna var
            cout << keytake << endl ;
            int wrapearound = strlen(key.c_str()); //store string length inna var 
            if wrapearound == strlen(key.c_str()); //if string length is== string length
            {
                          keytake = key[0]  ; //reinitialize
            }
            char pdf = predefine[i] ;//takeout from array and store in var.pdf
            char pdf2 = predefine[i] ;
            if(pdf == keytake && pdf2 == character)//compare character  
            {
                             int answer = pdf + pdf2 % 26; //var.answer will have position of
                             switch answer                           //cipher wewill determine 
                             case:0                                 //and cout ;
                             cout << "a";
                             break;
                             case:1
                             cout <<"b";
                             break;
                             ........ //for 25 times for each character
                             
            }
    }
}


```
 getting these error:
 stray '`' in program 
`b' undeclared (first use this function) & so on

---

### Post by spjackson on 2013-04-01
char constants are delimited by a single quote character, not backticks.
```

    char predefine[5] = {'a','b','c','d'}; //predefine array

```

---

### Post by r-senior on 2013-04-01
```
char predefine[5] = {`a`,`b`,`c`,`d`}; //predefine array
```

Are these backticks (`)? They should be single quotes (').

---

### Post by hatsoff on 2013-04-02
you are right!! hehehe
 now getting single error:

expected `(' before "wrapearound"

and please do tell me how i think solution of problem fair ,good ,bad..:)
how i improve my style? I want to be a world famous programmer:P?

```

#include <string>
#include <iostream>
using namespace std;

int main()
{
    char predefine[26] = {'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'}; //predefine array
    string plaintext;
    string key;
    cout <<"enter plaintext"; //taking input
    cin >> plaintext;
    cout <<"enter key"; 
    cin >> key;
    for(int i = 0; i < strlen(plaintext.c_str()) ; i++) //running loop
    {
            char character = plaintext[i] ; // each time a key takeout &store inna var
            cout << character << endl;
            char keytake = key[i];   //each time a key takeout & store inna var
            cout << keytake << endl ;
            int wrapearound = strlen(key.c_str()); //store string length inna var 
            if wrapearound == strlen(key.c_str()); //if string length is== string length
            {
                          keytake = key[0]  ; //reinitialize
            }
            char pdf = predefine[i] ;//takeout from array and store in var.pdf
            char pdf2 = predefine[i] ;
            if(pdf == keytake && pdf2 == character)//compare character  
            {
                             int answer = pdf + pdf2 % 26; //var.answer will have position of
                             switch (answer)                           //cipher wewill determine 
                             {
                             case 0:                                 //and cout ;
                             cout << "a";
                             break;
                             case 1:
                             cout <<"b";
                             break;
                             case 2:
                                  cout << "c";
                             case 3:
                                  cout << "d";
                             case 4:
                                  cout << "e";
                             case 5:
                                  cout << "f";
                             case 6:
                                  cout << "g";
                             case 7:
                                  cout << "h";
                             case 8:
                                  cout << "i";
                             case 9:
                                  cout << "j";
                             case 10:
                                  cout << "k";
                             case 11:
                                  cout << "l";
                             case 12:
                                  cout << "m";
                             case 13:
                                  cout << "n";
                             case 14:
                                  cout << "o";
                             case 15:
                                  cout << "p";
                             case 16:
                                  cout << "q";
                             case 17:
                                  cout << "r";
                             case 18:
                                  cout << "s";
                             case 19:
                                  cout << "t";
                             case 20:
                                  cout << "u";
                             case 21:
                                  cout << "v";
                             case 22:
                                  cout << "w";
                             case 23:
                                  cout << "x";
                             case 24:
                                  cout << "y";
                             case 25:
                                  cout << "z";
                             }
            }
    }
    system("PAUSE");
    return 0 ;
}

```

---

### Post by r-senior on 2013-04-02
> **hatsoff said:**
> now getting single error: expected `(' before "wrapearound"
You are missing brackets around the condition of this if statement:

```
if wrapearound == strlen(key.c_str()); //if string length is== string length
```

> and please do tell me how i think solution of problem fair ,good ,bad..:)
The switch statement and declaration of the array is ugly. If you have to type lots of repetitive things in code, it can be a sign that you are missing a more elegant solution. (You are, but we all have to start somewhere).

> how i improve my style? I want to be a world famous programmer:P?
Learn to use the features and style of the language. This looks like a C++ program written by a C programmer. It's the sort of C++ that I would write and I'm not even famous in my own house. You should aim higher.

---

### Post by GeneralZod on 2013-04-02
I've added some obvious corrections,  but a lot of the code is too bewildering to fix, in which case I've left comments - they're meant to be friendly criticism, so please don't take offense :) // +++ is something I've changed; // ### is a general comment.  A lot of the changes are to do with naming, which is pretty difficult even if you're a native English speaker :)

```

#include <string>
#include <iostream>
using namespace std;

// +++ Changed all occurrences of strlen(<string>.c_str()) to <string>.length() - this is C++, not C!
int main()
{
    // ### I don't know what "predefine" is or what it represents - the comment does not help at all, at is just tells me 
    // ### the same as the code! Give it a better name, and add an explanatory comment.
    // ### Note that "predefine" is a verb, whereas the thing it is describing looks to be a noun.
    // +++ Made it const - I can't see where it is altered, so give a clue that it is supposed to be unchanging, and get the compiler to enforce this.
    const char predefine[26] = {'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'}; //predefine array 
    string plaintext;

    cout <<"enter plaintext"; //taking input
    cin >> plaintext;
    // +++ Shifted declaration of "key" down - try to reduce the scope of variables as much as you can i.e. don't declare until just before it is used.
    // ### "key" is a non-descriptive name - it's possibly even misleading, as "key" seems to be a string rather than (as I would expect from the name) a char.
    // ### if this is a *cipher* key instead of a key on your keyboard, then call it cipherKey or something.
    string key; 
    cout <<"enter key"; 
    cin >> key;
    for(int i = 0; i < plaintext.length() ; i++) //running loop
    {
            // +++ Made const.
            // ### "character" is very generic.  "plainTextChar", perhaps? This is a matter of taste.
            // +++ Changed "inna" to "in a" variable throughout, although these comments are useless and just make things messy.
            // +++ Unless this is homework and you have been told to comment each line, remove them.
            const char character = plaintext[i] ; // each time a key takeout &store in a var
            cout << character << endl;
            // +++ Made const.
            // ### I have no idea what "keytake" is supposed to represent.
            // ### Also, this is a bug - it assumes that "key" is at least as long as "plaintext", but there is nothing that enforces this.
            const char keytake = key[i];   //each time a key takeout & store in a var
            cout << keytake << endl ;
            // +++ Changed "wrapearound" to "wraparound", although I'd prefer "wrapAround". Made it const.
            // ### I have no idea what wraparound represents - it sounds like a boolean, but is an int(?)
            const int wraparound = key.length(); //store string length in a var 
            // +++ Added brackets around the conditional.
            // ### It's impossible for this condition to ever be false, so I don't know why it is here.  The comment does not help and just makes me more confused :p
            if (wraparound == key.length()); //if string length is== string length
            {
                          // ### Why are we re-initializing?
                          keytake = key[0]  ; //reinitialize
            }
            // ### pdf is always pdf2 - why two variables?
            // ### Also, bad naming - I have no idea what the represent, and was wondering why you were using Portable Document Formats ;)
            // +++ Made them const regardless.
            const char pdf = predefine[i] ;//takeout from array and store in var.pdf
            const char pdf2 = predefine[i] ;
            // ### What is going on here? "compare character" does not help me! Again, using two different vars with the same value.
            if(pdf == keytake && pdf2 == character)//compare character  
            {
                             // ### "answer" is a bad name - I didn't ask a question! From the comment, it sounds like
                             // ### "cipherPos" or something would be a better name, in which case rename it to that and remove the comment.
                             // ###  Describe what the algorithm is doing, here.
                             // ### What is the significance of "26"? Why are we adding things together and taking the answer modulo it?
                             // ### Magic numbers in general are undesirable as they tell me nothing and are a pain to update if the number
                             // ### needs to change.  If "26" is supposed to be the length of "predefine", then define it as a constant with a sensible name, right next to
                             // ### predefine.
                             // +++ Made const regardless.
                             int answer = pdf + pdf2 % 26; //var.answer will have position of
                                                        //cipher wewill determine
                            // +++ Replaced switch statement with something more compact.
                            const char sensibleNameForThisIDoNotKnowWhatItIs = 'a' + answer;
                            cout << sensibleNameForThisIDoNotKnowWhatItIs;
                             
            }
    }
    // +++ system("PAUSE") is not portable.
    system("PAUSE");
    return 0 ;
}

```

---

### Post by hatsoff on 2013-04-03
> they're meant to be friendly criticism, so please don't take offense
Oh no no brother you are welcome!

> / +++ Changed all occurrences of strlen(<string>.c_str()) to <string>.length() - this is C++, not C!
> don't declare until just before it is used.
> 
// +++ Replaced switch statement with something more compact.


got it!
> I don't know what "predefine" is or what it represents - the comment does not help at all, at is just tells me
Actually er just imagine you have array of and you are comparing given input with array when you find that letter note down its position..(i dont know to which extend i'm successful).
> 
// ### It's impossible for this condition to ever be false, so I don't know why it is here.  The comment does not help and just makes me more confused :p

it works like this get plain text get cipher key match position of plain text with cipher text if cipher text 
come to the end loop it again (i'm not sure to which extend i'm successful)
> 
/ ### pdf is always pdf2 - why two variables?
 
it goes like this position of a character from "predefine array" for each plain text letter and cipher text
add them % 26 and you will get the position of encode letter. :)
hope it make sense!
> 
sensibleNameForThisIDoNotKnowWhatItIs

:) i have been using names even "hahaha" :)

---

