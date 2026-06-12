---
title: "C++ File String Access Question"
date: 2008-07-31
forum: Programming Talk
---

### Post by Neon612 on 2008-07-31
I'm trying to get a word from a multiple line file(each word is on a separate line).

```

#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main()
{
	int i=0;
	string adjectives[255];
	
	ifstream adjfile ("txt_adj.txt");
	if (adjfile.is_open())
	{
		
		while (! adjfile.eof() && i<255)
		{
			getline (adjfile,adjectives[i]);
			i++;
			cout << adjectives << endl;
		}
		
	adjfile.close();
	}

	return 0;
}
```

The while loop is where I suspect I'm going wrong. It will print out a hex string 255 times, the same string. What can I do to fix it?

---

### Post by WW on 2008-07-31
You are printing the address of the array adjectives.
Change the cout line to
```


			cout << adjectives[i-1] << endl;

```

---

### Post by era86 on 2008-07-31
Just move the i++ at the end of the loop.

Edit: and print out the actual string, not the stream address.

while (! adjfile.eof() && i<255)
{
    getline (adjfile,adjectives[i]);
    cout << adjectives[i++] << endl;
}

This code should do what you want.

---

### Post by dribeas on 2008-07-31
> **Neon612 said:**
> 
```

//...
	int i=0;
	string adjectives[255];
//...
        while (! adjfile.eof() && i<255)
//...
```


Your problem has already been solved, but here are my two cents. Try to use STL containers. Using std::vector instead of an array eases the i<255 check.

Also, there is a not-so-used way of processing input into STL containers (assumes only one word per line):
```

#include <iostream>
#include <fstream>
#include <vector>
#include <iterator>

void dump( std::string const &s )
{
   std::cout << s << std::endl;
}

int main()
{
   std::vector<std::string> adjs;
   std::ifstream adjfile ("txt_adj.txt");
   if (!adjfile.is_open()) return 1;

   std::copy( std::istream_iterator<std::string>(adjfile),
      std::istream_iterator<std::string>(), std::back_inserter(adjs) );
   std::for_each( adjs.begin(), adjs.end(), dump );
}

```

---

### Post by Neon612 on 2008-07-31
> **era86 said:**
> Just move the i++ at the end of the loop.

Edit: and print out the actual string, not the stream address.

while (! adjfile.eof() && i<255)
{
    getline (adjfile,adjectives[i]);
    cout << adjectives[i++] << endl;
}

This code should do what you want.

Thank you that did exactly what I wanted.
Now, will I be able to access each word separatly?

Something like I have the word CAT assigned to adjective[50]. Can I just go cout << adjective[50] to display the word? And will it be able to be reached for more than just displaying it that simply?

---

### Post by dwhitney67 on 2008-07-31
Yep, that should work.

As Dribeas mentioned, you really should consider using a vector to store the strings read from the file in lieu of the array.  The vector provides the means to access the data contained within it using the [] operator.

So in essence, the following should work:
[PHP]#include <vector>
#include <string>
#include <fstream>
#include <iostream>

int main()
{
  std::fstream datafile( "filename", std::ios::in );
  std::vector< std::string > words;

  if ( datafile )
  {
    char word[40] = {0};

    while ( datafile.getline( word, sizeof(word) ) )
    {
      // add the word to the vector
      words.push_back( word );
    }
  }

  // display all words
  for ( size_t i = 0; i < words.size(); ++i )
  {
    std::cout << words[i] << std::endl;
  }

  // display word 10 (note, if it does not exist then an
  // exception will be thrown!)
  std::cout << words[9] << std::endl;

  return 0;
}[/PHP]

---

### Post by Neon612 on 2008-07-31
Okay I may try the vector idea a bit later on. I'm working on teaching myself some basics of C++. And this forum is comming in very handy. :)

Is there a way that I can get rid of the cout line in the while loop but still have the loop do the same actions. I want each line of the file to be assigned to its respective array address but I don't want the word to be displayed.

---

### Post by dwhitney67 on 2008-07-31
Sure - delete the cout line; or comment it out (in case you need it for later).

---

### Post by Neon612 on 2008-07-31
while (! adjfile.eof() && i<255)
{
getline (adjfile,adjectives[i]);
cout << adjectives[i++] << endl;
}

Doesn't the i++ need to stay in there somewhere, other wise the loop count will not advance? Or am I missing something?

Edit: Nevermind I fixed my own problem. Comment out the cout line and add an i++ on a separate line. LIke I said, so far I'm completely self taught, so its a learning experience.

---

### Post by dwhitney67 on 2008-07-31
Sorry I missed that.  Your solution will work.

Alternatively, you can add the increment such as:
[PHP]while (! adjfile.eof() && i++ < 255)[/PHP]
or as:
[PHP]getline( adjfile, adjectives[i++] );[/PHP]
Personally, unless it is needed (and in the cases above, unfortunately it is), avoid the post-increment and instead rely on the pre-increment.  A '++i' is more efficient than a 'i++'.  The 'i++' not only increments the value in the variable 'i', but it also returns the value.  Since this value is not being assigned to anything, what's the point of using it?  It's such a shame that most C++ book authors don't explain this.

So hopefully in the near future when someone posts a for-loop or other similar construct, I will be seeing '++i' for the incrementer.  [-o<

---

### Post by dribeas on 2008-08-01
Agree @dwhitney67, preincrement is better than postincrement. For a simple int it does not make too much of a difference, but with more complex data structures it can make a difference.

Also note that if you use a vector as most people do (without std::copy and iterators) you don't need to take care of the counter:
```

   typedef std::vector<std::string> string_container;
   string_container adjs;
   std::string word;
   // read into vector
   while ( getline( std::cin, word ) ) // or while (std::cin >> word)
   {
      adjs.push_back( word );
   } 
   // print 1
   for ( string_container::const_iterator it = adjs.begin();
        it !=  adjs.end(); ++it )
   {
      std::cout << *it << std::endl;
   } 
   // print 2
   for ( unsigned int i = 0; i != adjs.size(); ++i )
   {
      std::cout << adjs[i] << std::endl;
   }

```

One of the small advantages in the read loop is that the code is simpler to read (once you get used): you read a work, you push it into the vector. No need to have any loop variables, no need to decide whether pre-increment or post-increment, in the loop condition or inside the {}...

I have also added two common ways of iterating over a container just for the sake of it. The first one (through the use of iterators) is better as it allows you to change the container type. (Just change the typedef for std::list<std::string>)...

Note that learning STL _is_ learning C++. The earlier the better.

   David

---

