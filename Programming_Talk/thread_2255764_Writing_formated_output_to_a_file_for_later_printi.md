---
title: "Writing formated output to a file for later printing in C99 - error checking?"
date: 2014-12-07
forum: Programming Talk
---

### Post by pauls2 on 2014-12-07
I am coding under the constraints of C99 using Geany and Ubuntu14.04.1.
I wrote a function to save formated text to a file so the information could be printed from a word processor if needed.
I don't have an error checking routine in that part of the code so if a path that doesn't exist is used in the filespec the program crashes.
Here is the code as it stands:
```

int saveprnfile(void)
{ // saves formatted output to a text file to be printed
    FILE *fptr;
    char *filename = "filename"; // this is just a title used by input
    char filespec[79]; // this will hold the filespec
    input(filename,79); // get path and file name
    strcpy(filespec, lin); // copy path and file name to 'filespec'
    lin[0] = '\0';
    fptr = fopen(filespec, "a"); // I have to append the lines into the file to maintain the formatting
    fprintf(fptr,"\t\t\t%s\n\n",filespec); // write the path and file name to the top of the file
    fprintf(fptr,"Header Design Suite\n");
    fprintf(fptr,"Open Source Software\n\n\n");
    fprintf(fptr,"\n\n======= Header Design Suite Input =======\n\n"); // list user input
    fprintf(fptr," Bore __________________ %2.3f\n", info.bore);
    fprintf(fptr," Stroke ________________ %1.3f\n", info.stroke);
    fprintf(fptr," Comp __________________ %2.1f to 1\n", info.compratio);
    fprintf(fptr," RPM ___________________ %4.1f\n", info.maxrpm);
    fprintf(fptr," Exhaust valve opens ___ %3.1f before BDC\n\n", info.exhaustopens);
    fprintf(fptr,"==========================================\n\n");
    fprintf(fptr,"======= Header Design Suite Output =======\n"); // list program output
    fprintf(fptr,"\n\nHeader: Four single primary tubes into common collector\n\n");
    fprintf(fptr,"-------------------------------------------------------\n\n");
    fprintf(fptr," Primary tube inside diameter: _ %1.3f\n\n", info.primarydia);
    fprintf(fptr," Primary tube length: __________ %2.1f\n\n", info.primarylength);     
    fprintf(fptr," Collector diameter: ___________ %1.3f\n\n", info.collectordia);
    fprintf(fptr," Collector length ______________ %2.3f\n\n\n", info.collectorlength);
    fclose(fptr);
    return(0);
}

```

I am looking for a way to either write the path if it doesn't exist or alert the user that the path doesn't exist and let them try again.

---

### Post by pauls2 on 2014-12-07
Well, when I pasted the code it lost the indenting and put a space into my line of '=' marks. But all the code is there.

I guess it helps if I use the correct slash to close the code --- sorry.

---

### Post by ofnuts on 2014-12-07
The path or the file? If the file isn't there it shouldn't be a problem. if the specific parent directory doesn't exist it's a different problem. However if fopen() fail to open/create the file for any reason (file exists and is write-protected...), then fptr is going to be NULL and you can test for this. When this happens you can check [errno](http://linux.die.net/man/3/errno) to get the specific error code, or just use [perror()](http://linux.die.net/man/3/perror) to print the relevant error message.

However, this kind of check should be done early in the program.... assume the user cannot do anything to fix the situation *now*. Are you going to loop endlessly? or abort and lose the results?

---

### Post by pauls2 on 2014-12-08
I plan to give the user the opportunity to use a different filespec or file name or to bag it and leave the function without saving the file.

In the research I have done to date it seams that C99 does not allow me to check the path at all and since the file is written by appending lines to it the only way it would not write is if the target file is read only or protected in some other way through permissions. So, I need to check to see if the file name is in use within the target directory by opening the file to read. If it does exist then I can let the user rename the file before continuing. If fopen returns NULL then it could mean that the path is not there or that the file doesn't exist. If the subsequent write operation fails then I think it is safe to say that the path probably doesn't exist. I will look through the logic on paper to see if I can make it work.

This seems to be a limitation of C99. As usual I am trying to swim up the waterfall. It is a great learning experience for this 64 year old. I am not used to limitations that are not self initiated so it is keeping me humble.
errno will return a -1 or NULL but I have no idea under what circumstances it will return -1. 
perror() is a "depreciated" function so it may not be around in the next incarnation of ANSI C. I try to avoid things that are likely to become obsolete. I will do some studying on errno() and fopen() to see what I can learn from them.

Thank you ,ofnuts, for the time you invested in helping me. I sometimes feel quite inadequate in my coding and knowing where to look and what I need to learn is a big plus.

---

### Post by SagaciousKJB on 2014-12-08
Have you considered fstat()?  It's not C99 but it's POSIX

---

### Post by pauls2 on 2014-12-08
> **SagaciousKJB said:**
> Have you considered fstat()?  It's not C99 but it's POSIX

There are a lot of ways to do what I would like to do if I were willing to step outside the bounds of C99. I have decided to limit my software to the C99 constraints.
I will find a way to limit the damage that results from a user using a nonexistant path or a file that already exits. It exercises my creativity to have to work around these challenges.

I thank you, SagaciousKGB, for the suggestion - in another world I might have not known the alternatives. I know some of them and choose to stay within the limits.

---

### Post by ofnuts on 2014-12-09
> **pauls2 said:**
> I plan to give the user the opportunity to use a different filespec or file name or to bag it and leave the function without saving the file.

In the research I have done to date it seams that C99 does not allow me to check the path at all and since the file is written by appending lines to it the only way it would not write is if the target file is read only or protected in some other way through permissions. So, I need to check to see if the file name is in use within the target directory by opening the file to read. If it does exist then I can let the user rename the file before continuing. If fopen returns NULL then it could mean that the path is not there or that the file doesn't exist. If the subsequent write operation fails then I think it is safe to say that the path probably doesn't exist. I will look through the logic on paper to see if I can make it work.

This seems to be a limitation of C99. As usual I am trying to swim up the waterfall. It is a great learning experience for this 64 year old. I am not used to limitations that are not self initiated so it is keeping me humble.
errno will return a -1 or NULL but I have no idea under what circumstances it will return -1. 
perror() is a "depreciated" function so it may not be around in the next incarnation of ANSI C. I try to avoid things that are likely to become obsolete. I will do some studying on errno() and fopen() to see what I can learn from them.

Thank you ,ofnuts, for the time you invested in helping me. I sometimes feel quite inadequate in my coding and knowing where to look and what I need to learn is a big plus.
Staying within C99 is a waste of your time because all compilers used to write applications for general computers implement the standard Linux library to some extent. Opening the file for read doesn't tell you much, in particular it won't tell you if you can write to it. If you don't want to use stat() then just open the file for write and check that you got a non-null file pointer.

---

### Post by SagaciousKJB on 2014-12-09
I'm pretty sure that once you try to open a file in a directory that's not there and it sets the file pointer to NULL, that errno will then have the appropriate "File does not exist" error code set.

I wouldn't worry too much about perror() being deprecated if you're wanting to stick to C99.  It's not likely to be taken out of the library any sooner than C99 would be.

Edit:

Actually paul, via man 3 perror, I don't see where it's desginated deprecated, and it is C99 compliant.  I would use it, it's pretty good for printing error messages.

Edit:

Here is how I would approach this

```
kenny@laptop:~$ ls ./real_directory ./nonreal_directory
ls: cannot access ./nonreal_directory: No such file or directory
./real_directory:
emptyfile  nonemptyfile
kenny@laptop:~$ cat ./test.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
	FILE *file;
	char *s = malloc(sizeof(char) * 79);
	int c;
	strcpy(s,argv[1]);

	while(1)
	{
		file = fopen(s,"a");
		if(file == NULL)
		{
			perror(s);
			printf("\n");
			printf("Please specify another file, the system can't resolve that path: ");
		}
		else
			break;
		fgets(s,79,stdin);
		s[strlen(s) - 1] = '\0';
		
	}
	printf("%ld", ftell(file));
	fclose(file);

	printf("\n");
	return 0;
}
kenny@laptop:~$
```

So you see I have a "real_directory" and a "non_realdirectory".  As ls shows one is real, the other doesn't exist.  Inside the real directory, there is an empty file and a non-empty file...

Here is how that works out in usage...

```
kenny@laptop:~$ ./test ./nonreal_directory/emptyfile
./nonreal_directory/emptyfile: No such file or directory

Please specify another file, the system can't resolve that path: ./real_directory/emptyfile
0
kenny@laptop:~$ ./test ./nonreal_directory/nonemptyfile
./nonreal_directory/nonemptyfile: No such file or directory

Please specify another file, the system can't resolve that path: ./real_directory/nonemptyfile
23
kenny@laptop:~$ ./test ./real_directory
./real_directory: Is a directory

Please specify another file, the system can't resolve that path: ./real_directory/totallynotrealfilethatodesnotexist
0
kenny@laptop:~$ ls -lah ./real_directory/
total 32K
drwxrwxr-x  2 kenny kenny 4.0K Dec  9 19:21 .
drwxr-xr-x 60 kenny kenny  24K Dec  9 19:15 ..
-rw-rw-r--  1 kenny kenny    0 Dec  9 19:14 emptyfile
-rw-rw-r--  1 kenny kenny   23 Dec  9 19:16 nonemptyfile
-rw-rw-r--  1 kenny kenny    0 Dec  9 19:21 totallynotrealfilethatodesnotexist
kenny@laptop:~$
```

Remember before that ./real_directory only had the two empty and nonemptyfiles in it.  The "totallynotrealfilethatdoesnotexist" was created by fopen with the append mode, but its filesize was still displayed as zero.

Using the file size is a reasonably foolproof way to test if the file is actually THERE or if the system simply created it by the fopen with append mode.  If the file is zero, it likely isn't "real" and even if it was, there was nothing there to overwrite anyway so it's relatively safe to then write to that.  If it was a lock file or something important like that, then as you assumed earlier it should have proper write permissions and errno/perror will detect this as well.

```
kenny@laptop:~$ cd ./real_directory/
kenny@laptop:~/real_directory$ chmod a-w ./emptyfile
kenny@laptop:~/real_directory$ ls -lah ./emptyfile 
-r--r--r-- 1 kenny kenny 0 Dec  9 19:14 ./emptyfile
kenny@laptop:~/real_directory$ cd
kenny@laptop:~$ ./test ./real_directory/emptyfile
./real_directory/emptyfile: Permission denied

Please specify another file, the system can't resolve that path: ^C
kenny@laptop:~$ 
```

So with a little bit of thought using ftell() you can check if the file is NOT EMPTY, and avoid altering it if so.

I just use perror() but I would assume that you could then check the relevant errno codes and be able to handle it silently or with more friendly language.  That's all perror really does anyway, is print the error codes into human readable form.  In your case you can make it more specific to your code instead of just vauge "permission denied"--you can provide more information such as, "That file was write protected," or something more user-friendly like that.

I understand where you're coming from about wanting to stick to C99 for the challenge.  It's kind of like using a bow or a black powder rifle to hunt versus a modern firearm.  There's an art and a reward all on its own.

---

### Post by pauls2 on 2014-12-11
I need to spend some timewith the code I have been given, the man pages, and test writing some code to see how I will implement this into my program.

I am learning a lot from this one problem and all the help I am getting.

Thanks for the encouragement and the homework SagaciousKGB.

---

### Post by SagaciousKJB on 2014-12-13
> **pauls2 said:**
> I need to spend some timewith the code I have been given, the man pages, and test writing some code to see how I will implement this into my program.

I am learning a lot from this one problem and all the help I am getting.

Thanks for the encouragement and the homework SagaciousKGB.

Your welcome.  I use similar logic with a "doesFileExist" function, but instead I use fstat()--that way I don't have to open the file at all.  But you could do the same with ftell(), just have the function return the filsize.  Then you can test in conditionals...

```
if(doesFileExist)
``` true if filesize is nonzero
```
if(!doesFileExist)
``` false if filesize is 0

But with ftell() you need to mind if it returns -1 so I would use longhand conditionals.

---

### Post by ofnuts on 2014-12-14
> **SagaciousKJB said:**
> Your welcome.  I use similar logic with a "doesFileExist" function, but instead I use fstat()--that way I don't have to open the file at all.  But you could do the same with ftell(), just have the function return the filsize.  Then you can test in conditionals...

```
if(doesFileExist)
``` true if filesize is nonzero
```
if(!doesFileExist)
``` false if filesize is 0

But with ftell() you need to mind if it returns -1 so I would use longhand conditionals.

You can't really distinguish between an empty file and a non-existing file that way... (and there are cases where this would be important)

---

### Post by SagaciousKJB on 2014-12-14
> **ofnuts said:**
> You can't really distinguish between an empty file and a non-existing file that way... (and there are cases where this would be important)

I already adressed that.

---

