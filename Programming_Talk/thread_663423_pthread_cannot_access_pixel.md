---
title: "pthread: cannot access pixel"
date: 2008-01-10
forum: Programming Talk
---

### Post by nephritiri on 2008-01-10
hi. iv bn writing a program of rotating a single 2D image. i applied pthreads so that i can speed up the running tym. 
here's my compressd code:

---

### Post by nephritiri on 2008-01-10
[HTML]

pthread_mutex_t mutex1 = PTHREAD_MUTEX_INITIALIZER;

struct spaceAttr       
{ int height;
  int width;
  int x;
  double thetaR;
  RGBImage outputImage,inputImage;
};



void *threadRotateFunction(void *struct1){

	pthread_mutex_lock( &mutex1 );
	...initialize some variables
	....extract variable values at struct1

	for (int y = 0; y < h; y++){

		nx = (int)((a-halfWidth)*cos(theR) - (y-halfHeight)*sin(theR)+halfWidth);

	    	ny = (int)((a-halfWidth)* sin(theR) + (y-halfHeight)*cos(theR)+halfHeight);

		if(nx < w && nx >= 0 && ny < h && ny >=0){

			outImg(nx,ny) = inImg(a,y);

		}
	}//for y
	pthread_mutex_unlock( &mutex1 );
	pthread_exit(0);
}//threadRotateFunction



int main () {
   
   spaceAttr struct1;


   int degree;

   int degreeStart = 0, degreeEnd = 45;

   double pi = 3.14159;



   char imageFileName[100];

   char outputFileFormat[100];

   strcpy(outputFileFormat,"rotatetest/%04d.jpg");



   readJpeg( struct1.inputImage, "SP2/sample1/closing/0000.jpg" );



   //object to rotate

   struct1.height = struct1.inputImage.height();

   struct1.width = struct1.inputImage.width();

   printf("%d %d\n",struct1.width,struct1.height);


   struct1.outputImage.resize( struct1.width,struct1.height );

   struct1.outputImage = struct1.inputImage;

   pthread_t th[degreeEnd];



   for(degree = 0; degree <= degreeEnd; degree++){

   	struct1.thetaR = (degree*pi)/180;	

	printf("entered: %d \n",degree);			

   	for (struct1.x = 0; struct1.x < struct1.width; struct1.x++){

	   	pthread_create(&th[struct1.x],0,threadRotateFunction, (void *)&struct1); 
   		

   	}//for x
   	for (int m = 0; m < struct1.width;  m++){
		pthread_join(th[m], 0);	
   	}//for m	

	
	sprintf( imageFileName, outputFileFormat, degree + degreeStart);

	writeJpeg( struct1.outputImage, imageFileName, 65 );

   }//while degree
   
	return 0;

}




[/HTML]

for every increment of degree to rotate, i create threads by the width of the img and each thread will rotate in each y coordinate.

to trace, i tried to print each entrance in degree and the entrane in x-loop.

but it turned out:

entered: 0
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 101 102 103 104 105 106 107 108 109 110 111 112 113 114 Cannot access pixel (115,300) of Image[300 x 300]!

it wasn't even able to access all the x's in the 0 degree.

can anyone give me any sugestion? tnx.

---

### Post by stroyan on 2008-01-10
Without seeing your code it is very difficult to say what problem you are encountering now.  If your code actually prints the "Cannot access pixel (115,300) of Image[300 x 300]!" message, what is the test that causes it to print that?

Your program could reach a resource limit creating threads.  You don't test the return value of pthread_create.  You could easily run out of address space if your program is creating a large stack for each thread.  The stack space per thread can be limited by using "ulimit -s" before starting a program or by using pthread_attr_setstacksize with thread attributes passed into pthread_create.  Here is a small example limiting stack size.
```
#include <pthread.h>
#include <stdio.h>
#include <errno.h>
#include <stdlib.h>
#include <unistd.h>

void *thread_func(void *arg)
{
    return (void*) 0;
}

int main(int argc, char *argv[])
{
    int result;
    pthread_attr_t attr;
    pthread_t thread;

    result = pthread_attr_init(&attr);
    if (result) { perror("pthread_attr_init failed"); exit(1); }
    result = pthread_attr_setstacksize(&attr, 1024*1024);
    if (result) { perror("pthread_attr_setstacksize failed"); exit(1); }
    result = pthread_create(&thread, &attr, thread_func, (void *) 0);
    if (result) { perror("pthread_create failed"); exit(1); }
    result = pthread_join(thread, NULL);
    if (result) { perror("pthread_join failed"); exit(1); }
    return 0;
}
```

As I wrote before, creating so many threads is not best for speed.  The possible speed benefit from multiple threads depends on having enough processor cores to run those threads in parallel.  There is overhead from threading.  Creating and destroying short lived threads is particularly expensive.

  The mutex used in your threadRotateFunction is preventing parallelism in the interesting computation code.  But it is not protecting the struct1.x field that is modified by main while threadRotateFunction is reading it.

  There are other opportunities to improve the speed of your code.  You could explicitly keep the result of the sin and cos functions in a variable.  You could use double precision nx and ny variables that are incremented by a precomputed amount for each increment of y.

---

### Post by nephritiri on 2008-01-11
hi.thank you very much for the supplied code. it really helped.
i was able to run  it and was able to write images. but i think, i agree with you that struct1.x was not protected here.

here's my modified code:

[HTML]
#define IMAGE_RANGE_CHECK



#include "image.h"

#include "jpegio.h"

#include "color.h"

#include "string.h"
#include "pthread.h"

struct spaceAttr       
{ int height;
  int width;
  double thetaR;
  RGBImage outputImage,inputImage;
  int degree;
};



void *threadRotateFunction(void *struct1){
	int h = ((struct spaceAttr *) struct1) -> height;
	int w = ((struct spaceAttr *) struct1) -> width;
        int deg = ((struct spaceAttr *) struct1) -> degree;
	double theR = ((struct spaceAttr *) struct1) -> thetaR;
	RGBImage outImg = ((struct spaceAttr *) struct1) -> outputImage;
	RGBImage inImg = ((struct spaceAttr *) struct1) -> inputImage;
	char imageFileName[100];

        char outputFileFormat[100];
        strcpy(outputFileFormat,"rotatetest/%04d.jpg");
        outImg.setAll(0);

	int halfHeight = h/2;

   	int halfWidth = w/2;
	int nx, ny, a,b;			

		for (a = 0; a < w; a++){
		for (b = 0; b < h; b++){

		nx = (int)((a-halfWidth)*cos(theR) - (b-halfHeight)*sin(theR)+halfWidth);

	    	ny = (int)((a-halfWidth)* sin(theR) + (b-halfHeight)*cos(theR)+halfHeight);

		if(nx < w && nx >= 0 && ny < h && ny >=0){

			outImg(nx,ny) = inImg(a,b);}
		}//foy b
		}//for a

		sprintf( imageFileName, outputFileFormat, deg);
		writeJpeg( outImg, imageFileName, 65 );	
}//threadRotateFunction



int main (int argc, char *argv[]) {
   
   spaceAttr struct1;

   int degreeEnd = 360;

   double pi = 3.14159;


   readJpeg( struct1.inputImage, "SP2/sample1/closing/0000.jpg" );



   struct1.height = struct1.inputImage.height();

   struct1.width = struct1.inputImage.width();

   struct1.outputImage.resize( struct1.width,struct1.height );

   struct1.outputImage = struct1.inputImage;
   
   int result;
   pthread_attr_t attr;
   result = pthread_attr_init(&attr);   
   pthread_t th[struct1.height];



   for(struct1.degree = 0; struct1.degree <= degreeEnd; struct1.degree++){

   struct1.thetaR = (struct1.degree*pi)/180;	   
			
    		if (result) { perror("pthread_attr_init failed"); exit(1); }
    		result = pthread_attr_setstacksize(&attr, 1024*1024);
    		if (result) { perror("pthread_attr_setstacksize failed"); exit(1); }	

	   	pthread_create(&th[struct1.degree],&attr,threadRotateFunction, (void *)&struct1);	   	
		if (result) { perror("pthread_create failed"); exit(1); }
   }//for degree
	
   for(struct1.degree = 0; struct1.degree <= degreeEnd; struct1.degree++){
		result = pthread_join(th[struct1.degree], NULL);
    		if (result) { perror("pthread_join failed"); exit(1); }		    				
   }//for degree
	return 0;

}//MAIN
[/HTML]

some images are written with the same filenames, thus, overwriting some.the filename should be increasing in order.
i.e.
Successfully written JPEG: rotatetest/0032.jpg
Successfully written JPEG: rotatetest/0039.jpg
Successfully written JPEG: rotatetest/0039.jpg
Successfully written JPEG: rotatetest/0039.jpg
Successfully written JPEG: rotatetest/0032.jpg
Successfully written JPEG: rotatetest/0032.jpg

in this modifies code's case, struct1.degree (counter for the increasing order of filename)  here was kinda not protected.... can someone give me an idea?
i reviewed mutexes.. but there's no shared resources here. hmm. (please correct me if im wrong)

---

### Post by nephritiri on 2008-01-11
im sorry. the i.e there was the wrong output.

---

### Post by stroyan on 2008-01-11
The struct1 variable is a shared resource.  The duplicate values for struct1.degree are to be expected.  The main function's thread gets to run for a while, creating threads and incrementing struct1.degree.  Then the other threads get their turns.  Several new threads run and look at the same current value of struct1.degree.  The values that each thread looks at need to be stable.  The simplest way to do that is to have a different "struct spaceAttr" for every thread.  You could use an array of structs or use malloc and free.  If you use malloc then either the thread would need to call free for the passed address or the main function should do it after pthread_join.

Your "pthread_t th[struct1.height];" array is the wrong size.  You use it with index values up to degreeEnd-1.

---

### Post by nephritiri on 2008-01-11
hi. thank you. now, im enlightened. i now use an array of structures. one structure for each thread. and i was able to write the images in sequence.

btw,thank you for correcting the size of array of threads. iv changed it from:

>pthread_t th[struct1.height]
to 
>pthread_t th[degreeEnd+1] 

the same with the size of array of structures

>spaceAttr struct1[degreeEnd+1]

because the range of degree of rotation will be [0,360]

however, i didnt get to print all the frames.after a number of them, i get a segmentation fault. i think iv been blinded to see what's wrong here. can you help me see it?

---

### Post by stroyan on 2008-01-12
A segmentation fault could result from many different causes.  It may be that the library functions you are calling are not actually thread-safe.  It might be that they just react badly to hitting a resource limit resulting in a failed system call.  You could run your program under a debugger or enable core dumping so you can look at the stack trace leading to the segmentation fault.  You could run your program under the strace command to see if there are any interesting system call failures leading up to the segmentation fault.

---

### Post by nephritiri on 2008-01-12
...

---

### Post by nephritiri on 2008-01-12
ur ryt. m kinda getting to be frustrated... but im still trying here. its my first tym to use pthreads. i use the g++ compiler in linux and i thought that since pthreads are already supported in linux, i can just include in it my code. 

hmmm. it may be a silly Q but are those header files im including you were pertaining to,maybe non-thread safe?

maybe il go try your other suggestions- debugger and stack trace.

thank so much though.
youve been a big help. :)

---

### Post by stroyan on 2008-01-12
The functions that you are using certainly could be unsafe with threading.  It takes hard work and attention to detail to make a library thread-safe.  If a library does not document that it is thread-safe then you should assume that it is not.  When libraries are thread-safe they often document additional requirements for how to use them safely from multiple threads.  Calling the wrong functions is one of the most common errors made by programmers trying to use threads.
I don't recognize the headers and functions that you are using.  I find no package in the ubuntu distribution that provides a jpegio.h file.  What libraries are you using?

---

### Post by nephritiri on 2008-01-12
i use the imagelab class library... it was created by my professor. we use it in school in the computer graphics class.

all those header files are already included in that lib.

i tried my luck in my other forum - linux forum. and someone suggested:

> I look at your code and I don't see one of the subsidiary threads use any data from another subsidiary thread, and I don't see your main thread use any of the results from any of the subsidiary threads. So why not just use fork() instead of pthreads? At least this will ensure that the same process will blow up as the one the misbehavior occurs in, which is a huge plus when debugging. Further, if you use fork(), struct1 doesn't have to be an array. Depending on how type RGBImage is laid out, you could have memory leaks if you use fork(), but they won't consume as much memory as having an array of 361 of these suckers.

And speaking of memory allocation, do you check the result of each and every malloc() in your program? I don't see any malloc() in the code you presented, but how about in functions readJpeg() and writeJpeg()?

And speaking of function writeJpeg(), you call it inside each of your threads. Does it call any functions which are not thread safe?

do you think it's more recommended to use fork() in my case?
coz im going to convert this code to rotate a 3D volume which really takes a lifetime to run.

---

### Post by CptPicard on 2008-01-12
> **nephritiri said:**
> 
coz im going to convert this code to rotate a 3D volume which really takes a lifetime to run.

Will you derive any real benefit from threading in this  case? I've got an intense number-crunching app which I data-parallelize for exactly 4 cores because that's what we've got, but no more, because there is no more gain...

---

### Post by stroyan on 2008-01-12
Using fork in place of pthread_create might help to avoid problems caused by library routines that are not thread-safe.  But the overhead of fork can be even more than pthread_create.  As I have written many times and CptPicard just wrote, you don't get the  best performance by starting so many threads (or processes).  You should limit them to the number of available CPU cores.  With bigger 3D data sets there can be important performance issues caused by threads fighting for cache lines and memory bandwidth.

---

### Post by nephritiri on 2008-01-13
i guess im stuck here. i only use an average pc. single-processor. 512mb ram.thats why im finding out a way to make my program run faster yet utilize only these available resources..

there's a lot of research and experiment to do i guesss,hehe. ur thoughts have helped enough.

thanks you so much though guys.

---

### Post by CptPicard on 2008-01-13
> **nephritiri said:**
> i guess im stuck here. i only use an average pc. single-processor. 512mb ram.thats why im finding out a way to make my program run faster yet utilize only these available resources..

You're not stuck, you're just doing it wrong. Spamming insane amounts of threads on hardware that essentially just supports a single CPU-intensive thread is not going to help in any way. Threading is only helpful when you're either waiting for I/O most of the time, or when you genuinely have a lot of processors/cores to utilize. Otherwise you're just shooting yourself in the foot.

---

### Post by nephritiri on 2008-01-13
hi. now i see why im wrong. you're right. maybe its not really recommended for me to use pthreads. 

i tried my luck by using fork() and wait() functions. and it worked. i didnt hit segmentation fault.
now, i have to extend this code to 3D rotation.which requires 4 for-loops. i do hope it will work.

thanks a lot! =>

---

