---
title: "learning C"
date: 2005-09-20
forum: Programming Talk
---

### Post by uten on 2005-09-20
Im doing a C programming course at school, but i realise my windows code doesnt work in ajunta. Im doing the fundamentals, structures, unions, pointers, functions. is it that the libraries in linux are different? i cant even get hello world to run. someone plz help. i just need some pointers as to how to start off coding

---

### Post by JmSchanck on 2005-09-20
Can you post the errors you get? my guess is you don't have the required packages installed like gcc libc and make. 

apt-get install build-essential

should fix it

---

### Post by uten on 2005-09-20
well on previous systems i had issues with libaries like conio.h and stdlib.h

---

### Post by LordHunter317 on 2005-09-21
Well, conio.h isn't a Standard C header, and it wouldn't work on UNIX.

stdlib.h is though, and should work everywhere.

---

### Post by David Marrs on 2005-09-21
[QUOTE=uten]Im doing a C programming course at school, but i realise my windows code doesnt work in ajunta. Im doing the fundamentals, structures, unions, pointers, functions. is it that the libraries in linux are different? i cant even get hello world to run. someone plz help. i just need some pointers as to how to start off coding[/QUOTE]
 Ah, yes. I discovered this problem when I tried to take my uni work home with me and compile it on my Borland compiler. It was the other way round for me: they ran Posix and I ran windows.

It's far easier to set up a unix environment in windows than it is to set up a windows environment in Linux so for your own code use one of the following:
[list=1]
[*]For a complete Posix environment you can install [Cygwin](http://www.cygwin.com/).
[*]Slightly less over-kill is [Msys](http://www.mingw.org/msys.shtml).
[*]Finally, from the same website, there's [MinGW](http://www.mingw.org/), which is basically Msys without the friendly bourne shell (you run it from the Windows Terminal).[/list]

Here's a hello world app, as run from the terminal, that should run from within Ubuntu. If it doesn't then you haven't installed all the necessary development tools and libs:
```
david@ubuntu$ more hello.c

#include<stdio.h>
#include<stdlib.h>

int main(){
  printf("Hello, world\n");
  exit(EXIT_SUCCESS);
}

david@ubuntu$ gcc hello.c
david@ubuntu$ ./a.out
Hello, world
david@ubuntu$

```

---

### Post by Radi0ShacK on 2005-09-21
Hi,
for conio.h u can use ncurses.h "the two libraries not the same though"

---

### Post by void_false on 2005-09-21
There's problem with iostream.h too.

---

### Post by jerome bettis on 2005-09-21
^ huh?  iostream is a C++ thing, not C

---

### Post by void_false on 2005-09-21
Oops. Sorry.  :-# But Anjuta has some probs with it too.
BTW I've searched for conio.h and found [this](http://www.boutell.com/lsm/lsmbyid.cgi/001104).

---

### Post by Roptaty on 2005-09-21
[QUOTE=void_false]There's problem with iostream.h too.[/QUOTE]

As jerome bettis said; iostream.h is a C++ header. Furthermore, iostream.h is a deprecated header. The new name is simply iostream.

If you are learning C/C++ and the book you are learning from uses conio.h or iostream.h... Get yourself a new updated book which follows the standard (and save yourself a lot of trouble). :)

---

### Post by void_false on 2005-09-21
After few minutes of googling I found out few important things:

Now I should use new naming scheme for C headers - remove .h and add c in the beggining. I.E. <stdio.h> should be <cstdio>

For C++ headers I should remove .h

And also should add this line "using namespace std;"

Now everything just rox.  :grin:

---

### Post by uten on 2005-09-21
[QUOTE=void_false]After few minutes of googling I found out few important things:

Now I should use new naming scheme for C headers - remove .h and add c in the beggining. I.E. <stdio.h> should be <cstdio>

For C++ headers I should remove .h

And also should add this line "using namespace std;"

Now everything just rox.  :grin:[/QUOTE]
 kool, thanks for all the help guys. im gonna continue working with it and keep you updated. My school is being really unfair and just teaching students to code in windows, heck they even teach .net and you have no choice. im trying to change that, they need to embrace the open source movement

---

### Post by jerome bettis on 2005-09-22
[QUOTE=uten]they need to embrace the open source movement[/QUOTE]

ehhhhhh i wouldn't say that but learning C through a nix environment is lots more fun than doing windows BS.  it's an appealing skill to have in the toolbox, and it will help you write better code everywhere else to some degree.  

but obviously it's less practical to the eggs in management, and i would think most people go to college to get jobs when they're done, therefore your school doesn't 'embrace the open source movement'. 

sometimes i think i'd rather just not get paid then write VB 5 days a week, but until i get something else figured out i'm _stuck_ .. ](*,)

---

### Post by YourSurrogateGod on 2005-09-24
[Here](http://www-ccs.ucsd.edu/c/) is a list of all standard ANSI C functions. Which can be quite helpful when you don't know what a particular function does or need a particular function to do something.

---

### Post by uten on 2005-10-27
ok i am doing a project for my data structures course, do you guys know any other function to use to clear the screen other than clrscr? because that is used in conio.h and ansi C doesnt support it. thanks

---

### Post by Jengu on 2005-10-27
#include <iostream> // should work

---

### Post by LordHunter317 on 2005-10-27
That's C++, not C, and it doesn't do what he wants anyway.

Why do you need to clear the screen?

---

### Post by uten on 2005-10-27
well its a series of menus, I not doin visual C, so its jus like an easy way to simulate the aesthetics of different menus. so like i wud out put one menu, read in the users choice, use switch to decide which is the next menu to display. if i dont use a clear screen function then all the menus pile up under each other, and looks untidy and confusing

---

### Post by uten on 2005-10-30
Ok i found how to port conio.h to linux except i am a bit confused. i have ncurses installed, got it from the repos, ncurses-base ncurses-lib etc. but when i type make it gives me errors, so what to do. 

i got the files from here:
[http://www.gerald-friedland.de/projects.html](http://www.gerald-friedland.de/projects.html)

found the link here:
[http://www.boutell.com/lsm/lsmbyid.cgi/001104](http://www.boutell.com/lsm/lsmbyid.cgi/001104)

anyone care to help? pleassssse

---

### Post by Buffalo Soldier on 2005-10-30
[QUOTE=uten]ok i am doing a project for my data structures course, do you guys know any other function to use to clear the screen other than clrscr? because that is used in conio.h and ansi C doesnt support it. thanks[/QUOTE]
This is what I usually do. Guys, I'm new to C too, so if this is wrong, please give me a smack down and correct me.
In Windows:
```
#include <stdio.h>

int main()
{
	char a;
	printf ("Test A B C D 1 2 3 4 5.\n");
	printf ("Test A B C D 1 2 3 4 5.\n\n");
	printf ("Would you like to clear screen?");
	scanf ("%c", &a);
	if (a == 'y')
	{
		system("[color=red]**cls**[/color]");
		printf("Screen has been cleared.\n");
	}
	else
		printf("Screen has not been cleared.\n");
   return 0;
}

```
In GNU/Linux:
```
#include <stdio.h>

int main()
{
	char a;
	printf ("Test A B C D 1 2 3 4 5.\n");
	printf ("Test A B C D 1 2 3 4 5.\n\n");
	printf ("Would you like to clear screen?");
	scanf ("%c", &a);
	if (a == 'y')
	{
		system("[color=red]**clear**[/color]");
		printf("Screen has been cleared.\n");
	}
	else
		printf("Screen has not been cleared.\n");
   return 0;
}

```
Or have I misunderstood the question and you're actually looking for something else.

---

### Post by uten on 2005-10-30
yes thats it!!!!!!!!!!!!!!!!!!!!!!!!!!!! thank you very much.

---

