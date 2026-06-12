---
title: "fopen --&gt; How to read what a file contains?"
date: 2010-06-21
forum: Programming Talk
---

### Post by hakermania on 2010-06-21
Hello all, I wanna check if a file contains the word "Permitted".
Unfortunately I don;t know very well how to use fopen. Can you help me a  bit? Thank you! Let as take for example that the file is at
/home/alex/file.txt
```
if ( words_in_/home/alex/file.txt = "Permitted" )
cout << "Permitted!"
else
cout << "Not permitted!"
```
 
I've though of making something like that but I don;t know how to read  the containers of a file....Thx in advance!

---

### Post by soltanis on 2010-06-21
```

#!/bin/bash
grep Permitted < file.txt

```

Now's a good time to introduce you to manual pages as well.

```

sudo apt-get install manpages-dev
man 1 grep
man 3 fopen
man 3 fgets

```

That will get you started.

---

### Post by rsmitty on 2010-06-21
I'm at work so I can't test right now, but it should be something along the lines of:
 
```

//Create File Pointer
FILE *fp;
 
//Open file for reading
fp = fopen('home/alex/file.txt','r')
 
string temp;
 
//Get file contents line by line
while(getline(fp,temp)){
//Check if "Permitted" is in current string
     if(temp.find("Permitted",0) != string::npos){
        cout<<"Permitted!"
     }
     else{
        cout<<"Not Permitted!"
     }
  }
 
//Close file
fclose(fp);
 
}
 

```
 
[]("http://www.cplusplus.com/forum/general/3200/")

---

### Post by MadCow108 on 2010-06-21
you can't mix c++ iostreams and c streams in that way.

open the file like this:
ifstream file("home/alex/file.txt");

and remove the close (or replace it with file.close() but not really necessary as it gets closed when file object gets destroyed)
then the code should be fine, except it does also trigger on things like: "123Permitted123"

If you don't want this and your key is seperated by whitespace you can use the formatted extraction operator:
```

string buffer;
string key("Permitted");
ifstream file("home/alex/file.txt");
while(file >> buffer) {
  if (buffer == key)
    //do stuff
}

```

here's a good reference:
[http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

for C look at fgets, fread and strstr, but its a little more work as you have to handle buffers yourself.

but as already mentioned such a simple problem can be solved faster with unix programs like grep

---

### Post by hakermania on 2010-06-22
Ok, here's how I've gone so far, but I got 2 errors, can you help me?
Code:
```

1. #include <stdio.h>
2. #include <cerrno>
3. #include <sys/stat.h>
4. #include <sys/types.h>
5. #include <pwd.h>
6. #include <unistd.h>
7. #include <string>
8. #include <iostream>
9. using namespace std;
10. int main()
11. {
12.    struct passwd *passwd;
13.    passwd = getpwuid ( getuid());
14.    string user(passwd->pw_name);
15.    user = "/home/" + user + "/.config/Home/unkilled.txt";
16. ifstream file( user );
17. 
18. string temp;
19. 
20. //Get file contents line by line
21. while(getline(user,temp)){
22. //Check if "Permitted" is in current string
23.    if(temp.find("permitted",0) != string::npos){
24.       cout<<"Permitted!";
25.   }
26.   else{
27.      cout<<"Not Permitted!";
28.   }
29. }
30. file.close;
31.
32. return 0;
33. }
```Errors:
```

1) /home/alex/Qt/check/main.cpp:line 16: error: variable ‘std::ifstream file’ has initializer but incomplete type
2) /home/alex/Qt/check/main.cpp:line 21: error: cannot convert ‘std::string’ to ‘char**’ for argument ‘1’ to ‘__ssize_t getline(char**, size_t*, FILE*)’

```

---

### Post by hakermania on 2010-06-22
Any suggestion ?? :/

---

### Post by MadCow108 on 2010-06-22
ifstream is defined in <fstream>, so you must include it.

and there are two getlines one in C one in C++
you want the c++ version so you either have to set the namespace:
std::getline(...)
or kick out the unneeded C header stdio.h (which would be correctly included as <cstdio> in C++)

also your string user initialization gets deleted by the following line, are you missing a += ?

---

### Post by Krupski on 2010-06-22
> **hakermania said:**
> Hello all, I wanna check if a file contains the word "Permitted".
Unfortunately I don;t know very well how to use fopen. Can you help me a  bit? Thank you! Let as take for example that the file is at
/home/alex/file.txt
```
if ( words_in_/home/alex/file.txt = "Permitted" )
cout << "Permitted!"
else
cout << "Not permitted!"
```
 
I've though of making something like that but I don;t know how to read  the containers of a file....Thx in advance!

You may be able to use this:

**File: ffind.c** ```

///////////////////////////////////////////////////////////
// ffind.c june 2010 rak.
// free software - use, modify and distribute freely
//
// usage ffind filename 'text-you-wish-to-find'
// note: wildcards OK for filename.
// note: search is NOT CASE SENSITIVE.
///////////////////////////////////////////////////////////

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>

#undef BUFSIZ
#define BUFSIZ 65535

int readln(FILE *, char *);

int main(int argc, char *argv[])
{
	FILE *fp;
	char buffer[BUFSIZ] = { 0 };
	char string[BUFSIZ] = { 0 };
	int n, line;

	/* copy search argument to "string" and uppercase it */
	for (n = 0; n < (int)strlen(argv[argc - 1]); n++) {
		string[n] = toupper(argv[argc - 1][n]);
	}

	/* for every filename found... */
	for (n = 1; n < (argc - 1); n++) {
		line = 0;
		fp = fopen(argv[n], "rb");

		if (fp == NULL) {
			fprintf(stderr, "Could not open %s\n", argv[n]);
		} else {
			while (!feof(fp)) {
				readln(fp, buffer);
				line++;
				/* if search string found */
				if (strstr(buffer, string)) {
					fprintf(stdout,
						"Found in %s (line %d)\n",
						argv[n], line);
					break;
				}
			}
			fclose(fp); /* close input file, do next */
		}
	}
	return 0;
}

/* read a line "clean" from fp and uppercase it */
int readln(FILE * fp, char *str)
{
	char buf[BUFSIZ] = { 0 };
	int n, len;
	fgets(buf, BUFSIZ, fp);
	len = strlen(buf);
	while (len > -1) {
		if (buf[len] < 0x21) {
			buf[len] = 0;
			len--;
		} else {
			break;
		}
	}
	len++;
	buf[len] = 0;
	strncpy(str, buf, BUFSIZ);
	for (n = 0; n < BUFSIZ; n++) {
		str[n] = toupper(str[n]);
	}
	return strlen(str);
}

```


I use it to search for strings that may be found in PHP or HTML files.

Here's what the output looks like:

```

root@storage:/home/shared/.web-server/phpBB3# ffind *.php "header"
Found in common.php (line 136)
Found in cron.php (line 27)
Found in faq.php (line 80)
Found in feed.php (line 145)
Found in index.php (line 141)
Found in mchat.php (line 89)
Found in memberlist.php (line 902)
Found in posting.php (line 1481)
Found in report.php (line 232)
Found in search.php (line 529)
Found in style.php (line 147)
Found in test.php (line 96)
Found in top_posters.php (line 47)
Found in ucp.php (line 123)
Found in viewforum.php (line 144)
Found in viewonline.php (line 72)
Found in viewtopic.php (line 1781)

```


Note: To avoid cluttering the screen, the program shows ONLY the first find. Any more match(es) in the same file are not displayed.


Hope this helps...

-- Roger

---

### Post by dwhitney67 on 2010-06-22
Per that fstream API, which is documented quite clearly at this [site]("http://www.cplusplus.com/reference/iostream/fstream/fstream/"), you need to pass a const char pointer to a string, not the STL string itself to the fstream constructor.

So...
```

std::string filename = "/home/me/foo.txt";

...

std::ifstream fileStream(filename**.c_str()**);

...


```

Hakermania -

Bookmark this page, and reference it often when you encounter a compiler error:

[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

---

