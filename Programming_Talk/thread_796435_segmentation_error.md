---
title: "segmentation error"
date: 2008-05-16
forum: Programming Talk
---

### Post by akimatsu123 on 2008-05-16
i can't for my life figure out what is wrong with this script. i get a segmentation error. ive isolated the problem to not being able to assign a value to userInput. but i can't figure out why. here is the code. 

```
#include <iostream>
#include <string>
#include <vector>
#include <cctype>
using namespace std;

int main(void)
{
	vector<string> words;
	int y = 0;
	int i = 0;
	int j = 0;

	string userInput;
	cout << "Enter your statement: ";
	getline(cin, userInput);
	cout << userInput;

	int size = userInput.size();
	
	for(; i < size; i++)
	{
		while(isspace(userInput[i]) == true)
		{
			continue;
		}
		
		j = i;

		while(isspace(userInput[j]) == false)
		{
			j++;
		}
		

		words.push_back(userInput.substr(i, j - i));

		y++;
		
		i = j;
	}
	
	for(unsigned int x = 0; x < words.size(); x++)
	{
		cout << words[x] << endl;
	}
	
	return 0;
}

```

---

### Post by nvteighen on 2008-05-16
I can understand only a little of C++, so I may possibly be pointing to the wrong way.

Are you sure your variable j is always less than size? You're increasing it inside a while loop without taking array size somehow as a condition to break... j may be taking intermediate values higher than your array size before reaching i = j. Print j's values to screen (cout, isn't it?) and watch how it is behaiving.

I remember dealing with something similar some days ago in C.

---

### Post by dwhitney67 on 2008-05-16
Since your program culminates with the printing of individual words from a line of text inputed by the user, I can only surmise that is your goal... to get the individual words.

Here's a simpler way:
[PHP]#include <iostream>    // for cout, cin, getline
#include <sstream>     // for istringstream
#include <string>
#include <vector>

using namespace std;

int main()
{
  string str;

  // Get user input
  cout << "Enter a string: ";
  getline(cin, str );

  // Define an input string stream(er), using the input string given.
  istringstream istr( str );

  // Define the vector where to store the words
  vector< string > words;

  // While not at the end of the input string streamer, get
  // each word contain within.
  while ( !istr.eof() )
  {
    string word;
    istr >> word;

    // Insert the word into the vector of words
    words.push_back( word );
  }

  // Display vector of words
  for ( unsigned int i = 0; i < words.size(); ++i )
  {
    cout << "word " << i << ": " << words[i] << endl;
  }

  return 0;
}[/PHP]

---

### Post by dwhitney67 on 2008-05-16
And your original code, now working of course!  See the comments within the code for what was originally done incorrectly.
[PHP]
#include <iostream>
#include <string>
#include <vector>
#include <cctype>

using namespace std;

int main(void)
{
  string userInput;

  cout << "Enter your statement: ";
  getline( cin, userInput );

  vector< string > words;

  for ( unsigned int i = 0, j = 0; i < userInput.size(); ++i )
  {
    while ( isspace( userInput[i] ) == true )
    {
      continue;
    }

    j = i;

    // make sure you don't index beyond userInput's size!!!
    while ( (isspace( userInput[j] ) == false) && (++j < userInput.size()) );

    words.push_back( userInput.substr( i, j - i ) );

    i = j;
  }

  for ( unsigned int x = 0; x < words.size(); ++x )
  {
    cout << words[x] << endl;
  }

  return 0;
}
[/PHP]

P.S.  Your code was generating a segmentation violation (actually, an exception was thrown) when you exceeded the length of userInput when using substr( pos, n ) with an erroneous value for 'n'.

---

