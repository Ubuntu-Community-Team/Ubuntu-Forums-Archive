---
title: "Installing NCurses"
date: 2008-03-21
forum: Programming Talk
---

### Post by rgcouto on 2008-03-21
Hello, I've installed ncurses on my ubuntu, but when I use the library "conio.h" or "ncurses.h" and compile my code with GCC, it returns me a strange error :/
```

/tmp/ccY6BDyH.o: In function `main':
main.c:(.text+0x201): undefined reference to `stdscr'
main.c:(.text+0x209): undefined reference to `wgetch'
collect2: ld returned 1 exit status

```

Do you know whats happening?


P.S.  - Sorry about my bad english..

---

### Post by WW on 2008-03-21
What was the command that you used to compile and link your code?

You might not have told the compiler to use the ncurses library.  You probably have to add an option like ***-lcurses***.

---

### Post by rgcouto on 2008-03-21
> **WW said:**
> What was the command that you used to compile and link your code?

You might not have told the compiler to use the ncurses library.  You probably have to add an option like ***-lcurses***.

Yeah ;) thx ... i've forgotten to call it when i compile....

---

### Post by rgcouto on 2008-03-21
Now i have an other problem ;/ OMG

I have this code:

```


#include <stdio.h>
#include <conio.h>

...

	char user[40], pwd[10], c;
	int i = 0;

...

	printf ("User Login\n");
	printf ("Insert your username:\n");
	fgets(user,50,stdin);
	printf ("Insert your password:\n");
	while (i <= 10) { 
		c = getch(); 
		pwd[i] = c; i++;
		printf("*"); 
	}

...

Then I have a function to test the login that returns "Hello, *username*" or "Autentication failed"


```

but when I compile e run it the programm waits for insert the username, but when I <enter> it returns me:

```
***********Autentication failed!!
*** stack smashing detected ***: ./a.out terminated
Aborted (core dumped)
```


What's happening now?!? 

I getting crazy with this error.. LOOL :P

---

### Post by supirman on 2008-03-21
See a problem?

char user[[COLOR="Red"]**40**[/COLOR]], pwd[10], c;

fgets(user,[COLOR="Red"]**50**[/COLOR],stdin);

---

### Post by supirman on 2008-03-21
See what happens when I enter > 40 characters as the name:

```
$)> ./a.out
Enter you name: aaaassssddddffffddddssssddddffffddddssssddd
user is aaaassssddddffffddddssssddddffffddddssssddd

*** stack smashing detected ***: ./a.out terminated
Aborted (core dumped)

```

I'm sure you can see the problem from the previous post.  If you don't know what's going on, feel free to ask for clarification.

---

### Post by rgcouto on 2008-03-27
I've changed the code now:

```


#include <stdio.h>
#include <conio.h>

...

	char user[40], pwd[10], c;
	int i = 0;

...

	printf ("User Login\n");
	printf ("Insert your username:\n");
	fgets(user,[COLOR="Red"]40[/COLOR],stdin);
	printf ("Insert your password:\n");
	while (i <=[COLOR="Red"]9[/COLOR]) { 
		c = getch(); 
		pwd[i] = c; i++;
		printf("*"); 
	}

...

Then I have a function to test the login that returns "Hello, *username*" or "Autentication failed"


```

and now when i compile, run, and insert the username it returns me:

```
***********Autentication failed!!
```

I'm close to freak out... GRRRRR ..[/QUOTE]

---

### Post by supirman on 2008-03-27
How are you comparing the password?  Are you using a strcmp?  You're filling character by character into the password buffer, but I don't see you manually adding a terminating \0 to the password buffer to allow it to be treated as a string.

---

