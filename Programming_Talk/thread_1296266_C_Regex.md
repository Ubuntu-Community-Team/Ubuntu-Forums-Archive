---
title: "C Regex"
date: 2009-10-20
forum: Programming Talk
---

### Post by matmatmat on 2009-10-20
I have this program:
```

#include <stdio.h>
#include "useful_functions.h"
#define MAXLINE 1000

int main(int argc, char *argv[]){
	char line[MAXLINE];
	long lineno = 0;
	int c, except = 0, number = 0, found = 0, ignore = 0;

	while (--argc > 0 && (*++argv)[0] == '-'){
		while (c = *++argv[0]){
			switch (c) {
				case 'x':
					except = 1;
					break;
				case 'n':
					number = 1;
					break;
				case 'i':
					ignore = 1;
					break;
				default:
					printf("Illegal option\n");
					argc = 0;
					found = -1;
			}
		}
	}
	FILE *fp;
	*++argv;
	fp = fopen(*argv, "r");
	*argv--;
	if (fp == NULL){
		while (getline(line, MAXLINE, stdin) > 0){
			lineno++;
			char oline[MAXLINE];
			if (ignore){
				copy(oline, line);
				strlower(line);
				strlower(*argv);
			}			
			if (match(line, *argv)){
				if (number){
					printf("%ld: ", lineno);
				}
				if (ignore){
					printf("%s", oline);
				}else{
					printf("%s", line);
				}
				found++;
			}
		}
	}else{
		while(getline(line,MAXLINE, fp) > 0){
			lineno++;
			char oline[MAXLINE];
			if (ignore){
				copy(oline, line);
				strlower(line);
				strlower(*argv);
			}	
			if (match(line, *argv)){
				if (number){
					printf("%ld: ", lineno);
				}
				if (ignore){
					printf("%s", oline);
				}else{
					printf("%s", line);
				}
				found++;
			}
		}
	}
	return found;
}


```
the functions defined in the header file are:
```

//strcpy clone
void copy(char to[], char from[]){
	int i = 0;
	while ((to[i] = from[i]) != '\0'){
		++i;
	}
}

//tolower clone
char lower(char c){
	if (c >= 'A' && c <= 'Z'){
		return c + 'a' - 'A';
	}else{
		return c;
	}
}

void strlower(char string[]){
	int i;
	for(i=0;string[i] != '\0';i++){
		string[i] = lower(string[i]);
	}
}

int getline(char s[], int lim, FILE *f){
	int c, i;
	for (i=0; i<lim-1 && (c=getc(f))!=EOF && c!='\n'; ++i){
		s[i] = c;
	}
	if (c == '\n'){
		s[i] = c;
		++i;
	}
	s[i] = '\0';
	return i;
}

int match(const char *string, char *pattern) { 
    int status;
	regex_t re;
	if(regcomp(&re, pattern, REG_EXTENDED|REG_NOSUB) != 0) {
    	return 0; 
    }
  	status = regexec(&re, string, (size_t)0, NULL, 0);
  	regfree(&re);
  	if(status != 0) {   
    	return 0; 
    }
  return 1; 
} 

```
when run like this:
```

ls | /.mgrep .c$

```
I expect it to print out all files that end with '.c', but it prints nothing

---

### Post by dwhitney67 on 2009-10-20
I am not at all familiar with the regex C library functions, however there are some basic errors in your code that perhaps are contributing to your app's woes.

Here's a modified source I built, that unfortunately still exhibits the same issue you reported.  It is a bit leaner than the code you presented, and because I use the gnu99 version of GCC, I had to rename getline() to be getLine().

```

#include "useful_functions.h"
#include <stdio.h>

#define MAXLINE 1000

int main(int argc, char *argv[])
{
   long lineno = 0;
   int c, except = 0, number = 0, found = 0, ignore = 0;

   --argc; ++argv;  // skip program name

   while (argc > 0 && (*argv)[0] == '-')
   {
      while ((c = *++argv[0]))
      {
         --argc;

         switch (c)
         {
            case 'x':
                except = 1;
                break;
            case 'n':
                number = 1;
                break;
            case 'i':
                ignore = 1;
                break;
            default:
                printf("Illegal option\n");
                argc = 0;
                found = -1;
         }
      }
   }

   FILE* fp = stdin;

   if (argc > 1 && *argv)
   {
      fp = fopen(*argv, "r");
      ++argv;
   }

   const char* pattern = *argv;

   if (fp != NULL && pattern != NULL)
   {
      char line[MAXLINE] = {0};

      while (getLine(line, MAXLINE, fp) > 0)  // note getLine() leaves the newline character in the buffer!
      {
         ++lineno;

         char oline[MAXLINE] = {0};

         if (ignore)
         {
            copy(oline, line);
            strlower(line);
            strlower(*argv);
         }
         if (match(line, pattern))
         {
            if (number)
            {
               printf("%ld: ", lineno);
            }
            if (ignore)
            {
               printf("%s", oline);
            }
            else
            {
               printf("%s\n", line);
            }
            found++;
         }
      }
   }
   else
   {
      printf("error, cmd line args messed up.\n");
   }

   return found;
}

```

P.S.  I assume the command line args could work as:
```

./mgrep file_list .c$

```

---

### Post by Arndt on 2009-10-21
> **matmatmat said:**
> I have this program:
```

#include <stdio.h>
#include "useful_functions.h"
#define MAXLINE 1000

int main(int argc, char *argv[]){
	char line[MAXLINE];
	long lineno = 0;
	int c, except = 0, number = 0, found = 0, ignore = 0;

	while (--argc > 0 && (*++argv)[0] == '-'){
		while (c = *++argv[0]){
			switch (c) {
				case 'x':
					except = 1;
					break;
				case 'n':
					number = 1;
					break;
				case 'i':
					ignore = 1;
					break;
				default:
					printf("Illegal option\n");
					argc = 0;
					found = -1;
			}
		}
	}
	FILE *fp;
	*++argv;
	fp = fopen(*argv, "r");
	*argv--;
	if (fp == NULL){
		while (getline(line, MAXLINE, stdin) > 0){
			lineno++;
			char oline[MAXLINE];
			if (ignore){
				copy(oline, line);
				strlower(line);
				strlower(*argv);
			}			
			if (match(line, *argv)){
				if (number){
					printf("%ld: ", lineno);
				}
				if (ignore){
					printf("%s", oline);
				}else{
					printf("%s", line);
				}
				found++;
			}
		}
	}else{
		while(getline(line,MAXLINE, fp) > 0){
			lineno++;
			char oline[MAXLINE];
			if (ignore){
				copy(oline, line);
				strlower(line);
				strlower(*argv);
			}	
			if (match(line, *argv)){
				if (number){
					printf("%ld: ", lineno);
				}
				if (ignore){
					printf("%s", oline);
				}else{
					printf("%s", line);
				}
				found++;
			}
		}
	}
	return found;
}


```
the functions defined in the header file are:
```

//strcpy clone
void copy(char to[], char from[]){
	int i = 0;
	while ((to[i] = from[i]) != '\0'){
		++i;
	}
}

//tolower clone
char lower(char c){
	if (c >= 'A' && c <= 'Z'){
		return c + 'a' - 'A';
	}else{
		return c;
	}
}

void strlower(char string[]){
	int i;
	for(i=0;string[i] != '\0';i++){
		string[i] = lower(string[i]);
	}
}

int getline(char s[], int lim, FILE *f){
	int c, i;
	for (i=0; i<lim-1 && (c=getc(f))!=EOF && c!='\n'; ++i){
		s[i] = c;
	}
	if (c == '\n'){
		s[i] = c;
		++i;
	}
	s[i] = '\0';
	return i;
}

int match(const char *string, char *pattern) { 
    int status;
	regex_t re;
	if(regcomp(&re, pattern, REG_EXTENDED|REG_NOSUB) != 0) {
    	return 0; 
    }
  	status = regexec(&re, string, (size_t)0, NULL, 0);
  	regfree(&re);
  	if(status != 0) {   
    	return 0; 
    }
  return 1; 
} 

```
when run like this:
```

ls | /.mgrep .c$

```
I expect it to print out all files that end with '.c', but it prints nothing

For me to be able to compile this, I need to include the file <regex.h> as well.

It's not a good idea to include code (function definitions) in .h files. Put them in a .c file and put the declarations in a .h file.

The cause of the problem is apparent if you put a trace output call in your function 'match'; the strings still end with a newline, so .c$ can never match.

---

### Post by matmatmat on 2009-10-22
> **Arndt said:**
> 
It's not a good idea to include code (function definitions) in .h files. Put them in a .c file and put the declarations in a .h file.

Sorry, I had it like this,
.h
```

void afunction();

```
.c
```

void afunction(){
}

```

---

### Post by johnl on 2009-10-22
Also, if you want to match the literal '.' character you need to escape it:

```
ls -l . | ./mpgrep "\.c"
```

---

### Post by dwhitney67 on 2009-10-22
> **johnl said:**
> Also, if you want to match the literal '.' character you need to escape it:

```
ls -l . | ./mpgrep "\.c"
```

Cool, thanks for that tip.  I tested the program I submitted earlier, and it works!

---

