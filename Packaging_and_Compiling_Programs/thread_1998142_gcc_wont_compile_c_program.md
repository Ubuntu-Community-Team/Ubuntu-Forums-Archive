---
title: "gcc wont compile c program"
date: 2012-06-06
forum: Packaging and Compiling Programs
---

### Post by Elifelet on 2012-06-06
Hi,
I am working on ubuntu 12.04 and learning to program in c.
I have a program that has:
```
#include <mysql/mysql.h>
```
and still when ever I try to compile the file I get this error:
```
:~/Documents/cpil$ make 5-1
gcc -o db1 -L/usr/lib/mysql -lmysqlclient -L/usr/include -lgd -L~/usr/include chapter5_1.c c_in_linux.a -lc
/tmp/ccGUFEYh.o: In function `main':
chapter5_1.c:(.text+0x26f): undefined reference to `mysql_init'
chapter5_1.c:(.text+0x28f): undefined reference to `mysql_options'
chapter5_1.c:(.text+0x2d3): undefined reference to `mysql_real_connect'
chapter5_1.c:(.text+0x332): undefined reference to `mysql_query'
chapter5_1.c:(.text+0x391): undefined reference to `mysql_query'
chapter5_1.c:(.text+0x3a9): undefined reference to `mysql_query'
chapter5_1.c:(.text+0x3b9): undefined reference to `mysql_use_result'
chapter5_1.c:(.text+0x3ef): undefined reference to `mysql_fetch_row'
chapter5_1.c:(.text+0x406): undefined reference to `mysql_free_result'
chapter5_1.c:(.text+0x412): undefined reference to `mysql_close'
collect2: ld returned 1 exit status
make: *** [5-1] Error 1

```

I realize the gcc do not find the relevant mysql.h and -lmysqlclient. 
I used the locate command in order to find mysql.h (/usr/include/mysql.h) but the library mysqlclient
seems still not to work, when I search for it I find it here: ```
/usr/lib/i386-linux-gnu/ 
```
although I have tried to changed the gcc command to:
 ```
gcc -o db1 -L/usr/lib/i386-linux-gnu/ -lmysqlclient -L/usr/include -lgd -L~/usr/include chapter5_1.c c_in_linux.a -lc
```

What am I doing wrong? why cant I compile?
Thanks
E.

---

### Post by TheFu on 2012-06-06
Header directories (search paths) are included using a -I, not a -L.
Header files and libraries are related, but not the same.  

BTW, this is not an odd question. It is probably a simple typo and you knew the answer already.

To prevent this sort of mistake, crafting a **makefile **for your project that handles dependencies and includes with the correct -I and -L directives would be my recommendation.  Build scripts should usually be avoided, since those become unmaintainable for non-trivial projects.  

If you are a beginner, starting with a build script that contains your gcc command is fine.
Something like this would be my beginning build.sh script:

> gcc -o db1 chapter5_1.c \
-I/usr/include -I~/usr/include \
-L/usr/lib/i386-linux-gnu/ -lmysqlclient -L/usr/lib -lgd -lc
Notice how similar parts are grouped together - compiled modules, includes, and libraries. Organization helps prevent common mistakes.

The default make command will not handle extra libs, as you expect, so typing "make 5-1" really shouldn't work at all. Do you have a makefile?

I'm confused by the use of "c_in_linux.a" - is that your library? Did you assemble it from .o files?  Which directory has it? That directory and include path probably need to be added to 2 lines of the build.sh script.

BTW, I've been using the same base makefile since 1993 for cross-platform development, so being a makefile expert is not necessary.

---

### Post by Elifelet on 2012-06-06
Hi TheFu
Thanks for your help.

I am learning c from a book called "c programing in linux"
I am in Chapter 5 and this is the program that I deal with:
```
/*****************************************************************
* C Programming in Linux (c) David Haskins 2008
* chapter5_1.c                                       	 *
*****************************************************************/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <mysql/mysql.h>
#include "c_in_linux.h"

int main(int argc, char *argv[], char *env[])
{
	char value1[255] = "",value2[255] = "",SQL[1024]="";
	int rc = 0;

	MYSQL *conn = NULL;
	MYSQL_RES *result = NULL;
	MYSQL_ROW row;

	printf("Content-type:text/html\n\n<html><body bgcolor=#23abe2>\n");
	strncpy(value1,(char *) getenv("QUERY_STRING"),255);
	printf("QUERY_STRING : %s<BR>\n", value1 );
	printf("<form>\n");
	//call the decode_value function to get value of "ITEM1"
	decode_value( "ITEM1=", (char *) &value1, 255);
	if(strlen(value1) > 0 )
		printf("<input type=\"TEXT\" name=\"ITEM1\" value=\"%s\">\n",value1);
	else
		printf("<input type=\"TEXT\" name=\"ITEM1\">\n");
	//call the decode_value function to get value of "ITEM2"
	decode_value( "ITEM2=", (char *) &value2, 255);
	if(strlen(value2) > 0 )
		printf("<input type=\"TEXT\" name=\"ITEM2\" value=\"%s\">\n",value2);
	else
		printf("<input type=\"TEXT\" name=\"ITEM2\">\n");
	printf("<input type=\"SUBMIT\">");
	printf("</form></body></html>\n");
	//OPEN DATABASE
	conn = mysql_init((MYSQL *) 0);
	mysql_options(conn,MYSQL_READ_DEFAULT_GROUP,"mysqlcapi");
	mysql_real_connect(conn, "localhost","","","test",0, NULL, 0);
	if(strcmp(value1,"delete") == 0 )
	{
  	sprintf(SQL,"delete from CIL");
		rc = mysql_query(conn,SQL);
	}
	//INSERT IF THERE IS ANY DATA
	if(strlen(value1) > 0 || strlen(value2) > 0)
	{
  	sprintf(SQL,"insert into CIL values ('%s','%s')",value1,value2);
		rc = mysql_query(conn,SQL);
	}
	//READ
	rc = mysql_query(conn,"select * from CIL");
	result = mysql_use_result(conn);
	while( (row = mysql_fetch_row(result)) != NULL)
	{
			printf("item1=%s   item2=%s<br>",row[0],row[1]);
	}
	mysql_free_result(result);
	mysql_close(conn);
  return 0;
}
```

There is also a make file:
```
#Makefile

SRC_CIL = decode_value.c
OBJ_CIL =  decode_value.o
CIL_INCLUDES = -I/usr/include/apache2 -I. -I/usr/include/apache2 -I/usr/include/apr-1
CIL_LIBS = -L/usr/lib/mysql -lmysqlclient -L/usr/lib -lgd -L~/public_html/Ventus/code

all: lib_cil chap1 chap2 chap3 chap4 chap5 chap6

lib_cil:
	gcc -c $(SRC_CIL)
	ar rcs c_in_linux.a $(OBJ_CIL)
	$(RM) *.o

chap1: 1-1 1-2 1-3 1-4 
1-1:
	gcc -o hello1 chapter1_1.c  -lc
1-2:
	gcc -o hello2 chapter1_2.c  -lc
1-3:
	gcc -o hello3 chapter1_3.c  -lc
	mv hello3 ~/public_html/cgi-bin
1-4:
	gcc -o hello4 chapter1_4.c  -lc	
	mv hello4 ~/public_html/cgi-bin

chap2: 2-1 2-2 2-3 2-4 2-5
2-1:
	gcc -o data1 chapter2_1.c  -lc
2-2:
	gcc -o data2 chapter2_2.c  -lc
2-3:
	gcc -o data3 chapter2_3.c  -lc
	mv data3 ~/public_html/cgi-bin
2-4:
	gcc -o data4 chapter2_4.c  -lc
	mv data4 ~/public_html/cgi-bin
2-5:
	gcc -o data5 chapter2_5.c  -lc
	mv data5 ~/public_html/cgi-bin

chap3: 3-1 3-2 3-3
3-1:
	gcc -o func1 chapter3_1.c  -lm
	mv func1 ~/public_html/cgi-bin
3-2:
	gcc -o func2 chapter3_2.c  -lm
	mv func2 ~/public_html/cgi-bin
3-3:
	gcc -o func3 chapter3_3.c  -lm
	mv func3 ~/public_html/cgi-bin

chap4: 4-1 4-2 4-3
4-1:
	gcc -o logic1 chapter4_1.c  -lc
	mv logic1 ~/public_html/cgi-bin
4-2:
	gcc -o logic2 chapter4_2.c  -lc
	mv logic2 ~/public_html/cgi-bin
4-3:
	gcc -o logic3 chapter4_3.c c_in_linux.a -lc
	mv logic3 ~/public_html/cgi-bin

chap5: 5-1
5-1:
	gcc -o db1 $(CIL_LIBS) chapter5_1.c c_in_linux.a -lc
	mv db1 ~/public_html/cgi-bin/db1

chap6: 6-1 6-2
6-1:
	gcc -o gdgraph1 $(CIL_LIBS) chapter6_1.c c_in_linux.a -lc
	mv gdgraph1 ~/public_html/cgi-bin
6-2:
	gcc -o gdgraph2 $(CIL_LIBS) chapter6_2.c c_in_linux.a -lc
	mv gdgraph2 ~/public_html/cgi-bin

chap8: 8-1
8-1:
	gcc -o ghost $(CIL_LIBS) chapter8_1.c -lc

clean:
	rm hello* data* 
 

```

regarding your question, yes I have made a library c_in_linux.a after I compiled to an object this code:
```
/*****************************************************************
* C Programming in Linux (c) David Haskins 2008
* decode_value.c                                       	 *
*****************************************************************/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void decode_value(const char *key, char *value, int size)
{
	int length = 0, i = 0, j = 0;
	char *pos1 = '\0',*pos2 = '\0';
	char code1 = '\0', code2 = '\0';

	strcpy(value,"");
	if( ( pos1 = strstr((char *) getenv("QUERY_STRING"), key)) != NULL )
	{
		for(i=0; i<strlen(key); i++) pos1++;
		if( (pos2 = strstr(pos1,"&")) != NULL )
		{
			length = pos2 - pos1;
		}
		else length = strlen(pos1);
		for(i = 0, j = 0; i <  length ; i++, j++)
		{
			if(j < size)
			{
				if(pos1[i] == '+') value[j] = ' ';
				else if(pos1[i] == '%')
				{
					i++;	code1 = pos1[i];
					i++;	code2 = pos1[i];
					if(code1 == '2' && code2== '0') value[j] = ' ';
					else if(code1 == '2' && code2== '1') value[j] = '!';//0x21
					else if(code1 == '2' && code2== '2') value[j] = '\"';
					else if(code1 == '2' && code2== '3') value[j] = '#';//0x23
					else if(code1 == '2' && code2== '4') value[j] = '$';//0x24
					else if(code1 == '2' && code2== '5') value[j] = '%';//0x25
					else if(code1 == '2' && code2== '6') value[j] = '&';//0x26
					else if(code1 == '2' && code2== '7') { value[j] = '\''; j++; value[j] = '\'';}//0x27
					else if(code1 == '2' && code2== '8') value[j] = '(';//0x28
					else if(code1 == '2' && code2== '9') value[j] = ')';//0x29
					else if(code1 == '2' && code2== 'B') value[j] = '+';//0x2B
					else if(code1 == '2' && code2== 'C') value[j] = ',';//0x2C
					else if(code1 == '2' && code2== 'F') value[j] = '/';//0x2F	
					else if(code1 == '3' && code2== 'A') value[j] = ':';//0x3A
					else if(code1 == '3' && code2== 'B') value[j] = ';';//0x3B
					else if(code1 == '3' && code2== 'C') value[j] = '<';//0x3C
					else if(code1 == '3' && code2== 'D') value[j] = '=';//0x3D
					else if(code1 == '3' && code2== 'E') value[j] = '>';//0x3E
					else if(code1 == '3' && code2== 'F') value[j] = '?';//0x3F	
					else if(code1 == '4' && code2== '0') value[j] = '@';//0x40	
					else if(code1 == '5' && code2== 'B') value[j] = '[';//0x5B
					else if(code1 == '5' && code2== 'C') value[j] = '\\';//0x5C
					else if(code1 == '5' && code2== 'D') value[j] = ']';//0x5D
					else if(code1 == '5' && code2== 'E') value[j] = '^';//0x5E
					else if(code1 == '7' && code2== 'B') value[j] = '{';//0x7B
					else if(code1 == '7' && code2== 'C') value[j] = '|';//0x7C
					else if(code1 == '7' && code2== 'D') value[j] = '}';//0x7D
					else if(code1 == '7' && code2== 'E') value[j] = '~';//0x7E
					else if(code1 == 'A' && code2== '3') { value[j] = 0xC2 ; j++; value[j] = 0xA3;}//0x27
					else if(code1 == '0' && code2== 'A') value[j] = ' ';
					else if(code1 == '0' && code2== 'D') j--;
					else value[j] = ' ';
				}
				else value[j] = pos1[i];
			}
		}
		if(j < size)
		{
			value[j] = '\0';
		}
		else value[size-1] = '\0';
	}
}
```

The problem that I see is that the compiler do not find the libraries and the .h files of mysql and there for give me these errors. and this is although I have pointed to the correct folder with -L.

---

### Post by TheFu on 2012-06-06
> **Elifelet said:**
> The problem that I see is that the compiler do not find the libraries and the .h files of mysql and there for give me these errors. and this is although I have pointed to the correct folder with -L.

I think you may be missing my point, but I could be wrong.

Header files are found with -I, not -L.  Headers inside .c files use either <> or "" - these mean different search paths.  #include <> looks relative to the paths in your -I (uppercase eye) and #include "" looks relative to the cwd.  At least that's what I recall, but I could be wrong and they might look relative to all paths.  Include order both in the C and make and compile steps matters.  This makes it possible for development teams to work together without having a complete copy of everything local. That was important in the old days with 10MB HDDs.

Libraries are found with -L, not -I (upper case eye).  Libraries are added on the link step.  You can fully spell out the static library path and location with the -l (lower case L)

I didn't look at the make file - but if you followed their instructions, then it should be nearly correct. Just change the -L for the mysql library location.

The location for the library that you built can be in any of those -L paths.  If you look at many Linux tools, you may have noticed they have a few commonly seen directories?
```

project/
   bin/
   lib/
   inc/
   src/
   doc/
 
```This is due to C/C++ developers organizing their code, headers, libraries, and binaries.  It would be good if you got in this same habit - placing headers in the inc/ and putting libraries into lib/ ... and the working program into bin/ .  I hope that makes sense.

It could be that you edited the makefile and broke it.  Inside, tabs are important, so are empty lines.  In the post of the makefile in this thread, could there be some extra blank lines at bad places?   You also need to check the editor that you use to ensure tabs are not automatically converted into spaces.

---

### Post by MadCow108 on 2012-06-06
to fix it move all the $(CIL_LIBS) to the end of the command line in the makefile:

e.g.
```
gcc -o ghost $(CIL_LIBS) chapter8_1.c -lc
```
to
```
gcc -o ghost chapter8_1.c -lc $(CIL_LIBS)
```
etc.

libraries need to be placed behind objects needing their symbols.
linking with libc should also not be needed, its implicit in gcc but it also does no harm.

---

### Post by Elifelet on 2012-06-07
Hi Guys!
MadCow108 - your solution worked!
TheFu - thanks for your explanation it cleared up my confusion.

Thanks for the help

---

### Post by TheFu on 2012-06-16
> **Elifelet said:**
> Hi Guys!
MadCow108 - your solution worked!
TheFu - thanks for your explanation it cleared up my confusion.
Thanks for the help

No problem.  We've all been where you are.  YOU had to get stuck with this to learn it. It happened to us all.  Also, a few weeks/months ago, you probably weren't ready to learn these concepts - so the timing was right too.

Think of all the people using IDEs that "just-handle-it" automatically so they never actually LEARN this stuff?  All they know is they can't link. It's broke.  "Someone please fix it for me."

Congratulations to you!

BTW, order only matters to ensure the modules are compiled before the link and during link, you want any functions with identical names to be resolved how you want them resolved.  It has been too long, so I don't recall whether having the same function in multiple .o and .a and .so files is an error or not.  Name collisions used to be common, so everyone started prefixing their function names with a few characters. This was before namespaces.  Anyway, it is just easier to prevent name collisions by using descriptive names.  Sorry that I've forgotten so much and can't explain it exactly for the C language used today.

Finally, marking this thread [SOLVED] would help others.

---

### Post by blakguypeez on 2012-06-22
> 
gcc -o db1 chapter5_1.c \
-I/usr/include -I~/usr/include \
-L/usr/lib/i386-linux-gnu/ -lmysqlclient -L/usr/lib -lgd -lc 

 
@TheFu:
Thanks for the detailed explaination.
First, I'm a long-time C programmer and have used gcc in the past, but, I am relatively new to programming with static libraries using gcc on linux.
Your illustration above solved my "undefined reference" problem.
Thanks   :KS

---

