---
title: "Help with a POSIX Program"
date: 2006-01-31
forum: Programming Talk
---

### Post by skyace888 on 2006-01-31
Hey guys!  I installed Ubuntu 5.10 on my laptop the other day to use for an operating systems course that I am taking.  I am a Linux newbie, but everything seemed to go ok.  Anyways, I have this assignment to do that I've been spending many hours on and can't seem to get anywhere.  The question is as follows:

POSIX defines a standard thread package in the context of the C programming language. Several manufacturers provide a POSIX thread package as a user library along with their C programming facilities. If you have a system available to you that supports threads, then design and implement a thread program so that one thread reads a file, while a second thread writes the data to another file.

My textbook does not talk much about POSIX except for saying that a POSIX file is "a named sequential collection of bytes."  It also gives an example Linux program that opens two files, and then copies the contents of one file into the other one byte at a time using the POSIX interface. I assume that this is similar to the answer except that the solution must use two threads.  Here is the code that the book gives:

#include <stdio.h>
#include <fcntl.h>

int main() {
int inFile, outFile;
char *inFileName = "in_test";
char *outFileName = "out_test";
int len;
char c;

inFile = open(inFileName, O_RDONLY);
outFile = open(outFileName, O_WRONLY);
// Loop through the input file
while((len = read(inFile, &c, 1)) > 0)
write(outFile, &c, 1);
// close files and quit
close(inFile);
close(outFile);
}

I have installed the Anjuta IDE and searched around the Internet for some POSIX/pthread examples.  I'm not sure how to approach this.  How can I get the two threads to work together?  All the examples that I've found just use the "pthread_create" and then call some useless function that doesn't do much.  Any assistance is greatly appreciated!

---

### Post by skyace888 on 2006-02-01
Following the examples I've found online, I have come up with the following code:

#include <stdio.h>
#include <pthread.h>
#include <fcntl.h>


void *parseFile(void *); // function prototype


int main(void)
{
int ret1;
int t = 0;

pthread_t firstThread;

ret1 = pthread_create (&firstThread, NULL, parseFile, (void *)t);

pthread_exit(NULL);

return 0;
}

void *parseFile(void *data) {
char *inFileName = "in_test";
char *outFileName = "out_test";
int inFile;
int outFile;
int len;
char c;

outFile = open(outFileName, O_WRONLY);
inFile = open(inFileName, O_RDONLY);
while((len = read(inFile, &c, 1)) > 0)
write(outFile, &c, 1);
close(inFile);
pthread_exit(NULL);
}

The program works correctly but I don't think that this is they way the intructions say to do it. I think I am only creating one thread here instead of two.

---

### Post by rydow on 2006-02-03
This seems to be the classical "producer consumer problem"

What you would like to do is to have the main thread read a file (producer) and pass it in chunks to another thread (consumer). In order to to do this you have to have some kind of sycronization so that the consumer knows when data is ready and when all data is passed. What one usually uses is a mutex or a semaphore.

Do some googling on "producer consumer problem" to get more info and I suggest you read your text book's chapter on threads in depth.

cheers
/Jonas

---

### Post by Richie P on 2006-02-04
I was going to suggest looking at the manual pages for pthreads starting with pthread_create, but it doesn't appear that those manual pages are included with the linux developer package :-/ and I can't see them anywhere else in synaptic either.

They are still on the internet though: [http://www.planetoid.org/technical/pthreads/manpages/](http://www.planetoid.org/technical/pthreads/manpages/).

Uhhgg reading that text book excerpt made me feel ill.

---

### Post by rydow on 2006-02-05
There is a good chapter on this in "Beginning Linux Programming" from Wrox, there is also the code to download. ([http://www.wrox.com/WileyCDA/WroxTitle/productCd-0764544977,descCd-download_code.html](http://www.wrox.com/WileyCDA/WroxTitle/productCd-0764544977,descCd-download_code.html))

Download the code untar it and grep for pthread.
( this is how to do it:
tar xvzf filename.tgz
cd filename
find . -name | xargs grep pthread
)
There is much to learn from this code and even more from the book.
/Jonas

---

