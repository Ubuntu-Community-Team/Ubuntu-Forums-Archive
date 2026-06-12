---
title: "Permutation Application"
date: 2009-07-17
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-17
i intend to develop an application which takes an input from a user and lists all its permuatations which have a dictionary meaning.
i have already made the code for generating permuatations in c using gcc.how shall i proceed with the second part.I intend the application to be open source fully.and also want to make a gui for it using gtk but i am new to it.
Please help and contribute.

---

### Post by dwhitney67 on 2009-07-17
Consider creating a list (or other data structure) of words that are available in the dictionary file(s) that are located in /usr/share/dict.

Then after you have accepted the user inputted word, determine all of the permutations of that word, and compare with what you have in your list.  Any permuted words that are in your list should be displayed to the user.

P.S.  This exercise would be a lot easier if you relied on a language other than C.  Consider C++ or even Python.

I threw this incomplete program together in a few minutes; just add the stuff you say you have already completed (ie. the means to determine the permutations).
```

#include <map>
#include <vector>
#include <string>
#include <fstream>
#include <iostream>


typedef std::map<std::string, unsigned int> WordMap;
typedef std::vector<std::string>            WordArray;


WordMap getWordsFromDictionary()
{
   WordMap      wmap;
   std::fstream dictionary("/usr/share/dict/linux.words", std::ios::in);

   if (dictionary)
   {
      std::string  word;
      unsigned int index = 0;

      while (getline(dictionary, word))
      {
         wmap.insert(std::make_pair(word, index++));
      }
   }

   return wmap;
}

std::string getWordInput()
{
   std::string word;

   std::cout << "Enter a word: ";
   std::cin  >> word;

   return word.substr(0, word.find_first_of(' '));
}

WordArray findWordPermutations(const std::string word, const WordMap& wmap)
{
   WordArray words;

   words.push_back(word);

   // TODO:  Determine word permutations, and assess if that each is a valid word.

   return words;
}

template <typename T>
void display(const T& str)
{
   std::cout << str << std::endl;
}

int main()
{
   WordMap     wmap     = getWordsFromDictionary();
   std::string word     = getWordInput();
   WordArray   permutes = findWordPermutations(word, wmap);

   std::cout << "\n\nOriginal user input with permutations...\n";
   std::for_each(permutes.begin(), permutes.end(), display<std::string>);
}

```

---

### Post by nipunreddevil on 2009-07-17
Thanks sir
I have used c++ a lot but not in linux,so your code looks a little difficult to understand.
Shall i try the same in c using structures or shall i master c++ in linux.
Is there any way i can read from a pdf in c/cpp.

---

### Post by dwhitney67 on 2009-07-17
In C you will need to develop a hash-map, or other container, where you can quickly look up words.  From your requirements, you need to assess whether a permuted word is indeed a legal word, and not just some jibberish.

As far as reading a PDF file, sure it can be done, but whether the data read is intelligible is another thing.  :-)

---

### Post by MadCow108 on 2009-07-17
if you decide to use c++ take a look at the very useful next_permutation and prev_permutation functions
[http://www.cplusplus.com/reference/algorithm/next_permutation/](http://www.cplusplus.com/reference/algorithm/next_permutation/)
with these and a fitting compare functionobject/function you can save implementing the whole permutate algorithm.

---

### Post by dwhitney67 on 2009-07-17
> **MadCow108 said:**
> if you decide to use c++ take a look at the very useful next_permutation and prev_permutation functions
[http://www.cplusplus.com/reference/algorithm/next_permutation/](http://www.cplusplus.com/reference/algorithm/next_permutation/)
with these and a fitting compare functionobject/function you can save implementing the whole permutate algorithm.
Good call.

Works like a charm...
```

#include <algorithm>
#include <map>
#include <vector>
#include <string>
#include <fstream>
#include <iostream>
#include <cstring>


typedef std::map<std::string, unsigned int> WordMap;
typedef std::vector<std::string>            WordArray;

const char* DICTIONARY = "/etc/dictionaries-common/words";

WordMap getWordsFromDictionary()
{
   WordMap      wmap;
   std::fstream dictionary(DICTIONARY, std::ios::in);

   if (dictionary)
   {
      std::string  word;
      unsigned int index = 0;

      while (getline(dictionary, word))
      {
         wmap.insert(std::make_pair(word, index++));
      }
   }
   else
   {
      std::cerr << "Error: Failed to open " << DICTIONARY << "." << std::endl;
   }

   return wmap;
}

std::string getWordInput()
{
   std::string word;

   std::cout << "Enter a word: ";
   std::cin  >> word;

   return word.substr(0, word.find_first_of(' '));
}

WordArray findWordPermutations(const std::string& word, const WordMap& wmap)
{
   using namespace std;

   WordArray words;
   char* copy = new char[word.size() + 1];

   strncpy(copy, word.c_str(), word.size());
   copy[word.size()] = '\0';

   sort(copy, copy + word.size());

   do
   {
      string result = copy;
      WordMap::const_iterator it = wmap.find(result);

      if (it != wmap.end())
      {
         words.push_back(result);
      }
   } while (next_permutation(copy, copy + word.size()));

   delete [] copy;

   return words;
}

template <typename T>
void display(const T& str)
{
   std::cout << str << std::endl;
}

int main()
{
   WordMap wmap = getWordsFromDictionary();

   if (wmap.size() == 0)
   {
      return -1;
   }

   std::string word     = getWordInput();
   WordArray   permutes = findWordPermutations(word, wmap);

   std::cout << "\n\nOriginal user input with permutations...\n";
   std::for_each(permutes.begin(), permutes.end(), display<std::string>);
}

```

---

