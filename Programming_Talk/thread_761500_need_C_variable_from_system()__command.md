---
title: "need C variable from system()  command"
date: 2008-04-21
forum: Programming Talk
---

### Post by garyed on 2008-04-21
I'm writing a C program that uses the system function that uses grep & auk  to get a number from a file.  I want to use the result as a variable for later calculations. The variable always ends up being 0 even though
the system function returns the number 50.  
Can anyone show me what am I doing wrong?

[Code]
#include <stdio.h>
#include <stdlib.h>
int y;
int main()
{
y=system ("cat /home/gary/check1|grep 'Maximum'|awk '{print $4}'"); 
printf ("Maximum counts are %d\n",y);
  return 0;
}
[/Code

---

### Post by Zugzwang on 2008-04-21
The "system" command returns the error code of the command executed. If your command runs nicely you will get a 0. See [here]("http://opengroup.org/onlinepubs/007908799/xsh/system.html") for details.

Edit: Note that the output of the program run will *not* be parsed by the system function. There are other ways of doing so (hint: Look at "popen").

---

### Post by ghostdog74 on 2008-04-21
> **garyed said:**
> I'm writing a C program that uses the system function that uses grep & auk  to get a number from a file.  I want to use the result as a variable for later calculations. The variable always ends up being 0 even though
the system function returns the number 50.  
Can anyone show me what am I doing wrong?

[Code]
#include <stdio.h>
#include <stdlib.h>
int y;
int main()
{
y=system ("cat /home/gary/check1|grep 'Maximum'|awk '{print $4}'"); 
printf ("Maximum counts are %d\n",y);
  return 0;
}
[/Code
the system() function returns 0 if the command execute without errors. your *nix commands indeed executed without errors. Is this your assignment and had to be done in C?  You should really use File I/O methods in C to read the line and get the things you want. This is more portable, IMO.

---

### Post by heikaman on 2008-04-21
> **Zugzwang said:**
> 
Edit: Note that the output of the program run will *not* be parsed by the system function. There are other ways of doing so (hint: Look at "popen").

[PHP]
#include <iostream>
#include <errno.h>

using namespace std;

int main(){
	FILE* stream=popen("expr 8 / 2","r");
	char* buffer=NULL;
	size_t len=0;
	int value=0;

	if(stream && getline(&buffer, &len, stream)){
		value=atoi(buffer);
	}else {
		perror("popen");
		exit(errno);
	}

	pclose(stream);
	free(buffer);

	cout << value << endl;

	return 0;
}

[/PHP]

---

### Post by garyed on 2008-04-21
> **Zugzwang said:**
> The "system" command returns the error code of the command executed. If your command runs nicely, you will therefore get a 0. See [here]("http://opengroup.org/onlinepubs/007908799/xsh/system.html") for details.
Just to be sure I understand correctly.
Does that mean that what I'm trying to do can't be done with the system() function because the only variable I'll be able to get is an error code?  As you can see I'm a novice at this. 

What I've done is written a shell script that gets the numbers from tune2fs  & posts an alert only on the boot-up before the forced file system check is going to run. It actually works fine but for security reasons I'd rather compile it in C so my password isn't exposed in a file.

---

### Post by ghostdog74 on 2008-04-21
> **garyed said:**
> Just to be sure I understand correctly.
Does that mean that what I'm trying to do can't be done with the system() function because the only variable I'll be able to get is an error code?  As you can see I'm a novice at this. 

someone just showed you popen, so you can try that
> 
What I've done is written a shell script that gets the numbers from tune2fs  & posts an alert only on the boot-up before the forced file system check is going to run. It actually works fine but for security reasons I'd rather compile it in C so my password isn't exposed in a file.

then just do it in a script. For your security concerns, it can be mitigated by assigning proper rights to whoever has permission to view/execute your script ( or access the whole system ). Not a problem at all.

---

### Post by Zugzwang on 2008-04-21
For fixing your program, see heikaman's example, it's quite nice (which is as far as I can see, C++, however since iostream is included).

Note that you can't really hide your password in the executable file, you can just make it uncomfortable to read it out. Use grep on your executable to search for the command you are calling. You will see that it's contained in it. There are ways to hide it there as well, but using a debugger it's always possible to find it!

---

### Post by garyed on 2008-04-21
> **ghostdog74 said:**
> .... Is this your assignment and had to be done in C?  ......

I'm not a student,  just a guy getting into Linux & a little programming for the fun of it.  Its a little overwhelming right now but this community is totally amazing.

---

