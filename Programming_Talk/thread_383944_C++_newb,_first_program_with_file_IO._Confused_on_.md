---
title: "C++ newb, first program with file I/O. Confused on a bunch of points."
date: 2007-03-13
forum: Programming Talk
---

### Post by Chake99 on 2007-03-13
Yes. Currently I've been making a bunch of small programs with the help of tutorials (not ones given in tutorials per se) to try and teach myself C++. Anyways I read the tutorial here: [http://www.cprogramming.com/tutorial/lesson10.html](http://www.cprogramming.com/tutorial/lesson10.html)) and I was trying to create a program that would save text files, append to text files, and read them.

This was the code I came up with: 
```
 #include <iostream>
#include <fstream>

using namespace std;

void read () {
	string name;
	cout<<"what is the name of the file you wish to read ?\n";
	getline(cin, name, '\n');
	ifstream b_file ( "test.txt" );
	cout<< b_file <<"\n";
	b_file.close();
}

void write () {
	string text;
	string name;
	
	cout<<"what is the name of the file you wish to write too?\n";
	getline(cin, name, '\n');
	cout<<"please enter the text you would like to write, up to 400 characters.\n";
	**cin.getline(text, 400);**
	ofstream a_file ( "test.txt" ); 
	a_file<< text;
	cout << "The text has been entered \n \n";
}

void append () {
	string text;
	string name;
	
	cout<<"what is the name of the file you wish to append too?\n";
	getline(cin, name, '\n');
	cout<<"please enter the text you would like to write, up to 400 characters.\n";
	**cin.getline(text, 400);**
	ofstream a_file ( "test.txt", ios::app );
	a_file<< text;
	cout << "The text has been entered \n \n";
}

int main () {
	bool end = false;
	char choice;
	do {
		cout<<"Do you want to:\n";
		cout<<"a. read a file\n";
		cout<<"b. write a new file or overwrite an old file\n";
		cout<<"c. append to an existing file\n";
		cout<<"d. quit\n \n";
		cin>> choice;
		switch (choice) {
			case 'a' : read();
				break;
			case 'b' : write();
				break;
			case 'c' : append();
				break;
			case 'd' : end = true;
				break;
		}
	} while (end == false) ;
	return 0;
}[/quote]

It will not compile with the two lines in bold, instead spitting out > test.cpp: In function &#8216;void write()&#8217;:
test.cpp:22: error: no matching function for call to &#8216;std::basic_istream<char, std::char_traits<char> >::getline(std::string&, int)&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/istream:581: note: candidates are: std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::getline(_CharT*, std::streamsize, _CharT) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/istream:397: note:                 std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::getline(_CharT*, std::streamsize) [with _CharT = char, _Traits = std::char_traits<char>]

```

For each of them. Replacing them both with getline(cin, text, '\n') however does work, but it does not allow me to limit the number of characters. Why can't I use cin.getline()?

Secondly, 
[quote]cout<< b_file <<"\n";  outputs what looks like a memory location/pointer in my read method. How would I output the entire file? I know this >  b_file>> str;
cout<< str;  supposedly outputs a single word, but that doesn't help me much.

Thirdly, replacing the examples of "test.txt" in my program with the variable name, name, results in further compile errors. How would one operate on a file-name that was inside a string?

Any help that could be given to a beginner would be great.

---

### Post by peabody on 2007-03-13
> **Chake99 said:**
> ... I was trying to create a program that would save text files, append to text files, and read them.

This was the code I came up with: 
```
 #include <iostream>
#include <fstream>

```


Methinks you should probably have an #include <string> just in case

> 

...

It will not compile with the two lines in bold, instead spitting out ```
test.cpp: In function ‘void write()’:
test.cpp:22: error: no matching function for call to ‘std::basic_istream<char, std::char_traits<char> >::getline(std::string&, int)’
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/istream:581: note: candidates are: std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::getline(_CharT*, std::streamsize, _CharT) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/istream:397: note:                 std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::getline(_CharT*, std::streamsize) [with _CharT = char, _Traits = std::char_traits<char>]

```


To my knowledge cin.getline doesn't have an overloaded version for the C++ string type.  That's what the getline stand alone function is for.

> 
For each of them. Replacing them both with getline(cin, text, '\n') however does work, but it does not allow me to limit the number of characters. Why can't I use cin.getline()?


This is a common problem of learning C++ before C.  C++ really has two ways strings can be represened.  The old C way of character arrays, and the new C++ way of the string type.  If you want to limit the characters, use a character array with cin.getline.

> 
Secondly, 
 outputs what looks like a memory location/pointer in my read method. How would I output the entire file? I know this  supposedly outputs a single word, but that doesn't help me much.


My C++ is rusty, so I hope someone better than I can enlighten, but I think you're going to have to use the .read() member function plus a buffer and a loop.  There might be an easier way, but I think that's going have to be it.

> 
Thirdly, replacing the examples of "test.txt" in my program with the variable name, name, results in further compile errors. How would one operate on a file-name that was inside a string?


Another problem of the (const char*) type vs the (string) type.  Try name.data().

> 
Any help that could be given to a beginner would be great.

Hope that helped but I'm no C++ expert.

---

### Post by Chake99 on 2007-03-14
Thanks a lot, and yeah it helped. I guess I was mixing up char array strings and c++ style ones. I was able to get my read() FUNCTION (I just realized I had been calling it a method because of java) to work by copying code from another tutorial, that I'm not sure I understand it, and when I tried to get the filename selection to work in a similar way it won't compile. 

This is my modified read method with comments explaining what I believe I'm doing:
```

void read () {
	int length; // the number of chars in the text file
	char * buffer; // a pointer named buffer to a char sized memory slot
	char * name[10]; // a pointer to 10 char sized memory slots
	cout<<"what is the name of the file you wish to read?\n";
	cin.getline(*name, 10); // memory slots pointed to by name now hold the name of file to open
	ifstream b_file ( name, ios::ate ); // doesn't work* 
	length = b_file.tellg(); // length is set to the position in the file
	b_file.seekg (0, ios::beg); // sets position to the beginning of file
	buffer = new char [length]; // buffer now points to a char array that is length slots long
	b_file.read (buffer,length); // reads the number of characters in the array length, and stores it in the location pointed to by buffer
	b_file.close(); // b_file is close
	cout.write (buffer,length); // outputs length of the characters stored at buffer.
	delete[] buffer;
	cout << "\n"
}

```
* I was hoping to open the file by passing the memory location of the name of the file to open. Like this it does not compile, but spits out >  test.cpp: In function &#8216;void read()&#8217;:
test.cpp:12: error: no matching function for call to &#8216;std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(char* [10], const std::_Ios_Openmode&)&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/fstream:442: note: candidates are: std::basic_ifstream<_CharT, _Traits>::basic_ifstream(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/fstream:428: note:                 std::basic_ifstream<_CharT, _Traits>::basic_ifstream() [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/iosfwd:89: note:                 std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(const std::basic_ifstream<char, std::char_traits<char> >&) 

If I change name to *name, it compiles, but trying to run the read() function delivers a segmentation fault.

Once again help from anyone would be great.

---

### Post by WW on 2007-03-14
Declare **name** as
```
    char name[10];
```
and remove the ***** from in front of **name** in the getline function call.

Your declaration, **char *name[10]**, declares **name** to be an array of 10 pointers to characters, not an array of 10 characters.

---

### Post by peabody on 2007-03-14
Yeah, what WW said, and I thought I might add something...

1) make sure all character arrays are the length of your intended string + 1.  This is because all C style strings are (well, *should be*) null terminated.  That is, the last character of the string is assumed to be a null byte.

2) arrays are another spot of confusion regarding C and C++.  Pointers are their own type, and arrays are another type, but everywhere you use an array it's sometimes the same as if you'd used a pointer.  This takes getting used to, as declaring an array and declaring a pointer are two different things.  For example:

```

#include <iostream>

using namespace std;

int main(int argc, char *argv[]) {
char *name;
char aryname[] = "Hello";

cout << "name uses " << sizeof(name) << " bytes while aryname uses " << sizeof(aryname) << " bytes." << endl;

name = aryname;

cout << "Name now points to the string: " << name << endl;
cout << "But name is still just " << sizeof(name) << " bytes." << endl;

return 0;
}

```

On x86 the output would be:

"name uses 4 bytes while aryname uses 6 bytes.
Name now points to the string: Hello
But name is still just 4 bytes."

notice how aryname is one bigger than the number of characters in the string "Hello"?  Notice how I was able to assign the array to the character pointer name?

aryname used by itself usually gets interpreted as a (char*) type, which uses 4 bytes on x86.  But declaring aryname set aside 6 bytes while declaring name set aside only 4.  sizeof can interpret the size of aryname correctly because it knows that it was declared as an array in this scope.  But sizeof(name) will always return 4 bytes in this context.

If that's extremely confusing, I'm willing to answer any questions you might have.

---

### Post by Wybiral on 2007-03-14
Well, the only difference really is that the compiler knows exactly how much memory that array is pointing to. It's really still a pointer, the compiler just knows more about what it's pointing to.

---

### Post by Chake99 on 2007-03-14
Java is so much easier... but I guess it just really sucks which is why I'm trying to learn c++. 

I think I get what you guys are saying about arrays, they're just pointers to a bunch of elements that unlike when a pointer is used can still be accessed independently (array[1]).

> **WW said:**
> Declare **name** as
```
    char name[10];
```
and remove the ***** from in front of **name** in the getline function call.

Your declaration, **char *name[10]**, declares **name** to be an array of 10 pointers to characters, not an array of 10 characters.

Alright, I think I understand what you are saying. I changed what you said and I get

```

void read () {
	int length;
	char * buffer;
	char name[11]; 
	cout<<"what is the name of the file you wish to read?\n";
	cin.getline(name, 10); 
	ifstream b_file ( name, ios::ate ); 
	length = b_file.tellg(); 
	b_file.seekg (0, ios::beg); 
	buffer = new char [length]; 
	b_file.read (buffer,length);  
	b_file.close(); 
	cout.write (buffer,length);
	delete[] buffer;
	cout << "\n";
}

```

Which then when running gives this: >  Do you want to:
a. read a file
b. write a new file or overwrite an old file
c. append to an existing file
d. quit

a
what is the name of the file you wish to read?
terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
Aborted


std::bad_alloc?

> bad_alloc (or classes derived from it) is used to report allocation errors from the throwing forms of new.  Which is funny because the only new in the function (buffer = new char [length]; ) used to work.

> 1) make sure all character arrays are the length of your intended string + 1. This is because all C style strings are (well, should be) null terminated. That is, the last character of the string is assumed to be a null byte.The tutorial I was using mentioned something like this, but I didn't get how it worked. When I declare a c-string is the last element by default a null byte, and do I just need to read info into previous characters? Or when I write cin.getline() does it automatically put a null char on to the end of the users string? Is the null char included in the number in the brackets of cin.getline? (yes I'm confused).

> notice how aryname is one bigger than the number of characters in the string "Hello"? Notice how I was able to assign the array to the character pointer name?
 
 aryname used by itself usually gets interpreted as a (char*) type, which uses 4 bytes on x86. But declaring aryname set aside 6 bytes while declaring name set aside only 4. sizeof can interpret the size of aryname correctly because it knows that it was declared as an array in this scope. But sizeof(name) will always return 4 bytes in this context.
 
 If that's extremely confusing, I'm willing to answer any questions you might have.

Ok, the size of a pointer remains constant regardless of how much it is pointing to. I sort of get it, but once you're giving the pointer large numbers of memory addresses to keep track of via arrays why wouldn't it increase? Does it work via a range or something?

I think I should switch tutorial sites.

And once again thanks guys, this help is great.

---

### Post by WW on 2007-03-14
Hi Chake99,

I compiled and ran this program.
```
#include <iostream>
#include <fstream>

using namespace std;

void read () {
	int length;
	char * buffer;
	char name[11]; 
	cout<<"what is the name of the file you wish to read?\n";
	cin.getline(name, 10); 
	ifstream b_file ( name, ios::ate ); 
	length = b_file.tellg(); 
	b_file.seekg (0, ios::beg); 
	buffer = new char [length]; 
	b_file.read (buffer,length);  
	b_file.close(); 
	cout.write (buffer,length);
	delete[] buffer;
	cout << "\n";
}

int main()
    {
    while (1)
        read();
    }

```

If I entered the name of a text file that existed, the program worked.  If I entered the name of a file that did not exist, or if I simply hit Enter without typing a name, or if I pressed ctrl-D, I got the same error that you did.  Your code doesn't check if the attempt to open the file was successful.  Are you sure the file that you entered actually exists?

---

### Post by Chake99 on 2007-03-14
That's bizarre. 

Your program works on my computer too, but mine reaches the error before one has the option of inputting the filename. I pasted your identical read method and there is no change. 

I added a cin.get(); after the cin.getline(); in my program and one can input a filename (unsure if it is read) but the program still reaches std::bad_alloc.

My main method is:
```
 int main () {
	bool end = false;
	char choice;
	do {
		cout<<"Do you want to:\n";
		cout<<"a. read a file\n";
		cout<<"b. write a new file or overwrite an old file\n";
		cout<<"c. append to an existing file\n";
		cout<<"d. quit\n \n";
		cin>> choice;
		switch (choice) {
			case 'a' : read();
				break;
			case 'b' : write();
				break;
			case 'c' : append();
				break;
			case 'd' : end = true;
				break;
		}
	} while (end == false) ;
	return 0;
}
```
So I fail to see the problem.

This is truly strange.

---

### Post by WW on 2007-03-14
Add this line immediately after ** cin >> choice; **
```

	cin.ignore(numeric_limits<streamsize>::max(), '\n');

```
The problem is that **cin >> choice ** only ``uses up'' one character from the input stream, so your Enter key is still in the buffer when you call **getline**.  That call to **ignore** will discard the existing input, so when you get to your **getline**, it really will get a new line of input.


P.S. I got that tip from a bit of code that forum member **lnostdal** gave in this thread: [http://ubuntuforums.org/showthread.php?t=380744](http://ubuntuforums.org/showthread.php?t=380744)

---

### Post by Chake99 on 2007-03-14
Thanks, it works perfectly now. Do you know the difference between cin.ignore() and cin.ignore(numeric_limits<streamsize>::max(), '\n'); though? I used the former, since i had seen it before and it was less intimidating, and it runs. Does cin.ignore only ignore one character or something?

---

### Post by WW on 2007-03-15
Here's a link to some information about **ignore**: [http://www.cplusplus.com/reference/iostream/istream/ignore.html](http://www.cplusplus.com/reference/iostream/istream/ignore.html)

> Does cin.ignore only ignore one character or something?

Yes, **ignore()** (with no arguments) will only ignore one character.  If you use this, and type two characters before hitting Enter, then the Enter will again be left over for your call to getline(...).  The call to ignore that I gave (which I glommed from lnostdal's code) will ignore all characters up to the next newline.

---

### Post by peabody on 2007-03-15
> **Chake99 said:**
> Java is so much easier... but I guess it just really sucks which is why I'm trying to learn c++. 

Eh, Java's not that bad.  My only complaint with Java I've ever had is that it's implemented with a virtual machine.  I really think the Java folks should have just gone with native language compilers from the get-go.

> 
I think I get what you guys are saying about arrays, they're just pointers to a bunch of elements that unlike when a pointer is used can still be accessed independently (array[1]).


Pretty much true, although if you point a pointer at an array, you can use the same subscripting syntax to access the array (name[0] would equal 'H').

> 
Which then when running gives this: 

std::bad_alloc?

 Which is funny because the only new in the function (buffer = new char [length]; ) used to work.


I'd use a cout << length to see what tellg was actually giving you.  If you passed a negative number to new I could imagine it would throw bad_alloc.

> 
The tutorial I was using mentioned something like this, but I didn't get how it worked. When I declare a c-string is the last element by default a null byte, and do I just need to read info into previous characters? Or when I write cin.getline() does it automatically put a null char on to the end of the users string? Is the null char included in the number in the brackets of cin.getline? (yes I'm confused).


When you declare arrays in C and C++, the values are completely random, they could be whatever was last in that memory.  The null byte is just the number 0.  getline will insert a null byte +1 spot past where it last put a character.  Here's a link to some docs on the getline function:

[http://cppreference.com/cppio/getline.html](http://cppreference.com/cppio/getline.html)

and here's some example code I wrote to illustrate the effect:

```

#include <iostream>

using namespace std;

int main(int argc, char *argv[]) {
        char dude[10];
        cin.getline(dude, 10);

        cout << "Last character is: " << (int) dude[9] << endl;
        return 0;
}

```

If you input more than 9 characters to this program, only 9 characters will be read into dude, and the 10th byte will be set to null (number zero, which will get printed).  If you input less than that, the null byte will be inserted earlier and dude[9] will represent whatever random piece of memory it previously was (which could happen to be zero on occasion).

> 
Ok, the size of a pointer remains constant regardless of how much it is pointing to. I sort of get it, but once you're giving the pointer large numbers of memory addresses to keep track of via arrays why wouldn't it increase? Does it work via a range or something?


Since you're a Java guy, let me say that, unlike Java, C and C++ don't know the length of arrays at run-time (only compile time) and therefore do not do any bounds checking.

I also should have clarified something...sizeof doesn't work at runtime, it's what they call a compiler macro.  Because the compiler can only work with what it was given, it knows that aryname was declared to be a 6 character array, but it only knows that name is a character pointer.  Whatever name gets pointed to is a run-time thing and the compiler has no way of knowing how much space name could be pointing to.  That has to be kept track of by the programmer.  In fact, if you pass an array to a function that takes an array, it's typically just passed as a pointer, so an integer argument is typically also passed to the same function, to tell it how long the array is.

> 
And once again thanks guys, this help is great.

No problem, and don't get discouraged.  Some say that C++ is quite possibly the most complicated language there is :).

---

