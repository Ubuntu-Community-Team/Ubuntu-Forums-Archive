---
title: "Segmentation fault in C program"
date: 2009-08-18
forum: Programming Talk
---

### Post by rahul_shilps on 2009-08-18
Hi all,
 
I am executing a program. I have actually got this program from my friend.
This program is to study and solve the problem of Reader/Writer Problem.
 
But when i execute this program it gives me : /Segmentation error
 
-------------------------------------------------------------------------------------
rdwrt.c
-------------------------------------------------------------------------------------
/* program to study Reader/Writer problem with Semaphore */
 
#include<stdio.h>
#include<pthread.h>
#include<semaphore.h>
 
void reader1();
void writer1();
void reader2();
void writer2();
 
sem_t rsem;
sem_t wsem;
sem_t x,y,z;
 
int rc=0, wc=0;
 
int main()
{
	int r,w,i=0,ch=2;
	pthread_t t1[5],t2[5];
 
	printf ("\n\nEnter the number of READERS: ");
	scanf ("%d", &r);
 
	printf ("\n\nEnter the number of WRITERS: ");
	scanf ("%d", &w);
 
	printf ("\n\nMENU\n\n\t1.READERS HAVE PRIORITY");
	printf ("\n\n\t2.WRITER HAVE PRIORITY");
 
	printf ("\n\n\tENTER YOUR CHOICE:");
	scanf ("%d", &ch);
 
	sem_init(&rsem, 0, 1);
	sem_init(&wsem, 0, 1);
 
	sem_init(&x, 0, 1);
	sem_init(&y, 0, 1);
	sem_init(&z, 0, 1);
 
	if (ch==1)
	{
		pthread_create(&t1[0], NULL, (void *)reader1, 0);
		pthread_create(&t2[0], NULL, (void *)writer1, 0);
 
		for (i=1;i<r-1;i++)
			pthread_create(&t1[i], NULL, (void *)reader1, (void *)i );
 
		for (i=1; i<w-1; i++)
			pthread_create(&t1[i], NULL, (void *)reader1, (void *)i );
 
		for (i=1; i<w-1; i++)
			pthread_create(t2[i], NULL, (void *)writer1, (void *)i);
 
		pthread_create(&t1[w-1], NULL, (void *)reader1, (void *)(w-1) );
		pthread_create(&t2[r-1], NULL, (void *)writer1, (void *)(r-1) );
 
		for (i=0;i<r;i++)
			pthread_join(t1[i], NULL);
 
		for (i=0;i<w;i++)
			pthread_join(t2[i], NULL);
	}
	else if (ch==2)
	{
		pthread_create(&t2[0], NULL, (void *)writer2, 0);
		pthread_create(&t1[0], NULL, (void *)reader2, 0);
 
		for (i=1;i,r-1;i++)
			pthread_create(&t2[i], NULL, (void *)reader2, (void *)i );
 
		for (i=1;i<w-1;i++)
			pthread_create(&t1[i], NULL, (void *)writer2, (void *)i );
 
		pthread_create (&t2[r-1], NULL, (void *)writer2, (void *)(r-1) );
		pthread_create (&t1[w-1], NULL, (void *)reader2, (void *)(w-1) );
 
		for(i=0; i<r; i++)
			pthread_join(t2[i], NULL);
 
		for(i=0; i<w; i++)
			pthread_join(t1[i], NULL);
	}
	else
		printf ("\nINVALID CHOICE....PROGRAM TERMINATED.");
 
	sem_destroy(&rsem);
	sem_destroy(&wsem);
 
	return 0;
}	// main function close
 
 
void reader1 (void *i)
{
	sem_wait(&rsem);
	rc++;
	if (rc==1)
		sem_wait(&wsem);
 
	sem_post(&rsem);
	printf ("\nREADER %d IS READING NOW", (int)i);
	sleep(1);
		sem_wait(&rsem);
	rc--;
	if(rc==0)
		sem_post(&wsem);
 
	sem_post(&rsem);
	printf ("\nREADER %d HAS FINISHED READING");
}
 
void writer1(void *i)
{
	sem_wait(&wsem);
	printf ("\nWRITER %d IS WRITING NOW", (int) i);
	sleep(1);
	sem_post(&wsem);
	printf ("\nWRITER %d HAS FINISHED WRITING");
}
 
void reader2(void *i)
{
	sem_wait(&z);
	sem_wait(&rsem);
	sem_wait(&x);
 
	rc++;
	if(rc==1)
		sem_wait(&wsem);
 
	sem_post(&x);
	sem_post(&rsem);
	sem_post(&z);
 
	printf ("\nREADER %d IS READING NOW", (int)i);
	sleep(1);
	sem_wait(&x);
	rc--;
	if (rc==0)
		sem_post(&wsem);
 
	sem_post(&x);
	printf ("\nREADER %d HAS FINISHED READING");
}
 
void writer2(void *i)
{
	sem_wait(&y);
	wc++;
 
	if (wc==1)
		sem_wait(&rsem);
 
	sem_post(&y);
	sem_wait(&wsem);
	printf ("\nWRITER %d IS WRITING NOW", (int) i);
	sleep(1);
	sem_post(&wsem);
	sem_wait(&y);
	wc--;
	if(wc==0)
		sem_post(&rsem);
 
	sem_post(&y);
	printf ("\nWRITER %d HAS FINISHED WRITING");
}
 
-----------------------------------------------------------------------------------------------------------------------------
 
*****************
O/P:
*****************
Enter the number of READERS: 4
 
 
Enter the number of WRITERS: 4
 
 
MENU
 
	1.READERS HAVE PRIORITY
 
	2.WRITER HAVE PRIORITY
 
	ENTER YOUR CHOICE:1
 
READER 0 IS READING NOW
READER 1 IS READING NOW
READER 2 IS READING NOW
READER 1 IS READING NOW
 **Segmentation fault**
*************************************************
 
Why i am getting this run time error? (as above in bold font)
 
Can you suggest me how can i correct my code?

---

### Post by johnl on 2009-08-18
Hi,

I compiled your program like so (note that the line numbers are way off from the copy-paste I had to do):

```

ledbettj@reznor:~/Projects/stest$ gcc -m32 -Wall test.c -g -o test -lpthread
test.c: In function 'main':
test.c:83: warning: passing argument 1 of 'pthread_create' makes pointer from integer without a cast
test.c:108: warning: left-hand operand of comma expression has no effect
test.c: In function 'reader1':
test.c:160: warning: implicit declaration of function 'sleep'
test.c:172: warning: too few arguments for format
test.c: In function 'writer1':
test.c:188: warning: too few arguments for format
test.c: In function 'reader2':
test.c:230: warning: too few arguments for format
test.c: In function 'writer2':
test.c:267: warning: too few arguments for format

```

You might want to take a close look at these warnings.

But, to solve your SEGFAULT:

```

ledbettj@reznor:~/Projects/stest$ gdb ./test
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(gdb) run
Starting program: /home/ledbettj/Projects/stest/test
[Thread debugging using libthread_db enabled]


Enter the number of READERS: 4


Enter the number of WRITERS: 4


MENU

        1.READERS HAVE PRIORITY

        2.WRITER HAVE PRIORITY

        ENTER YOUR CHOICE:1
[New Thread 0xf7dd76c0 (LWP 11204)]
[New Thread 0xf7dd6b90 (LWP 11207)]

[New Thread 0xf75d5b90 (LWP 11208)]
[New Thread 0xf6dd4b90 (LWP 11209)]
READER 0 IS READING NOW
[New Thread 0xf65d3b90 (LWP 11210)]
READER 1 IS READING NOW
[New Thread 0xf5dd2b90 (LWP 11211)]
READER 2 IS READING NOW
[New Thread 0xf55d1b90 (LWP 11212)]
READER 1 IS READING NOW

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xf7dd76c0 (LWP 11204)]
__pthread_create_2_1 (newthread=0x0, attr=0x0,
    start_routine=0x8048b9b <writer1>, arg=0x1) at pthread_create.c:529
529     pthread_create.c: No such file or directory.
        in pthread_create.c
(gdb) bt
#0  __pthread_create_2_1 (newthread=0x0, attr=0x0,
    start_routine=0x8048b9b <writer1>, arg=0x1) at pthread_create.c:529
#1  0x08048827 in main () at test.c:83

```

You can see that there was a problem creating a thread, and it starts at test.c line 83 (again your line number will be different).  I took a look at this line:

```

        for (i=1; i<w-1; i++)
            pthread_create(t2[i], NULL, (void *)writer1, (void *)i);

```

Based on the rest of your code, it looks like you are missing an address-of operator:
```

        for (i=1; i<w-1; i++)
            pthread_create(**&**t2[i], NULL, (void *)writer1, (void *)i);

```

Hopefully you can see how I debugged this and give it a shot yourself in the future :)

---

