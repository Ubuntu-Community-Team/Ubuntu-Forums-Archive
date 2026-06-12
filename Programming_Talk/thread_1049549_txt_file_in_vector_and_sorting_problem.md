---
title: "txt file in vector and sorting problem"
date: 2009-01-24
forum: Programming Talk
---

### Post by Marcus_TX on 2009-01-24
Hello,
i have a problem.
I would like to read a txt file with a unknown number of words in an vector.
I never used vector before so i need some kind of explanation how to do so.

and when i have this file in the vector then i have to check if they are all in order, if not then i have to sort them.

is there a way to use bubble sort to check if they are in order and if not use a different sort to get them in order, because bubble sort doesn't look like its the best for this kind of work.

Thanks already

Marcus

---

### Post by slavik on 2009-01-24
what language are you using and what exactly do you mean by reading the file into a vector?

do you want to have a sorted list of words in a text file?

---

### Post by Marcus_TX on 2009-01-24
Oh i forgot, it's C++

i have a file wordorder.txt

it's a txt file with on word in every line.

i need to get all words in the vector and then sort the alphabetical, if they are not in alphabetical order.
Then i need to lower all cases and then i have to check for words where the letters are in alphabetical order in the word like in BOX or in DEMOS. From this words i have to get all words that follow this order and are at least 4 letters long in a output file.

in the file they need to be in alphabetical order and need to be numbered.

This is the whole problem but i don't want a whole problem. I need to know how to get the words in the vector. The rest i hope i can figure out by myself.

---

### Post by kjohansen on 2009-01-24
if you have a vector

```

vector<string> words;

```
in the loop where you are reading the file

```

words.push_back(current word);

```

---

### Post by monkeyking on 2009-01-25
consider using a priority queue

[http://www.sgi.com/tech/stl/priority_queue.html](http://www.sgi.com/tech/stl/priority_queue.html)

---

### Post by Marcus_TX on 2009-01-25
> **kjohansen said:**
> if you have a vector


Ok i don't have a vector.
And somehow i need a little more explanation how to use it.
I am sorry about it.

---

### Post by monkeyking on 2009-01-25
This wiki contains a nice and working example.
[http://en.wikipedia.org/wiki/Vector_(STL](http://en.wikipedia.org/wiki/Vector_(STL))

But If you want the words to be in a sorted order,
you should use priority queue.
This will sort the elements for you.

I would be easier to help you,
if you supply your non-working code.

---

### Post by Marcus_TX on 2009-01-27
Ok that's what i have so far:
And it's probably pretty wrong.


[PHP]
#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
#include <vector>
#include <algorithm>

using namespace std;

int main (){
char wordarray [200];
int count;

int i;
//int word;

ifstream infile;
infile.open ("wordorder.txt", ifstream::in);
while (infile.bad ()){
		cout << "can't open file" << endl;
		return 1;
}

vector <int> wordorder;
for (i=0; i < 50000; i++){
	infile >> (i)
	wordorder:: pushback (i);

}
[/PHP]

---

### Post by Zugzwang on 2009-01-27
Three notes:
[LIST]
[*]First of all, since this is obviously homework, you will only get vague hints from us here. If you have severe problems in solving the problem, ask your lecturer.
[*]Second, in C++, all commands (except definitions where applicable) have to reside in functions, methods, procedures or something like that.
[*] Third, try to compile your C++ program and examine the error messages to see what's wrong. Use your lecture notes to interpret them.
[/LIST]

---

### Post by Marcus_TX on 2009-01-27
We have no notes about using a vector or anything else i want to use.
I don't want a ready made program, if i wanted this i wouldn't ask in the internet, where everybody of my class could see it.

My idea of the program i am doing is totally different to the other ones, because of how i want to write it.

Because i want to use a bubble sort to check if the letters in the program are in the right order, all the others will check every letter on it's own. But i found out that Bubble sort can tell you when it changed something, and when it does so, the word is wrong anyway.

Oh i hope this doesn't come over to rude or so. I don't mean it this way, but english is only my 2nd language.

---

### Post by monkeyking on 2009-01-27
[PHP]#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
#include <vector>
#include <algorithm>

using namespace std;

int main (){
  char wordarray [200];
  int count;

  int i;
  //int word;
  
  ifstream infile;
  infile.open ("wordorder.txt", ifstream::in);
  while (infile.bad ()){
    cout << "can't open file" << endl;
    return 1;
  }
  
  vector <int> wordorder;
  for (i=0; i < 50000; i++){
    infile >> (i)
      wordorder:: pushback (i);
    
  }  [/PHP]

This can't be your best try,
you haven't even checked if your parenthesis matches up.

You should first of all get a simple main program up and running,
a hallo world. 
You should compile with -Wall which will help you alot.

When this works you should build ontop of that, 
something like reading in the file, and very simply just output on your screen, to check if your reading works.

And then you should start learning about vectors, like instead of outputing to your screen then pushing your words into a vector.

good luck

by the way check this page [http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)
especially the reading of text files.

---

### Post by Marcus_TX on 2009-02-03
ok i still have problems with it.
i have to get a qsort or so into it so that i can find out if the word it self is in order, if it is so it should be written in a new file.

but somehow my versions of qsort don't work.

```
#include <string>
#include <algorithm>
#include <iostream>
#include <fstream>
#include <vector>
#include <functional>
#include <cctype>>

int main () {
	std::vector <std::string> vec;
	std::ifstream stream ("wordorder.txt");
	if (!stream) {
		std::cout << "Can't open file" << std::endl;
		return 1;
	}
	//read the wordlist into the vector
	std::copy (std::istream_iterator <std::string> (stream), std::istream_iterator <std::string> (), std::back_inserter(vec));
	//sort the list
	std::sort (vec.begin (), vec.end () );

	//convert all letters to lower case
	static struct transform_helper :std::unary_function < std::string, void>
	
	{
		void operator () (std::string &value)
		{
			std::transform (value.begin (), value.end (), value.begin (), &tolower);
		}
	}
	transform;

	std::for_each (vec.begin (), vec.end (), transform);

	void sort () (std::string &value);
	std::sort (vec.begin (), vec.end () );

```

---

