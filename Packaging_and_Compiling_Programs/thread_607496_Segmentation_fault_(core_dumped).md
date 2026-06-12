---
title: "Segmentation fault (core dumped)"
date: 2007-11-09
forum: Packaging and Compiling Programs
---

### Post by jordank on 2007-11-09
hey there, i'm working on a computer science assignment, and got an error after compiling with gcc.

it's a basic program that is supposed to decrypt, but i'm trying to bruteforce my way through it.
my code is the following: (sorry for the length)

#include <iostream>
#include <string>
using namespace std;




string starcheck (string key)
{
unsigned int i = 0;
int scroll = 0;
int temp = 0;
char alphabet[] = { 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', ' ', ',', '.', '!', '?', ']', '[', '*' } ;


while (i<key.length())
{
	if (key[i] == '*')
	{
		while (temp != 1)
		{
			if (key[i-1] == alphabet[scroll])
			{
			temp=1;
			scroll++;
			}
			else
			{scroll++;}
		}
	key[i] = 'a';
	key[i-1] = alphabet[scroll];
	}

i++;
}
return key;
}







int decrypt3 (string text,string key)
{
unsigned int pos = 0;
unsigned int pos2 = 0;
int result = 0;
int alphasize = 70;
int checker = 0;
unsigned int scroll = 0;
unsigned int scroll2 = 0;
unsigned int scroll3 = 0;
int temp = 0;
int temp2 = 0;
int temp3 = 0;
int counter;
int length = key.length();
int temp4 = 0;
string keycheck = "***";
string realkey = "aaa";
string newtext = "";
bool stringMatch = true;
char c1 = 'a';
char c2 = 'a';
int i = 0;
char alphabet[] = { 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', ' ', ',', '.', '!', '?', ']', '[', '*' } ;
while (1)
{
cout << "key is" << key;

i = 0;
c1 = 'a';

//sets realkey = key
while(c1!='\0')
	{
		c1 = key[i];
		realkey[i] = c1;
		i++;


	}

	realkey[i] = '\0';


while (pos < text.length())


{
//check for return
i = 0;
c1 = 'a';
c2 = 'a';
	while(c1!='\0' && c2!='\0')
	{
		c1 = key[i];
		c2 = keycheck[i];
		i++;
		if(c1 != c2)
		{
			stringMatch = false;
			break;
		}

	}
i = 0;
c1 = 'a';

if (stringMatch)
	{return 1;}
//end check
		while (temp != 1)
		{
			if (text[pos] == alphabet[scroll])
			{temp=1;}
			else
			{scroll++;}
		}
		while (temp2 != 1)
		{
			if (key[pos2] == alphabet[scroll2])
			{temp2=1;}
			else
			{scroll2++;}
		}
		while (temp4 != 1)
		{
			if (key[(length-1)] == alphabet[scroll3])
			{
			temp4=1;
			scroll3++;
			}
			else
			{scroll3++;}
		}
		if (temp==1 && temp2==1)
		{
		result = (scroll - scroll2);
		checker = scroll;
		}
		if (result<0)
		{
		result = result + alphasize;
		}
		if ((checker)>(alphasize/2))
		{
		temp3 = (scroll2+1);
			if (temp3>=alphasize)
			{temp3 = temp3%alphasize;}
		key[pos2] = alphabet[temp3];

		}

		scroll = 0;
		scroll2 = 0;
		cout << alphabet[result];
		newtext = newtext + alphabet[result];
		temp = 0;
		temp2 = 0;
		temp3 = 0;
		temp4 = 0;
		pos++;
		pos2++;
		if (pos2 >= key.length())
		{
		pos2 = 0;
		}
		result = 0;
	}





pos = 0;
pos2 = 0;
counter=0;
cout << endl;
realkey[(length-1)] = alphabet[scroll3];
//sets key equal to realkey
i = 0;
c1 = 'a';
	while(c1!='\0')
	{
		c1 = realkey[i];
		key[i] = c1;
		i++;

	}
	key[i] = '\0';
//check for * character in key, if found, take position and make one prior to it, it's value +1, and change * value to a
key = starcheck (key);
cout <<"key is" << key;
}
}






int main ()
{
string text = "TaHrLvbhJfyBA JBPKpjyFPLRdEBOnNvEfmnQbyqMHsdsnQvCupESnAudGIzstEnSOspqfVDItdDXASutBRoCfqBWAtbACRUJorf0EF,pAKOZrEvXLy.d6RDudyG7DT!tGEQHplHQDvxzg6HH?ws1GWmdCUsXmpg0E3[dKYIIndLSSygwI7tua";
string key = "aaa";
string whatiskey;
//cout << "Enter the message to decrypt:" << endl;
//getline(cin, text);
cout << "Enter the key:" << endl;
getline(cin, key);
cout << "Decrypting the message: [" << text << "] starting with the key [" << key << "]:" << endl;
whatiskey = decrypt3 (text, key);
cout << whatiskey;
return 0;
}


after compiling, i can run the program, but as soon as i put in any input it gives me:
segmentation fault (core dumped).


any ideas?

---

### Post by oberg on 2007-11-09
You'll run into a segmentation fault in several different cases.  When you try to dereference a null pointer or, in this case most likely, go out of bounds on an array.  I suggest compile you're program with a -g flag and use the gdb debugger.  I'm not going to go through your code and debug it for you, but a segmentation fault is pretty common in c and c++ programming.

```
 gcc -g <filename>
```

Then to run the gdb debugger on it type:

```
gdb <executable>
```

where executable will probably be a.out.  Type:

```
man gdb
```

to get a list of commands that can be used. 

Hope that helps.

---

### Post by dholbach on 2007-11-15
You can also try [https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

### Post by meatpan on 2007-11-15
Hello Jordank,

A segmentation fault occurs when you try to read or write to memory, when you do not have the correct access privileges.  Seg faults can be frustrating, but try to look at it as the system doing you a big favor and gracefully terminating your program before you do some serious damage.

Start simple with your debugging.  Try to reproduce your problem with the smallest piece of code possible.   You can do this easily in your example by commenting out a few code blocks.

Also, as mentioned above, a debugger will be very helpful.  Be patient with your debugger.  The good ones take a while to learn.

---

