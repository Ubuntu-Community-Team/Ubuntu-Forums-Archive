---
title: "Censored: Else If doesn't work"
date: 2008-03-25
forum: Programming Talk
---

### Post by WarMonkey on 2008-03-25
Whenever I run this program I made I get:

Code:

```
Insert first name: fdf
Insert last name: asdf
xxxxxxxxxxxxxxxxxxx: thing1
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
xxxxxxxxxxxxxxxxxxxxxxxxxxx: asd
xxxx thing1 xxxxxxxxxxxx, xxxxxxxxxxxxx. asdf's asd.
Continue? (y/n)
```

but I want to end up with:

Code:

```
Insert first name: fdf
Insert last name: asdf
xxxxxxxxxxxxxxxxxxxxxxxxxxxxx: thing1
xxxxxxxxxxxxxxxxxxxxx thing1, xxxxxxxxxxx.
Continue? (y/n)
```

The source is:
Code:

```
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int read (int& a) {
string line;
ifstream myfile ("example.txt");
if (myfile.is_open())
{
while (! myfile.eof() )
{
getline (myfile,line);
a++;

}
myfile.close();
}
}
int bodypart(string noun, string firstname, string lastname, string bw){
int z;
z=0;
if (noun==bw)
{
cout << "xxxxxxxxxxxxxxxxx " << noun << ", xxxxxxxxxxx" << "\n";
z=1;

}

else if (z==0){
string bodypart2;
cout << "Insert a second offensive noun: ";
cin >> bodypart2;
cout << "xxxr " << noun << " xxxxxxxxxxxx. " << lastname << "'s " << bodypart2 << "." << "\n";
}
else {
cout << "hdf";
}
}



int main() {
top:
int a;
a=0;
string firstname;
string lastname;
string noun;
cout << "Insert first name: ";
cin >> firstname;
cout << "Insert last name: ";
cin >> lastname;
cout << "Type in a noun that is offensive: ";
cin >> noun;
// begin I/O
read (a);
string bob[a];
string line;
int c;
c=a;
a=0;
ifstream myfile ("example.txt");
if (myfile.is_open())
{
while (! myfile.eof() )
{
getline (myfile,line);

bob[a] = line;
if (bob[a]==noun){
bodypart (noun, firstname, lastname, bob[a]);
}
a++;

}
myfile.close();
}

bodypart (noun, firstname, lastname, bob[a]);
string exit;
a:
cout << "Continue? (y/n) ";
cin >> exit;
if (exit=="y"){
goto top;
}
else if (exit=="n"){
return 0;
}
else {
cout << "Invalid command" << "\n";
goto a;
}
}
```

And, example.txt looks like:
Code:

```
thing1
thing2
etc...
```

[Edit: I replaced most of the outputs with x's because my previous post was jailed. Sorry, if the program is confusing.]

---

### Post by Wybiral on 2008-03-25
It would help if you indented your source code :)

---

### Post by WarMonkey on 2008-03-25
> **Wybiral said:**
> It would help if you indented your source code :)

Here you go, I'm not sure I did it right though:
```
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int read (int& a) {
	string line;
	ifstream myfile ("example.txt");
	if (myfile.is_open())
	{
		while (! myfile.eof() )
		{
			getline (myfile,line);
			a++;
			}
		myfile.close();
	}
}
int bodypart(string noun, string firstname, string lastname, string bw){
	int z;
	z=0;
	if (noun==bw)
	{
		cout << "xxxxxxxxxxxxxxxxx " << noun << ", xxxxxxxxxxx" << "\n";
		z=1;

		}

	else if (z==0){
		string bodypart2;
		cout << "Insert a second offensive noun: ";
		cin >> bodypart2;
		cout << "xxxr " << noun << " xxxxxxxxxxxx. " << lastname << "'s " << bodypart2 << "." << "\n";
		}
else {
	cout << "hdf";
	}
}



int main() {
	top:
	int a;
	a=0;
	string firstname;
	string lastname;
	string noun;
	cout << "Insert first name: ";
	cin >> firstname;
	cout << "Insert last name: ";
	cin >> lastname;
	cout << "Type in a noun that is offensive: ";
	cin >> noun;
	// begin I/O
	read (a);
	string bob[a];
	string line;
	int c;
	c=a;
	a=0;
	ifstream myfile ("example.txt");
	if (myfile.is_open()){
		while (! myfile.eof() ){
			getline (myfile,line);
			bob[a] = line;
			if (bob[a]==noun){
				bodypart (noun, firstname, lastname, bob[a]);
				}
			a++;
			}
		myfile.close();
		}

	bodypart (noun, firstname, lastname, bob[a]);
	string exit;
	a:
	cout << "Continue? (y/n) ";
	cin >> exit;
	if (exit=="y"){
		goto top;
		}
	else if (exit=="n"){
	return 0;
	}
else {
	cout << "Invalid command" << "\n";
	goto a;
}
}
```

---

### Post by LaRoza on 2008-03-25
> **WarMonkey said:**
> 
[Edit: I had to replace most of the outputs with x's because my previous post was jailed. ]

With good reason. Why don't you write something that is logical and inoffensive?

---

### Post by WarMonkey on 2008-03-25
> **LaRoza said:**
> With good reason. Why don't you write something that is logical and inoffensive?

Here is an inoffensive version :). However, I was unable to make it logical.
```
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int read (int& a) {
	string line;
	ifstream myfile ("example.txt");
	if (myfile.is_open())
	{
		while (! myfile.eof() )
		{
			getline (myfile,line);
			a++;
			}
		myfile.close();
	}
}
int bodypart(string noun, string firstname, string lastname, string bw){
	int z;
	z=0;
	if (noun==bw)
	{
		cout << "You are as nice as a " << noun << ", Do you want to be me best friend?" << "\n";
		z=1;

		}

	else if (z==0){
		string nn2;
		cout << "Insert a second nice-noun: ";
		cin >> nn2;
		cout << "Your mother is a " << noun << " do you want to be my best friend? You are Mrs. " << lastname << "'s " << nn2 << "." << "\n";
		}
else {
	cout << "hdf";
	}
}



int main() {
	top:
	int a;
	a=0;
	string firstname;
	string lastname;
	string noun;
	cout << "Insert first name: ";
	cin >> firstname;
	cout << "Insert last name: ";
	cin >> lastname;
	cout << "Type in a noun that is pleasant: ";
	cin >> noun;
	// begin I/O
	read (a);
	string bob[a];
	string line;
	int c;
	c=a;
	a=0;
	ifstream myfile ("example.txt");
	if (myfile.is_open()){
		while (! myfile.eof() ){
			getline (myfile,line);
			bob[a] = line;
			if (bob[a]==noun){
				bodypart (noun, firstname, lastname, bob[a]);
				}
			a++;
			}
		myfile.close();
		}

	bodypart (noun, firstname, lastname, bob[a]);
	string exit;
	a:
	cout << "Continue? (y/n) ";
	cin >> exit;
	if (exit=="y"){
		goto top;
		}
	else if (exit=="n"){
	return 0;
	}
else {
	cout << "Invalid command" << "\n";
	goto a;
}
}
```

---

### Post by WarMonkey on 2008-03-28
I forgot to mention that the problem is in the "int bodypart" function.

---

### Post by njkt on 2008-03-28
First issue is your use of GOTO statements instead of logic, instead of using goto to control the flow and repetition of the program try using a while loop.  The functions you use don't return anything, instead of using the address of the variable try passing information to the function and returning the result.


the issue you're having is more than likely because you have bad program flow, improve that and try again.

---

### Post by wozzinator on 2008-03-28
> **Wybiral said:**
> It would help if you indented your source code :)

You can't tab indent in the ubuntuforums.org message window. I posted code once and even with spaces and/or tabs you can't indent.

                                         Sorry for the rant, but someone once told me                                      to do that and I couldn't get indenting to work.

Also I tried putting 20 spaces in front of the line above and when I posted it, it automatically set it to the beginning of the line.

---

### Post by imdano on 2008-03-28
You can indent if you wrap the code in ```
 or [php] tags.
[php]    def _fast_is_up(self):
        data = (self.iface + '\0' * 16)[:18]
        try:
            result = fcntl.ioctl(self.sock.fileno(), SIOCGIFFLAGS, data)
        except IOError, e:
            if self.verbose:
                print "SIOCGIFFLAGS failed: " + str(e)
            return False
            
        flags, = struct.unpack('H', result[16:18])
        return bool(flags & 1)[/php]

[code]    def _fast_is_up(self):
        data = (self.iface + '\0' * 16)[:18]
        try:
            result = fcntl.ioctl(self.sock.fileno(), SIOCGIFFLAGS, data)
        except IOError, e:
            if self.verbose:
                print "SIOCGIFFLAGS failed: " + str(e)
            return False
            
        flags, = struct.unpack('H', result[16:18])
        return bool(flags & 1)
```

---

### Post by WarMonkey on 2008-03-28
> **imdano said:**
> You can indent if you wrap the code in ```
 or [php] tags.
[php]    def _fast_is_up(self):
        data = (self.iface + '\0' * 16)[:18]
        try:
            result = fcntl.ioctl(self.sock.fileno(), SIOCGIFFLAGS, data)
        except IOError, e:
            if self.verbose:
                print "SIOCGIFFLAGS failed: " + str(e)
            return False
            
        flags, = struct.unpack('H', result[16:18])
        return bool(flags & 1)[/php]

[code]    def _fast_is_up(self):
        data = (self.iface + '\0' * 16)[:18]
        try:
            result = fcntl.ioctl(self.sock.fileno(), SIOCGIFFLAGS, data)
        except IOError, e:
            if self.verbose:
                print "SIOCGIFFLAGS failed: " + str(e)
            return False
            
        flags, = struct.unpack('H', result[16:18])
        return bool(flags & 1)
```


Here is the code wrapped in PHP:

[PHP]#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int read (int& a) {
	string line;
	ifstream myfile ("example.txt");
	if (myfile.is_open())
	{
		while (! myfile.eof() )
		{
			getline (myfile,line);
			a++;
			}
		myfile.close();
	}
}
int bodypart(string noun, string firstname, string lastname, string bw){
	int z;
	z=0;
	if (noun==bw)
	{
		cout << "You are as nice as a " << noun << ", Do you want to be me best friend?" << "\n";
		z=1;

		}

	else if (z==0){
		string nn2;
		cout << "Insert a second nice-noun: ";
		cin >> nn2;
		cout << "Your mother is a " << noun << " do you want to be my best friend? You are Mrs. " << lastname << "'s " << nn2 << "." << "\n";
		}
else {
	cout << "hdf";
	}
}



int main() {
	top:
	int a;
	a=0;
	string firstname;
	string lastname;
	string noun;
	cout << "Insert first name: ";
	cin >> firstname;
	cout << "Insert last name: ";
	cin >> lastname;
	cout << "Type in a noun that is pleasant: ";
	cin >> noun;
	// begin I/O
	read (a);
	string bob[a];
	string line;
	int c;
	c=a;
	a=0;
	ifstream myfile ("example.txt");
	if (myfile.is_open()){
		while (! myfile.eof() ){
			getline (myfile,line);
			bob[a] = line;
			if (bob[a]==noun){
				bodypart (noun, firstname, lastname, bob[a]);
				}
			a++;
			}
		myfile.close();
		}

	bodypart (noun, firstname, lastname, bob[a]);
	string exit;
	a:
	cout << "Continue? (y/n) ";
	cin >> exit;
	if (exit=="y"){
		goto top;
		}
	else if (exit=="n"){
	return 0;
	}
else {
	cout << "Invalid command" << "\n";
	goto a;
}
}[/PHP]

---

### Post by lloyd_b on 2008-03-28
> **WarMonkey said:**
> I forgot to mention that the problem is in the "int bodypart" function.
```

int bodypart(string noun, string firstname, string lastname, string bw){
	int z;
	z=0;
	if (noun==bw)
	{
		cout << "You are as nice as a " << noun << ", Do you want to be me best friend?" << "\n";
		z=1;

		}

	else if (z==0){
		string nn2;
		cout << "Insert a second nice-noun: ";
		cin >> nn2;
		cout << "Your mother is a " << noun << " do you want to be my best friend? You are Mrs. " << lastname << "'s " << nn2 << "." << "\n";
		}
else {
	cout << "hdf";
	}
}
```

One point - it can *never* reach that final else.  You initialize "z" to 0, so unless it takes the "noun==bw" branch, it will take the "z==0" branch.  And the "z++" in the "noun==bw" branch serves no purpose - once it has taken that branch, it is not going to even test the remaining conditions (it'll skip directly to the final "}" and then return.

So, effectively, this function looks like this:
```
int bodypart(string noun, string firstname, string lastname, string bw)
{

	if (noun == bw) {
		cout << "You are as nice as a " << noun << ", Do you want to be me best friend?" << "\n"
	} else {
		string nn2;
		cout << "Insert a second nice-noun: ";
		cin >> nn2;
		cout << "Your mother is a " << noun << " do you want to be my best friend? You are Mrs. " << lastname << "'s " << nn2 << "." << "\n";
	}
}
```

Now, as for why it's never taking that old "else if" clause:
```

       if (myfile.is_open()) {
		while (! myfile.eof() ) {
			getline (myfile,line);
			bob[a] = line;
			if (bob[a]==noun) {
				bodypart (noun, firstname, lastname, bob[a]);
			}
			a++;
		}
		myfile.close();
	}

	bodypart (noun, firstname, lastname, bob[a]);
```

Within the while loop, you only call bodypart() after having tested that "noun" is equal to "bob[a]".  Since these become "noun" and "bw" within the function, no call at this point could possibly take the "else if" clause - noun will *always* equal bw from this call.

So the *only* time that these two variable can possibly be different is on the later call to bodypart

Try putting a "cout" before the second call to bodypart(), and see what the values of "noun" and "bob[a]" are.  It sounds like the function bodypart() is working as intended, but you're never giving it inputs that invoke the "else if".

And finally - ERASE THE WORD GOTO FROM YOUR VOCABULARY.  Sorry if this sounds harsh, but you simply aren't skilled enough to be using it.  It's a very bad habit in a beginning programmer, and leads to "spaghetti code" that's difficult (if not impossible) to understand.

Once you've gained more skill, you'll be aware of all the other constructs available to do things, and won't be tempted to use goto except in those rare situations where it *is* the best solution.
                
Lloyd B.

---

### Post by CptPicard on 2008-03-28
Well, seriously, "goto" should be just banished altogether. There is no good reason to use it for anything, period. In some kind of really low-level programming tasks you may use something similar like setjmp and longjmp... and higher-level languages specifically use exceptions for the sort of stuff that might otherwise require a goto.

---

### Post by lloyd_b on 2008-03-28
> **CptPicard said:**
> Well, seriously, "goto" should be just banished altogether. There is no good reason to use it for anything, period. In some kind of really low-level programming tasks you may use something similar like setjmp and longjmp... and higher-level languages specifically use exceptions for the sort of stuff that might otherwise require a goto.

Try reading the source code for some of the device drivers in the kernel.  The kernel hackers can and will use goto's in situations where it is appropriate.  The problem isn't that the goto is not useful - the problem is that it's generally only used properly by good programmers, and horribly abused by bad or inexperienced programmers.

Maybe gcc/g++ should have an option like "-allowgoto" that, if not specified, would generate errors if it encountered goto's in a program it was compiling :)

Lloyd B.

---

