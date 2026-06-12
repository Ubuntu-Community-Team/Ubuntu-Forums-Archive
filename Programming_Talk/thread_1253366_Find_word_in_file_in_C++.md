---
title: "Find word in file in C++"
date: 2009-08-30
forum: Programming Talk
---

### Post by Tclarkie on 2009-08-30
how do i find a word in a file in c++, i need it for a anagram app.

it needs to be able to search a whole dictionary and be able to set a variable as a word

all help apprecited

---

### Post by dwhitney67 on 2009-08-30
1.  Open the file.
2.  Begin reading individual lines of text from the file.
3.  Compare each line to determine if your search-word is present.

Alternative:  Before step 3, break the line of text into individual words.  This suggestion is only applicable if a line of text contains more than one word.

As far as implementing the code, well you are on your own.  This exercise has the undesirable scent of being a homework problem.  If I am wrong, prove otherwise.

---

### Post by RocketRanger on 2009-08-30
Look a the string library for easier implementation. There's a overview here: [http://www.cppreference.com/wiki/string/start](http://www.cppreference.com/wiki/string/start)

cctype has functions for converting cases in case you need to take that into account.

---

### Post by Tclarkie on 2009-08-31
any sort'a direct instructions, pls

---

### Post by dribeas on 2009-08-31
It depends on what you really need to do. You said that the file is a dictionary and you want to select a word from it. That is quite a vague set of requirements, do you want to keep the whole dictionary in memory for other purposes (or to select other words)? How do you want to choose the word from the set (random)? Do you need to perform searches in the words stored in the dictionary?

Now, the fact is that those answers will imply a decision on what container to use. Then, depending on the container you can use the STL algorithms with adapters to do the reading of the file into memory:

```

int main()
{
   std::vector<std::string> words;
   std::ifstream file( filename ); // where filename is a const char* with the name of the file
   std::copy( std::input_iterator<std::string>( file ), 
        std::input_iterator<std::string>(), std::back_inserter(words) );
   // select the word in the middle of the dictionary (no sanity checks):
   std::cout << words[ words.size() / 2 ] << std::endl;
}

```

The code above uses a linear storage facility, where words are stored in the order they were found in the file, and prints out the middle word. There are no sanity checks (if the file has no words the program will die...

If you choose another container (std::set for example) due to your storage requirements you may have to use a different iterator adapter (back_inserter will be changed to inserter)...

---

### Post by Tclarkie on 2009-08-31
i need to be abe to run a search through the dictionary so a can match the output of the anagram app

---

### Post by mupto on 2009-08-31
its finding a word in a c++ files only? or does this app have to also be in c++? because you could write this in bash in a couple lines very easily.

---

### Post by dribeas on 2009-08-31
> **Tclarkie said:**
> i need to be abe to run a search through the dictionary so a can match the output of the anagram app

If you only need to search for full words, then look into std::set or some other associative container. You may want to implement a [trie]("http://en.wikipedia.org/wiki/Trie") (or [Patricia trie]("http://en.wikipedia.org/wiki/Radix_tree")) on your own if you require more complex operations like searching for prefix matches of strings.

---

