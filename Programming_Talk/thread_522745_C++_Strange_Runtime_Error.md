---
title: "C++ Strange Runtime Error"
date: 2007-08-11
forum: Programming Talk
---

### Post by Yes on 2007-08-11
Here, I'll post my entire program:

```
#include <iostream>

#include <cstdlib>

#include <string>

using namespace std;

class Decimal {
	public:
		void getDecimal ();
		void convertDecimalToFraction (string);
		Decimal ();
		~Decimal ();
};

Decimal::Decimal () 
{
	
	
}

Decimal::~Decimal ()
{
	
}

void Decimal::getDecimal ()
{
	string decimal;
	
	cout << "\nPlease enter a decimal in the format x.y : " ;
	cin >> decimal;
	
	convertDecimalToFraction (decimal);
}

void Decimal::convertDecimalToFraction (string decimal) 
{
	double numerator = 0; 
	double denominator = 0;
	int currentPlace = 1;
	int dotIndex;
	
	dotIndex = decimal.find ('.', 0);
	
	for (unsigned int i = 0; i < (decimal.substr(dotIndex, decimal.length())).length(); i++)
	{
		switch ((decimal.substr(dotIndex, decimal.length())).at (i)) 
		{
			case '1':
				numerator+= (1/currentPlace);
				break;
			case '2':
				numerator+= (2/currentPlace);
				break;
			case '3':
				numerator+= (3/currentPlace);
				break;
			case '4':
				numerator+= (4/currentPlace);
				break;
			case '5':
				numerator+= (5/currentPlace);
				break;
			case '6':
				numerator+= (6/currentPlace);
				break;
			case '7':
				numerator+= (7/currentPlace);
				break;
			case '8':
				numerator+= (8/currentPlace);
				break;			
			case '9':
				numerator+= (9/currentPlace);
				break;
		}
		currentPlace*=10;
		
	}
	
	currentPlace = 1;
	
	for (unsigned int i =0; (decimal.substr(0, dotIndex)).length(); i++)
	{
		switch ((decimal.substr(0, dotIndex)).at (i)) 
		{
			case '1':
				denominator+= (1/currentPlace);
				break;
			case '2':
				denominator+= (2/currentPlace);
				break;
			case '3':
				denominator+= (3/currentPlace);
				break;
			case '4':
				denominator+= (4/currentPlace);
				break;
			case '5':
				denominator+= (5/currentPlace);
				break;
			case '6':
				denominator+= (6/currentPlace);
				break;
			case '7':
				denominator+= (7/currentPlace);
				break;
			case '8':
				denominator+= (8/currentPlace);
				break;			
			case '9':
				denominator+= (9/currentPlace);
				break;
		}
	}
	
	
}

class Fraction 
{
	public:
		int denominatorNum, numeratorNum;
		void convertFractionToDecimal (string);
		void getFraction ();
		Fraction ();
		~Fraction ();
};

Fraction::Fraction () 
{
	
}

Fraction::~Fraction () 
{
	
}

void Fraction::getFraction ()
{
	string fraction;
 	
	cout << "\nPlease enter a fraction in the format x/b ";
	cin >> fraction;
	
	convertFractionToDecimal (fraction);
}

void Fraction::convertFractionToDecimal (string fraction) 
{
	
	string denominatorChar, numeratorChar;
	int slashIndex = fraction.find('/', 0);
	
	numeratorChar = fraction.substr(0, fraction.length() - slashIndex);
	denominatorChar = fraction.substr(slashIndex+1, fraction.length());
	
	for (unsigned int i = 0; i < numeratorChar.length(); i++) 
	{
		for (int a = numeratorChar.length()-a; a < 0; a--) 
		{
			switch (numeratorChar.at(a)) {
				case '1': 
					numeratorNum+=1*10;
					break;
				case '2': 
					numeratorNum+=2*10;
					break;
				case '3': 
					numeratorNum+=3*10;
					break;
				case '4': 
					numeratorNum+=4*10;
					break;
				case '5': 
					numeratorNum+=5*10;
					break;
				case '6': 
					numeratorNum+=6*10;
					break;
				case '7': 
					numeratorNum+=7*10;
					break;
				case '8': 
					numeratorNum+=8*10;
					break;
				case '9': 
					numeratorNum+=9*10;
					break;		
			}		
		}
	}
	
	for (unsigned int i = 0; i < denominatorChar.length(); i++)
	{
		for (int a = denominatorChar.length()-a; a < 0; a--) 
		{
			switch (denominatorChar.at(a)) {
				case '1': 
					denominatorNum+=1*10;
					break;
				case '2': 
					denominatorNum+=2*10;
					break;
				case '3': 
					denominatorNum+=3*10;
					break;
				case '4': 
					denominatorNum+=4*10;
					break;
				case '5': 
					denominatorNum+=5*10;
					break;
				case '6': 
					denominatorNum+=6*10;
					break;
				case '7': 
					denominatorNum+=7*10;
					break;
				case '8': 
					denominatorNum+=8*10;
					break;
				case '9': 
					denominatorNum+=9*10;
					break;		
			}		
		}
	}
	
	cout << "\n\nThe decimal form of " << numeratorNum << "/" << denominatorNum 
			<< " is " << numeratorNum/denominatorNum << ".\n" << endl;
	
			
	system("pause");
}
	

int main()
{
	int userChoice = 0;
	Fraction fraction;
	Decimal decimal;
	
	cout << "Welcome to the Fraction Decimal Converter!  Your options are:" << endl;
	cout << "\n1. Convert a decimal to a fraction." << endl;
	cout << "2. Convert a fraction to a decimal." << endl;
	cout << "3. Quit." << endl;
	cout << "\nPlease enter the number for what you want to do: " ;
	cin >> userChoice;
	
	switch (userChoice) {
		
		case 1:
			decimal.getDecimal ();
			break;
		case 2:
			fraction.getFraction ();
			break;	
	}
	
	return 0;
}
```

The problem is in the getDecimal and getFraction functions, when I try to get the user's string. 

Here's the error I get:

```
terminate called after calling an instance of 'std::out_of_range'
     what(): basic_string::at
Aborted (core dumped)
```

What does this mean, and how do I fix it?

Thanks.

---

### Post by Jessehk on 2007-08-11
I'm too lazy to go through your code and find the source of the exceptions (but my tip would be to be sure to check all the areas in which you access a certain part of the string. It looks like your trying to get something that isn't there from the error message.)

My one bit of useful advice would be to be careful of copying versus references.

```

#include <iostream>
#include <string>

void greet_BAD( std::string person ) {
    // the "person" string is copied from
    // the string you supply to the function.
    // This takes more time and memory.
    std::cout << "Hello, " << person << std::endl;
}

void greet_GOOD( const std::string &person ) {
    // Here, we're using a const reference which
    // is similar to a pointer in that the actual object
    // is not copied, but the "location" of the object is
    // passed. Here, person is the exact same string you supplied
    // to the function, not a copy. This is much more efficient.
    std::cout << "Hello, " << person << std::endl;
}

int main() {
    std::string person( "Joe" );
    
    greet_BAD( person );
    greet_GOOD( person );
}

```

---

### Post by bigboy_pdb on 2007-08-11
To be honest I've only taken a quick look through your code. I was thinking that if the problem is with string manipulation then why not use numeric operations instead of string operations?

You could do this using the following methods:
```

/*
Convert the string so that there are two parts; a whole number 
that is greater than or equal to 0 and a decimal part that is between 
0 and 1. For example, if the number is 13.45 then the whole part 
is 13 and the decimal part is 0.45. Since I cannot remember how to 
convert strings to integers and doubles you may need to figure out 
that part by performing a search or reading a book/manual.
*/
int whole; // The whole part of the number
double decimal; // The decimal part of the number

/*
To get the rightmost (tens) digit in the whole part use the following code
*/
int digit = whole - ((int)(whole/10) * 10);

/*
To shift the digits right in the whole part use the following code
*/
whole = (int)(whole/10);

/*
To read the leftmost (tenths) digit in the decimal part use the following code
*/
int digit = (int)(decimal*10);

/*
To shift the digits left in the decimal part use the following code
*/
decimal = decimal*10 - (int)(decimal*10);

```

I haven't tested this code (because I'm pretty tired right now) but if you can understand the concepts then you should be able to use these methods to replace the string methods that you're using.

Tomorrow I'll try to come back and help you more if you want.

---

### Post by bigboy_pdb on 2007-08-11
After getting some sleep I took another look at the code and the error. What I've found is that usually when I get some sort of error stating that something is "out of range" or "out of bounds" that probably means that an operation is being performed on a place value that doesn't exist. In an array it would be an array position that doesn't exist and in a string it is most likely a character position that doesn't exist.

I can already see a few problems with your code. **decimal.substr(dotIndex, decimal.length())** returns everything from the decimal to the position past the last character.

Let me give an example.

"12.34" has a length of 5 (which means that **decimal.length()** has the value 5) and **dotIndex** would be 2. The character 0 in the string is "1", character 1 is "2", character 2 is ".", character 3 is "3", and character 4 is "4".

**decimal.substr(dotIndex, decimal.length())** starts at the character at dotIndex and gets decimal.length() characters following it. So it starts at character 2 and gets 5 characters. Thus, it gets characters 2 through 6, meaning it returns ".34" and it attempts to return a 4th, 5th, and 6th character that don't exist.

One thing that I think you should do is you should assign the value of what **decimal.substr(dotIndex, decimal.length())** (which will be different after you correct your code) to a variable and use the variable instead of repeatedly making that call because if you change one call and forget to change another, you may have a difficult time finding the bug.

Also, you should check if the string has a decimal in the first place, and you should check whether or not there are any characters following the decimal because someone could provide inputs like ".3" or "4." (although you should be doing more error checking than this in the end anyway but it's still something to take into consideration).

If your functions that take in the string that represents a rational number assume that all inputs will be of the form "x_0...x_i.x_i+1...x_n" where i >= 0 and n >= i+1 (which is basically saying that there must be at least one digit before the decimal and one digit following the decimal) then you can use the following code to extract the digits following the decimal.

**decimal.substr(dotIndex+1, decimal.length() - 1 - dotIndex)**

The **dotIndex+1** starts at the character following the decimal. The greatest number of characters that can ever be read from a string are **decimal.length()** characters because the characters go from 0 to **n** which means that **string.length()** returns **n+1**. If **dotIndex** is **i** and the last character is **n** then we want to read **n - i** characters (and thus we read **decimal.length() - 1 - dotIndex** characters since **decimal.length()** returns n+1).

---

### Post by Yes on 2007-08-12
Ok, thanks.  I haven't got a chance to try it out yet, but I'll let you know if it worked.

I have another question, though.  Why do people sometimes use std::cout, std::endl, etc. instead of just cout and endl?  Is that considered to be a better coding practice, or is it just a matter of preference?

---

### Post by bigboy_pdb on 2007-08-12
When people type "std::cout", "std::cin", or "std::endl" this is because they didn't specify the that the namespace of cout, cin, and endl is std.

The following code adds the code from the standard library "iostream" to the rest of your code and it specifies that the namespaces cout, cin, and endl belongs to the namespace std:
```

#include <iostream>
using std::cout;
using std::cin;
using std::endl;

```

Specifying this allows you to omit the "std::" from the other function calls. Doing this makes it easier to write code, it allows you to write it more quickly, and it makes your code easier to read. So in other words, it is a good idea to use "cout", "cin", and "endl" instead of "std::cout", "std::cin", and "std::endl" but you should use "using" to specify what namespace you're using.

---

### Post by aks44 on 2007-08-12
> **bigboy_pdb said:**
> Doing this makes it easier to write code, it allows you to write it more quickly, and it makes your code easier to read.

Well this is a long debated topic, but... I totally disagree on that ;)

IMHO the "speed gain" is totally neglectible, and contrary to what you said I find that the std:: prefix greatly improves readability.

Again, this is a matter of personal preference. As far as I'm concerned I used to use **using namespace std;** until I started working on real life projects, where I found unqualified names a pain to read & maintain.
Now the *only* case when I use a **using** directive is when a derived class' member hides a base one (eg. when overloading a function in the derived class).

The thing is: code should be designed for maintenability before any other matter (except correctness). If typing a few more keystrokes means that I won't have any trouble reading the code in a few months, well...

---

### Post by bigboy_pdb on 2007-08-12
> **aks44 said:**
> 
The thing is: code should be designed for maintenability before any other matter (except correctness). If typing a few more keystrokes means that I won't have any trouble reading the code in a few months, well...


I think that the order of precedence for what is considered to be important is dependent on the project and circumstances at hand. For example, portability or deadlines might be considered more important than having code that is maintainable by other programmers (especially if the project's programmers don't change often). Although people's bad habits can (and should) be changed and it should never be assumed that a programmer will be present for certain periods of time so I do agree that maintainability is important. Also, what you find easily maintainable someone else may not.

With respect to speed increases (when typing the code), that's dependent on how many times the person uses "cout", "cin", and "endl" and how fast the person can type. To be honest the speed increase is negligible for me as well, but I'm not assuming anything about the OP's abilities.

With respect to readability, that's dependent on the person who is reading the code and how the code is written (i.e. whitespace, tabbing, length of variable names, length of the lines). I usually find it easier to find occurrences of "cout" than "std::cout" (though I'm sure that I could train myself out of doing that).

In the end, it's a matter of the circumstances under which the code is being read and the person who's doing it. My response about using "std::" was based on what I looked up in a C++ book and the pros that I could think of at the time for using it. If there are a number of good reasons why it shouldn't be used that you're aware of and you have sources or links to them, perhaps you can post them (or maybe state them).

Outside of all this (and more generally), I know that the OP asked about "std::" but if this becomes anything more than simple responses to his/her question it might be a good idea to create a new thread in response because otherwise this thread will have two topics and the second isn't all that relevant to the first/original topic.

---

### Post by Yes on 2007-08-17
Ok, I've changed projects, but I'm still getting the same error.  Here's my new code:

```
#include <iostream>

#include <cstdlib>

#include <string>

#include <fstream>

using namespace std;


class M3Uplaylist 
{
	public:
		void getplaylistFile ();
		void makePlaylist (string);
		M3Uplaylist ();
		~M3Uplaylist ();
};

M3Uplaylist::M3Uplaylist ()
{
	
}

M3Uplaylist::~M3Uplaylist () 
{
	
}

void M3Uplaylist::getplaylistFile () 
{
	string playlistFile;
	int m3uFileExtensionLocation;
	
	cout << "Please enter the playlist name: ";
	cin >> playlistFile;
	cout << endl;
	
	m3uFileExtensionLocation = playlistFile.rfind (".m3u");
	
	if (m3uFileExtensionLocation != playlistFile.length () - 4)
	{
		cout << "Error:  Invalid filetype.  Must be type .m3u" << endl;
	}
	
	else 
	{
		makePlaylist (playlistFile);
	}
	
}

void M3Uplaylist::makePlaylist (string playlistFile)
{
	fstream playlist;
	string currentLine;
	string fileExtension;
	string playlistString;
	int songNumber = 0;
	int playlistCommaIndex;
	
	playlist.open (playlistFile.c_str()); 
	
	while (! playlist.eof() )
	{
		getline (playlist, currentLine);
		
		**fileExtension = currentLine.substr (currentLine.length () - 4, 3);**
		
		if ((fileExtension.compare (".mp3") || fileExtension.compare (".MP3")
			|| fileExtension.compare (".ogg") || fileExtension.compare (".OGG"))
			!= 0)
		{
			songNumber++;
			playlistCommaIndex = currentLine.find (',' , 0);
			playlistString += songNumber;
			playlistString += ".\t";
			playlistString += currentLine.substr (playlistCommaIndex+1, 
				currentLine.length () -1 -playlistCommaIndex);
			playlistString += "\n";
		}
			
	}
	
}


int main()
{
	
	M3Uplaylist m3uPlaylist;
	
	m3uPlaylist.getplaylistFile ();
	
	return 0;
}
```

The bolded bit is the parts that give me the error.  I don't think it's  trying to make the substring past the end of the currentLine, because if I get the same error when I make it go 0 characters from the starting point.

Thanks.

---

### Post by bigboy_pdb on 2007-08-17
Are there ever blank lines in a .m3u file? If so then that might be the cause of your error. You might want to try printing all the lines using something like:
cout << "#" << currentLine << "#" << endl;

You should put this line after **getline(playlist, currentLine)**. Also, while you're doing it you should comment out the rest of the code in the block for the while loop.

---

### Post by Yes on 2007-08-17
Hmm, that makes sense.  Since I'm not going to be displaying the contents of the file to the user, I just put an if statement that would check if the line was blank.

What could be causing my while loop to loop infinitely?

Also, if I open a file using the function myfile.open(file), if the file doesn't already exist, does it create the file?  Can you have multiple files open at once?

Thanks.

---

### Post by bigboy_pdb on 2007-08-18
I'm aware that you're not going to be posting the contents of the file to the user (due to your code). You can use print statements to help debug your code. The reason why you should use them (and why you should later learn to use debuggers) is because you have no way of knowing what information is within a variable if you don't check it. Printing variables to the screen is a method of checking what information is in the variable. In your final code, you can comment out your code that's for debugging and those lines will be ignored by the compiler (or you can use macros to do this once you learn how to use them).

You shouldn't only check to see if the string has a length of 0 because anything that has a length of less than 4 will cause your program to crash.

Don't forget to close your file after you are done reading it.

The following website might be a good place to look up information on file input and output (although based on your code it looks like you might have been using it):
[http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)

I would read in the lines of a file somewhat differently from them though.
```

#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main () {
	string line;
	ifstream myfile ("example.txt");
	if (myfile.is_open()) {
		getline (myfile,line);
		while (! myfile.eof() ) {
			// Insert procedures for handling each line in the place of this cout statement.
			cout << line << endl;
			
			getline (myfile,line);
		}
		myfile.close();
	} else {
		cout << "Unable to open file";
	}
	
	return 0;
}

```

The main differences between my code and theirs are that I called **getline (myfile,line)** once before the loop was entered and I call **getline (myfile,line)** at the end of the loop iteration.

My code does not attempt to process the variable **myfile** after the end of the file has been reached. Their code, on the other hand, does do this. Since you are using the same method, even if your file had no blank lines it would always attempt to process **currentLine** as an empty string on the last loop iteration. It would be a good idea to try and think about why this happens. Printing the lines of the file to the screen, as well as, changing the contents of the file that you're reading would help you to better understand this.

---

### Post by Yes on 2007-08-19
Sorry, but I have no idea why that would be.  Would you mind explaining it?

I finally got my program to work, it now reads the playlist file and writes the song name and artist to an HTML file.  I do have one problem, though.  When I test to see if the playlist file is "good" using the function playlistfile.good(), it returns false.  As I said, everything still works fine.  Is there anyway to see what the problem is?  Also, is there any way to see if the file exits before opening it?

Thanks.

---

### Post by bigboy_pdb on 2007-08-20
There are two different segments of code to look at and we'll call them **code segment 1** and **code segment 2**.

*code segment 1*:
```

1)	while (! myfile.eof() ) {
2)		getline (myfile,line);
	
		// Insert procedures for handling each line in the place of this cout statement.
3)		cout << line << endl;
}

```

*code segment 2*:
```

1)	getline (myfile,line);
2)	while (! myfile.eof() ) {
		// Insert procedures for handling each line in the place of this cout statement.
3)		cout << line << endl;
	
4)		getline (myfile,line);
}

```

When you open a file, there has been no attempt to read the file using the input file stream (**ifstream**) object. There is a read pointer that starts off at the beginning of the file. Once you read in a line or some information from the file, the read pointer is placed immediately after whatever it last read in the file.

Pretend that we are reading an empty file.

In *code segment 1* the end of the file has not been reached so at **1)** the code **! myfile.eof()** returns true and the loop is entered. At **2)** it attempts to read a line and the end of the file has been reached. Since there was nothing in the file, the variable **line** is an empty string. At **3)** it attempts to print the line that was read (which is an empty string) so a blank line is printed (that shouldn't be printed). The end of the loop has been reached so we return to **1)** and now **! myfile.eof()** returns false so the loop is exited.

In *code segment 2* the end of the file has not been reached. At **1)** it attempts to read a line and the end of the file has been reached. Since there was nothing in the file, the variable **line** is an empty string. At **2)** the code **! myfile.eof()** returns false so the loop is exited. Nothing was ever printed because the file was empty.

Now pretend that we are reading a file with one or more lines.

In *code segment 1* each line is read and printed. Once the last line has been read and printed, we have not reached the end of the file but there is nothing else to read. This case is exactly like the case with the blank file so an empty line gets printed (that shouldn't be printed).

In *code segment 2* each line is read and printed. The last line gets printed at **3)**. At **4)** there is an attempt to read in another line. However, since there is no line, the end of the file has been reached (and since there was nothing in the file, the variable **line** is an empty string). We are at the end of the loop so we return to line **2)** and the code **! myfile.eof()** returns false so the loop is exited. In this situation nothing other than the lines that were read were printed.

Thus, in general, *code segment 1* always prints an unnecessary extra blank line and *code segment 2* only prints the lines that were read in, meaning you should be using the style of *code segment 2* instead of *code segment 1*.

**[EDIT]**
If you create two different programs where the first one uses the code from *code segment 1*, the second one uses the code from *code segment 2*, and you print each line that is read from the file to the screen, you'll be able to better see what I'm talking about.
**[/EDIT]**

I also looked at some of your other threads to get an idea of how much you knew about C++ and I'm aware that it your first programming language. I'd definitely recommend buying a book on C++ to help you to better understand it. I found that Deitel & Deitel's "C++ How to Program" book was a pretty good introductory C++ programming book (although you might want to ask other people's opinions about what is available). You could also download "Thinking in C++" volumes 1 and 2 from the following website:
[http://mindview.net/Books/](http://mindview.net/Books/)

---

### Post by bigboy_pdb on 2007-08-20
In response to your second paragraph.

There wasn't a method called **good()** in your original code so you'll need to post it in order for me to look at it.

The function **myfile.is_open()** returns true if the file was opened successfully and false otherwise, meaning if the file doesn't exist, it will return false. You might want to read through the C++ website that I first posted a link to because most of its information is pretty useful (just remember what I said about how **getline (myfile,line)** should be used because they do it incorrectly).

Also, if all you were doing was trying to write a playlist to an HTML file then you might have been better off using something like bash scripting to do it because it would have required less effort. For example, you could have used the following code to read in the file (with bash scripting) and printed the snippet of HTML code for an unordered list (and then you could have copied it and pasted it into a web page):
```

filename="example.txt"
echo "<ul>"
while read line; do
	echo "<li>$line</li>"
done < <(cat $filename)
echo "</ul>"

```

**NOTE**: You might have to do more to the code but it would still be simpler than a C++ program.

If you want more information on bash scripting, you can do online searches on bash scripting and the Linux command line. You can also look at the following web pages:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

The "Advanced Bash Scripting-Guide" explains what different statements do and it gives a number of examples (but I wouldn't really say that it explains how to create advanced scripts) so don't be afraid to take a look at it.

**[EDIT]**
I'm not trying to discourage you from using C++. It is a powerful language that is very useful for low level programming and if you learn to use it, you will most likely learn other languages more easily. I'm simply trying to make you aware that some problems are easier to solve using a specific language.
**[/EDIT]**

---

### Post by bigboy_pdb on 2007-08-20
Another book that's worth taking a look at for C++ programming (that's freely available) is "Advanced Linux Programming" and it is available at the following url:
[http://www.advancedlinuxprogramming.com/](http://www.advancedlinuxprogramming.com/)

---

### Post by bigboy_pdb on 2007-08-20
Instead of posting links to books on other websites, I'll just post a link to a thread with books and programming resources. It's somewhat difficult to read because there's no consistent scheme, but it has useful links to free programming books.

The link is as follows:
[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)

---

### Post by Yes on 2007-08-26
Thank you so much for all the great links =D.

Yes, C++ was my first programming language, although I also know a fair amount of Java.  I know that it would be simpler to use a language other than C++ for what my program is trying to accomplish, but I really only made the program to teach me more about C++, specifically OOP and File I/O.

Anyway, I've fixed my problem with my good() functions, and my program seems to be working perfectly.  Thank you for all your help!

---

### Post by bigboy_pdb on 2007-08-27
You're welcome. I'm glad that you appreciate it.

If you like programming there are some other things that might be helpful to look into. The following is some information that I've posted on a few other threads:

> 
The programming concepts that I think a person should learn about are:
variables, conditional statements, loops, functions, recursion, objects/classes, reading from and writing to files, error handling, memory management, manipulating numbers, manipulating strings, regular expressions, and concurrency.

Learning a programming language isn't enough to write good programs though. A person should also learn about:
Run time complexity, proving that a program terminates, proving that a program is correct, proofs in general (of a logical, mathematical, or computer science related nature), algorithms, design patterns, debugging strategies, logic, and mathematics (subjects in algebra and discrete mathematics are closely related to computers).


---

