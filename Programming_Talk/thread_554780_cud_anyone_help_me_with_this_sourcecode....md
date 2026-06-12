---
title: "cud anyone help me with this sourcecode..."
date: 2007-09-19
forum: Programming Talk
---

### Post by azroule on 2007-09-19
i have a source code here...but it produce an error when compile..
what wrong with the "main"?
this program should be able to copy the content of binary and text file into another new file..let say for backup...

#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>

main()
{
	int fdin, fdout, value;
	char buffer[5000];

	fdin = open ("input.txt", O_RDONLY);
	fdout = open ("output.txt", O_WRONLY|O_APPEND|O_CREAT, S_IRWXU);
	
		bytes_read = read (fdin, buffer, 5000);
		write(fdout, buffer, value);

	close(fdin);
	close(fdout);
}

---

### Post by bobbocanfly on 2007-09-19
Dont know if it is the problem (you havent actually told us the problem/compiler output) but you should probably stick a return 0; at the end of your main()

---

### Post by Arwen on 2007-09-19
It gives &#8216;bytes_read&#8217; undeclared (first use in this function)'.What type of variable does "read" return?

---

### Post by Arwen on 2007-09-19
return 0 is only in c++ when main is : int main(){}
in c main is void,doesn't return anything..

---

### Post by raul_ on 2007-09-19
Isn't it fopen instead of open?

---

### Post by Arwen on 2007-09-19
OK bytes_read is int.at least it's compiled without errors.What's your problem now?

---

### Post by LaRoza on 2007-09-19
> **raul_ said:**
> Isn't it fopen instead of open?

There are two, open is a low level and fopen is high level.

---

### Post by LaRoza on 2007-09-19
> **Arwen said:**
> return 0 is only in c++ when main is : int main(){}
in c main is void,doesn't return anything..

In C, main() can be int also, and should be, as far as I know.

Compile with gcc:

[php]
#include <stdio.h>
int main(int args,char ** argv)
{
    puts("I am a C Program\n");
    return 0;
}
[/php]

---

### Post by Arwen on 2007-09-19
Is there any chance you need sth of these?->[http://www.thinkage.ca/english/gcos/expl/c/lib/fopen.html](http://www.thinkage.ca/english/gcos/expl/c/lib/fopen.html)
[http://irc.essex.ac.uk/www.iota-six.co.uk/c/i1_file_input_and_output.asp](http://irc.essex.ac.uk/www.iota-six.co.uk/c/i1_file_input_and_output.asp)

I mean sth like:
fdin = fopen ("input.txt", "r");
fdout = fopen ("output.txt", "wr");

---

### Post by Arwen on 2007-09-19
This works for me(if it's what you want,you can check the option for creating a not existing output file in the link I gave you)

> #include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>

main()
{
int fdin, fdout, value,bytes_read;
char buffer[5000];
char c;
fdin = fopen ("input.txt", "r");
fdout = fopen ("output.txt", "wr");

 
    while(1) {     /* keep looping... */
      c = fgetc(fdin);
      if(c!=EOF) {
        printf("%c", c); 
	//fprintf(fdout, buffer, value);
	fprintf( fdout, "%c", c );


 
        /* print the file one character at a time */
      }
      else {
        break;     /* ...break when EOF is reached */
      }
}


//bytes_read = read (fdin, buffer, 5000);
//write(fdout, buffer, value);

close(fdin);
close(fdout);
}

---

### Post by azroule on 2007-09-19
> **LaRoza said:**
> In C, main() can be int also, and should be, as far as I know.

Compile with gcc:

[php]
#include <stdio.h>
int main(int args,char ** argv)
{
    puts("I am a C Program\n");
    return 0;
}
[/php]

yeah i read bout that argc and argv before but duno how does it function and what it did.do i need to put it in this program?

---

### Post by hod139 on 2007-09-19
> **Arwen said:**
> 
in c main is void,doesn't return anything..
This is only true for older C standards.  According to the C99 standard main must return an int, just like C++.  Even for the older code, it is good practice to have main return an int.

---

### Post by LaRoza on 2007-09-19
> **azroule said:**
> yeah i read bout that argc and argv before but duno how does it function and what it did.do i need to put it in this program?

You don't need it.

argc is an integer that is the number of command line arguments, the command itself counts.

argv is an array of strings, in C, an array of null-terminated character arrays.

Example:
[php]
#include <stdio.h>

int main(int argc,char ** argv)
{
    int i;
    for (i = 0; i != argc; i++)
    {
        printf("Argument %i is %s\n",i,argv[i]);
    }
    return 0;
}[/php]

Compile and run. If you type words after running it, the program will list them,

---

