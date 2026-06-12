---
title: "[C++] Working out some bugs"
date: 2008-04-29
forum: Programming Talk
---

### Post by TreeFinger on 2008-04-29
I have been working on a few programs. they all work but have a few bugs. I was wondering if anyone would like to offer some suggestions or tips on how to fix them. Here is some source.

First program reads strings from user until eof is entered. it then counts how many times a string occurs..

[php]
// Chapter 3 - count how many times each distrinct word appears in input

/* current bugs:
        if a word appears twice, will output occurences of that word twice.. and so on.
*/

#include <iomanip>
#include <ios>
#include <iostream>
#include <string>
#include <vector>

using std::cin;                 
using std::cout;                
using std::endl;                using std::streamsize;
using std::string;              using std::vector;

int main() {
        cout << "Enter words, one at a time, and i'll count them for you: ";

        // place to put input
        string x;

        // vector to store all the strings
        vector<string> theStrings;

        // invariant: theStrings contains all strings entered so far by user
        while ( cin >> x ) {
                theStrings.push_back(x);
        }

        // separate input from output
        cout << endl;

        // how many strings have been entered
        vector<string>::size_type string_count = theStrings.size();

        // how many strings are currently distinct
        vector<string>::size_type distinct_count = string_count;

        // strings to be ignored
        vector<string> alreadyChecked;

        // invariant: have selected 0 words to be compared to other words so far
        vector<string>::size_type compare_against_others = 0;

        while ( compare_against_others != string_count ) {

                // counter for occurences of [compare_against_others] note: all strings appear at least once!
                int occurences = 1;

                // invariant: compared 0 words in theStrings vector to the current string
                vector<string>::size_type up_for_comparing = 0;

                while ( up_for_comparing != string_count ) {

                        // check if comparing same index
                        if ( compare_against_others == up_for_comparing )
                                ++up_for_comparing;
                        else {
                                // check if word1 == word2
                                if ( theStrings[compare_against_others].compare( theStrings[up_for_comparing] ) == 0 ) {
                                        ++occurences;   // word occurred again
                                        ++up_for_comparing;
                                }
                                else
                                        ++up_for_comparing;
                        }
                }
                // output of how many times the string occurs
                cout << "The string, \"" << theStrings[compare_against_others] << "\" appears "
                        << occurences << " times." << endl;

                // move to the next string
                ++compare_against_others;
        }

return 0;
}
[/php]

This program also reads strings from the user and stores the shortest and longest. I am trying to figure out a way to work out if several strings are the same length and also shortest or longest..

[php]
// Chapter 3 - report shortest and longest string in input
/* Bugs:
        if string to be compared to longest and shortest is == to either one.. not sure how to implement..
*/

#include <ios>
#include <iostream>
#include <string>
#include <vector>

using std::cin;                 
using std::cout;                
using std::endl;                using std::streamsize;
using std::string;              using std::vector;

int main() {
        // vector to store the strings
        vector<string> allStrings;

        // variable to read string
        string x;

        // invariant: allStrings contains all strings read so far
        while ( cin >> x ) {
                allStrings.push_back( x );
        }

        // separates input from output
        cout << endl;

        // variables containing current longest and shortest strings
        string longest = allStrings[0], shortest = allStrings[0];

        // variable containing count of strings in allStrings vector
        vector<string>::size_type total_strings = allStrings.size();

        // variable counting allStrings indexes
        vector<string>::size_type string_count = 1;

        // invariant: checked 1 of strings in allStrings vector so far
        while ( string_count != total_strings ) {

                // check if allStrings[string_count] is shorter than current shortest
                if ( allStrings[string_count].length() < shortest.length() ) {
                        shortest.clear();
                        shortest = allStrings[string_count];
                }

                // check if allStrings[string_count] is larger than current longest
                if ( allStrings[string_count].length() > longest.length() ) {
                        longest.clear();
                        longest = allStrings[string_count];
                }

                // move on to next string
                ++string_count;
        }

        // output the longest string
        cout << "Longest String entered: " << longest << endl;

        // output the shortest string
        cout << "Shortest String entered: " << shortest << endl;

return 0;
}
[/php]

thank you for any tips.

---

### Post by bfhicks on 2008-04-29
For the first one, you have a vector set up to store the already encountered words, but you never use it. After encountering a new word, insert that into the vector and then you'll have to check each index in that vector for repetitions.

The second looked like it worked correctly? I had to modify the input to make a stopping condition, though.
[PHP]
bool keep_going = true;
while ( keep_going ) {
    cin >> x;
    if (x.compare("stop") == 0) 
          keep_going = false;
    else 
	  allStrings.push_back( x );
}
[/PHP]

---

### Post by dwhitney67 on 2008-04-29
Here's a solution I came up with.  It relies on an STL map to handle the unique strings and the count of each.

[PHP]#include <map>
#include <string>
#include <iostream>

using namespace std;


int main()
{
  typedef  map< string, unsigned int >  Words;
  typedef  Words::const_iterator        WordsIter;


  Words words;
  string shortestWord;
  string longestWord;

  cout << "enter some words; when done, enter the word '--done--'" << endl;

  string input;
  while (true)
  {
    cin >> input;

    if ( input == "--done--" )
      break;

    if ( words.find( input ) == words.end() )
    {
      words[ input ] = 1;
    }
    else
    {
      words[ input ]++;
    }

    if ( shortestWord == "" || input.size() < shortestWord.size() )
      shortestWord = input;

    if ( longestWord == "" || input.size() > longestWord.size() )
      longestWord = input;
  }

  // output the number of words
  for ( WordsIter it = words.begin(); it != words.end(); ++it )
  {
    cout << "Word '" << it->first << "' occurred " << it->second << " time(s)." << endl;
  }

  cout << endl;
  cout << "The shortest word encountered was: " << shortestWord << endl;
  cout << "The longest word encountered was : " << longestWord  << endl;

  return 0;
}[/PHP]

---

### Post by TreeFinger on 2008-04-30
Thank you for the replies fellas. I worked on it tonight and fixed the bug for the first problem. Tomorrow I hope to getting around to fixing the other one. Not sure if this is the best way, but it is the only way I could figure out to do it.

[php]
// Chapter 3 | Problem 3 - count how many times each distinct word appears in input

/* current bugs:
	none known
*/

#include <iomanip>
#include <ios>
#include <iostream>
#include <string>
#include <vector>

using std::cin;                 
using std::cout;                
using std::endl;                using std::streamsize;

using std::string;		using std::vector;

int main() {
	cout << "Enter words, one at a time, and i'll count them for you: ";

	// place to put input
	string x;

	// vector to store all the strings
	vector<string> the_strings;

	// invariant: theStrings contains all strings entered so far by user
	while ( cin >> x ) {
		the_strings.push_back(x);
	}

	// separate input from output
	cout << endl;

	// how many strings have been entered
	vector<string>::size_type string_count = the_strings.size();

	// strings to be ignored
	vector<string> already_checked;

	// invariant: have selected 0 words to be compared to other words so far
	vector<string>::size_type compare_against_others = 0;
	
	while ( compare_against_others != string_count ) {

		// check if string has already been counted
		// count of strings in ignore vector
		vector<string>::size_type ignore_count = already_checked.size();

		// it is believed the string has not been checked
		bool checked = 0;

		//invariant: checked 0 of strings in already_checked vector
		for ( int count = 0; count != ignore_count; ++count ) {
			// check if compare_against_others string has already been counted - would be located in already_checked vector
			if ( the_strings[compare_against_others].compare( already_checked[count] ) == 0 ) {
				// word's occurence has already been counted
				checked = 1;
			}
		}
		// end of checking if string has already been counted

		// invariant: word has status of not checked
		while ( checked == 0 ) {
		
			// counter for occurences of [compare_against_others] note: all strings appear at least once!
			int occurences = 1;

			// invariant: compared 0 words in theStrings vector to the current string
			vector<string>::size_type up_for_comparing = 0;

			while ( up_for_comparing != string_count ) {

				// check if comparing same index
				if ( compare_against_others == up_for_comparing )
					++up_for_comparing;
				else {
					// check if word1 == word2
					if ( the_strings[compare_against_others].compare( the_strings[up_for_comparing] ) == 0 ) {
						++occurences;	// word occurred again
						++up_for_comparing;
					}
					else
						++up_for_comparing;
				}
			}
			// output of how many times the string occurs
			cout << "The string, \"" << the_strings[compare_against_others] << "\" appears "
				<< occurences << " times." << endl;

			// current string has been checked
			checked = 1;

			// Add String to list of already checked strings
			already_checked.push_back( the_strings[compare_against_others] );

			
		}
			// move to the next string
			++compare_against_others;
	}

return 0;
}
[/php]

---

### Post by pedro_orange on 2008-04-30
Dun dun dun!

Do my eyes deceive me or is someone doing the Koenig & Moo exercises?

---

### Post by GoCool on 2008-04-30
> **pedro_orange said:**
> Dun dun dun!

Do my eyes deceive me or is someone doing the Koenig & Moo exercises?

What is Koenig & Moo ???

---

### Post by tseliot on 2008-04-30
> **GoCool said:**
> What is Koenig & Moo ???
The book "Accelerated C++", I guess.

---

### Post by pedro_orange on 2008-05-01
> **tseliot said:**
> The book "Accelerated C++", I guess.

Correct. 

I consulted my copy yesterday evening and they are indeed chapter 3 Accelerated C++ exercises.

When I was reading it a while back there were hardly any solutions to these exercises on the net. 
If someone was willing to spend time on it; I think it would be a rather useful resource for budding C++ programmers.

---

