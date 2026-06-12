---
title: "in C, what gets single key inputs without the enter key?"
date: 2007-09-19
forum: Programming Talk
---

### Post by ant2ne on 2007-09-19
in C

What is the command to allow keyboard input that does not require the enter key to coninue.

For Example... The screen says "Press Y/N" and the program then waits for a Y or N but not Y+Enter or N+Enter.

---

### Post by CptPicard on 2007-09-19
getch()

EDIT: Whoops, getch() wasn't standard... been some time since I actually did C... let me get back to this if I find something for real ;) Googling "C reading single character without enter" produces interesting reading.

EDIT2: Here's a function I found... (must say it looks remarkably difficult for a simple thing..)

```

#include <termios.h>
#include <unistd.h>
#include <assert.h>
#include <string.h>
/*------------------------------------------------*/
int getch(void) {
      int c=0;

      struct termios org_opts, new_opts;
      int res=0;
          //-----  store old settings -----------
      res=tcgetattr(STDIN_FILENO, &org_opts);
      assert(res==0);
          //---- set new terminal parms --------
      memcpy(&new_opts, &org_opts, sizeof(new_opts));
      new_opts.c_lflag &= ~(ICANON | ECHO | ECHOE | ECHOK | ECHONL | ECHOPRT | ECHOKE | ICRNL);
      tcsetattr(STDIN_FILENO, TCSANOW, &new_opts);
      c=getchar();
          //------  restore old settings ---------
      res=tcsetattr(STDIN_FILENO, TCSANOW, &org_opts);
      assert(res==0);
      return(c);
}

```

---

### Post by Arwen on 2007-09-19
I've seen this:[http://gcc.gnu.org/ml/gcc/1999-09n/msg01188.html](http://gcc.gnu.org/ml/gcc/1999-09n/msg01188.html)
Do I have to add #include <curses.h>?Because when I do it,it says it does find file curses.h but when I don't add it it says undefined reference to getch() for "char a=getch();"
I think I'm using it wrong or sth?

---

### Post by Wim Sturkenboom on 2007-09-19
You have to install ncurses. It's however a bit overkill if you only want a getch() function. See example above that switches terminal to raw mode, gets the character using getc and switching the terminal back to it's original config.

---

### Post by Arwen on 2007-09-19
Yep it's libncurses5-dev.But the example gives segmentation fault and gdb's backtrace gives only "#0  0x080485d3 in main ()"..

---

### Post by Modred on 2007-09-19
> **Wim Sturkenboom said:**
> You have to install ncurses. It's however a bit overkill if you only want a getch() function. See example above that switches terminal to raw mode, gets the character using getc and switching the terminal back to it's original config.


Meh, egg on my face.  Should have read the request better.

---

### Post by rplantz on 2007-09-20
There is a good description of this in "Beginning Linux Programming" by Matthew and Stones. I see there's a fourth edition. I think mine is 3rd edition, but I assume this information is still there. It's not a very expensive book, and I think it has a lot of good practical information about programming linux applications.

---

### Post by gnusci on 2007-09-20
I guess you looking for something like this:

[PHP]
#include <stdio.h>
#include <string.h>

#include <sys/time.h>
#include <termios.h> 
#include <stdlib.h>

static struct termios g_old_kbd_mode;

// did somebody press somthing???
static int kbhit(void){
	struct timeval timeout;
	fd_set read_handles;
	int status;

	// check stdin (fd 0) for activity
	FD_ZERO(&read_handles);
	FD_SET(0, &read_handles);
	timeout.tv_sec = timeout.tv_usec = 0;
	status = select(0 + 1, &read_handles, NULL, NULL, &timeout);
	return status;
}

// put the things as they were befor leave..!!!
static void old_attr(void){
	tcsetattr(0, TCSANOW, &g_old_kbd_mode);
}


// main function
int main( void ){
	char ch;
	static char init;
	struct termios new_kbd_mode;

	if(init)
		return;
	// put keyboard (stdin, actually) in raw, unbuffered mode
	tcgetattr(0, &g_old_kbd_mode);
	memcpy(&new_kbd_mode, &g_old_kbd_mode, sizeof(struct termios));
	
	new_kbd_mode.c_lflag &= ~(ICANON | ECHO);
	new_kbd_mode.c_cc[VTIME] = 0;
	new_kbd_mode.c_cc[VMIN] = 1;
	tcsetattr(0, TCSANOW, &new_kbd_mode);
	atexit(old_attr);
	
	printf( "Press Any Key ('q' for exit) \n");
	while (!kbhit()){
		// getting the pressed key...
		ch = getchar();
		printf("You pressed - %c\n",ch);
		if(ch == 'q'){
			printf("bye... :)\n");
			exit(1);
		}
	}
	return 0;
}

[/PHP]

---

### Post by ant2ne on 2007-09-20
> **gnusci said:**
> I guess you looking for something like this:Yes that is perfect. Thanks. Isn't that very complicated form something so simple and common? OH well... thanks for the code. I'm gonna butcher it for my own needs.

---

### Post by gnusci on 2007-09-20
Oh well, give a look to [COLOR="Red"]termios.h[/COLOR], I think is the most important point...

[http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html](http://www.opengroup.org/onlinepubs/007908799/xsh/termios.h.html)

---

### Post by Wim Sturkenboom on 2007-09-21
> **ant2ne said:**
> Isn't that very complicated form something so simple and common?If getch was implemented as standard and gets was not, you would have asked the same question :)

You can always create a library (and associated include file) with your own functions for kbhit(), getch() etc. Link it during the compile when you need it.

PS I mentioned *gets*, but don't use it because it creates a buffer overflows vulnerability; use *fgets* instead.

---

### Post by ant2ne on 2007-09-21
> **Wim Sturkenboom said:**
> If getch was implemented as standard and gets was not, you would have asked the same question :)

You can always create a library (and associated include file) with your own functions for kbhit(), getch() etc. Link it during the compile when you need it.

PS I mentioned *gets*, but don't use it because it creates a buffer overflows vulnerability; use *fgets* instead.:confused: I don't think I'm at the skill level to be creating my own libraries at this time. Maybe in the future. So I should use fgets.... *examines program in progress*

---

### Post by gnusci on 2007-09-21
Well what actually (I think) **Sturkenboom** is that you can write your own "include" header files, so you can put your custom functions there so you can reuse them in different programs.

Something like, lets say you wrote the functions my_kbhit() and my_getch() and instead to put them inside the main program source file y can put them into you own header file and then include it every time you need.

let say you wrote something like (using psudocode):

**pmain.c**
[PHP]
#include<libray1.h>
#include<libray2.h>

void my_kbhit(void){
   .... bla bla bla...
}

void my_getch(void){
   .... bla bla bla...
}

int main(void){
   ... more bla...
   my_kbhit();
   my_getch();
   return 0;
}
[/PHP]

and now you can compile you code with the command:

**> gcc pmain.c -o pmain**

now you can du the same but you can slip the code in two files, one header and the main program, let see:


**pmain.h**
[PHP]
#include<libray1.h>
#include<libray2.h>

void my_kbhit(void){
   .... bla bla bla...
}

void my_getch(void){
   .... bla bla bla...
}

[/PHP]

**pmain.c**
[PHP]
#include<libray1.h>
#include<libray2.h>
#include<pmain.h> // here i did include the new header file

int main(void){
   ... more bla...
   my_kbhit();
   my_getch();
   return 0;
}
[/PHP]

now you can compile with:

**> gcc pmain.c -o pmain -I.**

Now you can reuse your function in every program you need just incuding the header.

---

### Post by ant2ne on 2007-09-21
```
#include <pthread.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <sys/time.h>
#include <termios.h> 
#include <unistd.h>
//---------------------------------------------------------------
// GLOBAL DECLARATIONS
//---------------------------------------------------------------
static struct termios g_old_kbd_mode;
//int j;
//---------------------------------------------------------------
// END GLOBAL DECLARTATIONS
//---------------------------------------------------------------



//-------------------------------------------------------
// KEYPRESS DITTY
//--------------------------------------------------------
	// did somebody press somthing???
static int kbhit(void)
	{
	    struct timeval timeout;
	    fd_set read_handles;
	    int status;

	    // check stdin (fd 0) for activity
	    FD_ZERO(&read_handles);
	    FD_SET(0, &read_handles);
	    timeout.tv_sec = timeout.tv_usec = 0;
	    status = select(0 + 1, &read_handles, NULL, NULL, &timeout);
	    return status;
	}

		// put the things as they were befor leave..!!!
static void old_attr(void)
	{
	    tcsetattr(0, TCSANOW, &g_old_kbd_mode);
	}
//-----------------------------------------------------------
// END KEYPRESS DITTY
//------------------------------------------------------------


//---------------------------------------------------------------
// MAIN
//---------------------------------------------------------------
int main(void)
{
    char ch;
    static char init;
    struct termios new_kbd_mode;
    if(init)
        return 0;
    // put keyboard (stdin, actually) in raw, unbuffered mode
    tcgetattr(0, &g_old_kbd_mode);
    memcpy(&new_kbd_mode, &g_old_kbd_mode, sizeof(struct termios));

    new_kbd_mode.c_lflag &= ~(ICANON | ECHO);
    new_kbd_mode.c_cc[VTIME] = 0;
    new_kbd_mode.c_cc[VMIN] = 1;
    tcsetattr(0, TCSANOW, &new_kbd_mode);
    atexit(old_attr);    
    //printf( "Press Any Key ('q' for exit) \n");
    while (!kbhit()){
        // getting the pressed key...
        ch = getchar();
	//if(ch != '')
	//{
            //printf("Buh-Bye...     =)\n");
            exit(1);
        //}
    }
    return 0;
} 
//---------------------------------------------------------------
// END MAINfs
//---------------------------------------------------------------

```
Having gutted the above code of all un needed terminal outputs. How would I make this a my_getchar.h in which my original calling program can receive the variable ch. Also, are there any includes that I don't need to include?

---

