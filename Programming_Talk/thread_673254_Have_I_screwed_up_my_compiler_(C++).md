---
title: "Have I screwed up my compiler? (C++)"
date: 2008-01-20
forum: Programming Talk
---

### Post by Jakk64 on 2008-01-20
I have been trying to write a program for c++ that would search a list of words for one that matches the letters i entered, so far i have this:
```
#include <iostream>
#include <fstream>
#include <cstring>
#include <algorithm>
using namespace std;

string name;
string letters;
string dictionary;
string dictionaryword;
int pairings = 0;


	int main()
		{
			cout<<"Please enter you desired letters\n";
			cin>>letters;
			name = letters;
			sort(letters.begin(), letters.end()); //sorts the letters in the string from lowest value to high
			pairings = 0; //resets the number of pairings
			ifstream intofile;
			intofile.open("wordlist.text");
				if(!intofile)
					{
						cout<<"Error locating file.";
					}
				while(!intofile.eof())
					{
						getline(intofile,dictionary);
						dictionaryword = dictionary;
						sort(dictionary.begin(), dictionary.end());//same as before
							if(letters == dictionary)
								{
								  cout<<"Your letters make the word:"<<dictionaryword<<endl;
								  pairings++;
								}
								
					}
					if(pairings==0)
					               cout<<"Sorry, no words found.\n";
			intofile.close();
			main();
			cin.get();
			return 0;
		}


```
On ubuntu it just stops working when it gets to the while loop, at first i thought this was my fault but after 30minutes of checking i decided to try it on my windows box, and it works just fine. So I am assuming that i have screwed up my installation of my compiler files or something but I'm not really sure. Any help will be greatly appreciated, Thanks :)

---

### Post by mathisdermaler on 2008-01-20
You have a recursive main function.  If you run that, I would expect it to run for quite some time and then die because it ran out of stack space.  What I am surprised about is that it ever finishes on windows.

If you have this trouble again in linux, you can use gdb to debug it.  At your shell prompt, type this.  (Replace <programname> with the name of your compiled executable file)

gdb <programname>
r 
CTRL+C
bt 

this will print out a stack trace that shows what line it's stuck at.

---

### Post by Jakk64 on 2008-01-20
Ah yes, sorry about the main();, its poor but it allowed me to use it repeatedly without opening it again and again.
And thanks for the help, il give it a shot now :)

---

