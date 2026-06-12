---
title: "c++ file input output handling"
date: 2010-02-11
forum: Programming Talk
---

### Post by akvino on 2010-02-11
I am going over input output handling for files. 

I wrote a program to open file for reading and take a string, or char[250] array, but when I did it with 'ch', reading character by character, it omitted all the white space.... 

Need a little help to read file with spaces char by char. It would be also beneficial if someone could suggest a way to copy a file char by char.

I did this some 3 years ago so please don't be to critical of my code, I am looking for professional suggestions on how to best handle file copies ch by ch, and am welcoming any suggestion on how to best handle buffers - ch by ch, or array ch[sizeof(buffer)]. 

```

//this is just a snipet

ifstream inFile;
char ch;

//....... inFile.open(somefilename);
//........ bla bla bla check if file is open is_open()

inFile >> ch
while (inFile) //possibly suggest better method than inFile.good()
{
     cout << ch;
     inFile >> ch;

}


inFile.close();

```

---

### Post by Some Penguin on 2010-02-11
For both sanity and performance reasons, you should probably use the lower-level routines read() and write() (from unistd.h) rather than ones that attempt to care about whitespace and the like.

---

### Post by dwhitney67 on 2010-02-11
fstream offers read() and write() capabilities, which should be used.

Reading a file, character by character, is a waste of resources, namely access to the HDD.  Consider reading the file in larger chunks, or all at once.  For an example of the latter, visit here (albeit the file is not copied to another file):
[http://www.cplusplus.com/reference/iostream/istream/read/](http://www.cplusplus.com/reference/iostream/istream/read/)

For an example of reading blocks, try something like:
```

#include <fstream>
#include <string>
#include <iostream>
#include <cstring>

int main(int argc, char** argv)
{
   using namespace std;

   fstream iFile(argv[1], ios::in | ios::binary);

   if (iFile)
   {
      string oFilename = argv[1];
      oFilename += ".copy";

      fstream oFile(oFilename.c_str(), ios::out | ios::binary);

      if (oFile)
      {
         const size_t BLOCK = 8 * 1024;    // 8K block size (arbitrarily chosen)
         char* buf = new char[BLOCK];

         while (iFile.read(buf, sizeof(buf)))
         {
            oFile.write(buf, iFile.gcount());

            memset(buf, 0, BLOCK);
         }

         delete [] buf;
      }
      else
      {
         cerr << "failed to open " << oFilename << endl;
         return -1;
      }
   }
   else
   {
      cerr << "failed to open " << argv[1] << endl;
      return -1;
   }
}

```
Note, I do not explicitly close the files above because I know that they will automatically be closed when the respective fstream object goes out of scope.

---

### Post by MadCow108 on 2010-02-12
> **Some Penguin said:**
> For both sanity and performance reasons, you should probably use the lower-level routines read() and write() (from unistd.h) rather than ones that attempt to care about whitespace and the like.

you have a strange definition of sanity...

If you don't need top notch performance stick with higher level functions (at least C level).
Using stuff like streambuf iterators is anyway not much slower than the low level ones. The difference is irrelevant in almost all cases.
Also the formated reads are not too much slower than the C formated reads (even faster in certain situations)

@op: The streambuf iterators are probably what you want
they read the unformated data from he file
[http://www.cplusplus.com/reference/std/iterator/istreambuf_iterator/](http://www.cplusplus.com/reference/std/iterator/istreambuf_iterator/)
or just use the read function. It works like a safer fread

@dwhitney
the C++ iostreams are buffered anyway.
I guess you don't have to add another buffer to your program to reduce load on the disk.
you can change the buffers (even disable them) by messing with the filebuf object returned by rdbuf()
[http://www.cplusplus.com/reference/iostream/filebuf/](http://www.cplusplus.com/reference/iostream/filebuf/)

---

### Post by akvino on 2010-02-12
> **dwhitney67 said:**
> fstream offers read() and write() capabilities, which should be used.

Reading a file, character by character, is a waste of resources, namely access to the HDD.  Consider reading the file in larger chunks, or all at once.  For an example of the latter, visit here (albeit the file is not copied to another file):
[http://www.cplusplus.com/reference/iostream/istream/read/](http://www.cplusplus.com/reference/iostream/istream/read/)

For an example of reading blocks, try something like:
```

#include <fstream>
#include <string>
#include <iostream>
#include <cstring>

int main(int argc, char** argv)
{
   using namespace std;

   fstream iFile(argv[1], ios::in | ios::binary);

   if (iFile)
   {
      string oFilename = argv[1];
      oFilename += ".copy";

      fstream oFile(oFilename.c_str(), ios::out | ios::binary);

      if (oFile)
      {
         const size_t BLOCK = 8 * 1024;    // 8K block size (arbitrarily chosen)
         char* buf = new char[BLOCK];

         while (iFile.read(buf, sizeof(buf)))
         {
            oFile.write(buf, iFile.gcount());

            memset(buf, 0, BLOCK);
         }

         delete [] buf;
      }
      else
      {
         cerr << "failed to open " << oFilename << endl;
         return -1;
      }
   }
   else
   {
      cerr << "failed to open " << argv[1] << endl;
      return -1;
   }
}

```
Note, I do not explicitly close the files above because I know that they will automatically be closed when the respective fstream object goes out of scope.


Thanks for the reply - this is binary. Few questions about this...

Please keep in mind that I am highly interested on finding 'the best way' done in the real world (I know there could be many 'best ways', but generally good developers utilize one or two options pending on their industry experience). 

Are there any issues with reading and sending binary in distributed computing, socket programming, and then copying the file on another system? Please keep in mind I never did binary read, copy, in C++ so to be safe it's better to ask up front than try to figure out what had gone wrong at the later time.

On the related note, I imagine it is easier for a computer to read binary, meaning faster/cleaner code in runtime. Do you have any thoughts on what is the fastest/HPC way of reading file vs. cleanest/smoothest, etc...

Are there any thoughts on the size of the buffer?

---

### Post by akvino on 2010-02-12
> **MadCow108 said:**
> you have a strange definition of sanity...

If you don't need top notch performance stick with higher level functions (at least C level).
Using stuff like streambuf iterators is anyway not much slower than the low level ones. The difference is irrelevant in almost all cases.
Also the formated reads are not too much slower than the C formated reads (even faster in certain situations)

@op: The streambuf iterators are probably what you want
they read the unformated data from he file
[http://www.cplusplus.com/reference/std/iterator/istreambuf_iterator/](http://www.cplusplus.com/reference/std/iterator/istreambuf_iterator/)
or just use the read function. It works like a safer fread

@dwhitney
the C++ iostreams are buffered anyway.
I guess you don't have to add another buffer to your program to reduce load on the disk.
you can change the buffers (even disable them) by messing with the filebuf object returned by rdbuf()
[http://www.cplusplus.com/reference/iostream/filebuf/](http://www.cplusplus.com/reference/iostream/filebuf/)
MadCow thanks for the reply, I haven't had a chance to examin your links as of now, but soon I will...

---

### Post by dwhitney67 on 2010-02-12
> **akvino said:**
> 
Are there any issues with reading and sending binary in distributed computing, socket programming, and then copying the file on another system?

There are no issues sending binary data from one system to another (via sockets), however it common practice to send such data in Network-Byte-Order (ie. Big Endian).

> **akvino said:**
> 
On the related note, I imagine it is easier for a computer to read binary, meaning faster/cleaner code in runtime. Do you have any thoughts on what is the fastest/HPC way of reading file vs. cleanest/smoothest, etc...

You can write the best optimized code in the universe, however if the data you want to read is resident on the HDD, then that will account for your application's biggest delay in processing the data.  IIRC, the heads of the HDD move to the position that need to be accessed; if your application is contending with another that also needs access to the HDD (for reading and/or writing), then this will create delays for both applications.

> **akvino said:**
> 
Are there any thoughts on the size of the buffer?

Continuing with my previous statements, this is the reason why it is a good idea to read data in larger chunks, than say one character at a time.  I'm not a h/w specialist, but I think reading in 4KB, or perhaps even 8KB, should be reasonable.  Every system is different; on one system there can be only a few processes running, whereas on another there could be many.  One system could have a 5200RPM HDD, another a 7200RPM HDD.  Because of these 'variables', oftentimes studies are conducted to determine how much data can reasonably sent, say in 1 second.

One may also need to take into consideration the capacity of the receiving machine(s), if the data is transmitted via RF or Ethernet.

NASA just launched a satellite (the Solar Dynamics Observatory) yesterday; look at what this 'baby' can do...
> 
The spacecraft, nicknamed SDO, is designed to transmit unprecedented reams of data from an extremely high Earth orbit. It should send back 150 million bits of data every second of every day, more than any other NASA Mission. That's equivalent to downloading 500,000 songs a day.

Quite impressive...
150 million bits per second is approximately 17.9 MBytes per second.

---

### Post by akvino on 2010-02-12
> **dwhitney67 said:**
> There are no issues sending binary data from one system to another (via sockets), however it common practice to send such data in Network-Byte-Order (ie. Big Endian).


You can write the best optimized code in the universe, however if the data you want to read is resident on the HDD, then that will account for your application's biggest delay in processing the data.  IIRC, the heads of the HDD move to the position that need to be accessed; if your application is contending with another that also needs access to the HDD (for reading and/or writing), then this will create delays for both applications.


Continuing with my previous statements, this is the reason why it is a good idea to read data in larger chunks, than say one character at a time.  I'm not a h/w specialist, but I think reading in 4KB, or perhaps even 8KB, should be reasonable.  Every system is different; on one system there can be only a few processes running, whereas on another there could be many.  One system could have a 5200RPM HDD, another a 7200RPM HDD.  Because of these 'variables', oftentimes studies are conducted to determine how much data can reasonably sent, say in 1 second.

One may also need to take into consideration the capacity of the receiving machine(s), if the data is transmitted via RF or Ethernet.

NASA just launched a satellite (the Solar Dynamics Observatory) yesterday; look at what this 'baby' can do...

Quite impressive...
150 million bits per second is approximately 17.9 MBytes per second.


Wow that NASA satellite - quite impressive... What is this world coming to! :o

BTW when you say >  There are no issues sending binary data from one system to another (via sockets), however it common practice to send such data in Network-Byte-Order (ie. Big Endian).
 - is there a good guide to follow, to get more familiar with Big Endian standards? I am trying to write code to copy over socket file from the client/daemon to the server/daemon on Linux cluster. Nothing crazy just little learning experience as I am planning to get more C++ (who knows maybe even change the career from sysadmin to C++ mid level dev) in the D 2010.

---

### Post by dwhitney67 on 2010-02-12
If you are working with a homogeneous cluster of systems, then the Network Byte Order (NBO) stuff might not be that important.  It's useful (and some may say good practice) to send data in NBO should the need arise where you need to send your data to a system that has a different architecture from your native system.

In today's world, most systems use Intel CPUs (Little Endian), whereas the the PowerPC (and ARM) is Big Endian.  The number of PowerPC systems may fall ever since Mac announced it would begin using the Intel chipset.  But still, there are other systems that expect data in a certain format, and NBO, which is analogous with Big Endian, is as good as any.

You can read more here: [http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

If your systems are on a local area network, why not just save yourself the trouble by sending files from System A to System B using 'scp' (secure copy).

If you must use sockets, choose a protocol (TCP or UDP), and then decide if you need to encapsulate the data in a proprietary packet, or just send the data as is.  Generally using TCP and sending the data as is is trivial enough.  For file transfers, usage of UDP is not recommended, but can be done.

---

### Post by akvino on 2010-02-12
> **dwhitney67 said:**
> If you are working with a homogeneous cluster of systems, then the Network Byte Order (NBO) stuff might not be that important.  It's useful (and some may say good practice) to send data in NBO should the need arise where you need to send your data to a system that has a different architecture from your native system.

In today's world, most systems use Intel CPUs (Little Endian), whereas the the PowerPC (and ARM) is Big Endian.  The number of PowerPC systems may fall ever since Mac announced it would begin using the Intel chipset.  But still, there are other systems that expect data in a certain format, and NBO, which is analogous with Big Endian, is as good as any.

You can read more here: [http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

If your systems are on a local area network, why not just save yourself the trouble by sending files from System A to System B using 'scp' (secure copy).

If you must use sockets, choose a protocol (TCP or UDP), and then decide if you need to encapsulate the data in a proprietary packet, or just send the data as is.  Generally using TCP and sending the data as is is trivial enough.  For file transfers, usage of UDP is not recommended, but can be done.

scp - meaning from the shell or from the c++ application (cause I am not aware of the second)?

This is my little programming exercise to get more familiar with C++.

---

### Post by akvino on 2010-02-12
Eh - here we go into the code

on [http://www.cplusplus.com/doc/tutorial/files/](http://www.cplusplus.com/doc/tutorial/files/)

to get the length of the file following code is used:
```


int main () {
  long begin,end;
  ifstream myfile ("example.txt");
  [b]begin = myfile.tellg();
  myfile.seekg (0, ios::end);
  end = myfile.tellg();[/b]
  myfile.close();
  cout << "size is: " << (end-begin) << " bytes.\n";
  return 0;
}
```
And I get it. It gets the first pointer with 
begin = myfile.tellg();

Then it sets the pointer to the end of the file, and then it gets end pointer and subtracts to get the 'bit' value.

Now in this code found at [http://www.cplusplus.com/reference/iostream/istream/read/](http://www.cplusplus.com/reference/iostream/istream/read/)

```

// read a file into memory
#include <iostream>
#include <fstream>
using namespace std;

int main () {
  int length;
  char * buffer;

  ifstream is;
  is.open ("test.txt", ios::binary );

  // get length of file:
  is.seekg (0, ios::end);
  length = is.tellg();
  is.seekg (0, ios::beg);

  // allocate memory:
  buffer = new char [length];

  // read data as a block:
  is.read (buffer,length);
  is.close();

  cout.write (buffer,length);

  delete[] buffer;
  return 0;
}


```

It is little unclear how it gets the size of the file, or am I not understanding something?
  // get length of file:
  is.seekg (0, ios::end);
  length = is.tellg();
  is.seekg (0, ios::beg);

This line 'is.seekg (0, ios::end);', sets the pointer to the end of the file, but then the next line 'length = is.tellg();' grabs the pointer. How is it that the is.tellg() returns the length, when there was no initial pointer from the beginning of the file?

---

### Post by MadCow108 on 2010-02-12
If you're just learning don't focus to much on all the too low level details like optimal buffer size.

Its much more effective if you learn to use the capabilities the language and libraries offer to you.
E.g. instead of bothering about buffers, use the already buffered C++ iostreams (they will probably have an optimized buffer for the most common type of harddisk).

Instead of trying to implement a transport protocol for heterogeneous clusters, use an existing implementation instead.
One that comes to mind is MPI (Message passing interface)
It is designed for high performance heterogeneous data transfer over various means and has many functions for parallel processing.
It takes care of all the low level stuff like endianess and so on.

Also there are specialized MPI implementations available from the Supercomputer vendors.
So its basically just a waste of time to learn the details except you really plan to help developing these specialized implementations.

edit concering new post:
the buffer iterator is placed in the beginning of the file when opening it (default behavior at least). This position is 0.
So you can directly seek to the end and get the length (end - 0 = length)
you have to seek explicitly to the beginning if your iterator is not to the start of the file (.e.g when appending)

---

### Post by akvino on 2010-02-15
> **dwhitney67 said:**
> fstream offers read() and write() capabilities, which should be used.

Reading a file, character by character, is a waste of resources, namely access to the HDD.  Consider reading the file in larger chunks, or all at once.  For an example of the latter, visit here (albeit the file is not copied to another file):
[http://www.cplusplus.com/reference/iostream/istream/read/](http://www.cplusplus.com/reference/iostream/istream/read/)

For an example of reading blocks, try something like:
```

#include <fstream>
#include <string>
#include <iostream>
#include <cstring>

int main(int argc, char** argv)
{
   using namespace std;

   fstream iFile(argv[1], ios::in | ios::binary);

   if (iFile)
   {
      string oFilename = argv[1];
      oFilename += ".copy";

      fstream oFile(oFilename.c_str(), ios::out | ios::binary);

      if (oFile)
      {
         const size_t BLOCK = 8 * 1024;    // 8K block size (arbitrarily chosen)
         char* buf = new char[BLOCK];

         while (iFile.read(buf, sizeof(buf)))
         {
            oFile.write(buf, iFile.gcount());

            memset(buf, 0, BLOCK);
         }

         delete [] buf;
      }
      else
      {
         cerr << "failed to open " << oFilename << endl;
         return -1;
      }
   }
   else
   {
      cerr << "failed to open " << argv[1] << endl;
      return -1;
   }
}

```
Note, I do not explicitly close the files above because I know that they will automatically be closed when the respective fstream object goes out of scope.


dwhitney67 - do you mind explaining this.. I am bit lost with this sample as I am having problems clearing buffer after successful read. 



Here is what I'am playing with:

```

// read a file into memory
#include <iostream>
#include <fstream>
using namespace std;

int main () {
  int length;
  char * buffer;

  ifstream is;
  is.open ("sample.txt", ios::binary );

  // get length of file:
  is.seekg (0, ios::end);
  length = is.tellg();
  is.seekg (0, ios::beg);
  
  cout <<"\nLength is "<< length<<endl;
  // allocate memory:
  buffer = new char[50];

  // read data as a block:
  
  while(is.good()){

	is.read (buffer,50);
  	//is.close();

  	cout.write (buffer,50);
  }
  delete[] buffer;
  return 0;
}

```


The problem is in the loop where while(is.good()) is a condition and I read buffer size 50. The text file I read in has 77 bytes and when I read in second time, it would read in 27 and remaining 23 would be displayed from the previous buffer read. So in essence I am not clearing buffer.

Few options came to mind (do buffer math) such as to calculate and implement exact number of reads per a buffer size in for(loop). Then I started thinking that my conditioning is wrong and I better ask for someone with more experience...


If I use this approach to read file into the buffer, how do I 'best' display the same file on the screen with a good conditional statement in my while/for read loop?

---

### Post by dwhitney67 on 2010-02-15
When you first 'new' your buffer, it is chock full of zeroes.  This is not the case after you have filled it with (50 bytes of) data.

Use memset() to clear the buffer before reusing it again, although this is not necessary.  To obtain the number of bytes that were written into the buffer by read(), call gcount() on the file stream object.

Another alternative is to read the file in all at once.  Since you know the length of the file, why not just allocate a buffer of that size, in lieu of a mere 50 bytes?

Anyhow, with approach #1,
```

#include <iostream>
#include <fstream>

using namespace std;

int main ()
{
   **ifstream is("sample.txt", ios::in | ios::binary);**

   is.seekg (0, ios::end);
   const size_t length = is.tellg();
   is.seekg (0, ios::beg);

   cout << "\nLength is " << length << endl;
  
   char* buffer = new char[50];

   while(**is**)
   {
      is.read (buffer,50);

      cout.write (buffer,**is.gcount()**);
   }

   delete[] buffer;

   return 0;
}

```

---

### Post by akvino on 2010-02-16
Thanks a bunch - that is exactly what I needed.

---

### Post by akvino on 2010-02-22
Generally speaking - when taking user input for file processing would you suggest using a char input[FileSize] solution vs. string input solution and why?

What is the syntax for opening file with the string:


If I wanted to convert this code to declare 'input' to a string:

```


char input[20];
   cout <<"\nPlease input the name of the file you want to open: "<<endl;
   cin.getline (input, 20);

     ifstream is(input, ios::in | ios::binary);

```

---

### Post by dwhitney67 on 2010-02-22
> **akvino said:**
> Generally speaking - when taking user input for file processing would you suggest using a char input[FileSize] solution vs. string input solution and why?

Use the latter.  Why... well, because I do not want to declare a 2GB (or more!) sized array on the stack or on the heap.  Don't assume that you will be opening a puny little file.

> **akvino said:**
> 
What is the syntax for opening file with the string:

```

std::string filename;

std::cout << "Enter filename: ";
std::cin  >> filename;

std::fstream inFile(filename.c_str(), std::ios::in);

if (inFile)
{
   // file successfully opened
}
else
{
   // error opening file
}

```

---

