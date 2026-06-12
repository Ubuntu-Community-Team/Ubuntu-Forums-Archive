---
title: "using getopt in C"
date: 2007-03-04
forum: Programming Talk
---

### Post by g3k0 on 2007-03-04
Greetings, I am using the getopt function and I had a question.  Is there anyway to easily, not require an argument after the r - example

./webserver -p 5000 -r

rather than

./webserver -p 5000 -r /asd

because it does this to me
[bwhit132@csunix webserver]$ ./webserver -p 5000 -r
./webserver: option requires an argument -- r


I want to allow the option but not have it as a necessity.  


this is what im doing with it
```
void processargs(int argc, char **argv) {
  int dirSize = 100;
  int next_option;
  const char* short_options = "p:r:";
  do {
    next_option = getopt(argc, argv, short_options);
    if (next_option != -1) {
      switch (next_option)
      {
        case 'p': /* -p -- port option  */
          port = optarg;
          break;
	case 'r':
		
	  myPath = malloc(dirSize);		//allocate because we are copying into a null ptr
	  while (getcwd(myPath,dirSize) == NULL){   //if the directory has a long name, reallocate size
		  free(myPath);
		  dirSize *= 2;
		  myPath = malloc(dirSize);		  
	  }
	 downPath = optarg;	
	 if (downPath == NULL){
		  printf("\nHAHAAAAA NULL BOY\n");
	 } else { printf("\n%s\n",downPath); }
	  break;
        default:
          /* Unknown option detected. Print it to standard
                output, and exit with exit code zero (normal termination). */
          fprintf(stderr, USAGE_STRING);
          exit(1);
  
      }
    }
  } while (next_option != -1);
  
  if (port == NULL) {
          fprintf(stderr, USAGE_STRING);
          exit(1);
  }
}

```




Edit: In case you were wondering I was just testing with the whole hahaha null boy thing..

---

### Post by Mr. C. on 2007-03-04
man 3 getopt

> 
       optstring is a string containing the legitimate option characters.   If
       such  a  character is followed by a colon, the option requires an argu-
       ment, so getopt places a pointer to the  following  text  in  the  same
       argv-element,  or  the  text  of the following argv-element, in optarg.
       Two colons mean an option takes an optional arg; if there  is  text  in
       the current argv-element, it is returned in optarg, otherwise optarg is
       set to zero.  This is a GNU extension.  If optstring  contains  W  fol-
       lowed  by a semicolon, then -W foo is treated as the long option --foo.
       (The -W option is reserved by POSIX.2 for  implementation  extensions.)
       This  behaviour is a GNU extension, not available with libraries before
       GNU libc 2.


---

### Post by g3k0 on 2007-03-04
ohhhh thanks.  I was looking at the wrong man page.  Thanks for your help

---

