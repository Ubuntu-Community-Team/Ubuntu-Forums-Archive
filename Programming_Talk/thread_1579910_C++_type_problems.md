---
title: "C++ type problems"
date: 2010-09-22
forum: Programming Talk
---

### Post by fapfag on 2010-09-22
Hi there.

I have some problems compiling my code.

A copy of my compilation:

```
 g++ -pedantic -Wall main.cpp hts_solver.cpp -o main
hts_solver.cpp:30: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:35: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:40: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:45: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:50: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:55: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:60: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:65: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:70: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:75: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:80: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:85: error: ‘string’ in class ‘hts_solver’ does not name a type
hts_solver.cpp:89: error: expected unqualified-id before ‘int’

```

Now, pardon me if I'm not compiling correctly.. I'm new to manually compiling code. Thought it'd be a good idea to learn, so please throw in some feedback here, if you feel like it :)

Note that I have tried all of the following, with the same result:
[LIST]
[*]using namespace std;
[*]using std::string;
[*]doing it with std::string everywhere (although it shouldn't be needed with "using std::string;", as far as I've read?)
[/LIST]

My code:

main.cpp
```
//HTS Programming solver
//main.cpp
#include <iostream>
using std::cout;
#include <string>
using std::string;

#include "hts_solver.h"

int main(int argc, char** argv)
{
	hts_solver h();
	cout << "hello world";
}
```

hts_solver.cpp
```
//HTS Programming solver
//hts_solver.h
#include <string>
using std::string;
#include <cstdlib>
#include <iostream>
using std::cout;
#include <curl/curl.h>
#include <curl/types.h>
#include <curl/easy.h>
//Includes in hts_solver.h
#include "hts_solver.h"

hts_solver::hts_solver(){
	cout << "in constructor";
	if( ! login() ){
		cout << "Error logging in.";
		exit( 1 );
	}
	else{
		cout << "logged in";
		logged_in = 1;
	}
}

hts_solver::~hts_solver(){
	curl_easy_cleanup( curl_handle );
}

hts_solver::string solve_1(){
	check_login();

}

hts_solver::string solve_2(){
	check_login();
	
}

hts_solver::string solve_3(){
	check_login();
	
}

hts_solver::string solve_4(){
	check_login();
	
}

hts_solver::string solve_5(){
	check_login();
	
}

hts_solver::string solve_6(){
	check_login();
	
}

hts_solver::string solve_7(){
	check_login();
	
}

hts_solver::string solve_8(){
	check_login();
	
}

hts_solver::string solve_9(){
	check_login();
	
}

hts_solver::string solve_10(){
	check_login();
	
}

hts_solver::string solve_11(){
	check_login();
	
}

hts_solver::string solve_12(){
	check_login();
}

hts_solver::int login(){
	cout << "in login";
	BufferStruct output;
	output.buffer = NULL;
	output.size = 0;
	curl_easy_setopt( curl_handle, CURLOPT_URL, "http://www.hackthissite.org");
	curl_easy_setopt( curl_handle, CURLOPT_WRITEDATA, (void*) &output);
	result = curl_easy_perform( curl_handle );
	
	cout << output.buffer;
	
	if( output.buffer ){
		free( output.buffer );
		output.buffer = NULL;
		output.size = 0;
	}
	
}

hts_solver::int check_login(){
	
}

hts_solver::string get_challenge(){

}

// This is the function we pass to LC, which writes the output to a BufferStruct
hts_solver::static size_t WriteMemoryCallback ( void *ptr, size_t size, size_t nmemb, void *data ){
	size_t realsize = size * nmemb;

	BufferStruct * mem = (BufferStruct *) data;

	mem->buffer = realloc(mem->buffer, mem->size + realsize + 1);

	if ( mem->buffer )
	{
		memcpy( &( mem->buffer[ mem->size ] ), ptr, realsize );
		mem->size += realsize;
		mem->buffer[ mem->size ] = 0;
	}
	return realsize;
}
```

hts_solver.h
```
//HTS Programming solver
//hts_solver.h

#ifndef HTS_SOLVER_H
#define HTS_SOLVER_H

//Includes
#include <string>
using std::string;
#include <curl/curl.h>
#include <curl/types.h>
#include <curl/easy.h>


//Defines
#define HTS_USER **
#define HTS_PASS **

//Structs
typedef struct buf_struct
{
	char * buffer;
	size_t size;
} BufferStruct;

class hts_solver{
	public:
		hts_solver();
		~hts_solver();
		string solve_1();
		string solve_2();
		string solve_3();
		string solve_4();
		string solve_5();
		string solve_6();
		string solve_7();
		string solve_8();
		string solve_9();
		string solve_10();
		string solve_11();
		string solve_12();
		
	private:
		//Variables
	
		int logged_in;
		
		//Curl-related variables
		CURL* curl_handle;
		CURLcode	 curl_result;
		
		//Functions
		int login();
		int check_login();
		string get_challenge();
		static size_t WriteMemoryCallback ( void *ptr, size_t size, size_t nmemb, void *data );
};

#endif
```

And yeah, my coding style isn't the prettiest at the moment. I sort of focused on getting it working.

I hope someone will be able to help. Any additional feedback will be appreciated as well :)

---

### Post by spjackson on 2010-09-22
> 
```

hts_solver::string solve_1(){
    check_login();

}

```That should be

```

string hts_solver::solve_1(){
    check_login();
    return string(); // or whatever it is that you are meant to be returning!
}

```and repeat for all the occurrences of similar errors.

---

### Post by GeneralZod on 2010-09-22
```

hts_solver::string solve_1(){
        check_login();

}

```

should be 

```

string hts_solver::solve_1(){
        check_login();

}

```

and the same for the other solve_*s :)

Edit: ^^^ Goddamnit :)

---

### Post by dwhitney67 on 2010-09-22
@ fapfag

Suggestions:

1.  Only include headers which are necessary.  For instance, including <string> is not required in main.cpp.

2.  Avoid "using" namespace directives in header files.

3.  In C++, there is no need to typedef a struct so as to bear a distinct name.  You can declare a struct in the same manner as you would as class.  In fact both are identical in every way, except that by default, all declarations within a class are private.
```

struct Foo
{
   int value;
};

int main()
{
   Foo f;    // legal syntax

   f.value = 5;
}

```

---

### Post by fapfag on 2010-09-22
It solved the problem. Silly me :P
Thanks for the help GeneralZod and spjackson.

And thanks for the feedback dwhitney67, I'll remember that :)

---

