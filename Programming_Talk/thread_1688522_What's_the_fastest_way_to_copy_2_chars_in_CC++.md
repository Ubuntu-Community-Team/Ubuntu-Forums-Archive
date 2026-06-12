---
title: "What's the fastest way to copy 2 chars* in C/C++?"
date: 2011-02-15
forum: Programming Talk
---

### Post by t1497f35 on 2011-02-15
Hi,
I'd like to copy two const chars* to a third one as fast as possible, here's what I came up with, is there a faster solution in C/C++?

```

#include <iostream>
#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main() {
    const char *name1 = "name1";
    size_t len1 = strlen(name1);
    const char *name2 = "name2";
    size_t len2 = strlen(name2);
    
    char *result = (char*)malloc(len1 + len2 + 1);
    if(result == NULL) {
        std::cerr << "malloc()" << std::endl;
        return 1;
    }

    memcpy(result, name1, len1);
    memcpy(result+len1, name2, len2);
    result[len1+len2] = '\0';

    std::cout << "result: \"" << result << "\"" << std::endl;

    free(result);
    return 0;
}

```Also, are there errors in my code?
And could I write instead of
result[len1+len2+1] = '\0';
this?:
result[len1+len2+1] =  0;

---

### Post by worksofcraft on 2011-02-15
> **t1497f35 said:**
> Hi,
I'd like to copy two const chars* to a third one as fast as possible, here's what I came up with, is there a faster solution in C/C++?

```

#include <iostream>
#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main() {
    const char *name1 = "name1";
    size_t len1 = strlen(name1);
    const char *name2 = "name2";
    size_t len2 = strlen(name2);
    
    char *result = (char*)malloc(len1 + len2 + 1);
    if(result == NULL) {
        std::cerr << "malloc()" << std::endl;
        return 1;
    }

    memcpy(result, name1, len1);
    memcpy(result+len1, name2, len2);
    result[len1+len2+1] = '\0';

    std::cout << "result: \"" << result << "\"" << std::endl;

    free(result);
    return 0;
}

```Also, are there errors in my code?
And could I write instead of
result[len1+len2+1] = '\0';
this?:
result[len1+len2+1] =  0;

besides the copying, strlen also takes time because it basically searches for the terminating '\0', counting characters as it goes.
OTOH if you can define them as arrays of characters you can use sizeof which is evaluated at compile time and is inclusive of the null terminator:
[php]
    const char name1[] = "name1";
    const char name2[] = "name2";
    char result[sizeof(name1) + sizeof(name2) - 1];
[/php]

memcpy will copy things as (long) words if they happen to have matching word boundaries thus making it 4 to 8 times faster than single byte copy, but it would probably be better to use the STL string class which handles all that memory allocation malarkey for you... a lot depends on what you want to achieve.

---

### Post by t1497f35 on 2011-02-15
Thanks a lot! (the 2 const char* are created dynamically when reading the dir and thus to get a stat of each file I'd have to add the name of each file to the current dir path at runtime).

---

### Post by Some Penguin on 2011-02-15
strncat() would also work.

That said, this is almost certainly *not* a bottleneck unless you're writing a very small and very fast program;  the speed of string concatenation is unlikely to matter.

---

### Post by t1497f35 on 2011-02-15
I agree that it doesn't really matter, I just wanted to test how much faster can I make it (out of fun and to learn C++ better).
I'm also slightly surprised there's no way (none that I found anyway) to do a stat (dirent doesn't cut it for XFS doesn't support dirent d_type) without having to add 2 strings together, I thought it'd be slightly faster if one could stat the filename and the file descriptor of the dir the file is in, thus one eliminates quite a few CPU cycles, on Google's servers and others where there are like hundreds of thousands files in a dir it could make a difference.. just my 0.04$ (0.04 because of inflation).

---

### Post by Some Penguin on 2011-02-15
*shrug* In that case, use a single fixed buffer of size 1 + twice maximum path length, scan linearly over first string (checking bounds!), scan linearly over second string (checking bounds), add terminating null -- unless you need to have separate buffers for some reason.   Should be faster than using separate strlen() or doing malloc/free every time.

---

### Post by forrestcupp on 2011-02-15
> **worksofcraft said:**
> but it would probably be better to use the STL string class which handles all that memory allocation malarkey for you... 

+1

I'd probably take the easy way out and just copy the chars to a string.

---

### Post by worksofcraft on 2011-02-15
> **forrestcupp said:**
> +1

I'd probably take the easy way out and just copy the chars to a string.

Also I think std::string maintains a length member so that it won't have to count characters every time and it knows exactly where to append the second string when it comes to concatenation.

One could easily write a test program to time a million string concatenations done with the old C string routines and malloc and then compare it to std::string... my bets are on std::string for performance ;)

---

### Post by psusi on 2011-02-15
If you want to do it the C way, then use strcpy and strcat rather than memcpy.  If you want to do it the C++ way, then use a std::string.

---

### Post by worksofcraft on 2011-02-16
> **psusi said:**
> If you want to do it the C way, then use strcpy and strcat rather than memcpy.  If you want to do it the C++ way, then use a std::string.

well if you just wanna know the relative speeds of strcpy, strncpy and memcpy... here they are:
```

$ g++ -Wall -O3 strspeed.cpp
strspeed.cpp: In function &#8216;int main()&#8217;:
strspeed.cpp:8: warning: unused variable &#8216;alignmetoalongboundary&#8217;
strspeed.cpp:10: warning: unused variable &#8216;alignmetoalongboundary_too&#8217;
$ ./a.out
string time =2.300000 seconds
strcpy time =1.040000 seconds
strncpy time =3.470000 seconds
memcpy time =0.130000 seconds

```

and I'll leave this listing so you can work out what purpose the unused variables served... yes they were essential for that result :D :popcorn:

[php]
#include <cstdio>
#include <cstring>
#include <ctime>
#include <string>

int main() {
	clock_t iStart;
	long alignmetoalongboundary;
	char aString[] = "Hello I am a really kewl string and that is why the processor is gunna copy me quite afew times now :)";
	long alignmetoalongboundary_too;
	char aStore[sizeof(aString)];
	std::string aCppString;

	iStart = clock();
	for (unsigned long i=0; i < 30000000L; ++i) {
		aCppString = aString;
	}
	printf("string time =%f seconds\n", float(clock()-iStart)/CLOCKS_PER_SEC);


	iStart = clock();
	for (unsigned long i=0; i < 30000000L; ++i) {
		strcpy(aStore, aString);
	}
	printf("strcpy time =%f seconds\n", float(clock()-iStart)/CLOCKS_PER_SEC);

	iStart = clock();
	for (unsigned long i=0; i < 30000000L; ++i) {
		strncpy(aStore, aString, sizeof(aString));
	}
	printf("strncpy time =%f seconds\n", float(clock()-iStart)/CLOCKS_PER_SEC); 	

	iStart = clock();
	for (unsigned long i=0; i < 30000000L; ++i) {
		memcpy(aStore, aString, sizeof(aString));
	}
	printf("memcpy time =%f seconds\n", float(clock()-iStart)/CLOCKS_PER_SEC);


	return 0;
}
[/php]

based on those figures which would you prefer to use ?

p.s. the test isn't fair on std::string because that is doing all your memory allocation as well as the copying, but the C versions are just doing the copying into a ready allocated buffer.

---

### Post by Arndt on 2011-02-16
> **t1497f35 said:**
> I agree that it doesn't really matter, I just wanted to test how much faster can I make it (out of fun and to learn C++ better).
I'm also slightly surprised there's no way (none that I found anyway) to do a stat (dirent doesn't cut it for XFS doesn't support dirent d_type) without having to add 2 strings together, I thought it'd be slightly faster if one could stat the filename and the file descriptor of the dir the file is in, thus one eliminates quite a few CPU cycles, on Google's servers and others where there are like hundreds of thousands files in a dir it could make a difference.. just my 0.04$ (0.04 because of inflation).

I don't think it's likely that they are keeping hundreds of thousands of files in one directory. Either the directory structure is very deep, a balanced tree, or they use a database.

---

### Post by t1497f35 on 2011-02-16
Thanks anyone!
@[worksofcraft]("http://ubuntuforums.org/member.php?u=386585") yep memcpy is quite a lot faster! thanks
PS: @[Some Penguin]("http://ubuntuforums.org/member.php?u=963358") yep, that's certainly true, thanks, I'll modify my code to use a single buffer instead of doing malloc/free for each new file as you noticed.
PPS: @[Arndt]("http://ubuntuforums.org/member.php?u=106064") Google does have such dirs, I remember them complaining that using Java's dir.listFiles() is very costly on dirs with huge amounts of files in them, specifically for this (and other) reason(s) they helped Sun implement nio2 which will come with Java7 and as Java7 gets released this year Google will probably reconsider using Java's own solution to iterate very large dirs instead of using custom code to do such stuff in Java.

---

### Post by psusi on 2011-02-16
The memcpy comparison is unfair because you left out the call to strlen() to figure out how much to tell it to copy.  The combination of strlen and memcpy will be slower than just strcpy.

---

### Post by worksofcraft on 2011-02-16
> **psusi said:**
> The memcpy comparison is unfair because you left out the call to strlen() to figure out how much to tell it to copy.  The combination of strlen and memcpy will be slower than just strcpy.

The test was to compare copying time exclusively.
My assumption is that string length was already known and the appropriate amount of memory already allocated. Establishing that would be a separate step for both strcpy and memcpy anyway :p

What I hadn't tested is whether C++ strings can take advantage of the fact that they already know the string lengths. So I added a second test where it copies a C++ string to another C++ string and the result:

```

$ ./a.out
string time =2.120000 seconds
string 2 string time =0.200000 seconds
strcpy time =1.040000 seconds
strncpy time =3.450000 seconds
memcpy time =0.120000 seconds

```

As you can see, when it doesn't have to look for that null terminator std::string is about 10 times faster and keep in mind it has all the memory management build in :popcorn:

---

### Post by psusi on 2011-02-16
> **worksofcraft said:**
> 
My assumption is that string length was already known and the appropriate amount of memory already allocated. Establishing that would be a separate step for both strcpy and memcpy anyway :p

No, strcpy finds the end of the string itself; it does not need to be told the length.  That is why your test is misleading: you have to add the strlen in order to call memcpy.  With C strings you don't usually keep the length around, which is why all of the C string functions find it automatically.

> **worksofcraft said:**
> As you can see, when it doesn't have to look for that null terminator std::string is about 10 times faster and keep in mind it has all the memory management build in :popcorn:

Yep.  std::string > strcpy > strlen + memcpy.

---

### Post by worksofcraft on 2011-02-16
> **psusi said:**
> No, strcpy finds the end of the string itself; it does not need to be told the length.  That is why your test is misleading: you have to add the strlen in order to call memcpy.  With C strings you don't usually keep the length around, which is why all of the C string functions find it automatically.



Yep.  std::string > strcpy > strlen + memcpy.

Lol I think we are talking at cross purposes. I meant that you need that length of the string for this bit (from the original post):
[php]
    char *result = (char*)malloc(len1 + len2 + 1);
[/php]

... so quite often strcpy has nowhere to copy into unless you did that first anyway. If you **did** do that first then using memcpy will be faster, but otherwise yep, sure use strcpy ;)

---

