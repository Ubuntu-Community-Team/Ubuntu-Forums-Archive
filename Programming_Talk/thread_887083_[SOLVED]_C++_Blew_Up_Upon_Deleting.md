---
title: "[SOLVED] C++ Blew Up Upon Deleting"
date: 2008-08-11
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-11
Look at the destructor code, i commented
[PHP]#include <fstream>
#include <iostream>
using namespace std;

class mkr {
	public:
		const char * name;
		char * data;
		short files;
		char ** fnames;
		char ** filedata;
		int * sizes;
		mkr(const char * n) {
			name = n;
			ofstream ofile (name, ios::binary);
			ofile.close();
			ifstream file (name);
			if (file.is_open()) {
				int size = file.tellg();
				data = new char [size];
				file.seekg (0, ios::beg);
				file.read (data, size);
				file.close();
				
				int pos=1;
				files = (short)data[0];
				fnames = new char*[files];
				filedata = new char*[files];
				sizes = new int[files];
				
				for (int i0=0;i0<files;i0++) {
					fnames[i0] = new char[20];
					for (int i1=0;i1<20;i1++) fnames[i0][i1] = data[pos+i1];
					pos+=20;
				}
				
				int i1;
				for (int i0=0;i0<files;i0++) {
					for (i1=pos;i1<size;i1++) {
						if (data[i1] == 0 && data[i1+1] == 0 && data[i1+2] == 0 && data[i1+3] == 0 && data[i1+4] == 0 && data[i1+5] == 0 && data[i1+6] == 0) {
							break;
						}
					}
					sizes[i0] = i1-pos;
					filedata[i0] = new char[sizes[i0]];
					for (int i=0;i<sizes[i0];i++) filedata[i0][i1] = data[pos+i];
					pos=i1+7;
				}
				delete[] data;
			} else cout << "Unable to Open MKR";
		}
//
//Destructor Here
//
		~mkr() {
			int datlen = 1+files*20+files*7;
			for (int i=0;i<files;i++) datlen += sizes[i];
			data = new char[datlen];
			data[0] = (char)files;
			int pos=1;
			for (int i0=0;i0<files;i0++) {
				for (int i1=0;i1<20;i1++) {
					data[pos+i1] = fnames[i0][i1];
				}
				//I have commented code out to find that this delete
				//is causing the problems, but below a similar delete doesn't
				delete[] fnames[i0]; //Segmentation fault (core dumped) here
				//This delete is deleteing parts of a 2D array (char **)
				pos+=20;
			}
			delete[] fnames;
			for (int i0=0;i0<files;i0++) {
				for (int i=0;i<sizes[i0];i++) data[pos+i] = filedata[i0][i];
				pos+=sizes[i0];
				for (int i=0;i<7;i++) data[pos+i] = (char)0;
				pos+=7;
				//This delete is Ok??
				//Its the same thing
				delete[] filedata[i0];
			}
			delete[] filedata;
			delete[] sizes;
			
			ofstream file (name, ios::binary);
			if (file.is_open()) {
				file.write (data, datlen);
				file.close();
			}
			delete[] data;
		}
};
[/PHP]
Here it the code that uses this class
[PHP]#include <iostream>
#include "MKR.h"

void put(mkr & i0, char * fname) {
	int size;
	char * data;
	ifstream file (fname);
	if (file.is_open()) {
		size = file.tellg();
		data = new char [size];
		file.seekg (0, ios::beg);
		file.read (data, size);
		file.close();
	} else {
		std::cout << "Unable to Open File" << std::endl;
		return;
	}
	
	i0.files++;
	char ** fnames = new char*[i0.files];
	for (int i=0;i<i0.files-1;i++) fnames[i] = i0.fnames[i];
	fnames[i0.files-1] = fname;
	delete[] i0.fnames;
	i0.fnames = fnames;
	
	int * sizes = new int[i0.files];
	for (int i=0;i<i0.files-1;i++) sizes[i] = i0.sizes[i];
	sizes[i0.files-1] = size;
	delete[] i0.sizes;
	i0.sizes = sizes;
	
	char ** filedata = new char*[i0.files];
	for (int i=0;i<i0.files-1;i++) filedata[i] = i0.filedata[i];
	filedata[i0.files-1] = data;
	delete[] i0.filedata;
	i0.filedata = filedata;
}

int main(int argc, char * argv[]) {
	if (argc < 3) {
		std::cout << "Usage: \"put package.mkr file.txt\"" << std::endl;
	}
	
	mkr n (argv[1]);
	for (int i=2;i<argc;i++) {
		//The next line does somthing that makes the destructor blow up
		put(n, argv[i]);//Commenting this line out fixes it
	}
	
	return 0;
}[/PHP]
Please don't rewrite all the code for me, just fix parts.

---

### Post by Mr.Macdonald on 2008-08-11
found something while debugging (reason for million return statements)
[PHP]

void put(mkr & i0, char * fname) {
	int size;
	char * data;
	ifstream file (fname);
	if (file.is_open()) {
		size = file.tellg();
		data = new char[size];
		file.seekg (0, ios::beg);
		file.read (data, size);
	} else {
		std::cout << "Unable to Open File" << std::endl;
		return;
	}
	file.close();
	
	i0.files++;	//gives a
					//terminate called after throwing an instance of 'std::bad_alloc'
					//  what():  St9bad_alloc
					//Aborted (core dumped)
					//Error??
	std::cout << i0.files << std::endl;return;
	char ** fnames = new char*[i0.files];return;
	for (int i=0;i<i0.files-1;i++) fnames[i] = i0.fnames[i];return;
	fnames[i0.files-1] = fname;return;
	delete[] i0.fnames;return;
	i0.fnames = fnames;return;
	
	int * sizes = new int[i0.files];return;
	for (int i=0;i<i0.files-1;i++) sizes[i] = i0.sizes[i];return;
	sizes[i0.files-1] = size;return;
	delete[] i0.sizes;return;
	i0.sizes = sizes;return;
	
	char ** filedata = new char*[i0.files];return;
	for (int i=0;i<i0.files-1;i++) filedata[i] = i0.filedata[i];return;
	filedata[i0.files-1] = data;return;
	delete[] i0.filedata;return;
	i0.filedata = filedata;return;
}
[/PHP]

Only change

---

### Post by dwhitney67 on 2008-08-11
I looked at your code; sorry but it rambles on for too long.  Perhaps if you spelt out your requirements, commented the code, chose better variable names, and structured your class a little better, I might be able to help.

Otherwise I suggest you run the code in the debugger (gdb or ddd).

-----------------------

I just looked at your second post.  An increment of a short shouldn't cause a SEGV/ABORT; the data on the heap has probably been corrupted when you performed one of the operations in one of the countless loops you have written.

Why are you not using std::vector??  It would be sooooo much easier than declaring arrays of pointers.  Use std::string in lieu of char pointers.  Use the tools that C++ offers!  Stop thinking in terms of C programming.

P.S Rule of thumb in OOD... try to avoid exposing the data in your class objects.  They should declared as private, protected, and as a last resort, public (but this is rare!).

---

### Post by Mr.Macdonald on 2008-08-11
i figured it out. In the put function i didn't set the fname to 20 bytes.

---

