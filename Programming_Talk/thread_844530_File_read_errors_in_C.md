---
title: "File read errors in C"
date: 2008-06-29
forum: Programming Talk
---

### Post by crashovaride on 2008-06-29
Hello All,

I'm working with a function which will read 2 files and redirect them to another folder location. The first portion works fine. And, i'm racking out my brain to fix this issue. 

I have changed the buffer size from 256 to 1024 all the way up to 3072. I have even defined new file information using FILE *s; and so on. I have even gone as far as to use fflush(f); fflush(s); fclose(f); and fclose(readfile); nothing works. It gets to a certain section of my text file and it bombs. I have included the code below as to what is going on. I have even made an external .h file thinking it will bomb there. However, i will also state the following in the comments; when i use the fclose(f); code and fclose(readfile); codes it bombs before opening the second file. When i don't use it. It bombs while reading the second file. Here is my code:

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
#include <string.h>
#include <assert.h>
#include <dirent.h>

	FILE *readfile;
	FILE *f;
	char buffer[255];

int main()
{
	    DIR *dir;
	    struct dirent *lister;

	printf("Checking for the presence of the file:............ ");
	char ffloc[1024] = {0};
	snprintf(ffloc, sizeof(ffloc), "%s/%s", getenv("HOME"), "start.txt");
	if (access(ffloc, F_OK) == 0)
		{
			printf("[ \33[1;32mOK\33[0m ]\n");
			printf("Starting redirects for file data.\n");

//FOLDER SCAN AND DUMP
	char keydb [1024] = {0};
	char fileget [1024] = {0};
	char folder_data [1024] = {0};
	char fileget2_dump[1024] = {0};
	snprintf(folder_data, sizeof(folder_data), "%s/%s", getenv("HOME"), "/newfolder/");
	snprintf(fileget2_dump, sizeof(fileget2_dump), "%s%s", getenv("HOME"), "/newfolder/fileget2.txt");
	    dir=opendir(folder_data); /* open the / directory*/
	    assert(dir != NULL); /* id dir is null assertaion error will occurred and program terminates*/
	    
	    while((lister=readdir(dir))!=NULL)
	    {
				if (strstr(lister->d_name, "newfolder"))
				{
					snprintf(keydb, sizeof(keydb), "%s/%s/%s/%s", getenv("HOME"), "newfolder/", lister->d_name, "database.txt");
					snprintf(fileget, sizeof(fileget), "%s/%s/%s/%s", getenv("HOME"), "newfolder/", lister->d_name, "fileget2.txt");
					printf("reading database.txt: %s\n", keydb);
					printf("reading fileget2.txt: %s\n", fileget);
					printf("Currently printing database.txt data. Please Wait.\n");
					FILE *f;
					readfile = fopen(keydb, "r");
						while (!feof(readfile))
						{
						if (readfile != NULL)
						{
						}

						char keydb_dump[1024] = {0};
							snprintf(keydb_dump, sizeof(keydb_dump), "%s%s", getenv("HOME"), "/database.db");
						f = fopen(keydb_dump, "a+");
							fgets(buffer, 256, readfile);
								fprintf(f, "%s", buffer);
						}
					printf("The database has been successfully exported. Proceeding to fileget2.txt\n");
				}
	    }
	    /*	HERE IS WHERE AS YOU CAN SEE THE fclose(f); etc, HAS BEEN COMMENTED OUT. WITHOUT THAT STATEMENT
	    	I CAN RUN THE APPLICATION UNTIL IT GETS TO THE fileget2_dump WHERE IT BOMBS OUT ON ME WITH SEGMENT FAULT
	    	AM I MISSING SOMETHING OR SHOULD THIS REALLY WORK? PLEASE LET ME KNOW I WOULD LIKE A SECOND OPINION HERE.
	    */
//	    fclose(f);
//	    fclose(readfile);
	    fflush(f);
	    fflush(readfile);
	    	    //BEGIN THE EXPORTATION FOR fileget2.TXT FILE

					readfile = fopen(fileget, "r");
						while (!feof(readfile))
						{
						if (readfile != NULL)
						{
						}

					f = fopen(fileget2_dump, "a+");
							fgets(buffer, 4096, readfile);
								fprintf(f, "%s", buffer);
								printf("Data: %s%s\n", buffer, f);
						}
					printf("The information from fileget2.txt has been exported.\n");

		}
		else
		{
			printf("[ FAILED ]\n");
			printf("The database is not currently installed.\n");
			printf("The read function has run successfully. Quitting.\n");
		}
	return 0;
}	
[/PHP]

Any suggestions? Even pointing me in the right direction. I have come this far, and i don't want to quit here for an oversight. Thank you in advanced. 

Kindest Regards.

---

### Post by Tony Flury on 2008-06-30
just a thought but 

you declare : 

```

char buffer[255] ;

```

but then when trying to move the 2nd file - you use
```

fgets(buffer, 4096, readfile); 

```

I would have thought that trying to read 4096 bytes into a 255 buffer will fail every time.

I would advise you to not use "magic numbers" in your code - it is far too easy to change one - and forget the other one. I would use something like : 

```

#define BFR_SIZE 255

char buffer[ BFR_SIZE ] ;
...
...
fgets( buffer, BFR_SIZE, readfile) ; 

```
and make sure you use BFR_SIZE everywhere you need the buffer size.

---

### Post by Amit Yaron on 2008-06-30
Did you notice you've declared "FILE *f" twice? Once as a global variable, and once inside an 'if' statement?

The file defined in the 'if' statement you open, while the one you flush  is the global one.

---

### Post by crashovaride on 2008-06-30
Ah, i see what you mean, Tony. However, i've been playing with the code using the 255 all along. However, when i was messing with the code; i was using different numbers to see if the problem was an error with the buffer. As, when it gets to a certain point in the file, it tends to bomb out.

I tried to use different approaches with the fflush, fclose, etc. And, i can't seem to solve the problem. I'm still uncertain as to what Amit wrote when he said "Did you notice you've declared "FILE *f" twice? Once as a global variable, and once inside an 'if' statement?" What exactly does that mean? I'm new to the world of C as a second programming language. 

I will try the suggested pointers. And, i'll see if that helps. Thanks for the assistance. 

Kindest Regards.

---

### Post by crashovaride on 2008-06-30
Tony, 

I've tried to use the suggested code you posted, however it's not compiling. I tried for 30 minutes to get it to work, and to no avail. Any suggestions?

Kindest Regards

---

### Post by dwhitney67 on 2008-06-30
If I were you, I would take a step back.  Restart your code development all over again, without referring to the rambling mess you have now.  Think in terms of modularizing your code.

Try to organize your code in which the variables are defined closest to the point where they are first used.  Initialize your variables as needed.  For instance:
[PHP]FILE *fp;
fp = fopen(...);[/PHP]
should be changed to:
[PHP]FILE *fp = fopen(...);[/PHP]
You can verify if a file was successfully opened by checking the file pointer returned by fopen().  Also, do not rely on feof() unless you fully understand how/when it reports an EOF-condition.  I recommend something like:
[PHP]FILE *fp = fopen("inputFile.txt", "r");
if (fp)
{
  char buf[256] = {0};

  while (fgets(buf, sizeof(buf), fp))
  {
    // do something with data in buf
  }
}[/PHP]
Also, for your application, I do not see the need need to stat a file for existence, as you did in the beginning of the main() function.

The issue concerning buffer sizes and using them appropriately is important.  Either declare constants to indicate sizes, or rely on the sizeof() function to get the size of a buffer.

Lastly, keep your indentation levels correct.  Personally, I think using tabs suck.  Use 2 or 3 white-spaces when indenting.

---

### Post by Tony Flury on 2008-06-30
> **crashovaride said:**
> Tony, 

I've tried to use the suggested code you posted, however it's not compiling. I tried for 30 minutes to get it to work, and to no avail. Any suggestions?

Kindest Regards

What error messages did you get ?

---

### Post by crashovaride on 2008-06-30
Tony,

Now that it's been determined that there is a loose nut behind the keyboard [me, and i just suffered an ID10-T error]. It works with what you suggested, and i've placed everything back to 255 and i'm still bombing in a certain section of the file.

I even went as far as to measure the characterization maybe that had something to do with it, but it bombs in exactly the same spot all the time. Right here on this section:

The length is : 29
Extracting: login_user_dbname

The length is : 18
Segmentation fault (core dumped)

Even if i put them in separate .h files. It will do the same thing. Yet, when i compile this program on it's own external it works... It's got me losing more hair! lol. I don't know if i should make each section it's own .o file, and make a shell script execute each one in an ordered fashion? Any suggestions? I'm up for anything at this point. 

dwhitney67, it's not a rambling mess. It's a rambling catastrophe. =] And, i'm trying to fix my spaghetti code. -- I do think you have helped me before. You know your [censored]. However, i'm considering breaking it down into external .h files as said. This code is raging on and on. Not what i want. Thanks all.

Kindest Regards.

---

### Post by Tony Flury on 2008-06-30
> **crashovaride said:**
> Tony,
I even went as far as to measure the characterization maybe that had something to do with it, but it bombs in exactly the same spot all the time. Right here on this section:

The length is : 29
Extracting: login_user_dbname

The length is : 18
Segmentation fault (core dumped)

Even if i put them in separate .h files. 


What do you mean - seperate .h files ? I always think it is a bad idea to have executable code in an .h file (unless you are defining a C++ template).

> 
It will do the same thing. 

Yet, when i compile this program on it's own external it works... It's got me losing more hair! 

Compile it on its own external ?? what do you mean ?

> 
lol. I don't know if i should make each section it's own .o file, and make a shell script execute each one in an ordered fashion? Any suggestions? I'm up for anything at this point. 

I think you are getting very confused ... a .o file is not executable - a .o file is an object file - and you then link one or more .o files together to make an executable.

> 
dwhitney67, it's not a rambling mess. It's a rambling catastrophe. =] And, i'm trying to fix my spaghetti code. -- I do think you have helped me before. You know your [censored]. However, i'm considering breaking it down into external .h files as said. This code is raging on and on. Not what i want. Thanks all.

Kindest Regards.

There will be a reason your code segmentation faults - likely candidates are : 
overflowing buffers
using data not initialized

---

### Post by crashovaride on 2008-06-30
Tony,

Separate .h files i use when projects span more than one section at a time. For instance read_database.h write_database.h, etc. 

When i compile one section (the one that fails in its own .c project) some magical reason it works properly. 

When i compile C programs to test them i normally run gcc file.c -o file.o this is just how i was taught to compile executable code. So, making a configuration file do the compiler jargon and then executing the .o files in an orderly manor. 

I'm sorry if i'm throwing you off.

---

### Post by Tony Flury on 2008-06-30
ok - i think i understand what you mean.

right - why not put each part of your code into a seperate function - and make sure you understand the scope of your declarations.

also the fact that the code is failing on the 2nd file - i would look to that part first.

Just had a thought - the fact that the 2nd part works in its own program - but not when part of the whole, suggests maybe that you have a problem with the scope of your variables.

an example (that someone else alluded too) :
```

#include <stdio>

int a = 3, x = 3 ; 

main() 
{
    printf("%d,%d\n", a, x) ;  // a = 5, x = 3
    if (a == 5)
    {
        int a = 7 ; 
        printf("%d,%d\n",a) ; // a = 7, x = 3
    }

    printf("%d,%d\n", a, x) ;  // a = 5, x = 3
}

```

I hope that this make sense. 

I think it was suggested that you have two definitions of "FILE *f ;", one that is global, and one that is local to a code block. You need to make sure that you are using what you expecting to, especially if one of them is initialised and another isn't.

---

### Post by crashovaride on 2008-06-30
tony, 

Here is the kicker now. When i put them in their own .h files and compile it gets to the same part and bombs again. I'm not sure what to make of one is global, and one is called inside a function. What does that mean? Programming resources suck when your a beginner. And, there aren't many good places to get direction from. 

Do you mean declare each use once in the int function() property as FILE *f;? Or, declare it in the intro before main?#-o This is making my head spin. But, i have to bite the bullet and learn this stuff. I can't be in an OS without knowing how to program. I feel like i'm in a car with no wheels!

i hope no one feels that i want someone else to do my work. I want to understand why this is not working. I need to see where so i can learn and understand. Please don't interpret this in any other manor. 

Thanks.

---

### Post by dwhitney67 on 2008-06-30
I suggest you start from the beginning.... What are your requirements?  That is, what are you attempting to accomplish?  Don't answer with code... just words.

If you specify correctly the requirements you are trying to solve, I can assist you with ideas for the design.  The implementation (that is the coding) is a mere trivial task, since it is obvious that you are familiar with the C language syntax.

---

### Post by crashovaride on 2008-06-30
Well, what i'm trying to do is 1) locate files to see if they exist (records) if they do exist, read them and redirect the output of the files. 2) Once the records are redirected; use a function to tar.gz them and then 3) open an ssh session and place them remotely. Once that is finished go back in and 4) clean the system. then close the program. Sounds simple for some; yet it's complex for me as i'm just in the beginning stages of programming in C for Linux. I would LOVE to see some tutorials however no tutorials really get to the point and all i see is for micro$hit.

I do appreciate the help though. Thanks in advanced.

---

### Post by dwhitney67 on 2008-07-01
> **crashovaride said:**
> Well, what i'm trying to do is 1) locate files to see if they exist (records) if they do exist, read them and redirect the output of the files. 2) Once the records are redirected; use a function to tar.gz them and then 3) open an ssh session and place them remotely. Once that is finished go back in and 4) clean the system. then close the program. Sounds simple for some; yet it's complex for me as i'm just in the beginning stages of programming in C for Linux. I would LOVE to see some tutorials however no tutorials really get to the point and all i see is for micro$hit.

I do appreciate the help though. Thanks in advanced.
It seems that you want to write an application to perform a specialized task; very doubtful that there would be any books/tutorials to guide you to a solution.  Thus you must rely on yourself to come up with a solution.

So, let's decompose your requirements a little further.  With respect to number 1 above, it would be necessary to know a) what files are of interest, and b) where are these files located (folder name), and lastly c) where is the content of each of these files to be stored?

Also, please clarify something... you stated above that you want to read the contents of each file of interest, and place what is read into a single (?) output file.  Ok, it seems easy enough.  Then you want to tar/compress this single output file.  Is this correct?

---

### Post by lisati on 2008-07-01
> **crashovaride said:**
> . I'm still uncertain as to what Amit wrote when he said "Did you notice you've declared "FILE *f" twice? Once as a global variable, and once inside an 'if' statement?" What exactly does that mean? .
Near the start of your code, you have FILE *f, which "declares" a file variable. Later on, after the "Printing database, please wait" message, you have it again. If you're just beginning C, it's generally safer to avoid having duplicate definitions....

---

### Post by crashovaride on 2008-07-01
dwhitney67,

The files will be located in the users home. I have the getenv("HOME") variable already set and working. The files are a listing of addresses, that the user sets, and the second file is a list of passwords the user also sets (believe me, stupid program -- however, i have to learn somewhere.) What the application will do is read those data files from a folder (given i'll state the folder name hypothetically as /home/someone/newfolder the folder will NEVER change, it's a static program it's paths are already laid out and that's what the users have to work with). 

The content of the files will be stored outside of the /home/user_name$/newfolder folder. So, in essence it will be dragged (or redirected) from newfolder to /home/user_name$/file1.txt and file2.txt

Each file read, would have it's own file with the original file name intact. However, moved from one folder to the next (back one). Once this is finished, i can use the system("tar -cf data.tar file1.txt file2.txt"); and system("gzip -9 data.tar"); commands to compress them. The ssh functions, ha. That's going to have to be done up in a C book of Network Programming. I'm already trying to make sense of the read file problems that i'm having now. And, i have 2 books "Beginning C from novice to professional" and "C in a nutshell." Not to mention the K&R Book.

Lisati,

I have changed what you suggested; and it didn't help. However i will remember that for the next time when i do design another program that once i declare something never to declare it again. 

Also, could this be that i'm not clearing the values of buffer, or readfile to 0 (NULL) before starting a new read? And, if so isn't that what fflush(f); fflush(readfile); and fclose(f); fclose(readfile); do? Or, am i totally off? God, i seriously feel useless without being able to program! This is frustrating. 

As always, thank you for the prompt replies. I really do appreciate the help you ladies and gents are providing me.

Thanks.

---

