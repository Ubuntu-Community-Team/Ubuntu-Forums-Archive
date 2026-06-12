---
title: "random_shuffle() C++"
date: 2009-06-24
forum: Programming Talk
---

### Post by Mirge on 2009-06-24
Just to throw together a quick example...

```

#include <iostream>
#include <string>
#include <algorithm>
#include <vector>

using namespace std;

int main(int argc, char * argv[])
{
    vector<string> strings;
    strings.push_back("One");
    strings.push_back("Two");
    strings.push_back("Three");
    strings.push_back("Four");
    strings.push_back("Five");

    cout << "First element in strings: " << strings[0] << endl;

    // Shuffle the vector.
    random_shuffle(strings.begin(), strings.end());

    cout << "After shuffle, first element in strings: " << strings[0] << endl;

    return 0;
}

```

It shuffles the vector as expected, but it constantly has the same order... each execution. It made me think I might need to seed it, but Google'ing around I ran into people saying it didn't need to be seeded, and then a bunch of arguments :P. Any thoughts?

Example output:
```

mike@mike-kubuntu:~/cpp$ ./random_shuffle
First element in strings: One
After shuffle, first element in strings: Five
mike@mike-kubuntu:~/cpp$ ./random_shuffle
First element in strings: One
After shuffle, first element in strings: Five
mike@mike-kubuntu:~/cpp$ ./random_shuffle
First element in strings: One
After shuffle, first element in strings: Five
mike@mike-kubuntu:~/cpp$ ./random_shuffle
First element in strings: One
After shuffle, first element in strings: Five
mike@mike-kubuntu:~/cpp$ ./random_shuffle
First element in strings: One
After shuffle, first element in strings: Five
mike@mike-kubuntu:~/cpp$ ./random_shuffle
First element in strings: One
After shuffle, first element in strings: Five
mike@mike-kubuntu:~/cpp$

```

---

### Post by Can+~ on 2009-06-24
Instead of asking, why don't you just added a srand(time(NULL)) and watch?

In fact, I just did it and worked.

---

### Post by Mirge on 2009-06-24
heh yeah I tried it after I posted, should have tried before posting. I had read posts where people said it didn't work though, strange.

Wonder why I don't need to #include cstdlib and ctime header files to use srand(time(NULL))...

---

### Post by Mirge on 2009-06-24
Anyway, I was working on a game that generates a jumbled up word and lets the user try to guess the word... user can also request a "hint". Here's what I have currently... compiles & runs... and as far as I can tell, works!

```

#include <iostream>
#include <string>
#include <vector>
#include <algorithm> // for random_shuffle()
#include <cstdlib>
#include <ctime>

using namespace std;

// ##############################################
class Word
{
    public:
    Word();
    Word(const string& word, const string& hint);
    
    const string& getJumbled() const;
    const string& getWord() const;
    const string& getHint() const;

    void setWord(const string& word);
    void setHint(const string& hint);

    private:
    void jumbleWord();
    string jumbled;
    string word;
    string hint;
};

// ##############################################
string strtoupper(string s);

// ##############################################
int main(int argc, char *argv[])
{
    srand(time(NULL));
    
    vector<string> words;
    words.push_back("wall");
    words.push_back("glasses");
    words.push_back("labored");
    words.push_back("persistent");
    words.push_back("jumble");

    vector<string> hints;
    hints.push_back("Do you feel you're banging your head against something?");
    hints.push_back("These might help you SEE the answer.");
    hints.push_back("Going slowly, is it?");
    hints.push_back("Keep at it!");
    hints.push_back("What this game is all about.");

    vector<Word> word_list;

    for(unsigned int i = 0; i < words.size(); i++)
    {
        word_list.push_back(Word(words[i], hints[i]));
    }

    // Shuffle our word list. Then pick the first element.
    random_shuffle(word_list.begin(), word_list.end());

    bool word_guessed = false;
    string guess;
    
    while(!word_guessed)
    {
        cout << "Your word is: " << word_list[0].getJumbled() << endl;
        cout << "Enter your guess, or enter H for a hint: ";
        cin >> guess;

        if(strtoupper(guess) == "H")
        {
            cout << word_list[0].getHint() << endl << endl;
            continue;
        }

        if(strtoupper(guess) == strtoupper(word_list[0].getWord()))
        {
            cout << "You guessed correctly! Great job!" << endl;
            word_guessed = true;
        }
    }

    return 0;
}


// ##############################################
Word::Word()
{
    this->word = "";
    this->jumbled = "";
}

// ##############################################
Word::Word(const string& word, const string& hint)
{
    this->word = word;
    this->hint = hint;

    this->jumbleWord();
}

// ##############################################
const string& Word::getJumbled() const
{
    return this->jumbled;
}

// ##############################################
const string& Word::getWord() const
{
    return this->word;
}

// ##############################################
const string& Word::getHint() const
{
    return this->hint;
}

// ##############################################
void Word::setWord(const string& word)
{
    this->word = word;
    this->jumbleWord();
}

// ##############################################
void Word::setHint(const string& hint)
{
    this->hint = hint;
}

// ##############################################
void Word::jumbleWord()
{
    this->jumbled = this->word;
    random_shuffle(this->jumbled.begin(), this->jumbled.end());
}

// #############################################
string strtoupper(string s)
{
    for(string::iterator i = s.begin(); i != s.end(); i++)
        *i = toupper(*i);

    return s;
}

```

---

### Post by Can+~ on 2009-06-24
Because much of the implementation of C++ revolves around the underlying libraries of C, so when you import one of the C++'s library it may and adding some of the C functionality underlying it.

For example, let's see the first lines of the /usr/include/c++/4.3.3/bits/ios_base.h

```
//
// ISO C++ 14882: 27.4  Iostreams base classes
//

#ifndef _IOS_BASE_H
#define _IOS_BASE_H 1

#pragma GCC system_header

#include <ext/atomicity.h>
#include <bits/localefwd.h>
#include <bits/locale_classes.h>
#include <cstdio>  // For SEEK_CUR, SEEK_END
```

*gasp* cstdio! What are you doing in here?

How does importing higher-level functionallity end up cluttering your namespace with it's lower-level implementation? One of the many questions I wonder when I see people trying to learn this.... *sigh*

Well, as the problem is solved, let's add the pythonic (pre-py3) solution

[PHP]Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> mylist = range(0, 10)
>>> mylist
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> import random
>>> random.shuffle(mylist)
>>> mylist
[2, 8, 9, 3, 6, 0, 7, 4, 5, 1]
>>> random.shuffle(mylist)
>>> mylist
[0, 4, 7, 2, 3, 1, 8, 5, 6, 9]
>>> [/PHP]

:KS

---

### Post by Mirge on 2009-06-24
> **Can+~ said:**
> Because much of the implementation of C++ revolves around the underlying libraries of C, so when you import one of the C++'s library it may and adding some of the C functionality underlying it.

For example, let's see the first lines of the /usr/include/c++/4.3.3/bits/ios_base.h

```
//
// ISO C++ 14882: 27.4  Iostreams base classes
//

#ifndef _IOS_BASE_H
#define _IOS_BASE_H 1

#pragma GCC system_header

#include <ext/atomicity.h>
#include <bits/localefwd.h>
#include <bits/locale_classes.h>
#include <cstdio>  // For SEEK_CUR, SEEK_END
```*gasp* cstdio!


So should I not bother including headers that already are included like the above mentioned? Or should I (for I guess portability?) always include those headers as well? Like my example above... I didn't "have" to include <ctime> or <cstdlib>... is it more "correct" to include them anyway, or just leave them out?

---

### Post by Can+~ on 2009-06-24
> **Mirge said:**
> So should I not bother including headers that already are included like the above mentioned? Or should I (for I guess portability?) always include those headers as well? Like my example above... I didn't "have" to include <ctime> or <cstdlib>... is it more "correct" to include them anyway, or just leave them out?

It won't matter, everything is protected with the #ifndef. So if you reinclude library, it won't overload the previous include.

So if you're going to use the cstdio functions, (re)include cstdio, if not, just leave the other libraries include them and don't look at them.

---

### Post by Mirge on 2009-06-24
Perfect, thanks much :)

---

### Post by Habbit on 2009-06-24
> **Mirge said:**
> So should I not bother including headers that already are included like the above mentioned? Or should I (for I guess portability?) always include those headers as well? Like my example above... I didn't "have" to include <ctime> or <cstdlib>... is it more "correct" to include them anyway, or just leave them out?

The Right Thing (TM) is to include the headers that declare what you use, because in some other platform, or a different version of the same C++ library, it might not be the case that the functionality is related. For example, there is talk of a new random numbers API for the next C++ standard, with the user being able to choose between different generators (planar, Mersenne Twister, etc) and distributions. Such a C++ library might not need to import the C random libs.

---

