---
title: "[C] Multithread includeproblem"
date: 2009-03-24
forum: Programming Talk
---

### Post by heamaster on 2009-03-24
Hi! I wonder what i should include to get this to work:

[PHP]#include <pthread.h>
#include <stdio.h>

void sell_ticket(int agent_id, int tickets_to_sell)
{
	for(int i = 0; i < 10; i++)
	{
		tickets_to_sell--;
		printf("Agent %d sold a ticket\n", tickets_to_sell);
	}
	printf("Agent %d is done\n", agent_id);
}

int main(){

	int tickets_to_sell;
	int agents;

	InitThreadPackage(0);
	for(int i = 0; i < agents; i++)
	{
		char name[32];
		sprintf(name, "Agent %d thread", i);
		ThreadNew(name, sell_ticket, 2, i, ( tickets_to_sell / agents ));
	}
	RunAllThreads();


return 0;
}
[/PHP]

My compiling error is:

implicit declaration of function RunAllThreads
implicit declaration of function InitThreadPackage
implicit declaration of function ThreadNew

---

### Post by dwhitney67 on 2009-03-24
You do not need <pthread.h>

However, you do need to include the header file(s) that contain the declarations for the InitThreadPackage(), ThreadNew(), and RunAllThreads().

You will also need to compile/link the implementation file (or library) for those functions with your main program.  Additionally, you will need to link with the pthread library, using -lpthread.

---

### Post by heamaster on 2009-03-24
I'm compiling with

[PHP]gcc -Wall -c file.c -lpthread -std=gnu99[/PHP]
then
[PHP]gcc -Wall -o file file.c -lpthread -std=gnu99[/PHP]
 but it doesnt work

---

### Post by dwhitney67 on 2009-03-24
Of course it does not work!  You are missing the implementation file for those Thread functions.  You also did not include the header file that defines them.

Where did you get the notion that calling those functions would work?  Is it perhaps possible that you wrote code based on someone's pseudocode?

---

### Post by heamaster on 2009-03-24
got the code from [http://www.youtube.com/watch?v=omE3YYpHhLo&feature=PlayList&p=9D558D49CA734A02&index=14]("http://www.youtube.com/watch?v=omE3YYpHhLo&feature=PlayList&p=9D558D49CA734A02&index=14")
They are using some "thread_107.h", but is there any such headers I can use?

---

### Post by dwhitney67 on 2009-03-24
You need that header file, and if the Thread functions are not implemented in that file, then you will also need the .c file that goes along with it.

The alternative is to implement those methods yourself.  Since it is a given that you are a newbie to POSIX threads, I would definitely recommend that you attempt to implement calls to the pthread library so that you can understand how it all works.

The pthread library calls that you probably need to be aware of at this time are pthread_create() and pthread_join().  Refer to the man-pages for information on these, or just Google for examples.

There is not a pthread library call for pthread_join_any(), but it would be nice if there were.  Thus the only tricky part you will have is figuring out how RunAllThreads() is implemented.

Also, and this is very important... your main() program is the _main-thread_.  If you spawn child-threads (using pthread_create), you cannot let your main-thread terminate, or all of your child-threads will terminate too.  Thus the main-thread should be the last thread to be terminated (exit).

P.S.  I am at my office at this moment; YouTube is a blocked-site, therefore I cannot visit it at this time.

---

