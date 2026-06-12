---
title: "[SOLVED] Remove n characters from beginning of a string in C"
date: 2008-10-20
forum: Programming Talk
---

### Post by roccivic on 2008-10-20
Howdy?

I'm writing (well, at least trying to) a program in C. This program will have a configuration file, which I need to access, locate some data and assign it to variables.
The configuration file looks like this:
```
PORT=999
DISPLAY=100
CAL_A=100
CAL_B=101
```

So far I've written the part that will open the file and locate the line containing "PORT=" or "DISPLAY=" etc...
But I can't figure out how to remove the "PORT=" part from the string and return whatever is left.

Oh, and need to return an integer :confused:

```
int get_port_address()
{
	int port;
	char line[100];

	FILE *fp;
	fp = fopen( "/home/user/.test/config", "r");
	if ( fp == 0 ) {
		printf( " Cannot open configuration file.\n " );
		return 0;
	}
	while ( fgets ( line, 100, fp ) != NULL) {
		if ( strncmp( line, "PORT=", 5 ) == 0 ) {
				/*
                                Hmmm, what to put here???
				*/
				return port;
		}
	}
}
```

Many thanks to everyone looking into this.

Rouslan

---

### Post by mike_g on 2008-10-20
You might want to look at using strtok:
```
/* strtok example */
#include <stdio.h>
#include <string.h>

int main ()
{
  char str[] ="PORT=1234";
  char * pch;
  printf ("Splitting string \"%s\" into tokens:\n",str);
  pch = strtok (str,"=");
  while (pch != NULL)
  {
    printf ("%s\n",pch);
    pch = strtok (NULL, "=");
  }
  return 0;
}

```
for more info: [http://www.cplusplus.com/reference/clibrary/cstring/strtok.html](http://www.cplusplus.com/reference/clibrary/cstring/strtok.html)

Edit: to convert the righthand section to an integer you can use strtol:
[http://www.cplusplus.com/reference/clibrary/cstdlib/strtol.html](http://www.cplusplus.com/reference/clibrary/cstdlib/strtol.html)

---

### Post by roccivic on 2008-10-20
Cool, that worked.

Many thanks

```
int get_port_address()
{
	int port = 1;
	char line[100];
	char * pch;

	FILE *fp;
	fp = fopen( "/media/disk/counter/source/current/config", "r");
	if ( fp == 0 ) {
		printf( " Cannot open configuration file. Exiting...\n " );
		return 0;
	}
	while ( fgets ( line, 100, fp ) != NULL ) {
		if ( strncmp( line, "PORT=", 5 ) == 0 ) {
			pch = strtok( line,"=" );
			pch = strtok( NULL, "=" );
			port = strtol( pch, NULL, 10 );
		}
	}
	return port;
}
```

---

