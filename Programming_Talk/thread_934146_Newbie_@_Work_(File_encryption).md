---
title: "Newbie @ Work (File encryption)"
date: 2008-09-30
forum: Programming Talk
---

### Post by cybermacro on 2008-09-30
Hi there. I've just started with C++ and i've made a very small and simple file encryption/decryption tool. I didn't test it thoroughly but it seems that it encrypts and decrypts text files aswell as executables that I've compiled withouth problems.

I'm not posting this for people to use as an encryption tool (feel free though!:P), but more to get some comments and feedback/critiscism on the way of file handling etc.

Thanks in advance, 
cybermacro

```
/********************************************************/
/*	Encryptor v0.1					*/
/*	Don't use this for any valuable or secret data	*/
/*      This is more or less a file I/O exercise, not a */
/*	professional encryption tool!			*/
/*	Anything in this code can be used and modified  */
/*	freely :-) enjoy.				*/
/*					-cybermacro	*/
/********************************************************/


//Headers
#include <iostream>
#include <fstream>
#include <string>
#include <cstdlib>

using namespace std;


//Function prototypes
int decryption(char* filename, int key);
int encryption(char* filename, int key);

//Init function
int main(int argc, char* argv[])
{
	//First of all, check if the amount of args is at least 4
	//Else, display an error/help message and quit
	if(argc < 4){
	cout << "Usage: " << argv[0] << " <mode> <file> <key>\n";
	cout << "Modes:" << endl;
	cout << "       d  decrypt\n" << "       e  encrypt\n";
	return 1;
	}

	//Check what mode has been chosen and call the function needed
	if(strcmp(argv[1],"e") == 0)
	{
		encryption(argv[2],atoi(argv[3])); 
	}
	else
	if(strcmp(argv[1],"d") == 0)
	{
		decryption(argv[2],atoi(argv[3])); 
	}
	else					
	{
		cout << argv[1] << " is not a valid option.\n";
		cout << "Usage: " << argv[0] << " <mode> <file> <key>\n";
		cout << "Modes:" << endl;
		cout << "       d  decrypt\n" << "       e  encrypt\n";
		return 1;
	}
	return 0;
	
}

int decryption(char* filename, int key)
{
	//We'll use decrypted to store the total decrypted string
	//Two buffers, one for the character that has been read from the file
	//Other one for the "algorythm"
	string decrypted = ""; 
	char charbuf; 
	int intbuf; 

	//Create two filestreams, one to read from and one to write to
	ifstream file_in;
	ofstream file_out;

	//Check if the file specified exists and open it
	file_in.open(filename); 
	if(!file_in){ 
		cerr << "ERROR: target file could not be read.\n";
		exit(1);
	}

	//The file has been opened correctly, now decrypt
	//Using just 5 lines of code!
	cout << "Input file opened, starting decryption process...\n";
	while(file_in.get(charbuf)){
		intbuf = charbuf;
		intbuf = intbuf - (key/2*3);
		charbuf = intbuf;
		decrypted = decrypted + charbuf;
	}
	
	//When the decryption has finished, close the input file
	//And open the output file (which is actually the same)
	//write out the decrypted version
	cout << "Decryption finished, writing file...\n";
	file_in.close();
	file_out.open(filename);
	file_out << decrypted;
	file_out.close();
	cout << "File written, thanks for using Encryptor.\n";
	return 0;
}

int encryption(char* filename, int key)
{
	//This function does exactly the same as the decryption function above
	//Only the algorythm is in the opposite direction
	string encrypted = ""; 
	char charbuf; 
	int intbuf; 
	ifstream file_in;
	ofstream file_out;
	file_in.open(filename); 
	if(!file_in){ 
		cerr << "ERROR: target file could not be read.\n";
		exit(1);
	}
	cout << "Input file opened, starting encryption process...\n";
	while(file_in.get(charbuf)){
		intbuf = charbuf;
		intbuf = intbuf + (key/2*3);
		charbuf = intbuf;
		encrypted = encrypted + charbuf;
	}
	cout << "Encryption finished, writing file...\n";
	file_in.close();
	file_out.open(filename);
	file_out << encrypted;
	file_out.close();
	cout << "File written, thanks for using Encryptor.\n";
	return 0;
}
```

---

### Post by snova on 2008-09-30
First of all, why are you using strcmp()? You can just as easily compare the first character alone, like this:

```
if( tolower( argv[1][0] ) == 'e' )
```

Note the addition of tolower()- that way it's case insensitive, a neat extra feature.

Secondly, there's a lot of code duplicated between encryption() and decryption(). I suggest you write a routine to open a file and check that if suceeded, and then move the call into main(), so that encryption() and decryption() can focus on what they're designed to do, and stop dealing with files. The same goes for the output file, which you should also check- it might not always succeed if the user tells the program to write to a file he doesn't have permission to write to.

Thirdly, you might also want to move the "Thanks for using encryptor" to main(), with similar intents as for the file code.

Nicely done anyway. One of the first "real" programs I ever wrote was a file encryptor. I rewrote it at least eight times before it even compiled :).

---

