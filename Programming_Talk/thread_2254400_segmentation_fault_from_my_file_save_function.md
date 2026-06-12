---
title: "segmentation fault from my file save function"
date: 2014-11-26
forum: Programming Talk
---

### Post by pauls2 on 2014-11-26
The function works well if the file doesn't exist and when I choose to overwrite an existing file.
When I try to rename a file the program closes with a segmentation fault code of 139.
I believe that the call to "fptr = fopen" the second time (first repeat loop) is the cause.
I have the "fclose" commented out in the case statement but I get the same fault whether it is commented out or active.

Here is the function as it is now:
```

int savfil(void)
{
    FILE *fptr;
    int x;
    char ch;
    char *filename = "filename";
    char filespec[79];
    do
    {
        x = 2;
        input(filename, 79); // get the path and filename
        strcpy(filespec, lin); // copy the entered path and filename
        lin[0] = '\0';
        clearscreen();
        printf("\t\n\n checking copy of %s on disk\n\n\n", filespec);
        fptr = fopen(filespec, "r");
        if(fptr != NULL) // there is a file
        {
            printf("file already exists; Rename your file or Overwrite?");
            printf("\n\nEnter R to rename or O to overwrite");
            ch = getchar();
            switch(ch)
            {
                case 'R':
                case 'r':
                x = 1;
                //fclose(fptr);
                break;
                case 'O':
                case 'o':
                x = 2;
                break;
            }
        }
    }
    while(x == 1);
    // fclose(fptr);
    fptr = fopen(filespec, "w"); // open the write pointer
    fwrite(&all, sizeof(all), 1, fptr); // write the file
    fclose(fptr); // close the pointer because we are done
    return 0;
}

```

I am attempting to check to see if a file exists using fopen(filespec,"r") so I can warn the user that there is already a file by that name in that location and offer a chance to rename the file to be saved or overwrite the file with new data.
The save function works fine if I save a file with a distinct name and when I choose to overwrite the file. I only get errors when I try to rename the file.

Can anyone point out how I can fix this?
This old man is working on a stroke over this... :(

Thank you for your time,
Paul

---

### Post by lisati on 2014-11-26
Please don't get a stroke over this, it's not worth it.... (Mrs Lisati experienced a stroke back in 2011)

My first thought is to check the space you've allowed for the file name. If you're intending to have a maximum length of 79 characters for the file name, it's probably best to allow at least 80 characters for the areas you're using to store it. This allows an extra byte for a terminating 0x00 character, and helps avoid the risk of accidentally overwriting something important if someone enters too many characters.

On a side note, if I've understood your code correctly, you're defaulting to "overwrite" if the user enters something other than O or R.

---

### Post by pauls2 on 2014-11-26
The space allotted for the filespec is 79 but the input function asks for the spec in 77 characters. 

Yes if something other than O or R is provided the program will overwrite the file by default.

I believe that after going through the loop and back the second call to "fptr = fopen(filespec, "r") " is where my problem is. I used print statements to localize the source of the error and it dies after the printf() statements just before the call to fopen. The loop is only used when trying to rename the file so it has to be in the loop. The filespec is reworked in the loop but it is not added to, it is rewritten each time so there is no memory overflow there. 

How many times can the fopen function be called before it needs to be closed? 

Is there a more elegant way to check for the existance of a file in ANSI C and allow renaming than what I am doing? 

I should confess that I have tried "if" statements, with and without loops but nothing worked as well as this one does. It will at least save a file with a distinct file name and overwrite an existing file.
I just need it to allow me to change the file name and recheck for an existing file and then save it.

---

### Post by lisati on 2014-11-26
This line worries me:
```
char *filename = "filename";
```
Unless I'm mistaken, this only allows for 8 characters in the file name.

---

### Post by pauls2 on 2014-11-26
The string literal is sent to the input function as part of the prompt - that is its only use.
here is the input() function:
```

int input(char *titl, int length)
{
    char buf[length]; // set the length of input
    buf[0] = '\0'; // initialize buf to an empty string
    char *p; // pointer to position in buf
    lin[0] = '\0'; // erase any string in lin
    // place prompt
    printf ("Enter %s in less than %d characters ",titl, length-2);
    if (fgets(buf, length, stdin) != NULL) // get the input
    {
     // test for and remove newline 
     if ((p = strchr(buf, '\n')) != NULL)
        {
           *p = '\0';
        }
      //  printf ("\n\n%s is %s \n", titl, buf);
    }
    strcpy(lin, buf); // copy input to global 'lin'
    return 0;

```

It takes the "title" and the length of the string to be returned. The "filename is just the title that is sent to the input function.

---

### Post by lisati on 2014-11-26
> **pauls2 said:**
> 
It takes the "title" and the length of the string to be returned. The "filename is just the title that is sent to the input function.
Oh, my bad.......

---

### Post by pauls2 on 2014-11-26
With well over 1800 lines of code I didn't want to post the entire program - I was affraid it would scare people off. :)

---

### Post by lisati on 2014-11-27
> **pauls2 said:**
> With well over 1800 lines of code I didn't want to post the entire program - I was affraid it would scare people off. :)

Don't worry about it. 

AFAIK a segmentation fault can be a symptom of a rogue pointer and/or something getting overwritten accidentally. Unfortunately I don't do much programming these days, so my troubleshooting skills are a little rusty.....

---

### Post by ofnuts on 2014-11-27
TL;DR....

Overly complicated logic to check for file existence....

Correct solution: use the stat() function for this. It will also allow you to check that the file is writable.. No more issue with the file opened.

Or re-using your technique: make sure that the file descriptor you use is only used for this and doesn't last long:
```

fptrcheck = fopen(filespec, "r");         
int file_exists=fptr != NULL;
if (file_exists) fclose(fptrcheck);
// from here everything is clean...

if (file_exists) {
....

```

---

### Post by SagaciousKJB on 2014-11-27
I debugged your program in gdb.  What I saw happen is that when you set x to 1, your program loops back to the contents in "do", setting x to 2.  Then when you call the input() function again, for whatever reason I still haven't figured out, neither the prompt in your printf() statement nor the fgets line executes.  Then when yous trip the '\n' from buf you're essentially setting it to nothing at all.  The program continues to try to write content to the filename copied into lin, but since it was blanked out it causes fwrite to segfault.

```
(gdb) r
Starting program: /home/kenny/testfile 

Breakpoint 1, input (titl=0x400b20 "filename", length=79) at testfile.c:57
(gdb) s
(gdb) 
(gdb) 
(gdb) 
(gdb) 
(gdb) 
Enter filename in less than 77 characters filename1
(gdb) advance 74
input (titl=0x400b20 "filename", length=79) at testfile.c:74
(gdb) s
(gdb) 
savfil () at testfile.c:23
(gdb) s
(gdb) 
(gdb) 
	

 checking copy of filename1 on disk


(gdb) 
(gdb) 
(gdb) display fptr
1: fptr = (FILE *) 0x403010
(gdb) s
1: fptr = (FILE *) 0x403010
(gdb) 
file already exists; Rename your file or Overwrite?

1: fptr = (FILE *) 0x403010
(gdb) s
Enter R to rename or O to overwriteR
1: fptr = (FILE *) 0x403010
(gdb) s
1: fptr = (FILE *) 0x403010
(gdb) s
1: fptr = (FILE *) 0x403010
(gdb) 
1: fptr = (FILE *) 0x403010
(gdb) s
1: fptr = (FILE *) 0x403010
(gdb) 
1: fptr = (FILE *) 0x403010
(gdb) 

Breakpoint 1, input (titl=0x400b20 "filename", length=79) at testfile.c:57
(gdb) 
(gdb) 
(gdb) 
(gdb) 
(gdb) 
(gdb) 
(gdb) display buf
2: buf = 0x7fffffffe5c0 "\n"
(gdb) s
2: buf = 0x7fffffffe5c0 "\n"
(gdb) 
2: buf = 0x7fffffffe5c0 ""
(gdb) 
2: buf = 0x7fffffffe5c0 ""
(gdb) 
2: buf = 0x7fffffffe5c0 ""
(gdb) 
savfil () at testfile.c:23
1: fptr = (FILE *) 0x403010
(gdb) 
1: fptr = (FILE *) 0x403010
(gdb) 
1: fptr = (FILE *) 0x403010
(gdb) 
Enter filename in less than 77 characters 	

 checking copy of  on disk


1: fptr = (FILE *) 0x403010
(gdb) 
1: fptr = (FILE *) 0x0
(gdb) 
1: fptr = (FILE *) 0x0
(gdb) 
1: fptr = (FILE *) 0x0
(gdb) 
1: fptr = (FILE *) 0x0
(gdb) 

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff7a636a8 in vfprintf () from /lib/x86_64-linux-gnu/libc.so.6
(gdb)
```

My recommendation would be to test your file pointer again before calling fwrite(), so you can have sensible error messages instead of just a segmentation fault.  I didn't study enough to determine what was wrong with your loop.  I just know that for whatever reason, when you run input() after choosing R, the fgets() doesn't run so you wind up just blanking out your buf.

Check out a tutorial on using gdb.  It really makes debugging like this less of a headache.

[[IMG]http://i1266.photobucket.com/albums/jj528/sagaciouskjb/Screenshot-11272014-023211AM.png[/IMG]](http://s1266.photobucket.com/user/sagaciouskjb/media/Screenshot-11272014-023211AM.png.html)

See, gdb shows that the prompt and regetting the user input for filename didn't execute, which is why "lin" is getting set to blank and crashing fwrite()

I've played around a little bit more, and it seems that the subequent call to fgets() only reads in a '\n' character.  Because of the way fgets operates, it stops immediately after this '\n' and since it does not get that input from the user on the second execution, I can only guess that you're leaving a '\n' in stdin to be read on the next subsequent call to fgets.  Now why printf() won't print the prompt, I have no idea.

Edit:

Playing some more, I'm sure it's something to do with my theory on stdin and the leftover '\n'.  If you add "getc(stdin) to the start of the input function, you'll have to hit enter once to enter a blank character, but then it will read the filename correctly and rename it accordingly.  The printf function doesn't seem to be able to print anything onto stdout until something reads this \n off stdin, but once it does it can execute normally.  Not sure how you can solve this, but it's definitely the problem.

Edit: A ltitle googl'ing later....

[http://stackoverflow.com/questions/2187474/i-am-not-able-to-flush-stdin](http://stackoverflow.com/questions/2187474/i-am-not-able-to-flush-stdin)
[http://c-faq.com/stdio/stdinflush2.html](http://c-faq.com/stdio/stdinflush2.html)

So if you put this code at the beginning of your input function, it will flush that extra \n out and take the input normally.

```
int c;
while ((c = getchar()) != '\n' && c != EOF);
```

---

### Post by pauls2 on 2014-11-27
**S**agaciousKGB,

Thank you!
I used to (a long time ago) code with TurboC for DOS and I didn't have to think about thpose pesky newline characters because I used the DOS "getch" and controlled the input process one character at a time.
I am occassionally reminded about it one way or another when I forget.

I added a second "getchar" in the save file function to strip out the newline character and it works fine now.
here is the code before I strip out the unnecessary parts:
```

int savfil(void)
{
    FILE *fptr;
    int x;
    char ch;
    char *filename = "filename";
    char filespec[79];
    do
    {
        x = 2;
        input(filename, 79); // get the path and filename
        strcpy(filespec, lin); // copy the entered path and filename
        lin[0] = '\0';
        clearscreen();
        printf("\t\n\n checking copy of %s on disk\n\n\n", filespec);
        fptr = fopen(filespec, "r");
        if(fptr != NULL) // there is a file
        {
            printf("file already exists; Rename your file or Overwrite?");
            printf("\n\nEnter R to rename or O to overwrite");
            ch = getchar();
            getchar();
            switch(ch)
            {
                case 'R':
                case 'r':
                x = 1;
                //fclose(fptr);
                break;
                case 'O':
                case 'o':
                x = 2;
                break;
            }
        }
    }
    while(x == 1);
    // fclose(fptr);
    fptr = fopen(filespec, "w"); // open the write pointer
    fwrite(&all, sizeof(all), 1, fptr); // write the file
    fclose(fptr); // close the pointer because we are done
    return 0;
}

```

Thank you for all your work and troubleshooting.
I am going to look for GDB or the GUI DDD to take care of these problems in the future!

No stroke for me today! 
Happy Thanksgiving, if you celebrate it - if not then just have a remarkable day!

Paul

---

### Post by ofnuts on 2014-11-27
printf() is line-buffered when it prints to a TTY session, nothing it displayed until the output stream contains a linefeed.

---

### Post by SagaciousKJB on 2014-11-28
No problem paul glad I helped, I learned something in additon to what ofnuts is saying.  Interesting problem I've never had before--hope I remember it if I ever do in the future.

---

