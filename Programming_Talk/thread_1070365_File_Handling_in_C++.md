---
title: "File Handling in C++"
date: 2009-02-15
forum: Programming Talk
---

### Post by nebu on 2009-02-15
If I use a fstream object to acess a file......

and while my fstream object is open..... 
if i edit the file externally and save it while my fstream object is open...... 
will my fstream object still have the old file or the new one....... 
if it is still the old file ......
is there a way for me to make the fstream have the new file without having to open the file yet again......

---

### Post by nvteighen on 2009-02-15
Hmm... the fstream will probably contain the old file, as what this stuff does is to load the file into memory and edit it from there... Updates only will occur when the buffer is flushed (usually, after a newline) or the file is closed.

If I'm not wrong, to have immediate access to a file's state, you have to use low-level functions. I'm not aware which these are in C++, but in C it's open(), read(), close() (compared to fopen(), etc. which are high-level).

---

### Post by magon on 2009-02-15
of course not!! the kernel does not handle concurrent access to files. but you can use the select system call to ask the kernel to notify you when the file is written by another process see "man select".

---

### Post by nvteighen on 2009-02-15
> **magon said:**
> of course not!! the kernel does not handle concurrent access to files. but you can use the select system call to ask the kernel to notify you when the file is written by another process see "man select".
And open() and such wouldn't help?

---

### Post by nebu on 2009-02-15
how do i do that in c++

i can use the system function to run the select command but then..... how do i get the the output of that command in my program.....

i can route the output of the system call to a file and then read that file.... but is there a more elegant way to go about the same.....

---

### Post by magon on 2009-02-15
> **nebu said:**
> how do i do that in c++

i can use the system function to run the select command but then..... how do i get the the output of that command in my program.....

i can route the output of the system call to a file and then read that file.... but is there a more elegant way to go about the same.....

select is a system call not a command !! can you explain what do you want to achieve exactly so that we can help you

---

### Post by nebu on 2009-02-15
i need to keep reading the data stored in a file and then using that data do some calculations and store the result in a sql database.....

the file will keep updating as time goes on and the program will keep on running and gathering more and more data as the file is updated...

---

### Post by dwhitney67 on 2009-02-15
I tried the code below for a file that contains ASCII data that is newline terminated, and it worked like a charm.

If your file will have binary data, or if it will have some other format, then perhaps getline() will not be the appropriate call to make.  Everything else, with respect to opening the file, and setting the file position should work though.

[php]
#include <fstream>
#include <iostream>
#include <unistd.h>

int main(int argc, char** argv)
{
  unsigned int readPos = 0;

  while (true)   // run forever
  {
    // open the file
    std::fstream* ifs = new std::fstream("test.dat", std::ios::in);

    if (ifs && ifs->is_open())
    {
      std::string data;

      // set the file to point to the last read position
      ifs->seekg(readPos);

      // read from the file
      while (getline(*ifs, data))
      {
        readPos = ifs->tellg();

        std::cout << data << " (" << readPos << ")" << std::endl;
      }

      // all of the data has been read; close the file, and delete the handle.
      ifs->close();
      delete ifs;
      sleep(1);
    }
    else
    {
      if (ifs) delete ifs;

      std::cerr << "Error:  Failed to open data file." << std::endl;
      break;
    }
  }
}
[/php]

---

### Post by nebu on 2009-02-15
yes.... what i was asking was how do i integrate this sort of code with the system call magon was talking about

---

### Post by dwhitney67 on 2009-02-15
Very good question... I do not know.

The select() system call requires a file (or socket) descriptor, which I do not believe are available from C++ stream containers.  I may be wrong though!

If you open your files using the C library system calls (e.g. open()), then you could use select(); now whether this will meet your needs will require yet another test program to be thrown together.  The program I posted earlier took me all of about 15 minutes to write... perhaps I can write another (sigh!).

---

### Post by dwhitney67 on 2009-02-15
Here... another stab at the problem, this time with the usage of select().
Unfortunately, I could not figure out how to continue reading the file without closing it first.  Note that the sleep() is used to give an opportunity for the kernel to close the file, and allow me to reopen it.

[php]
#include <iostream>
#include <cstdlib>
#include <cstdio>
#include <cstring>

int main(int argc, char** argv)
{
  int readPos = 0;

  while (true)
  {
    FILE* inFile = fopen("test.dat", "r");

    if (inFile)
    {
      char data[1024] = {0};

      fseek(inFile, readPos, SEEK_SET);

      while (fgets(data, sizeof(data), inFile))
      {
        readPos = ftell(inFile);

        std::cout << data << "(" << readPos << ")" << std::endl;
      }

      fd_set readfds;
      FD_ZERO(&readfds);
      FD_SET(fileno(inFile), &readfds);

      while (select(fileno(inFile) + 1, &readfds, 0, 0, 0) <= 0);

      fclose(inFile);
      sleep(1);
    }
    else
    {
      std::cerr << "Error:  Cannot open data file." << std::endl;
      break;
    }
  }
}
[/php]

---

### Post by rharriso on 2009-02-15
Well, I just did a homework assignment that utilizes the select function.

It's a littler verbose I know, but the way it works is, you have to add different file descriptors to a file descriptor set,  The copy that set, select on that copy. And then you know if a file descriptor has input to read. Then you read from that and write to whatever file descriptor you need. The pipes will be read from until the phrase :quit is received. I think thats what you need.

look for the man pages
all either in man section 2 or 3

> 
man select
man FD_SET
man open
man read
man write


[PHP]
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>

#define MAXBUFFER 6000

int chat(char* readName, char* writeName)
{
    int readDesc, writeDesc;
    readDesc = open(readName, O_RDONLY | O_NONBLOCK);
    writeDesc = open(writeName, O_WRONLY);
    
    fd_set watch, watchAgain; //original and copy of the fd set
    int maxDesc, readResult;
    char buffer[MAXBUFFER];   //pulls out of file
    printf("Connect\n");
    
    //set up the file descriptor set
    FD_ZERO(&watch); //remove all things from the set
    FD_SET(readDesc, &watch); //
    FD_SET(0, &watch);   //watches standard in
    
    maxDesc = readDesc>writeDesc?readDesc:writeDesc;
    
    //chat with the slave program
    while(FD_ISSET(readDesc, &watch) || FD_ISSET(0, &watch))
    {
        watchAgain = watch;
        
        //find which buffers have some info to give, if it fails, bail
        if(select(maxDesc+1, &watchAgain, NULL, NULL, NULL) <0){
            printf("SELECTION FAIL\n");
            return 0;readDesc;
        }
        
        //look at what the other person has to say
        if( FD_ISSET(readDesc, &watchAgain) ){
            
            //read as much as you can buffer
            readResult = read(readDesc, buffer, MAXBUFFER);
            
            //error found
            if(readResult < 0)
            {
                printf("PROBLEM WITH READ BUFFER\n");
                return 0;
            //ther is something to print out
            }else if(readResult > 0)
            {
                 //if they are quiting
                if(strncmp(buffer, ":quit", 5) == 0){
                    
                    //close everything down
                    printf("Disconnected\n");
                    close(readDesc);
                    close(writeDesc);
                    return 1;
                }else{
                    //write to screen
                    printf("Them: %s", buffer);
                 
                    //clear the buffer
                    int x = 0;
                    for(x = 0; x<MAXBUFFER; x++){
                        buffer[x] = '\0';
                    }                       
                }                
            }
            
        }
        //look at the keyboard
        if( FD_ISSET(0, &watchAgain) )
        {
            //read as much as you can buffer
            readResult = read(0, buffer, MAXBUFFER);
            
            //error found
            if(readResult < 0)
            {
                printf("PROBLEM WITH STDIN\n");
                return 0;
            //ther is something to print out
            }else if(readResult > 0)
            {
                //write to outgoing buffer
                write(writeDesc, buffer, MAXBUFFER);
                 
                
                //if you are quiting
                if(strncmp(buffer, ":quit", 5) == 0){
                    
                    //close everything down
                    printf("Disconnected\n");
                    close(readDesc);
                    close(writeDesc);
                    return 1;
                }
                    
                 //clear the buffer
                 int x = 0;
                 for(x = 0; x<MAXBUFFER; x++){
                     buffer[x] = '\0';
                 }                             
            }
        }
    }
}

int main(){
    int test, test2;
    char* readName;
    char* writeName;
    int isMaster = 0;    
    //if teh pipes are open then this is the master

    struct stat fileInfo, fileInfo2;
    if(stat("p1",&fileInfo) || stat("p2",&fileInfo2))
    {
        isMaster = 1;
        //need to create new files and destroy old ones
        mkfifo("p1", 0744);
        mkfifo("p2", 0744);
        
        //read to p1 and write to p2
        readName = "p1";
        writeName = "p2";
        
    }    
    //else this is the slave
    else{     
        readName = "p2";
        writeName = "p1";
    }
    
        
    //have the programs talk to each other
    chat(readName, writeName);
    
    if(isMaster){
        remove("p1");
        remove("p2");
        
    }

}
[/PHP]


What this program does is set up pipes between two instances of the program this is compiled to:

to run compile and run the program in two terminals
what gets enter in one program shows up on the other, until you enter ":quit" in either.

if you quit with control c you have to delete the pipes this program creates.

sorry I don't have a better example. I don't use select very often.

---

