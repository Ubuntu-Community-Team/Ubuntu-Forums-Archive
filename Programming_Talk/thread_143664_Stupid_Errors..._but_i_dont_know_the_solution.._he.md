---
title: "Stupid Errors... but i dont know the solution.. help please (its C)"
date: 2006-03-12
forum: Programming Talk
---

### Post by noob_Lance on 2006-03-12
Hey... when i try to compile the following code.. i get the errors below.

heres the code:
```

#include <stdio.h>
#include <string.h>
FILE *synclient;

int GenFile();
int OpenFile();
int RemoveFile();
int TrimString(char[]);
int GetState();
int ChangeState(int);

int main()
{
	GenFile();
}

int GenFile()
{
	system ("synclient -l > /tmp/synclient.tmp");
	GetState();
}
int OpenFile()
{
	if ((synclient = fopen("/tmp/synclient.tmp", "rb")) == NULL)
	{
		
	}
}
int GetState()
{
	char temp_name[40];
	char temp_delim[5];
	char temp_setting[20];
	int setting;
	OpenFile();
	while (fscanf(synclient, "%s %s %s", temp_name, temp_delim, temp_setting) == 1)
	{
		TrimString(temp_name);
		TrimString(temp_setting);
		if (temp_delim == "Touchpadoff")
		{
			setting = temp_setting;
			ChangeState(setting);
		}
	}
	fclose(synclient);
}
int TrimString(char temp[])
{
	strtrim(temp);
	return temp;
}
int ChangeState(int setting)
{
	if (setting == 0)
	{
		//turn touchpad off
		system("synclient touchpadoff=1");
	}
	else
	{
		//turn touchpad on
		system("synclient touchpadoff=0");
	}
}



```

and my errors:
```

lance@testbed:~$ gcc -o tester tester.c
tester.c: In function ‘GetState’:
tester.c:42: warning: assignment makes integer from pointer without a cast
tester.c: In function ‘TrimString’:
tester.c:51: warning: return makes integer from pointer without a cast
/tmp/cc0d0eH5.o: In function `TrimString':
tester.c:(.text+0xf3): undefined reference to `strtrim'
collect2: ld returned 1 exit status

```

---

### Post by toojays on 2006-03-12
The warning on line 42 is because ChangeState expects an int and you are passing it a string.

The warning on line 51 is because you have declared TrimString to return an int, and you are having it return a string.

The error you are getting is a linker error because the function strtrim() is not found in any of GCC's default library files (which basically means it's not a standard C or POSIX function). You would have received a more useful warning from the compiler about this issue (and others) if you had given gcc the options "-W -Wall".

---

### Post by rplantz on 2006-03-12
> **noob_Lance]Hey... when i try to compile the following code.. i get the errors below.
int TrimString(char temp[])
{
	strtrim(temp) said:**
> 

This function returns temp, which is a char *, but the function prototype says int.

Where is the function strtrim defined?

---

### Post by noob_Lance on 2006-03-13
```

lance@testbed:~$ gcc -o tester tester.c -W -Wall
tester.c: In function ‘main’:
tester.c:15: warning: control reaches end of non-void function
tester.c: In function ‘GenFile’:
tester.c:19: warning: implicit declaration of function ‘system’
tester.c:21: warning: control reaches end of non-void function
tester.c: In function ‘OpenFile’:
tester.c:28: warning: control reaches end of non-void function
tester.c: In function ‘GetState’:
tester.c:42: warning: assignment makes integer from pointer without a cast
tester.c:47: warning: control reaches end of non-void function
tester.c: In function ‘TrimString’:
tester.c:50: warning: implicit declaration of function ‘strtrim’
tester.c:51: warning: return makes integer from pointer without a cast
tester.c: In function ‘ChangeState’:
tester.c:65: warning: control reaches end of non-void function
/tmp/ccLjNZ8n.o: In function `TrimString':
tester.c:(.text+0xf3): undefined reference to `strtrim'
collect2: ld returned 1 exit status

```

thats with "-W -Wall"

im not the best with C so anyone wanna help me fix these errors haha

---

### Post by richbeales on 2006-03-13
First point: All your functions are defined as (e.g.) "int main()".  "int" is the return value, so unless your function is going to return an integer, then you want to make them void (i.e. return nothing).  Either make the function return an integer  -- "return 1;"  or make them void.

---

