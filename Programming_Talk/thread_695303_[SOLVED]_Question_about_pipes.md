---
title: "[SOLVED] Question about pipes"
date: 2008-02-12
forum: Programming Talk
---

### Post by WitchCraft on 2008-02-12
Hi!

I have a question concerning pipes:

I use this test program: myfunction.cpp
```

#include <iostream>
#include <cstdlib>

// http://gcc.gnu.org/onlinedocs/gcc-4.0.0/gcc/Function-Attributes.html
// int __attribute__ ((weak)) HelloWorld(int a) 
// int __attribute__ ((fastcall)) HelloWorld(int a) 
// int __attribute__ ((visibility ("default"))) HelloWorld(int a) 
// int __attribute__ ((visibility ("protected"))) HelloWorld(int a) 
int HelloWorld(int a)
{
	for(int i=0; i<a;++i)
	{
		printf("Hello, World!\n");
	}
	++a;
	return a*5;
}
                                                                                                       

static void CatchMeIfYouCan(int a, int b, int c, int d)
{
	a = 0 ;
	b = 1 ;
	c = 2 ;
	d = 3 ;
	printf("Blabla%d\n", a);
	printf("Blabla%d\n", b);
	printf("Blabla%d\n", c);
	printf("Blabla%d%d\n", b, a,c);
}

// "long long " is not supported by g++, it is from C99, and supported by gcc.
//float ManyTypes(int a, float b, double c, long d, long long e)
float ManyTypes(int a, float b, double c, long d, long double e)
{
	putc('a', stdout);
	printf("\nTohuwabohu%d\n", a);
	printf("Tohuwabohu%f\n", b);
	printf("Tohuwabohu%f\n", c);
	printf("Tohuwabohu%d\n", d);
	printf("Tohuwabohu%Lf\n", e);
}


int main(int argc, char** argv) 
{
	printf("\n---- Start ---------\n") ;
	int b = 2 ;
	b = HelloWorld(b) ;
	printf("\n---- Detoured part ---------\n") ;
	CatchMeIfYouCan(1,2,3,4) ;
	ManyTypes(5, 2.3, 3.14159, 1000000000, 1000000000.1458234850983) ;
	printf("\n---- End ---------\n") ;
	
	return EXIT_SUCCESS;
}


```


And then i use this code to load gdb (gnu debugger) and get the disassembly of the function "CatchMeIfYouCan", and determine the detourlength of this function and return this numeric value. This works excellently.

However, if i execute this code from a shared preloaded library, if doesn't work. Why? I cannot find the error... Is it because of pipes, or because of the fork, or because of something else?

detourlen.cpp
```

// Gets the hooklength from GDB disassembly of function

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h> // for execlp
#include <fcntl.h>


#define MAX_RETURNSIZE 100000

void startDebugger()  ;
void stopDebugger()   ;
char gdbRead()        ;
void gdbWrite(char c) ;
void ReadGDBoutputUntilPrompt(unsigned char* ptr_chrarray_GDBOutput) ; // If data is NULL copy to stdout
void writeDebugger(unsigned char* cmd, unsigned char* answer)        ;

int intFileDescriptor_WRITE_TO_GDB, intFileDescriptor_READ_FROM_GDB, intFileDescriptor_READ_ERR_FROM_GDB ;


void gdbWrite(char chrCharacter)
{
	write(intFileDescriptor_WRITE_TO_GDB, &chrCharacter, 1) ;
	fsync(intFileDescriptor_WRITE_TO_GDB)                   ;
}


char gdbRead()
{
	char chrCharacter   ;
	read(intFileDescriptor_READ_FROM_GDB, &chrCharacter, 1) ;
	return chrCharacter ;
}


void writeDebugger (unsigned char* chrptr_GDBcmd, unsigned char* chrptr_GDBanswer)
{
	unsigned char chrarrayEmptyAnswer[MAX_RETURNSIZE] ;
	if ( chrptr_GDBanswer == NULL ) 
		chrptr_GDBanswer = chrarrayEmptyAnswer    ;
	
	// fprintf (stderr, "COMMAND>%s\n", cmd) ;
	write (intFileDescriptor_WRITE_TO_GDB, (const char*) chrptr_GDBcmd, strlen( (const char*)  chrptr_GDBcmd) ) ;
	write (intFileDescriptor_WRITE_TO_GDB, "\n", 1) ;
	
	/*
	FILE *stream;
	stream = fdopen (intFileDescriptor_WRITE_TO_GDB, "w");
    fprintf (stream, "%s\n", chrptr_GDBcmd);
    fclose (stream);
	*/
	
	fsync (intFileDescriptor_WRITE_TO_GDB)          ;
	ReadGDBoutputUntilPrompt (chrptr_GDBanswer)     ;

	//fprintf (stderr, "******\n%s\n******\n", chrptr_GDBanswer) ;
}


void ReadGDBoutputUntilPrompt(unsigned char* ptr_chrarray_GDBOutput)
{
	char  chrarray_Buffer[256], chrCharacter ;
	char* chrptr_GDBprompt = "(gdb)"         ;
	int   intNumberOfBytesRead, intGDBpromptLength = strlen(chrptr_GDBprompt) ;
	
	if ( intGDBpromptLength > 255 )
		exit(-1) ;
	
	memset(chrarray_Buffer, 0, 256) ;
	while (1)
	{
		memmove(chrarray_Buffer, chrarray_Buffer + 1, intGDBpromptLength - 1 )         ;
		intNumberOfBytesRead = read(intFileDescriptor_READ_FROM_GDB, &chrCharacter, 1) ;
		if ( intNumberOfBytesRead != 1 ) 
			break ;
		chrarray_Buffer[intGDBpromptLength - 1] = chrCharacter ;
		
		if ( ptr_chrarray_GDBOutput != NULL )
		{
			*ptr_chrarray_GDBOutput = chrCharacter ;
			ptr_chrarray_GDBOutput++               ;
		}
		//else
			//printf ("%c", chrCharacter) ;

		if ( chrarray_Buffer[intGDBpromptLength - 1] == 0 ) 
			exit(-1) ;
		
		if ( !strcmp (chrptr_GDBprompt, chrarray_Buffer) ) 
			break ;
	}
	if ( ptr_chrarray_GDBOutput != NULL )
		*ptr_chrarray_GDBOutput = 0 ;
}


void stopDebugger()
{
	close(intFileDescriptor_WRITE_TO_GDB)      ;
	close(intFileDescriptor_READ_ERR_FROM_GDB) ;
	close(intFileDescriptor_READ_FROM_GDB)     ;
}


void startDebugger()
{
	unsigned char tmp_string[1024] ;
	int	intStdin_PIPE[2]       ;
	int	intStdout_PIPE[2]      ;
	int	intStderr_PIPE[2]      ;
	
	pid_t pid_ForkID  ;
	
	if ( (pipe(intStdin_PIPE) != 0)	|| (pipe(intStdout_PIPE) != 0) || (pipe(intStderr_PIPE) != 0) )
	{
		fprintf (stderr, "Could not create pipes!\n") ;
		exit (-1) ;
	}
	
	pid_ForkID = fork() ;
	
	if (pid_ForkID == -1)
	{
		fprintf(stderr, "Fork Failure\n") ;
		exit(-1) ;
	}
	
	if (pid_ForkID == 0)
	{
		// We are child
		close(0); // Close childs stdin	  
		dup2(intStdin_PIPE[0], STDIN_FILENO)   ; // Child now has STDIN that is intStdin_PIPE[0]
		close(intStdin_PIPE[0])     ; 
		close(intStdin_PIPE[1])     ; 
		
		close(1); // Close childs stdout
		dup2(intStdout_PIPE[1], STDOUT_FILENO)  ; // Child now has STDOUT that is intStdout_PIPE[1]
		//setvbuf (stdout, (char*)NULL, _IONBF, 0); // Do not buffer stdout!
		close(intStdout_PIPE[0])    ;
		close(intStdout_PIPE[1])    ;
		
		close(2); // Close childs STDERR 
		dup2(intStderr_PIPE[1], STDERR_FILENO)  ;
		close(intStderr_PIPE[0])    ;
		close(intStderr_PIPE[1])    ;
		
		//execlp("gdb","gdb", (char *)0) ;
		execlp("gdb","gdb", (char*) 0)   ;
		
		// If we get here, the execlp failed!
		fprintf (stderr, "Execution of gdb failed!\n") ;
		exit(-1) ;
	}
	else
	{
		intFileDescriptor_READ_ERR_FROM_GDB = intStderr_PIPE[0] ;    // Read from stderr
		intFileDescriptor_READ_FROM_GDB = intStdout_PIPE[0]     ;   // Read from stdout
		intFileDescriptor_WRITE_TO_GDB = intStdin_PIPE[1]       ;  // Write to stdin
		
		close( intStdin_PIPE[0]  ) ;   // No reads from stdin
		close( intStdout_PIPE[1] ) ;  // No writes to stdout
		close( intStderr_PIPE[1] ) ; // No writes to stderr
		
		ReadGDBoutputUntilPrompt(NULL);
	}
}


unsigned long FuncGetDetourLength(char* chrptr_FunctionName, char* chrptr_Path)
{
	int intDetourLength ;
	unsigned char chrarray_GDBOutput[MAX_RETURNSIZE]      ; // appx. 100 kb, not less, or you risk segmention faults
	unsigned char chrarray_CommandOpen[2048]              ;
	unsigned char chrarray_CommandDisassemble[2048]       ;	
	sprintf( (char*) chrarray_CommandOpen, "file %s", chrptr_Path) ;
	sprintf( (char*) chrarray_CommandDisassemble, "disassemble %s", chrptr_FunctionName) ;
	
	startDebugger() ;	
	writeDebugger(chrarray_CommandOpen, NULL) ;
	writeDebugger(chrarray_CommandDisassemble, chrarray_GDBOutput) ;
	stopDebugger()  ;
	
	//printf("\nData read: \n%s\n", chrarray_gdbOutput)  ;
	
	unsigned char* chrptr_GDBOutput = chrarray_GDBOutput ;
	char* chrptr_NewLine = NULL                          ;
	char* chrptr_pos1 = NULL                             ;
	char* chrptr_pos2 = NULL                             ;
	int intFuse = 0                                      ;
	while (1)
	{
		++intFuse ;
		chrptr_NewLine = strstr( (const char*) chrptr_GDBOutput, "\n")  ;
		chrptr_pos1 = strstr( (const char*) chrptr_GDBOutput, "+")      ;
		
		if ( (chrptr_pos1 > chrptr_NewLine) && ( chrptr_NewLine != 0) )
		{
			chrptr_GDBOutput = (unsigned char*) ++chrptr_NewLine        ;
			continue ;
		}
		
		chrptr_pos2 = strstr((char*) chrptr_GDBOutput, ">")             ;
		char chrptr_Number[chrptr_pos2 - chrptr_pos1]                   ;
		memcpy(chrptr_Number, ++chrptr_pos1, chrptr_pos2-chrptr_pos1-1) ;
		memset(chrptr_Number + (chrptr_pos2 - chrptr_pos1), 0 , 1)      ;	
		intDetourLength = atoi(chrptr_Number)                           ;
		
		if (intDetourLength < 5 && intFuse < 101)
		{
			chrptr_GDBOutput = (unsigned char*) ++chrptr_NewLine ;
			continue ;
		}
		else 
			break ;			
	}
	return (unsigned long) intDetourLength ;
}


int main()
{
	char* symbol = "CatchMeIfYouCan" ;
	char* strPath = "~/Desktop/myfunction" ; 
	printf("Detour length of %s = %d.\n",symbol, FuncGetDetourLength(symbol, strPath)) ;
	return EXIT_SUCCESS ;	
}


```


detourlen.cpp (as shared library)
```

// Gets the hooklength from GDB disassembly of function

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h> // for execlp
#include <fcntl.h>


#define MAX_RETURNSIZE 100000

void startDebugger()  ;
void stopDebugger()   ;
char gdbRead()        ;
void gdbWrite(char c) ;
void ReadGDBoutputUntilPrompt(unsigned char* ptr_chrarray_GDBOutput) ; // If data is NULL copy to stdout
void writeDebugger(unsigned char* cmd, unsigned char* answer)        ;

int intFileDescriptor_WRITE_TO_GDB, intFileDescriptor_READ_FROM_GDB, intFileDescriptor_READ_ERR_FROM_GDB ;


void gdbWrite(char chrCharacter)
{
	write(intFileDescriptor_WRITE_TO_GDB, &chrCharacter, 1) ;
	fsync(intFileDescriptor_WRITE_TO_GDB)                   ;
}


char gdbRead()
{
	char chrCharacter   ;
	read(intFileDescriptor_READ_FROM_GDB, &chrCharacter, 1) ;
	return chrCharacter ;
}


void writeDebugger (unsigned char* chrptr_GDBcmd, unsigned char* chrptr_GDBanswer)
{
	unsigned char chrarrayEmptyAnswer[MAX_RETURNSIZE] ;
	if ( chrptr_GDBanswer == NULL ) 
		chrptr_GDBanswer = chrarrayEmptyAnswer    ;
	
	// fprintf (stderr, "COMMAND>%s\n", cmd) ;
	write (intFileDescriptor_WRITE_TO_GDB, (const char*) chrptr_GDBcmd, strlen( (const char*)  chrptr_GDBcmd) ) ;
	write (intFileDescriptor_WRITE_TO_GDB, "\n", 1) ;
	
	/*
	FILE *stream;
	stream = fdopen (intFileDescriptor_WRITE_TO_GDB, "w");
    fprintf (stream, "%s\n", chrptr_GDBcmd);
    fclose (stream);
	*/
	
	fsync (intFileDescriptor_WRITE_TO_GDB)          ;
	ReadGDBoutputUntilPrompt (chrptr_GDBanswer)     ;

	//fprintf (stderr, "******\n%s\n******\n", chrptr_GDBanswer) ;
}


void ReadGDBoutputUntilPrompt(unsigned char* ptr_chrarray_GDBOutput)
{
	char  chrarray_Buffer[256], chrCharacter ;
	char* chrptr_GDBprompt = "(gdb)"         ;
	int   intNumberOfBytesRead, intGDBpromptLength = strlen(chrptr_GDBprompt) ;
	
	if ( intGDBpromptLength > 255 )
		exit(-1) ;
	
	memset(chrarray_Buffer, 0, 256) ;
	while (1)
	{
		memmove(chrarray_Buffer, chrarray_Buffer + 1, intGDBpromptLength - 1 )         ;
		intNumberOfBytesRead = read(intFileDescriptor_READ_FROM_GDB, &chrCharacter, 1) ;
		if ( intNumberOfBytesRead != 1 ) 
			break ;
		chrarray_Buffer[intGDBpromptLength - 1] = chrCharacter ;
		
		if ( ptr_chrarray_GDBOutput != NULL )
		{
			*ptr_chrarray_GDBOutput = chrCharacter ;
			ptr_chrarray_GDBOutput++               ;
		}
		//else
			//printf ("%c", chrCharacter) ;

		if ( chrarray_Buffer[intGDBpromptLength - 1] == 0 ) 
			exit(-1) ;
		
		if ( !strcmp (chrptr_GDBprompt, chrarray_Buffer) ) 
			break ;
	}
	if ( ptr_chrarray_GDBOutput != NULL )
		*ptr_chrarray_GDBOutput = 0 ;
}


void stopDebugger()
{
	close(intFileDescriptor_WRITE_TO_GDB)      ;
	close(intFileDescriptor_READ_ERR_FROM_GDB) ;
	close(intFileDescriptor_READ_FROM_GDB)     ;
}


void startDebugger()
{
	unsigned char tmp_string[1024] ;
	int	intStdin_PIPE[2]       ;
	int	intStdout_PIPE[2]      ;
	int	intStderr_PIPE[2]      ;
	
	pid_t pid_ForkID  ;
	
	if ( (pipe(intStdin_PIPE) != 0)	|| (pipe(intStdout_PIPE) != 0) || (pipe(intStderr_PIPE) != 0) )
	{
		fprintf (stderr, "Could not create pipes!\n") ;
		exit (-1) ;
	}
	
	pid_ForkID = fork() ;
	
	if (pid_ForkID == -1)
	{
		fprintf(stderr, "Fork Failure\n") ;
		exit(-1) ;
	}
	
	if (pid_ForkID == 0)
	{
		// We are child
		close(0); // Close childs stdin	  
		dup2(intStdin_PIPE[0], STDIN_FILENO)   ; // Child now has STDIN that is intStdin_PIPE[0]
		close(intStdin_PIPE[0])     ; 
		close(intStdin_PIPE[1])     ; 
		
		close(1); // Close childs stdout
		dup2(intStdout_PIPE[1], STDOUT_FILENO)  ; // Child now has STDOUT that is intStdout_PIPE[1]
		//setvbuf (stdout, (char*)NULL, _IONBF, 0); // Do not buffer stdout!
		close(intStdout_PIPE[0])    ;
		close(intStdout_PIPE[1])    ;
		
		close(2); // Close childs STDERR 
		dup2(intStderr_PIPE[1], STDERR_FILENO)  ;
		close(intStderr_PIPE[0])    ;
		close(intStderr_PIPE[1])    ;
		
		//execlp("gdb","gdb", (char *)0) ;
		execlp("gdb","gdb", (char*) 0)   ;
		
		// If we get here, the execlp failed!
		fprintf (stderr, "Execution of gdb failed!\n") ;
		exit(-1) ;
	}
	else
	{
		intFileDescriptor_READ_ERR_FROM_GDB = intStderr_PIPE[0] ;    // Read from stderr
		intFileDescriptor_READ_FROM_GDB = intStdout_PIPE[0]     ;   // Read from stdout
		intFileDescriptor_WRITE_TO_GDB = intStdin_PIPE[1]       ;  // Write to stdin
		
		close( intStdin_PIPE[0]  ) ;   // No reads from stdin
		close( intStdout_PIPE[1] ) ;  // No writes to stdout
		close( intStderr_PIPE[1] ) ; // No writes to stderr
		
		ReadGDBoutputUntilPrompt(NULL);
	}
}


unsigned long FuncGetDetourLength(char* chrptr_FunctionName, char* chrptr_Path)
{
	int intDetourLength ;
	unsigned char chrarray_GDBOutput[MAX_RETURNSIZE]      ; // appx. 100 kb, not less, or you risk segmention faults
	unsigned char chrarray_CommandOpen[2048]              ;
	unsigned char chrarray_CommandDisassemble[2048]       ;	
	sprintf( (char*) chrarray_CommandOpen, "file %s", chrptr_Path) ;
	sprintf( (char*) chrarray_CommandDisassemble, "disassemble %s", chrptr_FunctionName) ;
	
	startDebugger() ;	
	writeDebugger(chrarray_CommandOpen, NULL) ;
	writeDebugger(chrarray_CommandDisassemble, chrarray_GDBOutput) ;
	stopDebugger()  ;
	
	//printf("\nData read: \n%s\n", chrarray_gdbOutput)  ;
	
	unsigned char* chrptr_GDBOutput = chrarray_GDBOutput ;
	char* chrptr_NewLine = NULL                          ;
	char* chrptr_pos1 = NULL                             ;
	char* chrptr_pos2 = NULL                             ;
	int intFuse = 0                                      ;
	while (1)
	{
		++intFuse ;
		chrptr_NewLine = strstr( (const char*) chrptr_GDBOutput, "\n")  ;
		chrptr_pos1 = strstr( (const char*) chrptr_GDBOutput, "+")      ;
		
		if ( (chrptr_pos1 > chrptr_NewLine) && ( chrptr_NewLine != 0) )
		{
			chrptr_GDBOutput = (unsigned char*) ++chrptr_NewLine        ;
			continue ;
		}
		
		chrptr_pos2 = strstr((char*) chrptr_GDBOutput, ">")             ;
		char chrptr_Number[chrptr_pos2 - chrptr_pos1]                   ;
		memcpy(chrptr_Number, ++chrptr_pos1, chrptr_pos2-chrptr_pos1-1) ;
		memset(chrptr_Number + (chrptr_pos2 - chrptr_pos1), 0 , 1)      ;	
		intDetourLength = atoi(chrptr_Number)                           ;
		
		if (intDetourLength < 5 && intFuse < 101)
		{
			chrptr_GDBOutput = (unsigned char*) ++chrptr_NewLine ;
			continue ;
		}
		else 
			break ;			
	}
	return (unsigned long) intDetourLength ;
}

void __attribute__ ((constructor)) onLoad (void) 
{
	char* symbol = "CatchMeIfYouCan" ;
	char* strPath = "~/Desktop/myfunction" ; 
	printf("Detour length of %s = %d.\n",symbol, FuncGetDetourLength(symbol, strPath)) ;
	return EXIT_SUCCESS ;	
}

```

PS: Shared preloaded library:

g++ -fPIC -rdynamic -c detourlen.cpp
g++ -shared -o libdetourlen.so detourlen.o -lc -ldl -lelf


start with:
LD_LIBRARY_PATH=. LD_PRELOAD=libdetourlen.so ./myfunction

---

### Post by WitchCraft on 2008-02-12
bump

---

### Post by WitchCraft on 2008-02-12
bump

---

### Post by WitchCraft on 2008-02-12
bump.

---

### Post by stroyan on 2008-02-13
I haven't look at your code details.
I wonder if it is so easy to get any c++ code to run from an LD_PRELOAD.
If the program that you are preloading into is not using the same g++
library files then your library may be missing the runtime libraries it expects.

---

### Post by WitchCraft on 2008-02-13
Yes it is easy. 
It also doesn't work if i include write(...) in myfunction.cpp, so the runtime library should be included...

But it is somehow as if the file descriptors get closed... 

if i include 
intFileDescriptor_WRITE_TO_GDB = fcntl(STDIN_FILENO,  F_DUPFD, 0);
	
prior to
write (intFileDescriptor_WRITE_TO_GDB, (const char*) chrptr_GDBcmd, strlen( (const char*)  chrptr_GDBcmd) ) ;

the i get somewhat further, but it ends in a segmentation fault...

---

### Post by WitchCraft on 2008-02-13
bump.

---

### Post by WitchCraft on 2008-02-13
bump.

---

### Post by WitchCraft on 2008-02-13
bump.

---

### Post by WitchCraft on 2008-02-13
bump.

---

### Post by WitchCraft on 2008-02-13
bump

---

### Post by LaRoza on 2008-02-13
[color="red"]Acting as moderator:[/color]

Do not bump so much, every 24 hours at the most is enough.

Seee [The Bump Thread]("http://ubuntuforums.org/showthread.php?t=520091")

---

### Post by stroyan on 2008-02-13
The only problem I see is that the LD_PRELOAD=libdetourlen.so setting is left in the environment when you start gdb.  The library then tries to start another gdb from that gdb.  It recurses and repeats.  I corrected that by adding putenv("LD_PRELOAD=");
to the onLoad function.

---

### Post by WitchCraft on 2008-02-13
> **stroyan said:**
> 
The only problem I see is that the LD_PRELOAD=libdetourlen.so setting is left in the environment when you start gdb.  The library then tries to start another gdb from that gdb.  It recurses and repeats.  I corrected that by adding putenv("LD_PRELOAD=");
to the onLoad function.


Oh damn, infinite recursion - yea that's it. 
Problem solved.
Thank you! Thank you VERY VERY VERY much!

---

