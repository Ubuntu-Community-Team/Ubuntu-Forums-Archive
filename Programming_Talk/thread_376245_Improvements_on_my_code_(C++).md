---
title: "Improvements on my code? (C++)"
date: 2007-03-04
forum: Programming Talk
---

### Post by rekahsoft on 2007-03-04
Hi all, i am wondering if anybody can looking through my little app i made to query text and see if everything is the best it can be. Following is the code; Thanks for your input :D

File: file_unreadable_error.h```
#ifndef __FILE_UNREADABLE_ERROR_H
#define __FILE_UNREADABLE_ERROR_H

#include <string>
#include <stdexcept>

class file_unreadable_error: public std::runtime_error {
	public:
		file_unreadable_error(const std::string&);
};
#endif
```File: file_unreadable_error.cc```
#include "file_unreadable_error.h"

using std::string;
using std::runtime_error;

file_unreadable_error::file_unreadable_error(const string& msg) : runtime_error(msg) {}
```File: tquery.h```
#ifndef __TQUERY_H
#define __TQUERY_H

#include <string>
#include <vector>
#include <fstream>
#include <sstream>
#include <utility>
#include <iostream>
#include "file_unreadable_error.h"

class textquery {
	public:
		textquery() throw();
		textquery(const std::string&, const std::string&) throw(file_unreadable_error);
		textquery(std::ifstream&, const std::string&) throw(file_unreadable_error);
		textquery(const std::vector<std::string>&) throw();
		textquery(const textquery&) throw();

		const textquery& operator=(const textquery&) throw();
		const bool operator!=(const textquery&) throw();

		void set_search_key(const std::string&) throw();
		const std::string& get_search_key() const throw();
		
		void set_text(const std::vector<std::string>&) throw();
		void set_text_from_file(const std::string&) throw(file_unreadable_error);

		const std::vector<std::pair<int, std::string> > locate(const bool = false) throw();
	private:
		std::string search_key;
		std::vector<std::string> text;
};
#endif
```File: tquery.cc```
#include "tquery.h"

#include <iterator>

using std::pair;
using std::string;
using std::vector;
using std::ifstream;
using std::stringstream;

textquery::textquery() throw() {}

textquery::textquery(const std::string& filepath, const string& given_search_key) throw(file_unreadable_error) : search_key(given_search_key) {
	ifstream inputf(filepath.c_str()); //create input file stream from given filepath
	if (inputf.good()) { //if file is readable
		string file_line;
		while (inputf >> file_line)
			text.push_back(file_line);
		inputf.close();
	} else {
		throw file_unreadable_error("Error reading from file");
	}
}

textquery::textquery(ifstream& inputf, const string& given_search_key) throw(file_unreadable_error) : search_key(given_search_key) {
	if (inputf.good()) { //if file is readable
		string file_line;
		while (inputf >> file_line)
			text.push_back(file_line);
		inputf.close();
	} else {
		throw file_unreadable_error("Error reading from file");
	}
}

textquery::textquery(const vector<string>& given_text) throw() : text(given_text) {}
textquery::textquery(const textquery& other) throw() : search_key(other.search_key), text(other.text) {}

const textquery& textquery::operator=(const textquery& other) throw() {
	search_key = other.search_key;
	text = other.text;
}

const bool textquery::operator!=(const textquery& other) throw() {
	return (search_key != other.search_key && text != other.text ? true : false);
}

const string& textquery::get_search_key() const throw() {
	return search_key;
}

void textquery::set_search_key(const string& new_key) throw() {
	search_key = new_key;
}

void textquery::set_text(const vector<string>& given_text) throw() {
	text = given_text;
}

void textquery::set_text_from_file(const string& filepath) throw(file_unreadable_error) {
	ifstream inputf; //create file input stream
	inputf.open(filepath.c_str()); //open file
	if (inputf.good()) { //if file is readable
		string file_line;
		while (getline(inputf, file_line)) //read line by line
			text.push_back(file_line); //add line to vector of lines
		inputf.close(); //close input file stream
	} else { //file not readable
		throw file_unreadable_error("Error reading from file");
	}
}

const std::vector<std::pair<int, std::string> > textquery::locate(const bool exact) throw() {
	vector<pair<int, string> > resaults;

	int line = 1; //current line number
	int search_key_tokens = 0; //number of words contained in search_key

	string tmp;
	stringstream token_counter(search_key); //stringstream to break search_key into tokens (individual words)
	for (; token_counter >> tmp; ++search_key_tokens); //count tokens of search_key

	//interate through vector containing lines of text so that individual lines can be processed
	for (vector<string>::iterator x = text.begin(); x != text.end(); ++x, ++line) {
		stringstream ss(*x); //stringstream to break line into words
		vector<string> words; //vector to hold words of the current line being processed
		while (ss >> tmp) { //read word into temporary
			if (!exact) {
				//iterate through word character by character and change all upercase to lowercase
				for (string::size_type s = 0; s != tmp.size(); ++s) {
					if (isupper(tmp[s]))
						tmp[s] = tolower(tmp[s]);
				}
			}
			words.push_back(tmp); //add token to word vector
		}

		//iterate through vector containing words of the current line to be processed character by character
		for (vector<string>::iterator y = words.begin(); y != words.end() - (search_key_tokens - 1); ++y) {
			tmp = *y; //get first word
			//make a string as long as the search_key
			for (int var = 1; var != search_key_tokens; ++var) {
				(tmp += " ") += *(y+var);
			}

			string tmp_key = search_key; //don't modify original search_key instead create temporary
			if (!exact) {
				//if exact is off then iterate through temporary seach key
				for (string::size_type s = 0; s != tmp_key.size(); ++s) {
					if (isupper(tmp_key[s])) //if character from temporary search key is uppercase make lower case
						tmp_key[s] = tolower(tmp_key[s]);
				}
			}
			
			bool match = true; //bool that shows if the current string of words from the line matches the key
			//iterate through tmp_key and tmp_txt to see if they match
			for (string::iterator iter_key = tmp_key.begin(), iter_txt = tmp.begin(); iter_key != tmp_key.end(); ++iter_key, ++iter_txt) {
				if (*iter_key != *iter_txt) { //if character from the tmp_key do not match the corrisponding character in tmp_txt
					match = false; //no match
					break; //stop checking tmp_key to tmp_txt because they are not the same
				}
			}

			if (match) {
				resaults.push_back(make_pair(line, *x)); //there is a match; add the current line and text to resaults
				break; //no need to search the rest of the line; we know there is already a match
			}
		}
	}
	return resaults;
}
```File: textqueryer.cc```
#include <string>
#include <vector>
#include <cstdlib>
#include <iostream>
#include <cstring>

#include "tquery.h"
#include "file_unreadable_error.h"

using std::cin;
using std::cout;
using std::endl;
using std::pair;
using std::string;
using std::vector;

void usage() {
	cout << "Usage: textqueryer [OPTIONS] [SEARCH_KEY] " << "\n\n"
	     << "Options:" << "\n"
	     << "-f [FILEPATH] [SEARCH_KEY]" << "\n"
	     << "-x [FILEPATH] [SEARCH_KEY]" << "\n"
	     << endl;
}

int main(int argv, char** argc) {
	if (argv == 4) {
		textquery q;
		bool exact = false;
		string query_search_key = argc[3];
		string query_source = argc[2];
		
		if (argc[1][0] == '-') {
			for (int x = 1; x != strlen(argc[1]); ++x) {
				if (argc[1][x] == 'f') {
					try {
						q.set_text_from_file(query_source);
					} catch (const file_unreadable_error& ioe) {
						cout << ioe.what() << endl;
						return EXIT_SUCCESS;
					}
				} else if (argc[1][x] == 'x') {
					exact = true;
				} else {
					cout << "Invalid option \"" << argc[1][x] << "\"" << endl;
					usage();
					return EXIT_SUCCESS;
				}
			}
		}

		q.set_search_key(query_search_key);
		vector<pair<int, string> > resaults = q.locate(exact);

		for (vector<pair<int, string> >::iterator iter = resaults.begin(); iter != resaults.end(); ++iter)
			cout << "(" << iter->first << "): " << iter->second << endl;
	} else {
		usage();
	}
	return EXIT_SUCCESS;
}
```

---

### Post by thumper on 2007-03-04
All these comments are purely stylistic as I didn't check the actual behaviour of your program.


 * Never start any of your own identifiers with double underscores as they are reserved for the compiler vendor
 * Don't inlcude <iostream> in any header file, instead use <iosfwd>
 * Don't add throw specifiers to your function prototypes. They have generally been agreed as an abomination in the standard, and they just cause more problems than they were ment to solve.
 * textquery defines != but not ==.  If you define one, do both, and implement one as the negative of the other (and make it const)
 * 'inputf >> file_line' doesn't read a line from a file, but a word.  You probably want to use std::getline(inputf, file_line)
 * you implement the reading from a file in three places.  Write it once, and call it from all three distinct places (private function)
 * really don't use <cstdlib> or <cstring>.  Find another way.
 * results doesn't have an 'a'
 * Learn to use the boost libraries for options parsing, they are worth the effort.

HTH.

---

### Post by rekahsoft on 2007-03-04
> **thumper said:**
>  * Don't inlcude <iostream> in any header file, instead use <iosfwd> could you explain why?> **thumper said:**
>  * Don't add throw specifiers to your function prototypes. They have generally been agreed as an abomination in the standard, and they just cause more problems than they were ment to solve.Could you explain this more> **thumper said:**
>  * textquery defines != but not ==.  If you define one, do both, and implement one as the negative of the other (and make it const)oops, that is a mistake> **thumper said:**
>  * 'inputf >> file_line' doesn't read a line from a file, but a word.  You probably want to use std::getline(inputf, file_line)oops, another mistake> **thumper said:**
>  * really don't use <cstdlib> or <cstring>.  Find another way.Could you explain why. Also how would i go about doing that?> **thumper said:**
>  * results doesn't have an 'a'lol my mistake> **thumper said:**
>  * Learn to use the boost libraries for options parsing, they are worth the effort.ok i will look into it

---

### Post by rekahsoft on 2007-03-05
Anybody?

---

### Post by thumper on 2007-03-05
[quote=rekahsoft]
[quote=thumper]
* Don't inlcude <iostream> in any header file, instead use <iosfwd>
[/quote]
could you explain why?[/quote]

<iostream> has references to some static objects, in particular cin, cout, and cerr.  If you have this included in multiple places in header files, then you can get a multiple definition error for the statics.

This is the whole reason that the <iosfwd> header exists.  <iosfwd> forward declares the important classes for C++ I/O.  You still need to include <iostream> in your source files before using cin, cout, or cerr.

---

### Post by thumper on 2007-03-05
[quote=rekahsoft]
[quote=thumper]
* Don't add throw specifiers to your function prototypes. They have generally been agreed as an abomination in the standard, and they just cause more problems than they were ment to solve.
[/quote]
Could you explain this more[/quote]

If it is purely your own code, then fine.  Although they are still a pain to enforce.

The problem comes more when calling into other APIs where you don't have control over the exceptions that are raised, and you find yourself catching and wrapping other peoples exceptions.  This is not good.

Do you know what happens if an exception is thrown that isn't listed?

Better to read, understand, and use the exception guarantees as outlined by Herb Sutter in his book Exceptional C++.  Writing code that conforms to the strong exception guarantee is slightly more difficult, but makes for more robust code.

---

### Post by thumper on 2007-03-05
[quote=rekahsoft]
[quote=thumper]
* really don't use <cstdlib> or <cstring>. Find another way.
[/quote]
Could you explain why. Also how would i go about doing that?[/quote]

Ok, firstly what are you using the headers for?

The reason that they start with 'c' is that they are C header files that have been wrapped into the std namespace.  Generally there are better solutions than using C header files.

If it is just for return codes, define them yourself in your main source file.  Sure define them as global constants (in an anonymous namespace of course), but don't use <cstdlib>.

---

### Post by rekahsoft on 2007-03-05
ok...i will look into it. Thanks for the suggestions

---

