---
title: "C++ Helps: varible comparison"
date: 2007-08-25
forum: Programming Talk
---

### Post by t3hi3x on 2007-08-25
I have a simple c++ app talks to a server. I am trying to get it where it compares to series of strings and replys

here is an excerpt from the code:

```
...
      if (reply = "JOIN")

	{
	std::cout << "This reciever has been aloud to join the server";
	}

      if (reply = "REFUSE")
	
	{	
	std::cout << "This reciever has been rejected by the server";
	}
...
```
i get this error when i try to make it:

> 
simple_client_main.cpp: In function ‘int main(int, int*)’:
simple_client_main.cpp:42: error: could not convert ‘reply. std::basic_string<_CharT, _Traits, _Alloc>::operator= [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>](((const char*)"JOIN"))’ to ‘bool’
simple_client_main.cpp:46: error: could not convert ‘reply. std::basic_string<_CharT, _Traits, _Alloc>::operator= [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>](((const char*)"REFUSE"))’ to ‘bool’
make: *** [simple_client_main.o] Error 1


i dont understand why it thinks i am trying to convert it to a boolean  value. its a string compared to a string. when there is section of code that couts the reply varible and it works just fine.

i'm pretty much a noob to c++ and this is my first real application, so i'm sure this is something i dont know about c++ and string.h header.

any way, thanks for the help.

---

### Post by t3hi3x on 2007-08-25
...
      if (reply == "JOIN")

	{
	std::cout << "This reciever has been aloud to join the server";
	}

      if (reply == "REFUSE")
	
	{	
	std::cout << "This reciever has been rejected by the server";
	}
...


****.

---

### Post by mgoblue on 2007-08-25
> **t3hi3x said:**
> ...
      if (reply **== **"JOIN")

	{
	std::cout << "This reciever has been aloud to join the server";
	}

      if (reply **==** "REFUSE")
	
	{	
	std::cout << "This reciever has been rejected by the server";
	}
...


****.

Incase you don't see what he did, use two ='s instead of one.

---

### Post by t3hi3x on 2007-08-25
> **mgoblue said:**
> Incase you don't see what he did, use two ='s instead of one.

haha yea. figured that out as i posted it. kinda feel like an idiot, but maybe it'll help SOMEBODY haha.

---

### Post by bashologist on 2007-08-25
Yea, in the first post you were using an assignment as the error messages would suggest (operator=). But will two even compare strings? I don't think you can compare with operator==. Maybe try strcmp, or boost::iequals for string objects.

---

### Post by t3hi3x on 2007-08-25
> **bashologist said:**
> Yea, in the first post you were using an assignment as the error messages would suggest (operator=). But will two even compare strings? I don't think you can compare with operator==. Maybe try strcmp, or boost::iequals for string objects.

actually it compiled without incident so apparently == and != will compare strings as well as int, char, etc..

---

### Post by bashologist on 2007-08-25
> **t3hi3x said:**
> actually it compiled without incident so apparently == and != will compare strings as well as int, char, etc..

Yea you're right, it works for the string class. For case insensitive comparison I always use boost::iequals so I don't need this. operator== is ugly anyways. n_n

test.cpp:
```
#include <iostream>
using namespace std;

int main()
{
	string test1 = "blah";
	char test2[5] = "blah";
	if (test1 == "blah")
	{
		cout << "works for string class\n";
	}
	if (test2 == "blah")
	{
		cout << "works for char arrays\n";
	}
	return 1;
}

```
Output:
```
satan@ubuntu:~$ g++ test.cpp -o test && ./test
works for string class
```

---

### Post by t3hi3x on 2007-08-25
does "return 0;" exit the subroutine even if i'm in a while loop?

sorry i learned in vb so all this is weird lol

---

### Post by ryno519 on 2007-08-25
> **t3hi3x said:**
> does "return 0;" exit the subroutine even if i'm in a while loop?

sorry i learned in vb so all this is weird lol

The return statement will end the function/method and return that value to whatever called it. Since int main is the entry point it will terminate your program when that function finishes. So yes, a return statement will end a function.

If you just want to exit a while look, try using a break statement.

---

### Post by t3hi3x on 2007-08-25
awesome. turned out to be something else.

heres another n00b question. i have the int main. 

since it is in a simple app right now it wont do what i want do with it.

how do i make a multiple subroutine app? 

eg. i want bool main to connect. return a true or false. close if false and continue with opperations if true.

you guys are helping a whole lot. i dont do well with books.

---

### Post by ryno519 on 2007-08-25
> **t3hi3x said:**
> awesome. turned out to be something else.

heres another n00b question. i have the int main. 

since it is in a simple app right now it wont do what i want do with it.

how do i make a multiple subroutine app? 

eg. i want bool main to connect. return a true or false. close if false and continue with opperations if true.

you guys are helping a whole lot. i dont do well with books.

You can't have a bool main. The only entry point available to you (by default) is the following...

int main()

or

int main(int argc, char** argv)

The latter is for when you want to pass command line arguments. If you want to make a function that returns a bool, consider the following.

```

#include <string>
#include <iostream>

using namespace std;

bool isBlah(string inVal)
{
  if(inVal == "blah")
    return true;
  return false;
}

int main()
{
  string test1 = "blah";
  
  if(isBlah(test1))
    cout << "It IS blah!" << endl;
  else
    cout << "It isn not blah :(" << endl;

  return 0;
}


```

What that will do is the program will execute the main function when it runs, the main function creates a string with the value "blah", main passes the string to the isBlah function which returns a bool based on whether or not the string equals "blah" and returns a messaging indicating the outcome.

Here's a link you might be interested in;

[http://cprogramming.com/](http://cprogramming.com/)

It has a lot of tutorials and examples for beginners and intermediates.

---

### Post by samjh on 2007-08-25
> **t3hi3x said:**
> how do i make a multiple subroutine app? 

eg. i want bool main to connect. return a true or false. close if false and continue with opperations if true.

You mean something like this?
```
bool connectFunction()
{
    // Put code here
    if (connection == "success!") {
        return true;
    } else {
        return false;
    }
}

int main()
{
    // Put code here
    bool allgood = connectFunction();
    if (allgood == false) {
        cout << "uh oh, I have to exit now";
        return 0;
    }
    // Put code here
}
```

---

### Post by t3hi3x on 2007-08-25
that is exaclty wanted i wanted. i thought it was something like that, but wasnt too sure.

thanks

---

### Post by t3hi3x on 2007-08-26
wow. this project is moving right along. if some is bored can they tell me how to use classes. say i wanted to use some code from a media player say amarok to get a streaming system working. how would use the commands that are in the cpp files. i'm pretty sure i'd have to use a .h file...actually i dont know lol. i can look it up, but i'm really bad with documentation. i do so much better with examples.

---

### Post by slavik on 2007-08-26
are you writing a plugin for amarok? if so, check the project page, there should be sample plugins and such.

if you want to use the media playing functionality of amarok (or whatever else) start at the universal starting point (main) and dig through there.

---

### Post by t3hi3x on 2007-08-26
i'm actually righting a piece of software that is music receiver. i have it working in visual basic (yuck) and need to use a linux OS, so i'm writing it in C++. i figured i just learn it by taking jump of the high dive...i'm getting there just taking me a bit.

---

### Post by slavik on 2007-08-26
then I suggest looking through amarok code and trying to copy it (then your code must be whatever gpl amarok is), or you may want to look into gstreamer. :)

---

### Post by t3hi3x on 2007-08-26
here's one for ya, and thanks again for helping me out. c++ tutorials dont help me at all.

how can i run two functions at once:

my client program seems to disconnect from the server after the bool authReceiver which has the create socket and then sends a packet then waits for a packet. how can i get it where it constantly waits for a packet instead of just waiting for it:

ex.
```

boot authReceiver ()

{
//auth code

do
{

//incoming packets code

}
while ( x != 0);
return false;
}



```
run this (basically) with out it being the sole thing running. basicly i am wanting to play the music i get from the server. while still waiting for more urls.

---

### Post by slavik on 2007-08-26
threading and/or non-blocking reads.

you can use pthreads, would be pretty easy.

here's is my code I used to parallel matrix multiplication (it is GPL3):

note1: code is not optimal (it uses 2D arrays)
note2: it can be done without using any mutexes  in this specific application.

```

/*
 *      threads.c
 *
 *      Copyright 2007 Vyacheslav Goltser <slavikg@gmail.com>
 *
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 3 of the License, or
 *      (at your option) any later version.
 *
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
 */

#include <stdio.h>
#include <pthread.h>
#include <unistd.h>

#define JOBS 10 //number of threads to make
#define MSIZE 1000 //row and column size of matrix

void *calc(void *arg); //our ''worker''

long long int matrix1[MSIZE][MSIZE];
long long int matrix2[MSIZE][MSIZE];
long long int matrix_result[MSIZE][MSIZE];
FILE *logfile;

//matrix_result = matrix1 * matrix2

int i=0;
int pt_counter = 0;

pthread_t threads[JOBS];
pthread_mutex_t mutex_i = PTHREAD_MUTEX_INITIALIZER;

int main(int argc, char** argv) {
	FILE *m1 = fopen("matrix1","r");
	FILE *m2 = fopen("matrix2","r");
	FILE *mr = fopen("matrix_result","w");
	logfile = fopen("matrix_log","w");
	int tid[JOBS];
	int c;

	//read in the matrices
	for (c = 0; c < MSIZE*MSIZE; c++) {
		fscanf(m1,"%lld",&matrix1[c/MSIZE][c%MSIZE]);
		fscanf(m2,"%lld",&matrix2[c/MSIZE][c%MSIZE]);
	}

	//create the threads
	for (pt_counter = 0; pt_counter < JOBS; pt_counter++) {
		tid[pt_counter] = pt_counter;
		pthread_create(&threads[pt_counter],NULL,calc,&tid[pt_counter]);
	}

	//wait for all threadsto finish
	for (pt_counter = 0; pt_counter < JOBS; pt_counter++) {
		pthread_join(threads[pt_counter],NULL);
	}

	//write out the result
	for (c = 0; c < MSIZE*MSIZE; c++) {
		fprintf(mr,"%lld",matrix_result[c/MSIZE][c%MSIZE]);
		if ((c+1)%10==0 && c>0 ) fprintf(mr,"\n");
		else fprintf(mr,", ");
	}

	return 0;
}

//there is a way to do away with mutexes ...
void *calc(void *arg) {
	int cell; //cell #
	int row, col; //row and column to compute
	int counter; //counter for the for loop

	pthread_mutex_lock(&mutex_i); //lock i in order to test and increment it
	while(i < MSIZE*MSIZE) {
		cell = i++;
		fprintf(logfile,"%d - %d\n",*(int*)arg,cell);
		pthread_mutex_unlock(&mutex_i);//unlock i to allow other threads to use it
		row = cell/MSIZE;
		col = cell%MSIZE;
		for (counter = 0; counter < MSIZE; counter++) {
			matrix_result[row][col] += matrix1[row][counter] * matrix2[counter][col];
		}
		pthread_mutex_lock(&mutex_i); //lock i for next while iteration (to check and increment it)
	}
	pthread_mutex_unlock(&mutex_i);//unlock i since we are done running

	pthread_exit(NULL);
}

```

---

