---
title: "(C++) Reading a file with fstream always gives me an extra char"
date: 2010-03-24
forum: Programming Talk
---

### Post by WillFerrellLuva on 2010-03-24
my objective here is to read a file and store it in a string.  I always seem to be getting an extra character in my string for some reason:

```

#include <fstream>
#include <iostream>
#include <string>
using namespace std;


int main()

{
	fstream in;
	char char_temp = ' ';
	int int_temp = 0;
	int int_count[10] = {0}; 
	int char_count[26] = {0};
	string contents = "";
	
	in.open("test");
	if(in.good())
	{
		while(!in.eof())
		{
			in>>char_temp;
			contents += char_temp;
		}
	}
	else 
	{
		cout << "Error opening file." << endl;
	}
	in.close();
	
	//contents.erase(contents.size()-1); 
	for(unsigned int i = 0; i < contents.size(); i++)
	{
		cout << contents[i] << endl;
	}

```

I can just erase the last char but this solution bothers me.  Anybody know what I am doing wrong here?  Any help will be greatly appreciated.

---

### Post by soltanis on 2010-03-24
Although I am not familiar with the particular C++ semantics, I can tell you that in C when you are reading a file, the EOF marker is not set until after the last read which reached the end of file. In other words, you'd do

```

read -> returns last char in file
read -> returns last char in file, sets EOF flag

```

The way you should protect against this is *after* you do the read you check the EOF flag, then write the char into your buffer if it's clear. Otherwise you close the file/buffer.

---

### Post by WillFerrellLuva on 2010-03-24
tyvm for the info.

---

