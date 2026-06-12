---
title: "fops/ using memcmp question"
date: 2010-07-16
forum: Programming Talk
---

### Post by sacredfaith on 2010-07-16
Greetings,

Quick info:
**OS**: 10.04 Lucid
**g++**: g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
**Program Specification**: Creates a large file (user specified), and then does a search for the last element in the list (forcing the computer to search the entire file). Start/Stop times are recorded appropriately.
**Problem**: While the program compiles and runs, memcmp doesn't appear to be working - I'm not sure if my fops are coded correctly (or if my memcmp is either, for that matter). These appear near the bottom of the code within the if statement (which is contained within a while statement). Note that the time is not recorded (despite the matching string being appended to the file)...actually, I don't think the 'if' statement is even entered. 

```

#include<iostream>
#include<fstream>
#include<time.h>
#include<string.h>
#include<cstdlib>
#include<stdlib.h>
#include<stdio.h>
#include<unistd.h>
#include<fcntl.h>
#include<sys/stat.h>
#include<sys/types.h>
using namespace std;

int main(){
    // Declare fops variables
    unsigned long sb_current_pos=0,f_size=0;
    FILE * file_p;

    // Declare random number generator variables
    unsigned int iseed = (unsigned int)time(NULL);
    srand(iseed);

    // Define bash command to create file "scanthis.txt"
    string command ="dd if=/dev/urandom of=scanthis.txt conv=notrunc status=noxfer bs=1M count=";

    // Note that the string 'file_size' is ONLY used to allow for user-defined file creation length    
    string file_size;

    // vars for measuring computation time
    clock_t start_time,stop_time;
    double t_diff=0;

    // Test string
    string test = "So_that_your_faith_would_not_rest_on_the_wisdom_of_men_but_on_the_power_of_God_1_Cor_2_5";
    
    // Defining search buffer size
    unsigned long sb_size = test.length();    


    //********************CODE BEGINS HERE...I mean, really********************
    
    //adapted from www.geekpedia.com/tutorial38_Searching-for-a-string-in-a-File.html
    

    // Creating the search buffer
    char* search_buf=(char*)malloc(sb_size);
    cout << "Starting..." <<  endl;
    cout << "Input Desired File Size:" << endl;
    cin >> file_size;

    // Taking the user-defined file size and appending it to 
    // 'command'
    command = command+file_size;

    // Execute 'command' to actually create the file
    system(command.c_str()); 
    cout << command << endl;

    // Inform user-space what in the wide wide world of sports is going on
    cout << "File Creation Complete!" << endl;

    // Begin fops by opening the newly created file
    // Note the "a" is to open in "append" mode
    file_p = fopen("scanthis.txt","a");

    // Append the test string to the file of random-ness
    fputs(test.c_str(),file_p);

    // Let user space know the search is starting
    cout << "Starting..." << endl;

    // fseek repositions the "file stream indicator"
    fseek(file_p,0,SEEK_END);
    f_size = ftell(file_p);
    cout << f_size << endl;
    fseek(file_p,0,SEEK_SET);

    // Start timer
    start_time = clock();    
    while(sb_current_pos<f_size)
    {
        // Update file pointer
        fseek(file_p,sb_current_pos,SEEK_SET);

        // Read from file
        fread(search_buf,1,sb_size,file_p);

        // If the strings match, free the buffer, 
        // stop the clock, and calculate the time difference 
        if(!memcmp(search_buf,test.c_str(),sb_size))
        {
            free(search_buf);
            stop_time = clock();
            t_diff = ((double)(stop_time - start_time))/CLOCKS_PER_SEC;
            cout << "Test Complete!" << endl << "Time: " << t_diff << " seconds" << endl;
            return 0;
        }

    sb_current_pos++;
    }

    // close the file
    fclose(file_p);
    cout << "okay...I'm done..." << sb_current_pos << endl;
    return 0;
}

```**Output:**
```

Starting...
Input Desired File Size:
10
10+0 records in
10+0 records out
dd if=/dev/urandom of=scanthis.txt conv=notrunc status=noxfer bs=1M count=10
File Creation Complete!
Starting...
10485848
okay...I'm done...10485848

```I've got some cout's in there for debugging. Don't forget that memcmp returns zero if they match (hence the !0 in the if statement).

As an aside, when posting questions (I'm asking since I'm relatively new) is it better to post this much information? 


Kind Regards,

-sf

---

### Post by MadCow108 on 2010-07-16
always check the return codes of functions related to files.

You'll see all reads fail.
This is because you open the file in write mode.
So either reopen the file in read mode, or better open it in readwrite mode with
either "rw" or "a+"

Why are you mixing C and C++?
at least use the correct headers which are the basename of the C headers with a c in front and no extension.
And using malloc in a C++ program might cause big confusion as you always have to look up with delete to use.
Stick to new. This should also work with all good C apis (just not with those that take ownership of users memory)

And your algorithm is very inefficient.
Have a look at this:
[http://en.wikipedia.org/wiki/String_searching_algorithm](http://en.wikipedia.org/wiki/String_searching_algorithm)

---

### Post by sacredfaith on 2010-07-16
MadCow,

Thank you so much for your advice and criticism, I found it to be polite and constructive. Doing stupid things is a part of learning ~ I try to remember that (or at least keep telling myself that). 

> always check the return codes of functions related to files.Great advice! I really need to learn stuff like this. After some searching I did this:

```
   
        flag = fread(search_buf,1,sb_size,file_p);
        if(flag!=sb_size)
        {
            fputs("Reading Error",stderr);
            exit(1);
        }

```(with flag declared as int).....is there a better way to check return codes?

> So either reopen the file in read mode, or better open it in readwrite  mode with
either "rw" or "a+"This solved the problem directly. Thank you so much! I'm going to leave it open so that I can learn more about this though.


> 
Why are you mixing C and C++?I wanted the speed of C file operations with the string library (translation: somebody told me to do this and gave me that as a reason). Could you explain in a little more detail why this is a bad idea? 

> And using malloc in a C++ program might cause big confusion as you  always have to look up with delete to use.Why? (sorry if this is a dumb question)

> And your algorithm is very inefficient.Good observation. So I'm trying to see how long it takes for a given computer to read a file of user-defined length so I can compare the read times. I need to do this in a worst-case scenario environment (i.e. the target string is located at the end of the file), and I'm trying to figure out if I need hash tables or not (i.e. if it can do the searching in microseconds then coding up an advanced hashing algorithm will be a waste of time). 

Still, I'm really thankful you showed me those resources (as well as improving my file handling), as I will most assuredly be applying that knowledge in the future. 

I like learning about programming for that reason...once you learn how to do something smarter than the last time you did it, you don't forget it - and chances are, you'll be able to either help someone who made the same mistake, or code smarter in the future. 

Again, I'm leaving this open for just a bit longer (no pun intended) for academic reasons.

Also, did I put too much information in the opening question? Or is that good?

Kind Regards,

-sf

---

### Post by MadCow108 on 2010-07-17
> **sacredfaith said:**
> MadCow,

Thank you so much for your advice and criticism, I found it to be polite and constructive. Doing stupid things is a part of learning ~ I try to remember that (or at least keep telling myself that). 

Great advice! I really need to learn stuff like this. After some searching I did this:

```
   
        flag = fread(search_buf,1,sb_size,file_p);
        if(flag!=sb_size)
        {
            fputs("Reading Error",stderr);
            exit(1);
        }

```(with flag declared as int).....is there a better way to check return codes?


have a look at the manpages of fread. man fread
the return value of fread is size_t which is an unsigned integral type with a width depending on system (32 bit 64 bit).
So flag should be the same type.
Also it returns the number of bytes read which may not be sb_size if end of file is encountered (checkable with feof)
better check for error with ferror.
You can also print the error with perror("prefix") or strerror()


> 
I wanted the speed of C file operations with the string library (translation: somebody told me to do this and gave me that as a reason). Could you explain in a little more detail why this is a bad idea? 

it is more of a myth that c++ stream library is slower than the C stream library. They may have been very valid 10 years ago but the implementation has much improved since then.
While there are some penalties due to the higher abstraction, in most problems this does not play a big role (disk IO is much slower than CPU).
But c++ streams are mostly much easier and safer to use which outweighs the
slight performance difference mostly.
If in doubt benchmark first, and then decide.

> 
[QUOTE]
And using malloc in a C++ program might cause big confusion as you always have to look up with delete to use.

Why? (sorry if this is a dumb question)
[/QUOTE]
you cannot use free on memory allocated with new and delete on memory allocated with malloc.
If you are careful you can of course mix them, but there is no real advantage and it just makes your code more error prone.

If you do not need construction of objects which is provided by new for classes you can always use the placement new, get_temporary_buffer and the uninitialized_copy algorithms.

---

### Post by sacredfaith on 2010-07-18
MadCow,

Again, thank you for your patience and willingness to teach. It's been cool to learn about the low-level line between C/C++ in the realm of memory management, file operations, and good idea/bad idea programming practices. Success and solved. 

Kind Regards,

-sf

---

