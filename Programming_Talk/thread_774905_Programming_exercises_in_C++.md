---
title: "Programming exercises in C++"
date: 2008-04-29
forum: Programming Talk
---

### Post by StOoZ on 2008-04-29
where can I find a site , with a list of exercises/questions (and preferably also solutions) for which I can use to solve and improve my programming skills?
im looking for exercises that involves only standard c++, not some gui or anything like that.

thanks.

---

### Post by LaRoza on 2008-04-29
> **StOoZ said:**
> where can I find a site , with a list of exercises/questions (and preferably also solutions) for which I can use to solve and improve my programming skills?
im looking for exercises that involves only standard c++, not some gui or anything like that.

thanks.

The sticky has a link to a thread with such sites. Most tasks are language independant.

---

### Post by dwhitney67 on 2008-04-29
Below are two problems I had to resolve today (for an employment test).  Perhaps you could try to solve them as well.

P.S.  The time limit I was afforded was 2 hours.  See if you can do that too!

-----------------------------------
1) Munging phrase pairs

A file format exists to store a list of phrase pairs. A phrase pair is a pair of phrases that may be translations of each other with some probability. We attach the probability and other information to the phrase pair as well, for use when translating. The text format looks like this:

PP <num src tokens (N)> <num trg tokens (M)> <src token 1> ... <src token N> $ <trg token 1> ... <trg token M> & <other info>

For example, in a French to English system:

PP 2 2 l' homme $ the man & blah

We also have a "munged" format for the same information, which is better for certain applications. It looks like this:

<num src tokens (N)> <src token 1> ... <src token N> $ <num trg tokens (M)> <trg token 1> ... <trg token M> & <other info>

So the above example has the following munged form:

2 l' homme $ 2 the man & blah

Write a C++ program using STL components that will read in the first format and write out the munged format. Bonus question: what would you do next to try to make it run faster?

(Note: the source and target phrase tokens can contain either of the delimiters $, & and they are not escaped! Phrases will never contain a space within a single token, however. Assume fields are separated by a single space character.)

===
2) n-Gram Counter

Your task is to write an n-gram counter in C++ using STL components. An n-gram is a contiguous sequence of n tokens in a string. For example, the sentence "do you know that I know you know that I know that ?" has
11 3-grams, 12 2-grams, and 13 1-grams. Since there are multiple instances of some of the n-grams, there are actually only 8 unique 3-grams, 7 unique 2-grams, and 6 unique 1-ngrams.

Given a plain text document, your program will count up the number of times each unique n-gram is seen and print out each n-gram and its count in sorted descending order. Your program should do this for all n-grams where 1 <= n <= 3. For example, for the sentence above, your program will output something like this:

==== 3-grams ====
2 you know that
2 know that I
2 that I know
1 do you know
1 know that ?
1 know you know
1 I know you
1 I know that

==== 2-grams ====
3 know that
2 you know
2 that I
2 I know
1 do you
1 know you
1 that ?

==== 1-grams ====
4 know
3 that
2 you
2 I
1 do
1 ?

---

### Post by Davahub on 2011-01-14
Hi do you have to solution you came up for the exercises?
 
Best,
 
David Huber

---

### Post by |{urse on 2011-01-14
This thread kinda got necro'd but I noticed noone answered the OP's question.

[http://www.cplusplus.com]("http://www.cplusplus.com")

I'm also kinda curious what the solution to the n-gram counter problem is ^^

---

### Post by worksofcraft on 2011-01-14
The way I like to study is to read about it and then try to make up my own exercises... like here is one I been playing with just moments ago to do with the new C++0x standard:
[php]
// g++ -std=c++0x tuple.cpp
// testing c++ tuple extension
// note casts to unsigned are to ensure both 32 and 64 bit compatibility
#include <cstdio>
#include <tuple>
using namespace std;

int main() {
	long rectifier = 856286;
	// make a tuple from an arbitrary collection of data 
	auto myTuple = make_tuple(1, 2.0, "myTuple", rectifier);
	// sizeof operator works as expected
	printf("myTuple size (in bytes) is: %u\n", (unsigned) sizeof(myTuple));
	// getting number of elements needs to explicitly identify the type
	printf("myTuple has %u elements\n", (unsigned) tuple_size<decltype(myTuple)>::value);
	return !printf("no exceptions!\n");
}
[/php]

I can also really recommend the various pages [ e.g. this one at Bjarne Stroustrup's site]("http://www2.research.att.com/~bs/bs_faq2.html")

lol ... silly me... I suddenly realize this was an inappropriately bumped dead fossil thread from 2008 :P

---

### Post by Lootbox on 2011-01-15
> **|{urse said:**
> I'm also kinda curious what the solution to the n-gram counter problem is ^^

I was bored, so I coded something up that works and makes use of STL algorithms:

```

#include <string>
#include <iostream>
#include <sstream>
#include <fstream>
#include <map>
#include <vector>
#include <deque>
#include <algorithm>
#include <iterator>
#include <utility>

using namespace std;

void PrintUsage(char* file_name)
{
    cout << "Usage: " << file_name << " input-file n\n";
    cout << "(this finds all unique n-grams in input-file, where 1 <= n <= 3)" << endl;
}

// ProcessArguments returns true if and only if the supplied arguments are valid.
bool ProcessArguments(char** argv, ifstream& input, int& gram_order)
{
    stringstream arg_ss;
    arg_ss << argv[2];
    arg_ss >> gram_order;
    
    if (arg_ss.fail() || gram_order < 1 || gram_order > 3)
        return false;
    
    input.open(argv[1]);
    return input.is_open();
}

// Turn the "queue" of words into a single phrase:
string ConstructNGram(const deque<string>& words)
{
    string result = words[0];
    for (size_t i = 1; i < words.size(); ++i) {
        result += " " + words[i];
    }
    
    return result;
}

// Functor used to sort and display results:
struct PairFn {
    // Used for sorting:
    bool operator()(const pair<string, int>& lhs, const pair<string, int>& rhs)
    {
        // Sort first by count in decreasing order:
        if (lhs.second != rhs.second)
            return lhs.second > rhs.second;
        
        // Otherwise, sort reverse alphabetically:
        return lhs.first > rhs.first;
    }
    
    // Used for display:
    string operator()(const pair<string, int>& ngram)
    {
        stringstream display_ss;
        display_ss << ngram.second << " " << ngram.first;
        return display_ss.str();
    }
};

int main(int argc, char** argv)
{
    if (argc != 3) {
        PrintUsage(argv[0]);
        return -1;
    }
    
    ifstream input;
    int gram_order;
    if (!ProcessArguments(argv, input, gram_order)) {
        cout << "Bad arguments. ";
        PrintUsage(argv[0]);
        return -1;
    }
    
    map<string, int> ngram_counts;
    deque<string> previous_words;
    string word;
    for (int i = 0; i < gram_order - 1; ++i) {
        input >> word;
        previous_words.push_back(word);
    }
    
    // Read the n-gram and record them in the map:
    while (input >> word) {
        previous_words.push_back(word);
        ++ngram_counts[ConstructNGram(previous_words)];
        previous_words.pop_front();
    }
    
    input.close();
    
    // Use a vector to sort and display the results:
    vector<pair<string, int> > results(ngram_counts.begin(), ngram_counts.end());
    sort(results.begin(), results.end(), PairFn());
    transform(results.begin(), results.end(), ostream_iterator<string>(cout, "\n"), PairFn());
    
    return 0;
}

```

The construction of the string in ConstructNGram is a possible source of inefficiency (especially if we let n be a large number). You can reduce it by using substrings instead.

---

