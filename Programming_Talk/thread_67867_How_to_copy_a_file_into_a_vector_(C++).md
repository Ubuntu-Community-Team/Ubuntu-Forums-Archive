---
title: "How to copy a file into a vector? (C++)"
date: 2005-09-21
forum: Programming Talk
---

### Post by Kyral on 2005-09-21
Hey all.

For a program I'm writing, I need to copy a file character for character into a vector of type char. That includes spaces and endlines. Thing is I kinda don't know how to do it. I was thinking that I could do

 ```
vector.push_back ( file );
``` 

But I'm not sure. Thanks for your help!

PS. If anyone could explain the system() function to me it would be great

---

### Post by LordHunter317 on 2005-09-21
The most trivial way would be to do something like:```
#include <algorithm>
#include <fstream>
#include <iterator>
#include <vector>

int
main()
{
	typedef std::istream_iterator<char> istream_iterator;
	std::ifstream file("example.txt");
	std::vector<char> input;

        file >> std::noskipws;
	std::copy(istream_iterator(file), istream_iterator(),
			  std::back_inserter(input));
}
```Really, the file >> std::noskipws; is the critical operation here: it turns off whitespace skipping on formatted input streams.  Using copy is just convient for slurping a whole file.

---

### Post by bihe on 2005-09-21
read a file and process every single char:
```

#include <iostream>
#include <fstream>
using namespace std;

int main()
{
    int blank_count = 0;
    int char_count = 0;
    int sentence_count = 0;
    char ch;

    ifstream iFile("file.txt");

    if (! iFile)
    {
        cout << "Error opening input file" << endl;
        return -1;
    }

    while (iFile.get(ch))
    {
        switch (ch) {
            case ' ':
                blank_count++;
                break;
            case '\n':
                break;
            case '.':
                sentence_count++;
                break;
            default:
                char_count++;
                break;
        }
    }

    cout << "There are " << blank_count << " blanks" << endl;
    cout << "There are " << char_count << " characters" << endl;
    cout << "There are " << sentence_count << " sentences" << endl;

    return 0;
}

``` 

[google ...](http://www.google.com/search?q=c%2B%2B+read+file&start=0&ie=utf-8&oe=utf-8)

---

### Post by LordHunter317 on 2005-09-21
Your posted code has a problem: that check won't capture all whitespace.  One should use isspace() instead.

I should point out that even though my example uses char, unless you're going to completely ignore lines in whatever you're going to do, reading into a vector<std::string> might be more wortwhile, as then doing line based manipulations is eaiser.

Though, if you're going to do that, slurping into a strstream may be the best solution.  Then you can treat your in-memory copy just like any other I/O stream.

---

### Post by thumper on 2005-09-21
[QUOTE=LordHunter317]The most trivial way would be to do something like:```
#include <algorithm>
#include <fstream>
#include <iterator>
#include <vector>

int
main()
{
 typedef std::istream_iterator<char> istream_iterator;
 std::ifstream file("example.txt");
 std::vector<char> input;

        file >> std::noskipws;
 std::copy(istream_iterator(file), istream_iterator(),
     std::back_inserter(input));
}
```Really, the file >> std::noskipws; is the critical operation here: it turns off whitespace skipping on formatted input streams.  Using copy is just convient for slurping a whole file.[/QUOTE]An alternative is to use the streaming of the file buffer directly using the rdbuf.  This way goes through a temporary string, and constructs the vector from that:
```
#include <vector>
#include <fstream>
#include <sstream>
#include <iostream>

int main(int argc, char* argv[])
{
   if (argc < 2) {
      std::cout << "usage: " << argv[0] << " <filename>\n";
      return 2;
   }

   std::ifstream fin(argv[1]);
   if (fin) {
      std::stringstream ss;
      // this copies the entire contents of the file into the string stream
      ss << fin.rdbuf();
      // get the string out of the string stream
      std::string contents = ss.str();
      std::cout << contents;
      // construct the vector from the string.
      std::vector<char> buff(contents.begin(), contents.end());
   }
   else {
      std::cout << "Couldn't open " << argv[1] << "\n";
      return 1;
   }
   return 0;
}
```

---

### Post by Kyral on 2005-09-21
Wow I didn't expect this much response....

---

### Post by LordHunter317 on 2005-09-21
[QUOTE=thumper]An alternative is to use the streaming of the file buffer directly using the rdbuf.[/quote]I mentioned that, though didn't post code ;), and called it a strstream for some reason :(

However, doing that for the *sole purpose* of putting the data in a vector is pointless, and requires 2X the RAM to complete the copy, to boot.

However, for about any other task where you're not doing line-based I/O, this is probably a superior solution. :)

Though for all practical textual I/O purposes I do, I end up using boost::tokenizer or something wrapped around it, which makes dealing with textual data intuitive and generally easy, for a lot of formats.

---

### Post by jerome bettis on 2005-09-21
i think the answer to most questions like this is "look at the boost libraries".  and it's usually a very good answer.

---

### Post by LordHunter317 on 2005-09-21
Well, I can think of a lot of I/O cases where boost::tokenizer would be useless, even for formatted I/O.  XML is the most obvious and biggest one: a traditional tokenizer (e.g., boost::tokenizer) is rather inadequate here.

That being said, boost::tokenizer is a templated tokenizer, so you could write your template that parsed XML in a more sane fashion.  

However, dealing with XML in a stream like fashion almost never make sense, ignoring a few cases.

But yes, boost:: is wonderful and anyone beginning or experienced with C++ should always  check there first before writing any code.

---

### Post by jerome bettis on 2005-09-22
[QUOTE=LordHunter317]But yes, boost:: is wonderful and anyone beginning or experienced with C++ should always check there first before writing any code.[/QUOTE]

right that's really all i was trying to say.  whether or not it will be a help to him here i have no idea.  in fact i have no idea why you would actually need to do this  but whatever.  i would be interested in hearing why he's doing this

btw you just seem to know everything about everything programming all the time, and that deserves a lot of respect.

---

### Post by thumper on 2005-09-22
[QUOTE=LordHunter317]But yes, boost:: is wonderful and anyone beginning or experienced with C++ should always  check there first before writing any code.[/QUOTE]C'mon, any experienced C++ person should already know what it has to offer and shouldn't need to check every time 8-)

---

### Post by LordHunter317 on 2005-09-22
[QUOTE=jerome bettis]in fact i have no idea why you would actually need to do this  but whatever.[/quote]I can think of a few reasons.  Mostly dealing with statistical distribution of letters/words in a file.  Doing a lot of searching is easier in a vector than a string.

> i would be interested in hearing why he's doing thisAye.  Me as well.

> btw you just seem to know everything about everything programming all the time, and that deserves a lot of respect.Not hardly ;)

---

### Post by Kyral on 2005-09-23
[QUOTE=jerome bettis]right that's really all i was trying to say. whether or not it will be a help to him here i have no idea. in fact i have no idea why you would actually need to do this but whatever. i would be interested in hearing why he's doing this

btw you just seem to know everything about everything programming all the time, and that deserves a lot of respect.[/QUOTE]


I can show you why. If you would just follow the link to the project page...

[http://www.clarkson.edu/projects/cosi/fa2005/students/petermcv/]("http://www.clarkson.edu/projects/cosi/fa2005/students/petermcv/")

Tis the second one :P

Comments welcome, flames will be redirected to /dev/null :P

---

### Post by thumper on 2005-09-23
That doesn't enlighten any.  What does the testing procedure have to do with copying a file into a vector?

Why do it in C++?

---

### Post by Kyral on 2005-09-23
1) I only know C++ right now

2) The program reads a file into the vector to act as a buffer, then outputs it into script to be echoed in the shell script

---

### Post by LordHunter317 on 2005-09-23
It's silly to read it in to a vector just as a buffer, and especially silly to do it as a vector<char>.  Use a stringstream, as thumper showed how.  That gives you I/O streams semantics with in-memory storage.

But if you're just going to write it out to a script, I don't see the point.

Anyway, what you want to do can easily be accomplish by rdiff-backup, a simple command to pull the package list, and some glue.

---

