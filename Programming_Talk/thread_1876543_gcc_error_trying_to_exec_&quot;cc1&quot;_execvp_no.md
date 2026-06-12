---
title: "gcc: error trying to exec &quot;cc1&quot;: execvp: no such file or directory"
date: 2011-11-06
forum: Programming Talk
---

### Post by shawnat88 on 2011-11-06
I've been working on a shell for my Operating Systems course. My shell can't compile or run any programs using the gcc command. I get the following error when I try: 

gcc: error trying to exec "cc1": execvp: no such file or directory

It was never stated that I need to be able to compile or run programs, but I'd like to implement it anyway. I appreciate any help or suggestions.

```

#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<string.h>
#include<fcntl.h>
#include<errno.h>

 /****************************************************************************
** Shawn Taylor
** CSC425 Project 1
** Felt Grace Shell version 1.0
** 11/4/2011
******************************************************************************/
extern int errno;

void parse(char *string, char **args, int signal)
{
	int code = signal;
	char delimiter;

	if(code == 0)
		delimiter = ' ';
	else
		delimiter = ':';

	char *tok = strtok(string, &delimiter);

	int i = 0;
	while(tok != NULL)
	{
		args[i] = malloc(sizeof(char) * strlen(tok));
		strcpy(args[i], tok);

		if(code == 1)
			strncat(args[i], "/", 1);

		tok = strtok(NULL, &delimiter);
		i++;
	}
 	//terminate my_argv and my_envp
	args[i] = (char *)0;	
}

int attach_path(char *cmd, char **args)
{
	char tempPath[128];
	int file;

	int i;
	for(i = 0; args[i] != NULL; i++) //search path for args
	{	
		strcpy(tempPath, args[i]);
		strcat(tempPath, cmd);
		
		if((file = open(tempPath, O_RDONLY)) > 0)
		{
			if(faccessat(0, tempPath, F_OK, 0) == 0)
			{
				strcpy(cmd, tempPath);
				close(file);
				break;
			}
			else
			{
				close(file);
				printf("Access Denied\n");
			}
		}
	}

	return 0;
}

void execute_command(char *path_arg, char **opts_args, char**env_args)
{
	int i;
	int pId = fork();
	
	if(pId == 0)
	{	
		i = execve(path_arg, opts_args,env_args);
		if(i != 0)
		{				
			printf("error: %s\n", strerror(errno));
			printf("%s: %s\n", path_arg,"Command Not Found");
			exit(1);
		}
	}
	else
	{
		wait(NULL);
	}
}

int main(int argc, char **argv, char **envp)
{
	char dir[50];
	char command[128];
	char *my_argv[100];
	char *my_envp[100];

	//Get environment and parse it
	char *environment = getenv("PATH");
	parse(environment, my_envp, 1);

	//Get user environment
	char* userEnvironment = getenv("USER");
	strncat(userEnvironment,"@~",2);
	
	//Clear screen and start shell
	int index;
	for(index = 0; index < 100; index++)
	{
		putchar('\n');
	}

	printf("***************************\n");
	printf("%s\n","***** Felt Grace v1.0 *****");
	printf("***************************\n");

	while(1)
	{	
		//show the prompt with current directory
		printf("%s%s$ ", userEnvironment, getcwd(NULL, 0));
		
		//Get command input and create termporary copy
		fgets(command,127,stdin);
		char* commandCopy = command;
		
		if(strncmp(command, "exit", 4) == 0)
		{	
			printf("***************************\n");
			return 0;
		}

		//Parse command
		parse(commandCopy, my_argv, 0);

		//attach path to command
		attach_path(command, my_envp);
			
		if(strncmp(my_argv[0], "cd", 2) == 0)
		{
			int dirChange;
			dirChange = chdir(my_argv[1]);
				
			if(dirChange != 0)
				printf("%s\n", "Error Changing Directory");
		}
		else
		if(strncmp(my_argv[0], "execute", 7) == 0)
		{
			FILE* file;
			file = fopen(my_argv[1], "r");
			char batch_command[128];
			char batchCommandCopy[128];
				
			//Loop through file and get commands
			while(fgets(batch_command, 128, file) != NULL)
			{	
				int i;
				char c;
				for(i = 0; i < strlen(batch_command); i++)
				{
					c = batch_command[i];
					if(c != '\n')
						batchCommandCopy[i] = batch_command[i];
					else
						batchCommandCopy[i] = (char)0;
				}
					
				//Attach Path to batch command			
				attach_path(batchCommandCopy, my_envp);
				
				printf("\n");

				//Execute batch command
				execute_command(batchCommandCopy, argv, my_envp);	

				printf("\n");
			}
			
				fclose(file);
		}
		else
		{
			//Execute single command
			execute_command(command, my_argv, my_envp);
		}		
		
		int i; 	
		for(i = 0; my_argv[i] != NULL; i++)
		{
			free(my_argv[i]);
		}
	}

	int i;
	for(i = 0; my_envp[i] != NULL; i++)
	{
		free(my_envp[i]);
	}
	
	return 0;
}

```

---

### Post by learnbash on 2011-11-06
you need to install.i am assuming you are using fedora/rhel/centos

```


yum install gcc-c++


```

---

### Post by shawnat88 on 2011-11-06
This program is in C. gcc works works in bash, just not in my shell. I'm using ubuntu. Sorry for not mentioning that before.

---

### Post by Bachstelze on 2011-11-06
First: turn on all compiler warnings (-pedantic -Wall -Wextra) and run your program in valgrind. You have a lot of memory leaks, buffer overflows and other problems. And it segfaults when you just press Enter without typing anything.

> **learnbash said:**
> you need to install.i am assuming you are using fedora/rhel/centos

```


yum install gcc-c++


```

Awesome: someone posts on Ubuntu Forums, assume they're running Fedora. :D

---

### Post by learnbash on 2011-11-06
i am sorry sir that was just assumption.

---

### Post by Bachstelze on 2011-11-06
Also why do you clear the screen when your shell starts? It's annoying and no real shell does that.

(Yes, yes, I am looking at the problem you described too, but it's more complicated. :p)

---

### Post by Bachstelze on 2011-11-06
Basically, cc1 is not in your PATH. But it's not in your PATH when you run gcc from a "normal" shell either, so I'm not sure what it is that you do differently and prevents gcc from finding cc1 when it tries to run it...

---

### Post by shawnat88 on 2011-11-06
I'm trying your suggestions now. Just finished installing Valgrind. Segmentation fault after hitting enter with nothing entered...ugh. I'll correct that. 

As for the clear screen thing, I just thought it would be nice to clear the screen and start fresh; though I would rather have the prompt appear on the top of the console. That's low priority right now though.

---

### Post by Bachstelze on 2011-11-06
See posts above that were moved~~

---

### Post by shawnat88 on 2011-11-06
I fixed the segmentation faults that I found. Still getting that 'cc1' error though. Not sure how to fix that yet. Valgrind says I have no leaks but 1 file open. :confused:

Updated Code:
```

#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<string.h>
#include<fcntl.h>
#include<errno.h>
#include<sys/wait.h>
 /****************************************************************************
** Shawn Taylor
** CSC425 Project 1
** Felt Grace Shell version 1.0
** 11/4/2011
******************************************************************************/
extern int errno;

void parse(char *string, char **args, int signal)
{
	int code = signal;
	char delimiter;
	char *tok;
	int i;
	
	if(code == 0)
		delimiter = ' ';
	else
		delimiter = ':';
	
	i = 0;
	tok = strtok(string, &delimiter);

	while(tok != NULL)
	{
		args[i] = malloc(sizeof(char) * strlen(tok));
		strcpy(args[i], tok);

		if(code == 1)
			strncat(args[i], "/", 1);

		tok = strtok(NULL, &delimiter);
		i++;
	}

 	/*terminate my_argv and my_envp*/
	args[i] = (char *)0;	
}

int attach_path(char *cmd, char **args)
{
	char tempPath[128];
	int file;
	int i;

	for(i = 0; args[i] != NULL; i++) /*search path for args*/
	{	
		strcpy(tempPath, args[i]);
		strcat(tempPath, cmd);
		
		if((file = open(tempPath, O_RDONLY)) > 0)
		{
			if(faccessat(0, tempPath, F_OK, 0) == 0)
			{
				strcpy(cmd, tempPath);
				close(file);
				break;
			}
			else
			{
				close(file);
				printf("Access Denied\n");
			}
		}
	}

	return 0;
}

void execute_command(char *path_arg, char **opts_args, char**env_args)
{
	int i;
	int pId = fork();
	
	if(pId == 0)
	{	
		i = execve(path_arg, opts_args,env_args);
		if(i != 0)
		{				
			printf("error: %s\n", strerror(errno));
			printf("%s: %s\n", path_arg,"Command Not Found");
			exit(1);
		}
	}
	else
	{
		wait(NULL);
	}
}

int main(int argc, char **argv, char **envp)
{
	char command[128];
	char *my_argv[100];
	char *my_envp[100];
	char *environment;
	char* userEnvironment;
	int index;

	/*Get environment and parse it*/
	environment = getenv("PATH");
	parse(environment, my_envp, 1);

	/*Get user environment*/
	userEnvironment = getenv("USER");
	strncat(userEnvironment,"@~",2);
	
	/*Clear screen and start shell*/
	for(index = 0; index < 100; index++)
	{
		putchar('\n');
	}

	printf("***************************\n");
	printf("%s\n","***** Felt Grace v1.0 *****");
	printf("***************************\n");
	
	start: 
	while(1)
	{	
		char* commandCopy;
		
		do
		{
			/*show the prompt with current directory*/
			printf("%s%s$ ", userEnvironment, getcwd(NULL, 0));

			/*Get command input and create termporary copy*/	
			fgets(command,127,stdin);
			commandCopy = command;
		}

		/*Checks for empty string*/
		while((strncmp(command, "\n", 1)) == 0);
		
		if((strncmp(command, "exit", 4)) == 0)
		{	
			printf("***************************\n");
			return 0;
		}

		/*Parse command*/
		parse(commandCopy, my_argv, 0);

		/*attach path to command*/
		attach_path(command, my_envp);
			
		if(strncmp(my_argv[0], "cd", 2) == 0)
		{
			int dirChange;
			dirChange = chdir(my_argv[1]);
				
			if(dirChange != 0)
				printf("%s\n", "Error Changing Directory");
		}
		else
		if(strncmp(my_argv[0], "execute", 7) == 0)
		{
			char batch_command[128];
			char batchCommandCopy[128];
			FILE *file;
			
			/*Test for valid file input after typing "execute"*/
			if(my_argv[1] == NULL)
				goto start;
			if(strstr(my_argv[1], ".bat") == NULL)
				goto start;

			file = fopen(my_argv[1], "r");
				
			/*Loop through file and get commands*/
			while(fgets(batch_command, 128, file) != NULL)
			{	
				char c;
				int commandLength;
				int index;

				commandLength = strlen(batch_command);

				for(index = 0; index < commandLength; index++)
				{
					c = batch_command[index];

					if(c != '\n')
						batchCommandCopy[index] = batch_command[index];
					else
						batchCommandCopy[index] = (char)0;
				}
					
				/*Attach Path to batch command*/		
				attach_path(batchCommandCopy, my_envp);
				
				printf("\n");

				/*Execute batch command*/
				execute_command(batchCommandCopy, argv, my_envp);	

				printf("\n");
				
				fclose(file);
			}
			
		}
		else
		{
			/*Execute single command*/
			execute_command(command, my_argv, my_envp);
		}	
	
		for(index = 0; my_argv[index] != NULL; index++)
		{
			free(my_argv[index]);
		}
	}

	for(index = 0; my_envp[index] != NULL; index++)
	{
		free(my_envp[index]);
	}
	
	return 0;
}

```

Valgrind Output: 
```

==31497== Memcheck, a memory error detector
==31497== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==31497== Using Valgrind-3.6.1-Debian and LibVEX; rerun with -h for copyright info
==31497== Command: test
==31497== 
--31497-- Valgrind options:
--31497--    --suppressions=/usr/lib/valgrind/debian-libc6-dbg.supp
--31497--    --tool=memcheck
--31497--    --leak-check=yes
--31497--    --show-reachable=yes
--31497--    --num-callers=20
--31497--    --track-fds=yes
--31497--    -v
--31497-- Contents of /proc/version:
--31497--   Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011
--31497-- Arch and hwcaps: X86, x86-sse1-sse2
--31497-- Page sizes: currently 4096, max supported 4096
--31497-- Valgrind library directory: /usr/lib/valgrind
--31497-- Reading syms from /lib/i386-linux-gnu/ld-2.13.so (0x4000000)
--31497--   Considering /lib/i386-linux-gnu/ld-2.13.so ..
--31497--   .. CRC mismatch (computed 1a2ed160 wanted fece6135)
--31497--   Considering /usr/lib/debug/lib/i386-linux-gnu/ld-2.13.so ..
--31497--   .. CRC is valid
--31497-- Reading syms from /usr/bin/test (0x8048000)
--31497--   Considering /usr/bin/test ..
--31497--   .. CRC mismatch (computed ee5926fa wanted a3840d1e)
--31497--    object doesn't have a symbol table
--31497-- Reading syms from /usr/lib/valgrind/memcheck-x86-linux (0x38000000)
--31497--    object doesn't have a dynamic symbol table
--31497-- Reading suppressions file: /usr/lib/valgrind/debian-libc6-dbg.supp
--31497-- Reading suppressions file: /usr/lib/valgrind/default.supp
--31497-- REDIR: 0x4016b80 (index) redirected to 0x3803e847 (vgPlain_x86_linux_REDIR_FOR_index)
--31497-- Reading syms from /usr/lib/valgrind/vgpreload_core-x86-linux.so (0x4022000)
--31497-- Reading syms from /usr/lib/valgrind/vgpreload_memcheck-x86-linux.so (0x4025000)
==31497== WARNING: new redirection conflicts with existing -- ignoring it
--31497--     new: 0x04016b80 (index               ) R-> 0x04028c7e index
--31497-- REDIR: 0x4016d40 (strlen) redirected to 0x4029045 (strlen)
--31497-- Reading syms from /lib/i386-linux-gnu/libc-2.13.so (0x4040000)
--31497--   Considering /lib/i386-linux-gnu/libc-2.13.so ..
--31497--   .. CRC mismatch (computed 365f96ac wanted ff3422fe)
--31497--   Considering /usr/lib/debug/lib/i386-linux-gnu/libc-2.13.so ..
--31497--   .. CRC is valid
--31497-- REDIR: 0x40b6630 (rindex) redirected to 0x4028adc (rindex)
--31497-- REDIR: 0x40b5d00 (__GI_strcmp) redirected to 0x4029a0a (__GI_strcmp)
--31497-- REDIR: 0x40b6310 (__GI_strlen) redirected to 0x402902a (__GI_strlen)
--31497-- REDIR: 0x40b5b40 (index) redirected to 0x4028bc7 (index)
--31497-- REDIR: 0x40bc8b0 (__GI_strncmp) redirected to 0x40294b2 (__GI_strncmp)
--31497-- REDIR: 0x40b8ba0 (strchrnul) redirected to 0x402ab9f (strchrnul)
--31497-- REDIR: 0x40b2430 (malloc) redirected to 0x40287f1 (malloc)
--31497-- REDIR: 0x40b28e0 (free) redirected to 0x4027b7d (free)
==31497== 
[COLOR="Red"]==31497== FILE DESCRIPTORS: 1 open at exit.[/COLOR]
==31497== Open file descriptor 0: /dev/pts/0
==31497==    <inherited from parent>
==31497== 
==31497== 
[COLOR="red"]==31497== HEAP SUMMARY:
==31497==     in use at exit: 0 bytes in 0 blocks
==31497==   total heap usage: 32 allocs, 32 frees, 2,017 bytes[/COLOR] allocated
==31497== 
==31497== All heap blocks were freed -- no leaks are possible
==31497== 
==31497== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 6)
--31497-- 
--31497-- used_suppression:     11 U1004-ARM-_dl_relocate_object
==31497== 
==31497== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 6)


```

---

### Post by Arndt on 2011-11-06
> **shawnat88 said:**
> I fixed the segmentation faults that I found. Still getting that 'cc1' error though. Not sure how to fix that yet. Valgrind says I have no leaks but 1 file open. :confused:


I wouldn't worry about fd 0 being open (though why it doesn't say the same thing for fd 1 I don't know).

I'm not sure what you put in argv[0] for the program being called. Some don't care, but perhaps gcc tries to use it and gets confused. What does your shell put there?

---

### Post by shawnat88 on 2011-11-06
To give an example, typing "execute test1.bat" at my shells prompt would mean that my_argv[0] is "execute" and my_argv[1] is "test.bat". argv[0] is "./felt" if I do "gcc -o felt felt.c" when compiling.

---

### Post by Arndt on 2011-11-07
> **shawnat88 said:**
> To give an example, typing "execute test1.bat" at my shells prompt would mean that my_argv[0] is "execute" and my_argv[1] is "test.bat". argv[0] is "./felt" if I do "gcc -o felt felt.c" when compiling.

Yes, that could very well confuse gcc. Try letting argv[0] be "gcc" instead.

---

### Post by shawnat88 on 2011-11-07
I'm only using "my_argv" now instead of "argv". my_argv[0] is "gcc" my_argv[1] is "-o". Getting the same error.

```

#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<string.h>
#include<fcntl.h>
#include<errno.h>
#include<sys/wait.h>
 /*********************************************************************************
** Shawn Taylor
** CSC425 Project 1
** Felt Grace Shell version 1.0
** 11/7/2011
**
**Instructions: 
**Compile and run felt.c to start the shell. Try different commands; not everything
**is supported. Type "execute" followed by the name and extension of a bat file for 
**batch mode.
**
**	What works(tested):	What doesn't work: 
**
**	- rm			- multiple string commands in batch mode
**	- p			- gcc - returns an error
**	- ls
**	- cat
**	- kill
	- cd
**
***********************************************************************************/
extern int errno;

void parse(char *string, char **args, int signal)
{
	int code = signal;
	char delimiter;
	char *tok;
	int i;
	
	if(code == 0)
		delimiter = ' ';
	else
		delimiter = ':';
	
	i = 0;
	tok = strtok(string, &delimiter);

	while(tok != NULL)
	{
		args[i] = malloc(sizeof(char) * strlen(tok));
		strcpy(args[i], tok);

		if(code == 1)
			strncat(args[i], "/", 1);

		tok = strtok(NULL, &delimiter);
		i++;
	}

 	/*terminate my_argv and my_envp*/
	args[i] = (char *)0;	
}

int attach_path(char *cmd, char **args)
{
	char tempPath[128];
	int file;
	int i;

	for(i = 0; args[i] != NULL; i++) /*search path for args*/
	{	
		strcpy(tempPath, args[i]);
		strcat(tempPath, cmd);
		
		if((file = open(tempPath, O_RDONLY)) > 0)
		{
			if(faccessat(0, tempPath, F_OK, 0) == 0)
			{
				strcpy(cmd, tempPath);
				close(file);
				break;
			}
			else
			{
				close(file);
				printf("Access Denied\n");
			}
		}
	}

	return 0;
}

void execute_command(char *path_arg, char **opts_args, char**env_args)
{
	int i;
	int pId = fork();
	
	if(pId == 0)
	{	
		i = execve(path_arg, opts_args,env_args);
		if(i != 0)
		{				
			printf("error: %s\n", strerror(errno));
			printf("%s: %s\n", path_arg,"Command Not Found");
			exit(1);
		}
	}
	else
	{
		wait(NULL);
	}
}

int main()
{
	char command[128];
	char *my_argv[100];
	char *my_envp[100];
	char *environment;
	char* userEnvironment;
	int index;

	/*Get environment and parse it*/
	environment = getenv("PATH");
	parse(environment, my_envp, 1);

	/*Get user environment*/
	userEnvironment = getenv("USER");
	strncat(userEnvironment,"@~",2);
	
	/*Clear screen and start shell
	for(index = 0; index < 100; index++)
	{
		putchar('\n');
	}*/

	printf("***************************\n");
	printf("%s\n","***** Felt Grace v1.0 *****");
	printf("***************************\n");
	
	start: 
	while(1)
	{	
		char* commandCopy;
		
		do
		{
			/*show the prompt with current directory*/
			printf("%s%s$ ", userEnvironment, getcwd(NULL, 0));

			/*Get command input and create termporary copy*/	
			fgets(command,127,stdin);
			commandCopy = command;
		}

		/*Checks for empty string*/
		while((strncmp(command, "\n", 1)) == 0);
		
		if((strncmp(command, "exit", 4)) == 0)
		{	
			printf("***************************\n");
			return 0;
		}

		/*Parse command*/
		parse(commandCopy, my_argv, 0);

		/*attach path to command*/
		attach_path(command, my_envp);
			
		if(strncmp(my_argv[0], "cd", 2) == 0)
		{
			int dirChange;
			dirChange = chdir(my_argv[1]);

			if(dirChange != 0)
				printf("%s\n", "Error Changing Directory");
		}
		else
		if(strncmp(my_argv[0], "execute", 7) == 0)
		{
			char batch_command[128];
			char batchCommandCopy[128];
			FILE *file;
			
			if(my_argv[1] == NULL)
			{
				/*No file Specified*/
				printf("No file specified!\n");
				goto start;
			}

			if(strstr(my_argv[1], ".bat") == NULL)
			{
				/*wrong file extension*/
				printf("Incorrect file specified! \".bat\" extension only.\n");
;				goto start;
			}

			if((file = fopen(my_argv[1], "r")) == NULL)
			{ 
				/*file doesn't exists*/
				printf("File does not exist!\n");
				goto start;
			}	
			
			while(fgets(batch_command, 128, file) != NULL)
			{	
				/*Loop through file and get commands*/
				
				char c;
				int commandLength;
				int index;

				commandLength = strlen(batch_command);

				for(index = 0; index < commandLength; index++)
				{
					//Removing '\n' from batch command if it exists 
		
					c = batch_command[index];

					if(c != '\n')
						batchCommandCopy[index] = batch_command[index];
					else
						batchCommandCopy[index] = (char)0;
				}
				
				/*Parse batch_command*/
				parse(batch_command, my_argv, 0);
					
				/*Attach Path to batch command*/		
				attach_path(batchCommandCopy, my_envp);
				
				printf("\n");

				/*Execute batch command*/
				execute_command(batchCommandCopy, my_argv, my_envp);	
			}

			fclose(file);
		}
		else
		{	
			printf("%s",my_argv[0]);
			/*Execute single command*/
			execute_command(command, my_argv, my_envp);
		}	
	
		for(index = 0; my_argv[index] != NULL; index++)
		{
			free(my_argv[index]);
		}
	}

	for(index = 0; my_envp[index] != NULL; index++)
	{
		free(my_envp[index]);
	}
	
	return 0;
}

```

---

### Post by Arndt on 2011-11-07
> **shawnat88 said:**
> I'm only using "my_argv" now instead of "argv". my_argv[0] is "gcc" my_argv[1] is "-o". Getting the same error.

[/code]

You are not letting the subprocess inherit PATH. gcc calls a number of other programs, and it needs PATH. Easiest is to just pass on your own environment. Is there any reason to change it?

I suggest inserting plenty of debug output statements, so you know that the values of your variables are what they should be.

Try a simple command like "date".

---

### Post by shawnat88 on 2011-11-07
date works.

---

### Post by Arndt on 2011-11-07
> **shawnat88 said:**
> date works.

Good, but strange. It doesn't for me.

---

### Post by shawnat88 on 2011-11-07
somehow I valgrinded the wrong program or something. Doing it correctly I get the following output. There are many problems that I have to fix.

Before using program:
```

==16308== Memcheck, a memory error detector
==16308== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==16308== Using Valgrind-3.6.1-Debian and LibVEX; rerun with -h for copyright info
==16308== Command: ./felt
==16308== 
==16308== Conditional jump or move depends on uninitialised value(s)
==16308==    at 0x40B6CF3: strtok (strtok.S:160)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308== 
==16308== Use of uninitialised value of size 4
==16308==    at 0x40B6CF5: strtok (strtok.S:161)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308== 
==16308== Conditional jump or move depends on uninitialised value(s)
==16308==    at 0x40B6CFE: strtok (strtok.S:165)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308== 
==16308== Invalid write of size 1
==16308==    at 0x40290C0: strcpy (mc_replace_strmem.c:311)
==16308==    by 0x8048961: parse (felt.c:49)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308==  Address 0x41be040 is 0 bytes after a block of size 24 alloc'd
==16308==    at 0x4028876: malloc (vg_replace_malloc.c:236)
==16308==    by 0x8048945: parse (felt.c:48)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308== 
==16308== Invalid read of size 1
==16308==    at 0x804898D: parse (felt.c:52)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308==  Address 0x41be040 is 0 bytes after a block of size 24 alloc'd
==16308==    at 0x4028876: malloc (vg_replace_malloc.c:236)
==16308==    by 0x8048945: parse (felt.c:48)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308== 
==16308== Invalid write of size 2
==16308==    at 0x804899C: parse (felt.c:52)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308==  Address 0x41be040 is 0 bytes after a block of size 24 alloc'd
==16308==    at 0x4028876: malloc (vg_replace_malloc.c:236)
==16308==    by 0x8048945: parse (felt.c:48)
==16308==    by 0x8048BF2: main (felt.c:124)
==16308== 

```

Using gcc in the program:
```

***************************
***** Felt Grace v1.0 *****
***************************
shawn@~/home/shawn/Public/CSC425/Problems/Source$ gcc -o felt felt.c
==16321== Conditional jump or move depends on uninitialised value(s)
==16321==    at 0x40B6CF3: strtok (strtok.S:160)
==16321==    by 0x8048D50: main (felt.c:165)
==16321== 
==16321== Use of uninitialised value of size 4
==16321==    at 0x40B6CF5: strtok (strtok.S:161)
==16321==    by 0x8048D50: main (felt.c:165)
==16321== 
==16321== Conditional jump or move depends on uninitialised value(s)
==16321==    at 0x40B6CFE: strtok (strtok.S:165)
==16321==    by 0x8048D50: main (felt.c:165)
==16321== 
==16321== Invalid write of size 1
==16321==    at 0x40290C0: strcpy (mc_replace_strmem.c:311)
==16321==    by 0x8048961: parse (felt.c:49)
==16321==    by 0x8048D50: main (felt.c:165)
==16321==  Address 0x41bf2ab is 0 bytes after a block of size 3 alloc'd
==16321==    at 0x4028876: malloc (vg_replace_malloc.c:236)
==16321==    by 0x8048945: parse (felt.c:48)
==16321==    by 0x8048D50: main (felt.c:165)
==16321== 
==16321== Conditional jump or move depends on uninitialised value(s)
==16321==    at 0x40B6D54: strtok (strtok.S:232)
==16321==    by 0x8048D50: main (felt.c:165)
==16321== 
==16321== Invalid read of size 1
==16321==    at 0x40290B4: strcpy (mc_replace_strmem.c:311)
==16321==    by 0x8048A31: attach_path (felt.c:70)
==16321==    by 0x8048D6A: main (felt.c:168)
==16321==  Address 0x41be040 is 0 bytes after a block of size 24 alloc'd
==16321==    at 0x4028876: malloc (vg_replace_malloc.c:236)
==16321==    by 0x8048945: parse (felt.c:48)
==16321==    by 0x8048BF2: main (felt.c:124)
==16321== 
==16324== Syscall param execve(argv[i]) points to unaddressable byte(s)
==16324==    at 0x40DB93F: execve (execve.c:60)
==16324==    by 0x8048FDD: main (felt.c:245)
==16324==  Address 0x41bf2ab is 0 bytes after a block of size 3 alloc'd
==16324==    at 0x4028876: malloc (vg_replace_malloc.c:236)
==16324==    by 0x8048945: parse (felt.c:48)
==16324==    by 0x8048D50: main (felt.c:165)
==16324== 
==16324== Syscall param execve(envp[i]) points to unaddressable byte(s)
==16324==    at 0x40DB93F: execve (execve.c:60)
==16324==    by 0x8048FDD: main (felt.c:245)
==16324==  Address 0x41be040 is 0 bytes after a block of size 24 alloc'd
==16324==    at 0x4028876: malloc (vg_replace_malloc.c:236)
==16324==    by 0x8048945: parse (felt.c:48)
==16324==    by 0x8048BF2: main (felt.c:124)
==16324== 
gcc: error trying to exec 'cc1': execvp: No such file or directory
shawn@~/home/shawn/Public/CSC425/Problems/Source$ ^C==16321== 

```

---

### Post by terry_a_g on 2011-11-08
You need to review what the environment is and what a path is.  You're pretty far off.  Try typing env in a bash prompt to see what should be going into my_envp.

---

### Post by shawnat88 on 2011-11-08
Quite the difference. But It seems that I am parsing the path correctly at least. Are you saying that my_envp should look almost line for line what the second output looks like?

typing "env" in my shell:
```

/usr/lib/lightdm/lightdm/
/usr/local/sbin/
/usr/local/bin/
/usr/sbin/
/usr/bin/
/sbin/
/bin/
/usr/games/

```

typing "env" in bash:
```

SSH_AGENT_PID=1540
GPG_AGENT_INFO=/tmp/keyring-oFIJuQ/gpg:0:1
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=014baad273b8897a0cd11e22000000f0-1320482772.617785-1176529454
WINDOWID=79691782
GNOME_KEYRING_CONTROL=/tmp/keyring-oFIJuQ
GTK_MODULES=canberra-gtk-module:canberra-gtk-module
USER=shawn
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK=/tmp/keyring-oFIJuQ/ssh
SESSION_MANAGER=local/shawn-TOSHIBA-NB205:@/tmp/.ICE-unix/1503,unix/shawn-TOSHIBA-NB205:/tmp/.ICE-unix/1503
USERNAME=shawn
DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=ubuntu
PWD=/home/shawn/Public/CSC425/Problems/Source
GNOME_KEYRING_PID=1494
LANG=en_US.UTF-8
MANDATORY_PATH=/usr/share/gconf/ubuntu.mandatory.path
UBUNTU_MENUPROXY=libappmenu.so
COMPIZ_CONFIG_PROFILE=ubuntu
GDMSESSION=ubuntu
SHLVL=1
HOME=/home/shawn
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
IBUS_ENABLE_SYNC_MODE=1
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-FOAfdFhU5L,guid=232bd14cfe7deaf7311e91ff000000b5
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0
XDG_CURRENT_DESKTOP=Unity
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/shawn/.Xauthority
_=/usr/bin/env

```

---

### Post by Bachstelze on 2011-11-08
> **shawnat88 said:**
> 
typing "env" in my shell:
```

/usr/lib/lightdm/lightdm/
/usr/local/sbin/
/usr/local/bin/
/usr/sbin/
/usr/bin/
/sbin/
/bin/
/usr/games/

```


Goodness, that's definitely not right. Environment variables must be KEY=value pairs, not just random strings.

---

