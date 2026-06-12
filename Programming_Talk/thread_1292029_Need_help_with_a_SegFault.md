---
title: "Need help with a SegFault"
date: 2009-10-15
forum: Programming Talk
---

### Post by BlackSwordD2 on 2009-10-15
this is an implementation of the head function called myhead that uses system calls. it works under all cases as it should except when reading standard input such as

$ ./myhead
bird
bird
cat
[SegFault]

if anyone could help me track down this error it would be great


```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <errno.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>

#define FILE_BUFFER_SIZE 512
#define INIT_BUFF_SIZE 50
#define INC_BUFF_SIZE 10


//Prototypes:
char *get_next_line(int fd);
int get_next_char(int fd);


int main(int argc, char *argv[])
{
  char *file = NULL, *line = NULL;  //Note: these vars are initialized.
  int num_lines = 10;  //The default number of lines.
  int fd = 0;//If no file provided, read from standard input.

  //Check if invalid number of arguments and print usage message:
  if (argc > 4) 
  {
    fprintf(stderr,"Usage: myhead [-nN] [FILE]\n");
    return EXIT_FAILURE; 
  }

  //Decode arguments based on number of arguments:
  //(Does only limited error checking for invalid arguments!)
  switch (argc) 
  {
  case 1:
    //No arguments so print 10 lines from standard input, defaults.
    break;
	
  case 2:
    //Either (1) optional lines from standard input, or (2) defualt lines from a file:
    if (strncmp(argv[1],"-n",2) == 0) 
	{
      num_lines = atoi(argv[1] + 2); 
	  }
    else
      file = argv[1];
    break;
	
  case 3:
    //Either (1) optional lines from file, or (2) separated optional lines from standard input:
    if (strncmp(argv[1],"-n",2) == 0) 
	{
      if (strlen(argv[1]) == 2)
		num_lines = atoi(argv[2]);
		
      else 
	  {
		num_lines = atoi(argv[1] + 2);
		file = argv[2]; 
		} 
	}
    else 
	{
      fprintf(stderr,"Invalid arguments: Usage: myhead [-nN] [FILE]\n");
      return EXIT_FAILURE; 
	  }
    break;
	
  case 4:
    //Must have separated optional lines and file:
    if (strcmp(argv[1],"-n") == 0) 
	{
      num_lines = atoi(argv[2]);
      file = argv[3]; 
	  }
    else 
	{
      fprintf(stderr,"Invalid arguments: Usage: myhead [-nN] [FILE]\n");
      return EXIT_FAILURE; 
	  } 
	  
	}
    
  //If a file argument was given, then open it (else will use default stdin):
  //printf("%i\n",fd);
  if (file != NULL) 
  {
    //File pathname was given, Open file for reading:
    if ((fd = open(file, 2)) == -1) 
	{
      fprintf(stderr,"Error opening file %s: %s\n",file, strerror(errno));
      return EXIT_FAILURE; 
	  } 
  }

  //Read and print out the specified number of lines:
  int i;
    for (i=0; i<num_lines; i++) 
	{
      //Get next line from file:
      //printf("%i\n",fd);
      line = get_next_line(fd);
      //Check if actually got line or if EOF/error:
      if (line != NULL) 
	  {
		//Got line so print it:
		printf("%s\n", line);
		free(line);
		}
      else 
	  {
		if(errno > 0)
		{
			fprintf(stderr,"Error while reading file %s: %s\n",file, strerror(errno));
			return EXIT_FAILURE;
		}
	
		//No line, see if error or just EOF:
		else
			break;
		}
	}

  //If a file was read from, close it:
  if (file != NULL)
    close(fd);
  
  //Normal termination:
  return EXIT_SUCCESS;
}



//Function to get next line from open stream and place it as a legal string into
//a line buffer that is created locally and is static so it can be returned.
//Returns string (pointer to line buffer), or else NULL if error or immediate EOF.
//Note that it does not return any line terminator chars (newline or '\n').
int get_next_char(int fd){
  static int cnt = 0;
  static char char_buff[FILE_BUFFER_SIZE];
  int next_char;
  //printf("%i\n",fd);

  if(cnt == 0){
    read(fd,char_buff, FILE_BUFFER_SIZE);
    next_char = char_buff[cnt++];
    //printf("%i %c\n",cnt,next_char);
    
    
    return next_char;}
  else if(cnt == FILE_BUFFER_SIZE){
    cnt = 0;
    read(fd, char_buff, FILE_BUFFER_SIZE);
    next_char = char_buff[cnt++];
    //printf("%i %c\n",cnt,next_char);
   
    
    return next_char;}
  else{
    next_char = char_buff[cnt++];
    //printf("%i %c\n",cnt,next_char);
    
    return next_char;}
}

char *get_next_line(int fd){
  char *line_buff = malloc(INIT_BUFF_SIZE);
  int buff_pos = 0, buff_length = (INIT_BUFF_SIZE);
  int next_char;

  //Loop throughs chars until encounter EOL, EOF, or error,
  //placing chars into next position in line_buff:

  while ((next_char = get_next_char(fd)) != '\n' && next_char != EOF)
    {
      if (buff_pos < buff_length){
	
	*(line_buff + buff_pos++) = next_char;
	//printf("%i %s\n",buff_pos,line_buff);
	}
      else{
	//line_buff = line_buff - buff_pos;
	line_buff = realloc(line_buff, INC_BUFF_SIZE + strlen(line_buff));
	buff_length = buff_length + INC_BUFF_SIZE;
	//line_buff = line_buff + buff_pos;
	*(line_buff + buff_pos++) = next_char;
	//printf("%i %s\n",buff_pos,line_buff);
	//buff_pos = buff_pos + 1;
	  }
     }

  //Make sure that line_buff always contains a valid string:
  *(line_buff + buff_pos) = '\0';

  //Check whether to return string, else NULL:
  if (next_char == EOF && (buff_pos == 0 || errno > 0)){
    //Was at EOF already or there was an error:
    free(line_buff);
    return NULL;}
  else
    //Got a line (which might be blank) so return:
    
    //printf("%i %s\n",buff_pos,line_buff);
    return line_buff;
}


// EOF


```

---

### Post by Arndt on 2009-10-15
> **BlackSwordD2 said:**
> this is an implementation of the head function called myhead that uses system calls. it works under all cases as it should except when reading standard input such as

$ ./myhead
bird
bird
cat
[SegFault]

if anyone could help me track down this error it would be great


```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <errno.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>

#define FILE_BUFFER_SIZE 512
#define INIT_BUFF_SIZE 50
#define INC_BUFF_SIZE 10


//Prototypes:
char *get_next_line(int fd);
int get_next_char(int fd);


int main(int argc, char *argv[])
{
  char *file = NULL, *line = NULL;  //Note: these vars are initialized.
  int num_lines = 10;  //The default number of lines.
  int fd = 0;//If no file provided, read from standard input.

  //Check if invalid number of arguments and print usage message:
  if (argc > 4) 
  {
    fprintf(stderr,"Usage: myhead [-nN] [FILE]\n");
    return EXIT_FAILURE; 
  }

  //Decode arguments based on number of arguments:
  //(Does only limited error checking for invalid arguments!)
  switch (argc) 
  {
  case 1:
    //No arguments so print 10 lines from standard input, defaults.
    break;
	
  case 2:
    //Either (1) optional lines from standard input, or (2) defualt lines from a file:
    if (strncmp(argv[1],"-n",2) == 0) 
	{
      num_lines = atoi(argv[1] + 2); 
	  }
    else
      file = argv[1];
    break;
	
  case 3:
    //Either (1) optional lines from file, or (2) separated optional lines from standard input:
    if (strncmp(argv[1],"-n",2) == 0) 
	{
      if (strlen(argv[1]) == 2)
		num_lines = atoi(argv[2]);
		
      else 
	  {
		num_lines = atoi(argv[1] + 2);
		file = argv[2]; 
		} 
	}
    else 
	{
      fprintf(stderr,"Invalid arguments: Usage: myhead [-nN] [FILE]\n");
      return EXIT_FAILURE; 
	  }
    break;
	
  case 4:
    //Must have separated optional lines and file:
    if (strcmp(argv[1],"-n") == 0) 
	{
      num_lines = atoi(argv[2]);
      file = argv[3]; 
	  }
    else 
	{
      fprintf(stderr,"Invalid arguments: Usage: myhead [-nN] [FILE]\n");
      return EXIT_FAILURE; 
	  } 
	  
	}
    
  //If a file argument was given, then open it (else will use default stdin):
  //printf("%i\n",fd);
  if (file != NULL) 
  {
    //File pathname was given, Open file for reading:
    if ((fd = open(file, 2)) == -1) 
	{
      fprintf(stderr,"Error opening file %s: %s\n",file, strerror(errno));
      return EXIT_FAILURE; 
	  } 
  }

  //Read and print out the specified number of lines:
  int i;
    for (i=0; i<num_lines; i++) 
	{
      //Get next line from file:
      //printf("%i\n",fd);
      line = get_next_line(fd);
      //Check if actually got line or if EOF/error:
      if (line != NULL) 
	  {
		//Got line so print it:
		printf("%s\n", line);
		free(line);
		}
      else 
	  {
		if(errno > 0)
		{
			fprintf(stderr,"Error while reading file %s: %s\n",file, strerror(errno));
			return EXIT_FAILURE;
		}
	
		//No line, see if error or just EOF:
		else
			break;
		}
	}

  //If a file was read from, close it:
  if (file != NULL)
    close(fd);
  
  //Normal termination:
  return EXIT_SUCCESS;
}



//Function to get next line from open stream and place it as a legal string into
//a line buffer that is created locally and is static so it can be returned.
//Returns string (pointer to line buffer), or else NULL if error or immediate EOF.
//Note that it does not return any line terminator chars (newline or '\n').
int get_next_char(int fd){
  static int cnt = 0;
  static char char_buff[FILE_BUFFER_SIZE];
  int next_char;
  //printf("%i\n",fd);

  if(cnt == 0){
    read(fd,char_buff, FILE_BUFFER_SIZE);
    next_char = char_buff[cnt++];
    //printf("%i %c\n",cnt,next_char);
    
    
    return next_char;}
  else if(cnt == FILE_BUFFER_SIZE){
    cnt = 0;
    read(fd, char_buff, FILE_BUFFER_SIZE);
    next_char = char_buff[cnt++];
    //printf("%i %c\n",cnt,next_char);
   
    
    return next_char;}
  else{
    next_char = char_buff[cnt++];
    //printf("%i %c\n",cnt,next_char);
    
    return next_char;}
}

char *get_next_line(int fd){
  char *line_buff = malloc(INIT_BUFF_SIZE);
  int buff_pos = 0, buff_length = (INIT_BUFF_SIZE);
  int next_char;

  //Loop throughs chars until encounter EOL, EOF, or error,
  //placing chars into next position in line_buff:

  while ((next_char = get_next_char(fd)) != '\n' && next_char != EOF)
    {
      if (buff_pos < buff_length){
	
	*(line_buff + buff_pos++) = next_char;
	//printf("%i %s\n",buff_pos,line_buff);
	}
      else{
	//line_buff = line_buff - buff_pos;
	line_buff = realloc(line_buff, INC_BUFF_SIZE + strlen(line_buff));
	buff_length = buff_length + INC_BUFF_SIZE;
	//line_buff = line_buff + buff_pos;
	*(line_buff + buff_pos++) = next_char;
	//printf("%i %s\n",buff_pos,line_buff);
	//buff_pos = buff_pos + 1;
	  }
     }

  //Make sure that line_buff always contains a valid string:
  *(line_buff + buff_pos) = '\0';

  //Check whether to return string, else NULL:
  if (next_char == EOF && (buff_pos == 0 || errno > 0)){
    //Was at EOF already or there was an error:
    free(line_buff);
    return NULL;}
  else
    //Got a line (which might be blank) so return:
    
    //printf("%i %s\n",buff_pos,line_buff);
    return line_buff;
}


// EOF


```

Run it under gdb (compile and link with -g first) and you will see where it crashes.

---

### Post by fct on 2009-10-15
And for the sake of completeness, use this knowledge to debug segfaults with gdb:

[http://www.unknownroad.com/rtfm/gdbtut/gdbsegfault.html](http://www.unknownroad.com/rtfm/gdbtut/gdbsegfault.html)

---

### Post by Arndt on 2009-10-15
> **Arndt said:**
> Run it under gdb (compile and link with -g first) and you will see where it crashes.

I tried it myself, and indeed you will, but it won't be helpful. Get the tool valgrind and use it - you are corrupting the memory arena somehow by writing into unallocated memory. Valgrind will tell you where.

Or just singlestep the program carefully using gdb, noting what values all variables take. This time the input is so small that this is a useful approach.

---

### Post by BlackSwordD2 on 2009-10-15
ok popped it into gdb and did this following closely with the guide on gdb

```
(gdb) run
Starting program: /home/blake/Desktop/myhead 
test1
test1
test2


Program received signal SIGSEGV, Segmentation fault.
0xb7ed4e91 in ?? () from /lib/tls/i686/cmov/libc.so.6
(gdb) backtrace
#0  0xb7ed4e91 in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0xb7ed6fb2 in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ed89c5 in malloc () from /lib/tls/i686/cmov/libc.so.6
#3  0x08048b14 in get_next_line (fd=0) at /home/blake/Desktop/lab2.c:183
#4  0x080489a6 in main (argc=1, argv=0xbfbfa1b4)
    at /home/blake/Desktop/lab2.c:117
(gdb) frame 3
#3  0x08048b14 in get_next_line (fd=0) at /home/blake/Desktop/lab2.c:183
183	  char *line_buff = malloc(INIT_BUFF_SIZE);
(gdb) print *line_buff
$4 = 49 '1'
(gdb) frame 4
#4  0x080489a6 in main (argc=1, argv=0xbfbfa1b4)
    at /home/blake/Desktop/lab2.c:117
117	      line = get_next_line(fd);
(gdb) print fd
$5 = 0
(gdb) print line
$6 = 0x9114008 ""

```

---

