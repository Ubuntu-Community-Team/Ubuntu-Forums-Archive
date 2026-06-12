---
title: "stat() function business!"
date: 2005-12-07
forum: Programming Talk
---

### Post by blacklantern on 2005-12-07
Okay, first let me spell out everything that's going on. I'm trying to finish a peer-to-peer project for school. It's a pretty primitive project, and it calls for me to use the stat() function, which grabs important information for a file. I'm trying to grab each file from the directory and place the information I want into a struct, and create an array of these structs. The problem is, even though the program adds the files "." and ".." to the array, any file that I create can't be accessed; the program tells me that the file doesn't exist. 

Here's all the important info:

struct dirent *dp;
struct stat   statbuf;
DIR *impdir, *otherdir;
struct filepoll
{
        char *filename; //The name of the file
    int filesize; //The size of the file in bytes
    time_t modded;//The date of modification of the file
    int nottodelete; //an integer determining flagging a file or deletion;
                     //0 == file should be deleted from the node's neighbors
                     //1 == file should should be kept in the node's neighbors
};

struct filepoll impFiles[MAXFILES]; //the program's record of the important directory


..........
.........


//2.   opendir(impdir)
                impdir = opendir("./important");

                //3.   Set all files in list's checkbit to zero (can do later)
                for(i = 0; i < (maxFiles - 1); i++)
                        impFiles[i].nottodelete = 0;

                //4.   loop through impdir
                printf("Right before readdir!! \n");
                while ((dp = readdir(impdir)) != NULL)
                {
                        printf("Right before stat!! \n");
                        printf("File %s \n", (dp->d_name));
                        if (stat(dp->d_name, &statbuf) == -1) //file could not be accessed CHANGED
                        {
                                perror("A file could not be accessed.");
                                exit(1);
                        }


And here's the relevant part of my output:


Right before readdir!! 
Right before stat!! 
File . 
Right before filename list search!! 
Adding file to program recordsRight before stat!! 
File .. 
Right before filename list search!! 
Adding file to program recordsRight before stat!! 
File test.txt 
A file could not be accessed.: No such file or directory


As you can see, the opendir and readir work perfectly, but for some reason my file is inaccessible. I don't know why the program says it doesn't exist - I put the test.txt file in the /important directory myself. Even stranger is that readdir() finds the file and prints it out, but stat() says it isn't there. My partner and I thought it may have been due to file permissions, but I got the same output even after I set gave rwx access to everyone; owner, group and other.

By no means am I asking for any code to be written, I'm just stuck here - I can't think of anything to do to help me debug. It just seems like one of those things that you know or you don't. If anyone would be willing to lend their opinion on the problem, I'd greatly appreciate it.

---

### Post by toojays on 2005-12-07
Change your "perror("A file could not be accessed.");" line to "perror(NULL);". That might give you a clue . . .

---

### Post by blacklantern on 2005-12-07
[QUOTE=toojays]Change your "perror("A file could not be accessed.");" line to "perror(NULL);". That might give you a clue . . .[/QUOTE]


No other clue - now the output just says 'No such file or directory' minus the 'A file could not be accessed' part.

---

### Post by toojays on 2005-12-07
Sorry, my bad, I didn't see the output the first time.

The trouble is, stat is looking in the current working directory, not the impdir directory. The argument for stat needs to be "./important/test.txt", or you need to use chdir() to change directory before calling stat.

---

### Post by blacklantern on 2005-12-07
[QUOTE=toojays]Sorry, my bad, I didn't see the output the first time.

The trouble is, stat is looking in the current working directory, not the impdir directory. The argument for stat needs to be "./important/test.txt", or you need to use chdir() to change directory before calling stat.[/QUOTE]


as you can see, the dp->d_name is needed, as the program cycles through filenames. That being the case, I can't hardcode the name of the file. Would it be wise to make a string, like char * impdir, set it to "./important", and do a strcat with dp->d_name?

---

### Post by thumper on 2005-12-07
That would be my suggestion, although don't forget to free the string you create with strcat.

---

### Post by blacklantern on 2005-12-07
Thanx, everyone - it worked perfectly. :)

---

### Post by blacklantern on 2005-12-07
Question - why would a closedir command cause a segfault if I use the same Dir* argument that I used in opendir?

---

### Post by toojays on 2005-12-08
Do you mean the argument you passed to opendir, or the value returned by opendir?

Did the same code work without a segfault before you fixed your stat() problem?

---

