---
title: "Writing a custom getpass() routine for multiple platforms"
date: 2014-11-17
forum: Programming Talk
---

### Post by SagaciousKJB on 2014-11-17
Well, I've been trying to modify a password manager program I like to not echo the passwords as I enter them.  I've got a routine using getch() from conio.h for Windows, but opted to use the the getpas() function from the standard libc even though it's considered obsolete.  I found a stackoverflow page that explains it will crash OSX if used, but it works fine on Linux.  So I wanted to make a header file that will define a getpass() function accordingly for each platform.  Just using the standard on Linux, conio.h on Windows and the method I found on stackoverflow for OSX.

I don't use any computers with OSX though, just want this to be as portable as I can and able to work on any OS I anticipate needing it for.  Does this look like it will work on OSX?  Is that the proper way to test for that platform?

I prefer the way getpass() from the standard library performs.  One thing in particular is that the prompt to enter the password cannot be deleted, where as in my routine you can backspace right over the prompt and then not pass the right information.



```
/*getpass.h*/
#ifndef PGETCH
#define PGETCH
#ifdef __unix__
#include <termios.h>
#include <unistd.h>

/*Use getpas() in the libc libaries.  It is obsolete but works on Linux.  Use getch() from conio.h on Windows, and custom function below for OSX.
  getpas() in libc will crash OSX*/

#elif _MSC_VER  || __WIN32__ || __MS_DOS__
#include <conio.h>

char *getpass(const char *prompt) 
{
	int i=0;
	char *pass, c;
	pass = malloc(sizeof(char) * 256);
	if(pass == NULL)
	{
		exit(1);
	}

	printf("\n%s", prompt);
	while((c=getch()) != '\r')
	{
		if(c == '\b')
		{
			i--;
			printf("\b \b");
		}
		else
		{
			pass[i] = c;
			printf("*");
			i++;
		}
	}
	pass[i] = '\0';

	return pass;

}
#elif __APPLE__
#include <termios.h>
#include <unistd.h>

static struct termios n_term;
static struct termios o_term;

static int
cbreak(int fd) 
{
   if((tcgetattr(fd, &o_term)) == -1)
      return -1;
   n_term = o_term;
   n_term.c_lflag = n_term.c_lflag & ~(ECHO|ICANON);
   n_term.c_cc[VMIN] = 1;
   n_term.c_cc[VTIME]= 0;
   if((tcsetattr(fd, TCSAFLUSH, &n_term)) == -1)
      return -1;
   return 1;
}

int getch() 
{
   int cinput;

   if(cbreak(STDIN_FILENO) == -1) {
      fprintf(stderr, "cbreak failure, exiting \n");
      exit(EXIT_FAILURE);
   }
   cinput = getchar();
   tcsetattr(STDIN_FILENO, TCSANOW, &o_term);

   return cinput;
}

#define BACK_SPACE 127

char *getpass(const char *prompt) 
{
	int i=0;
	char *pass, c;
	pass = malloc(sizeof(char) * 256);
	if(pass == NULL)
	{
		exit(1);
	}

	printf("\n%s", prompt);
	while((c=getch()) != '\n')
	{
		if(c == BACK_SPACE)
		{
			i--;
			printf("\b \b");
		}
		else
		{
			pass[i] = c;
			printf("*");
			i++;
		}
	}
	pass[i] = '\0';

	return pass;
#endif
#endif

```

---

