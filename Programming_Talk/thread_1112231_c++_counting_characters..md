---
title: "c++ counting characters."
date: 2009-03-31
forum: Programming Talk
---

### Post by Vandorin on 2009-03-31
I'm making a code that counts the words and characters in a text file, so far I've been able to get it to count the right amount of words, but whenever I try to get it to count the characters, it always comes up with 0. I'm sure it's just a pointer somewhere wrong so that the file is reading the end of it, and not counting any chracters, but this is what I have so far:

```

#include <iostream>
#include <string>
#include <fstream>
using namespace std;
void mygetline(istream& is, string &str);
int main()
{
       string filename;
       cout << "Enter Filename" << endl;
       mygetline ( cin, filename );
       ifstream in_file (filename.c_str());
       if ( in_file.is_open() == false )
       {
               cout << "\a Error: coult not open file ";
               system("pause");
               exit(-1);
       }
       int count = 0;
       string word;
       while(in_file >> word )
       {
               count++;
       }

       cout << count << " Words " << endl;

       int count_char = 0;
       char ch;

       while (in_file >> ch  && in_file.eof() == false)
       {
               count_char++;
       }
       cout << count_char << "Characters " << endl;



       system("pause");

}

void mygetline(istream& is, string &str)
{
   str = "";                    // remove old contents
   if (is != cin && is.peek() == '\n')        // skip to next line if needed
       is.get();

   char ch;
   while((ch=is.get()) != '\n' && ch != EOF)    // keep reading chars until
       str += ch;                                // end of line or file reached

}
	


```

Does anyone know what is wrong with it? Or can someone please point me in the right direction? Thanks :D

---

### Post by clustermonkey on 2009-03-31
At the beginning of the loop to count characters you are
already at EOF.  Easiest is to close and reopen the file.

---

### Post by Yacoby on 2009-03-31
> **clustermonkey said:**
> At the beginning of the loop to count characters you are
already at EOF.  Easiest is to close and reopen the file.
Using the seekg function is ever easier
```
std::istream::seekg(0)
```

So you would use
```
in_file.seekg(0)
```

---

### Post by dwhitney67 on 2009-03-31
OMG!

Use getline() to read input from the command line:
```

...
getline(std::cin, filename);
...

```

To read the number of words and characters in the file:
```

...
while (infile >> word)
{
  ++count;
  count_char += word.size();
}
...

```

P.S.  If you need to count the white-spaces and the newlines, then do as Yacoby indicated to seek to the end of the file to compute the difference between the end position and the begin position of the file.
```

...
// get length of file:
in_file.seekg(0, ios::end);
count_char = in_file.tellg();
in_file.seekg(0, ios::beg);
...

```

---

### Post by Vandorin on 2009-03-31
Awesome, thanks guys! I totally forgot about seekg haha, thanks for helping me out :D

---

### Post by 1clue on 2009-03-31
Another thing, if your string is entirely loaded in RAM then you can simply make a copy of the pointer before you start counting words.

I have to ask, is this for a class?  If you just wanted a word count utility, then "wc" does everything you are talking about.

---

### Post by Garratt on 2009-04-01
string line;
int totalChars=0;

while (getline(cin, line)
{
totalChars += line.length();
}

length() works to :P

or if you are counting non-blanks check a post i made a few days ago.

---

