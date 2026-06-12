---
title: "[HELP] Constructing a String from an Array"
date: 2008-08-15
forum: Programming Talk
---

### Post by loganwm on 2008-08-15
I have input stored in a struct array "substring_table[32]"

the fields are these: substring_table[x].offset = location in input_string
                      substring_table[x].length = length of string

What function/method can I use to combine each char into a string?

I'm having trouble where it gives me incompatible data types and such, can anyone help me?


```

//
//	input_string		holds input from get_input()
//	substring_array		typedef for the struct used to split strings in find_substring()
//	substring_table		structure array used to house information on substring of input_string
//	
//
//

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_NUM_OF_WORDS 32
#define MAX_NUM_OF_CHARS 256

#define CHAR_SPACE 32
#define CHAR_NULL 0

struct substring_array {
	int offset;
	int length;
};

//Array to store the current query
char input_string[MAX_NUM_OF_CHARS];
//Structure to hold substring data
struct substring_array substring_table[MAX_NUM_OF_WORDS];


int get_input() {
	gets(input_string);
}


int find_substring(const char *string) {
	int start_loc = 0;
	int current_word = 0;
	int current_word_length = 0;
	int i = 0;

	substring_table[current_word].offset = start_loc;
	for (i = 0; i < MAX_NUM_OF_CHARS; i++) {
		if (string[i] != CHAR_SPACE && string[i] != CHAR_NULL) {
			current_word_length++;
			start_loc++;
			substring_table[current_word].length = current_word_length;
		}
		else if (string[i] == CHAR_SPACE) {
			current_word++;
			current_word_length = 0;
			start_loc++;
			substring_table[current_word].offset = start_loc;
		} 
	}
}

int convert_substring(int current_word) {
	int i;
	int offset = substring_table[current_word].offset;
	int length = substring_table[current_word].length;
	char tmpstring[256];
	char tmpchar[1];
	for (i = offset; i < offset+length; i++) {
		printf("%c ",input_string[i]);
	}
}

int debug_print_substring_table() {
	int i;
	for (i = 0; i < MAX_NUM_OF_WORDS; i++) {
		printf("Word: %d  Offset: %d  Length: %d\n",i,substring_table[i].offset,substring_table[i].length);
	}
}

int main() {
	get_input();
	find_substring(input_string);
	debug_print_substring_table();
	convert_substring(0);
	convert_substring(1);
	convert_substring(2);
}
```

convert_substring() is where my problem is, please forgive the horrible structure and organization, it's the fruits of 2 nights of insomnia induced coding.

---

### Post by dwhitney67 on 2008-08-15
Below I have included the code such that it should now compile.  Whether it works (and it appears it doesn't) is another issue.

Questions for you...
1 - Is this a class exercise?
2- Is there a reason why you elected not to use strtok()?
3- Why do all of your functions return an int?  You know it is ok to declare a function that returns nothing (void)?

[PHP]//	Name	Synaptic AI
//	Version	1.00
//	Author	Logan Meers
//
//	input_string		holds input from get_input()
//	substring_array		typedef for the struct used to split strings in find_substring()
//	substring_table		structure array used to house information on substring of input_string
//	
//
//

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_NUM_OF_WORDS 32
#define MAX_NUM_OF_CHARS 256

#define CHAR_SPACE 32
#define CHAR_NULL 0

struct substring_array {
	int offset;
	int length;
};

//Array to store the current query
char input_string[MAX_NUM_OF_CHARS];
//Structure to hold substring data
struct substring_array substring_table[MAX_NUM_OF_WORDS];


int get_input() {
    // never use gets()
	//gets(input_string);
	fgets( input_string, sizeof(input_string), stdin );
	return 0;
}


int find_substring(const char *string) {
	int start_loc = 0;
	int current_word = 0;
	int current_word_length = 0;
	int i = 0;

	substring_table[current_word].offset = start_loc;
	for (i = 0; i < MAX_NUM_OF_CHARS; i++) {
		if (string[i] != CHAR_SPACE && string[i] != CHAR_NULL) {
			current_word_length++;
			start_loc++;
			substring_table[current_word].length = current_word_length;
		}
		else if (string[i] == CHAR_SPACE) {
			current_word++;
			current_word_length = 0;
			start_loc++;
			substring_table[current_word].offset = start_loc;
		} 
	}
	return 0;
}

int convert_substring(int current_word) {
	int offset = substring_table[current_word].offset;
	int length = substring_table[current_word].length;
	//char tmpstring[256];
	//char tmpchar[1];
	for (int i = offset; i < offset+length; i++) {
		printf("%c ",input_string[i]);
	}
	return 0;
}

int debug_print_substring_table() {
	for (int i = 0; i < MAX_NUM_OF_WORDS; i++) {
		printf("Word: %d  Offset: %d  Length: %d\n",i,substring_table[i].offset,substring_table[i].length);
	}
	return 0;
}

int main() {
	get_input();
	find_substring(input_string);
	debug_print_substring_table();
	convert_substring(0);
	convert_substring(1);
	convert_substring(2);
    return 0;
}[/PHP]

---

### Post by loganwm on 2008-08-15
I tried out strtok for my purposes and was quite displeased that it's not quite right for what I'm doing.

No this isn't a class exercise, but it is something I've wanted to work on for quite a while.

I have them returning int for now, simply because I haven't added the debug checks yet, but I plan to do that sooner or later.

I solved my original problem I believe, but now I don't believe the substring_convert(int current_word) is working after it processes the first word.

If you wanna try it for me simply compile it and enter the string "this is it" when the program starts, in theory, it should print "this \n is \n it" but it only prints "this" followed by a few blank lines for me.

```
//	Name	Synaptic AI
//	Version	1.00
//	Author	Logan Meers
//
//	input_string		holds input from get_input()
//	substring_array		typedef for the struct used to split strings in find_substring()
//	substring_table		structure array used to house information on substring of input_string
//	
//
//

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_NUM_OF_WORDS 32
#define MAX_NUM_OF_CHARS 256

#define CHAR_SPACE 32
#define CHAR_NULL 0

struct substring_array {
	int offset;
	int length;
};

//Array to store the current query
char input_string[MAX_NUM_OF_CHARS];
//Structure to hold substring data
struct substring_array substring_table[MAX_NUM_OF_WORDS];


int get_input() {
	gets(input_string);
}


int find_substring(const char *string) {
	int start_loc = 0;
	int current_word = 0;
	int current_word_length = 0;
	int i = 0;

	substring_table[current_word].offset = start_loc;
	for (i = 0; i < MAX_NUM_OF_CHARS; i++) {
		if (string[i] != CHAR_SPACE && string[i] != CHAR_NULL) {
			current_word_length++;
			start_loc++;
			substring_table[current_word].length = current_word_length;
		}
		else if (string[i] == CHAR_SPACE) {
			current_word++;
			current_word_length = 0;
			start_loc++;
			substring_table[current_word].offset = start_loc;
		} 
	}
}

int convert_substring(int current_word) {
	int i;
	int offset = substring_table[current_word].offset;
	int length = substring_table[current_word].length;
	char tmpstring[256] = "";
	for (i = offset; i < offset+length; i++) {
		tmpstring[i] = input_string[i];
	}
	printf("%s \n",tmpstring);
}

int debug_print_substring_table() {
	int i = 0;
	for (i = 0; i < MAX_NUM_OF_WORDS; i++) {
		printf("Word: %d  Offset: %d  Length: %d\n",i,substring_table[i].offset,substring_table[i].length);
	}
}

int main() {
	int i = 0;
	get_input();
	find_substring(input_string);
	for (i = 0; i < 3; i++) {
		convert_substring(i);
	}
}

```

---

### Post by dwhitney67 on 2008-08-15
Ok, let's take this one step at a time.

0 - Add a prompt so that the operator knows to input a string.

1 - Do not use gets().  One can easily overrun the buffer being passed to this library function.  For instance, if I enter more than 256 character.  Use fgets() instead.

2 - At a minimum, add a "return 0" to each of your functions.

3 - Compile your code with "gcc -Wall -pedantic".  This will show the warnings that are in your code.  Correcting the code per suggestions 1 and 2 above will help to remove these warnings.

Let me know when you are done with these suggestions and in the meantime I will look for the bug in your code.

---

### Post by loganwm on 2008-08-15
> **dwhitney67 said:**
> Ok, let's take this one step at a time.

0 - Add a prompt so that the operator knows to input a string.

1 - Do not use gets().  One can easily overrun the buffer being passed to this library function.  For instance, if I enter more than 256 character.  Use fgets() instead.

2 - At a minimum, add a "return 0" to each of your functions.

3 - Compile your code with "gcc -Wall -pedantic".  This will show the warnings that are in your code.  Correcting the code per suggestions 1 and 2 above will help to remove these warnings.

Let me know when you are done with these suggestions and in the meantime I will look for the bug in your code.

I was aware the gets() was vulnerable  to overflow, but unaware of and alterative.

I can fix the code, but it wouldn't be for the rest of the evening, I'm currently on my Pocketpc.

I appreciate your heelp as always Dwhitney.

The bug probably isn't anything major, but its bugging me since I can't begin testing the text command processing yet.

---

### Post by dwhitney67 on 2008-08-15
You should learn to use 'gdb', or the GUI front-end of it, 'ddd'.  In finding the bug in your code, I did not use either of these, nevertheless they are invaluable tools for debugging C/C++ code.

Anyhow, I found the bug in the code, and also added a few extra things to make the code more user friendly.  Here it is:
[PHP]//	Name	Synaptic AI
//	Version	1.00
//	Author	Logan Meers
//
//	input_string		holds input from get_input()
//	substring_array		typedef for the struct used to split strings in find_substring()
//	substring_table		structure array used to house information on substring of input_string
//	
//
//

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_NUM_OF_WORDS 32
#define MAX_NUM_OF_CHARS 256

#define CHAR_SPACE ' '
#define CHAR_NULL  '\0'
#define CHAR_CR    '\n'

struct substring_array {
	int offset;
	int length;
};

//Array to store the current query
char input_string[MAX_NUM_OF_CHARS];

//Structure to hold substring data
struct substring_array substring_table[MAX_NUM_OF_WORDS];

int num_words = 0;


int get_input() {
	//gets(input_string);
	printf( "Enter a string: " );
	fgets(input_string, sizeof(input_string), stdin);
return 0;
}


int find_substring(const char *string) {
	int start_loc = 0;
	int current_word = 0;

	substring_table[current_word].offset = start_loc;

	//for (int i = 0; i < MAX_NUM_OF_CHARS; i++) {

	for (int i = 0; i < strlen(input_string); ++i) {
		if (string[i] == CHAR_CR)
			continue;

		if (string[i] != CHAR_SPACE) {
			++start_loc;
			++substring_table[current_word].length;
		}
		else if (string[i] == CHAR_SPACE) {
			++current_word;
			++start_loc;
			substring_table[current_word].offset = start_loc;
		} 
	}
	num_words = current_word + 1;
return 0;
}

int convert_substring(int current_word) {
	int offset = substring_table[current_word].offset;
	int length = substring_table[current_word].length;
	char tmpstring[MAX_NUM_OF_CHARS] = {0};
	for (int i = offset; i < offset+length; ++i) {
		tmpstring[i-offset] = input_string[i];   // your bug was here, with the index of tmpstring
	}
	printf("%s\n",tmpstring);
return 0;
}

int debug_print_substring_table() {
	for (int word = 0; word < num_words; ++word) {
		printf("Word: %d  Offset: %d  Length: %d:\t", word,
                                                              substring_table[word].offset,
                                                              substring_table[word].length);

		convert_substring(word);
	}
return 0;
}

int main() {
	get_input();

	find_substring(input_string);

	debug_print_substring_table();
return 0;
}[/PHP]

---

### Post by dwhitney67 on 2008-08-15
Btw, a simpler way to accomplish your task:
[PHP]#include <stdio.h>
#include <string.h>

int main( int argc, char **argv )
{
  char input[256] = {0};

  printf( "Enter a string: " );
  fgets( input, sizeof(input), stdin );

  size_t numWords = 0;

  char *word = strtok( input, " \t\n" );

  if ( word != 0 )
  {
    do
    {
      printf( "Word %d, Pos = %d, Len = %d:\t%s\n", ++numWords, word-input, strlen(word), word );

    } while ( (word = strtok( NULL, " \t\n" )) != 0 );
  }

  return 0;
}[/PHP]

---

