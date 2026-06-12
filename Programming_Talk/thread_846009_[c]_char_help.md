---
title: "[c] char help"
date: 2008-07-01
forum: Programming Talk
---

### Post by gormsby on 2008-07-01
I wrote a stupid 'encryption' algorithm in PHP and want to port it to c. 

Here is it in php:

```

function ENCE($Unsafe)
{
	for($x=0;$x<strlen($Unsafe);$x++){
		$Safe .= chr(ord($Unsafe[$x])+1) . RandStr();
	}
	return $Safe;
}

```

```

function DECE($Safe)
{
	for($x=0;$x<strlen($Safe);$x++){
		if(!fmod($x,2)) $Unsafe .= chr(ord($Safe[$x])-1);
	}
	return $Unsafe;
}

```

```

function RandStr()
{
	return chr(rand(33,47));
}

```

So it takes a string like 
"hello"
and turns it into something like
"I(f"m.m+p&".. or "I"f'm$m%p*"


I just need some help with porting it to c, i'm not that good with chars/memory allocation though.

---

### Post by mynamewastaken on 2008-07-01
I don't know enough about php to tell you, but I can point you to some resources on c char's and such:

[http://www.cs.swarthmore.edu/~newhall/unixhelp/C_chars.html](http://www.cs.swarthmore.edu/~newhall/unixhelp/C_chars.html)
[http://www.physics.drexel.edu/students/courses/Comp_Phys/General/C_basics/c_tutorial.html#pointers](http://www.physics.drexel.edu/students/courses/Comp_Phys/General/C_basics/c_tutorial.html#pointers)

---

### Post by gormsby on 2008-07-02
here is what i have so far:

```

#include <stdio.h>
#include <time.h>

int fRand();
void fEncrypt(char* cString);

int main()
{
	srand(time(0));
	char cUnsafe[] = "wget http://www.google.com";
	fEncrypt(cUnsafe);
}

void fEncrypt(char* cString)
{
	printf("Encrypting string: %s\n",cString);
	int iUN = strlen(cString)*2;
	char cSafe[iUN];
	int x=1,y=0;
	for(x=0;y<iUN;x++){
		cSafe[y++] = cString[x]+1;
		cSafe[y++] = (char)fRand();
	}
	cSafe[iUN] = '\0';
	printf("Encrypted string: %s\n",cSafe);
}

int fRand()
{
	int iRand;
	iRand = rand() %(125-33+1)+33;
	return iRand;
}

```

The PHP code might look a bit confusing, but all it does is go through a string and get the ascii code +1 of each character and turns it into a character (ie 97 into 'a'), but puts a random character in between each one.

EG:
the string 'abcdef'
will turn into something like this:
'bCcyd]eNffgq'
Or 'b&cod|e]fKgo'
Or '**b**r**c**b**d**"**e**H**f**`**g**1'.

I wrote the C code to encrypt it, but have no way of returning it. Blah.

---

### Post by Zugzwang on 2008-07-02
Depending on why you want to use C, you can use C++-classes for making string manipulation simple. Example: (Warning! Ugly C/C++-mix ahead)

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <string>
#include <time.h>

int fRand();
std::string fEncrypt(char* cString);

int main()
{
	srand(time(0));
	char cUnsafe[] = "wget http://www.google.com";
	printf("Encrypting string: %s\n",cUnsafe);
	printf("Encrypted string: %s\n",fEncrypt(cUnsafe).c_str());
	fEncrypt(cUnsafe);
}

std::string fEncrypt(char* cString)
{
	int iUN = strlen(cString)*2;
	char cSafe[iUN+1];
	int x=1,y=0;
	for(x=0;y<iUN;x++){
		cSafe[y++] = cString[x]+1;
		cSafe[y++] = (char)fRand();
	}
	cSafe[iUN] = '\0';
	return cSafe;
}

int fRand()
{
	int iRand;
	iRand = rand() %(125-33+1)+33;
	return iRand;
}
[/PHP]

Here, the class std::string is used for string containment. In pure C, you would allocate memory and let "fEncrypt" return the pointer to that location, **but it is the programmer's task to free it again afterwards**:
[PHP]
#include <stdio.h>
#include <time.h>
#include <string.h>
#include <malloc.h>

int fRand();
char* fEncrypt(char* cString);

int main()
{
	srand(time(0));
	char cUnsafe[] = "wget http://www.google.com";
	printf("Encrypting string: %s\n",cUnsafe);
	char *result = fEncrypt(cUnsafe);
	printf("Encrypted string: %s\n",result);

        // Explicit deletion
	free(result);
}

char* fEncrypt(char* cString)
{
	int iUN = strlen(cString)*2;

        // Allocation
	char *cSafe = malloc(sizeof(char)*(iUN+1));
	int x=1,y=0;
	for(x=0;y<iUN;x++){
		cSafe[y++] = cString[x]+1;
		cSafe[y++] = (char)fRand();
	}
	cSafe[iUN] = '\0';
	return cSafe;
}

int fRand()
{
	int iRand;
	iRand = rand() %(125-33+1)+33;
	return iRand;
}
[/PHP]

By the way, when you allocate a char array, you have to make it one char larger than you actually need (to contain the '\0' character).

---

### Post by skeeterbug on 2008-07-02
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

int fRand();
char* fEncrypt(char*);
char* fDecrypt(char*);

int main(void)
{
	time_t t = time(NULL);
	
	srand(t);
	
	char *cUnsafe = "abc";
	char *results = fEncrypt(cUnsafe);
	printf("%s\n", results);

	char *dresults = fDecrypt(results);
	printf("%s\n", dresults);

	free(results);
	free(dresults);

        return EXIT_SUCCESS;
}

char* fEncrypt(char* cString)
{
	printf("Encrypting string: %s\n",cString);
	int len = strlen(cString)*2;
	char *cSafe = malloc(len + 1);
	if(cSafe != NULL)
	{
		int x=1,y=0;
		for(x=0;y<len;x++){
			cSafe[y++] = cString[x]+1;
			cSafe[y++] = (char)fRand();
		}
		printf("Encrypted string: %s\n",cSafe);
		return cSafe;
	}
	else
	{
		printf("malloc failed.");
		return NULL;
	}
}

char *fDecrypt(char* cString)
{
	printf("Decrypting string: %s\n",cString);
	int len = strlen(cString) / 2;
	char *cSafe = malloc(len + 1);
	if(cSafe != NULL)
	{
		int x;
		int y = 0;
		for(x=0;x<len;x++)
		{
			cSafe[x] = (char)cString[y] - 1;
			y+=2;
		}
		printf("Decrypted string: %s\n",cSafe);
		return cSafe;
	}
	else
	{
		printf("malloc failed.");
		return NULL;
	}
}

int fRand()
{
	int iRand = rand() %(125-33+1)+33;
	return iRand;
}

```

Added fDecrypt.

---

### Post by skeeterbug on 2008-07-02
Also - Comments never hurt anyone. :)

---

