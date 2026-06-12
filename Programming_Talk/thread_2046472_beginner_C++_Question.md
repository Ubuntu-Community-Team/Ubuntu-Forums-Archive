---
title: "beginner C++ Question"
date: 2012-08-23
forum: Programming Talk
---

### Post by jonathonc on 2012-08-23
I figured instead of registering on another forum, I'd come here and maybe someone can answer my basic question. Right now I am testing my development skills and trying a simple exercise. I am trying to produce a program that will take a user inputed string and convert each individual character to the numeric value of the alphabet (e.g. A=/1/, Z=/26/) 

This is nothing more then a basic string crypter and soon I will program a decrypter. I have got a little bit of it through previous knowledge and looking up some stuff but now I am stuck as to what to do. Here is what I have so far:

```
#include <iostream>
#include <string>
using namespace std;

int main () {
	string uncrypt;
	int num;
	int c;
	cout << "Please enter your word to be crypted: ";
	cin >> uncrypt;
	num = uncrypt.length();
	for(c = 0; (c = num); c++) 
	{
		//Stuff Here
	}
	
	
	}

```

---

### Post by WinterMadness on 2012-08-23
> **jonathonc said:**
> I figured instead of registering on another forum, I'd come here and maybe someone can answer my basic question. Right now I am testing my development skills and trying a simple exercise. I am trying to produce a program that will take a user inputed string and convert each individual character to the numeric value of the alphabet (e.g. A=/1/, Z=/26/) 

This is nothing more then a basic string crypter and soon I will program a decrypter. I have got a little bit of it through previous knowledge and looking up some stuff but now I am stuck as to what to do. Here is what I have so far:

```
#include <iostream>
#include <string>
using namespace std;

int main () {
	string uncrypt;
	int num;
	int c;
	cout << "Please enter your word to be crypted: ";
	cin >> uncrypt;
	num = uncrypt.length();
	for(c = 0; (c = num); c++) 
	{
		//Stuff Here
	}
	
	
	}

```

There are a few easy ways to do this, you can take the letter 'A' and do this with the character data type I believe. But I havent done it in some time and I dont feel like looking up how to do it (I think you just convert it to an integer type), tbh im not even really sure if its c++ that does it or another language...

If you're just starting out, I dont really want to throw type conversions at you and such, so theres the easy intuitive way that works.

Make an array that contains a-z, use the position + 1 to figure out which number it is in the array/alphabet

so if you look up A, youll return 0, add 1, youll get 1. B, 1, +1=2 etc

the method I gave you is only really good if you just want to tinker with c++ as a beginner and just want to get it to work. Im almost certain most languages contain features to do exactly what you are talking about, but im terrible at remembering specific things, and i often rely on documentation if i havent used something in a while :P

---

### Post by DarkAmbient on 2012-08-23
*I've not programmed in C/C++ for a long time now, so could be rather off on the syntax/keywords*

You could make an array that holds the alfabeth. Then just loop through it, then you get the letter + it's numeric value by index of array. Knowing this then perhaps you could work you way forth from there?

```
char alfa[]="abcdefghijklmnopqrstuvwxyz";
 
for (int i=0; i < sizeof(alfa); i++) { // I recall a char is 1 byte, right?
    std::cout << alfa[i] << " = " << (i+1) << std::endl;
}
```

Edit: WinterMadness beat me to it ;)

---

### Post by spjackson on 2012-08-23
Note that this is wrong in two respects.
```
    for(c = 0; (c = num); c++)   
```Try this
```

#include <iostream>
#include <string>
#include <cstdio>
#include <cctype>
//using namespace std;

// encode the character to a 2 digit number
// return empty string if there is no valid conversion
std::string cipher(char uncrypt_character)
{
    std::string result;
    if (isalpha(uncrypt_character))
    {
        int encoded_value = 1 + toupper(uncrypt_character) - 'A';
        char number[3];
        sprintf(number, "%02d", encoded_value);
        result = number;
    }

    return result;
}

int main () {
    std::string uncrypt;
    std::string crypt;

    std::cout << "Please enter your word to be crypted: ";
    std::cin >> uncrypt;
    int num = uncrypt.length();
    for(int c = 0; c < num; c++) 
    {
        std::string this_crypt = cipher(uncrypt[c]);
        if (this_crypt.empty())
        {
            std::cerr << "No idea what to do with '" << uncrypt[c] << "'\n";
        }
        else
        {
            crypt += this_crypt;
        }
    }
    std::cout << crypt << "\n";
}

```Note that H and h both translate to the same thing, i.e. 08. I've used a leading zero, so that there is a difference between M (13) and AC (0103).

---

### Post by jonathonc on 2012-08-23
> **spjackson said:**
> Note that this is wrong in two respects.
```
    for(c = 0; (c = num); c++)   
```Try this
```

#include <iostream>
#include <string>
#include <cstdio>
#include <cctype>
//using namespace std;

// encode the character to a 2 digit number
// return empty string if there is no valid conversion
std::string cypher(char uncrypt_character)
{
    std::string result;
    if (isalpha(uncrypt_character))
    {
        int encoded_value = 1 + toupper(uncrypt_character) - 'A';
        char number[3];
        sprintf(number, "%02d", encoded_value);
        result = number;
    }

    return result;
}

int main () {
    std::string uncrypt;
    std::string crypt;

    std::cout << "Please enter your word to be crypted: ";
    std::cin >> uncrypt;
    int num = uncrypt.length();
    for(int c = 0; c < num; c++) 
    {
        std::string this_crypt = cypher(uncrypt[c]);
        if (this_crypt.empty())
        {
            std::cerr << "No idea what to do with '" << uncrypt[c] << "'\n";
        }
        else
        {
            crypt += this_crypt;
        }
    }
    std::cout << crypt << "\n";
}

```Note that H and h both translate to the same thing, i.e. 08. I've used a leading zero, so that there is a difference between M (13) and AC (0103).

Your code seems to work pretty much perfectly. Now I just have to figure out how it works lol You are using code I have not learned yet.

---

### Post by spjackson on 2012-08-23
> **jonathonc said:**
> Your code seems to work pretty much perfectly. Now I just have to figure out how it works lol You are using code I have not learned yet.
Feel free to ask about anything you don't understand, but it is of course worthwhile trying to understand it yourself first.

---

### Post by jonathonc on 2012-08-23
> **spjackson said:**
> Feel free to ask about anything you don't understand, but it is of course worthwhile trying to understand it yourself first.

Looking up individual functions and the libraries I can do but what I do not understand is how the code before "int main()" works. I thought that the program will always go to main first. I have only been learning C++ for two weeks and before that I was learning very basic programming languages so please excuse me.

---

### Post by DarkAmbient on 2012-08-23
I think that the best would be if you'd wrote this yourself tbh. It's nothing wrong with copy/paste, other than that you don't learn much from it. Do you best to learn by redoing simple as non-simple tutorial until you get a hang of whatever topic the tutorial brings up. Else you will have a really hard time later on with C. I know this from personal experience. Did a lot of copy/paste when I first started out with C ~12 years ago, and it really slows you down.

---

### Post by jonathonc on 2012-08-23
> **DarkAmbient said:**
> I think that the best would be if you'd wrote this yourself tbh. It's nothing wrong with copy/paste, other than that you don't learn much from it. Do you best to learn by redoing simple as non-simple tutorial until you get a hang of whatever topic the tutorial brings up. Else you will have a really hard time later on with C. I know this from personal experience. Did a lot of copy/paste when I first started out with C ~12 years ago.

I'm not trying to copy and paste others' code. What you saw was what I coded and I got stuck. What spjackson posted I did copy and paste so that I may execute the code and then see how it runs. I figure since he just about nailed what I was going for then I could study his code and realize how to do it. I am currently reading a book: Jumping into C++ by Alex Allain but I am trying to separate myself from the book and do a little coding on my own for some better hands on learning.

---

### Post by spjackson on 2012-08-23
> **jonathonc said:**
> Looking up individual functions and the libraries I can do but what I do not understand is how the code before "int main()" works. I thought that the program will always go to main first. I have only been learning C++ for two weeks and before that I was learning very basic programming languages so please excuse me.
A C/C++ program does start executing at main(). The code before main is simply a function which gets called within the for loop. It is pretty similar in nature to the function length() that you already call. The one essential difference is that my function cipher() [apologies for misspelling this as cypher - it's a blind spot of mine], is not part of any class, whereas length() is part of the std::string class.

---

### Post by DarkAmbient on 2012-08-23
Sorry if you took it as I jumped at you, didn't mean it like that. Wanted to point out the importance of understanding everything you use in your code. C is really fun to code with, and once you get a hang of it and can do some cool stuff it gets even better. :)

---

