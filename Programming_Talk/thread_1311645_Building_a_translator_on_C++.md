---
title: "Building a translator on C++"
date: 2009-11-02
forum: Programming Talk
---

### Post by jualin on 2009-11-02
I am beginning to write a translator program which will translate a string of text found on a file using parallel arrays. The language to translate is pig Latin. I created a text file to use as a pig latin to English dictionary. I didn't want to use any two dimension arrays; I want to keep the arrays in one dimension. Basically I want to read a text file written in PigLatin and using the dictionary I created I want to output the translation to English on the command line.

My pseudo-code idea is:

Open the dictionary text file.

Ask the user for the name of the text file written in PigLatin that he/she wants to translate to English

Searching each word on the user's text file and comparing to the Dictionary to then translate the word accordingly. Keep on going until there are no more words to translate.

Show the translated words on the command line screen.

I was thinking on using a parallel arrays, one containing the english translated words and another one containing the pig latin words.

Any ideas on how to get started with this.

Thank you.

---

### Post by MadCow108 on 2009-11-02
consider a map for one way translation:
[http://www.cplusplus.com/reference/stl/map/](http://www.cplusplus.com/reference/stl/map/)

using this and streams its about a ~10 lines program
(of course this approach of translating will not give very good results)

---

### Post by liquidbee on 2009-11-02
Not sure if reading the file over and over again for each word would be the best way.

```
word1:translation1
word2:translation2
```

Read the whole file into a two dimensional vector and you are pretty much ready to go - since the word1/word2 will be keys, take the word and get it's value ( translation ).

---

### Post by jualin on 2009-11-02
> **liquidbee said:**
> Not sure if reading the file over and over again for each word would be the best way.

```
word1:translation1
word2:translation2
```

Read the whole file into a two dimensional vector and you are pretty much ready to go - since the word1/word2 will be keys, take the word and get it's value ( translation ).

Can I use parallel arrays instead (in one dimension)? I know it sounds more complicated but I would like to learn one dimension first.

Let's say that the dictionary has a format similar to this:

> ABSOLUTEHAY             ABSOLUTE
ACEDPLAY                PLACED
ACESFAY                 FACES
ADMITHAY                ADMIT
ADVANCEDHAY             ADVANCED

Thus the Pig Latin words are in alphabetical order with their corresponding English translation.

How can I declare this type of array. Should I use a while loop or a for loop.
Thank you.

---

### Post by A_Fiachra on 2009-11-02
Parallel arrays are almost always a mistake in a language that supports associative arrays (aka maps, dictionaries)

---

### Post by jualin on 2009-11-02
> **A_Fiachra said:**
> Parallel arrays are almost always a mistake in a language that supports associative arrays (aka maps, dictionaries)

Many people have told me that it is easier to do another way but it is just a matter of learning parallel arrays. I want to learn it the hard way first to then learn the easy way. Do you know how to use the parallel array? Thank you.

---

### Post by terry_a_g on 2009-11-02
You might try a less ambitious project if all you're trying to learn is parallel arrays.  You're looking at file IO, string comparison, copying memory, and dynamic memory reallocation in addition to parallel arrays with this project.  These can be tricky for someone just starting out.

Here's a contrived example of parallel arrays if you're just trying to figure out how they work.  It doesn't do any error checking.

```
#include <iostream>
using namespace std;

int main(int argc, char *argv[])
{
    int numbers[10] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    const char * words[10] = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten"};
    int input;

   cout << "Enter a number between 1 and 10: ";
   cin >> input;

   for(int i = 0; i < 10; ++i) {
        if(numbers[i] == input) {
            cout  << "You entered " << words[i]  << endl;
            break;
        }
    }
    return 0;
}
```

---

