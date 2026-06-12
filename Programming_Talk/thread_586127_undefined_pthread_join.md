---
title: "undefined pthread_join"
date: 2007-10-22
forum: Programming Talk
---

### Post by prachijpp on 2007-10-22
Here is my code:

[COLOR="Red"]#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<time.h>
#include<pthread.h>

pthread_t hour_thread , min_thread , sec_thread;
time_t rawtime;
struct tm *mytime;
		
void set_time() {
	system("clear");
	rawtime = time(&rawtime);
	mytime = localtime(&rawtime);
	printf("Current time : %s" , asctime(mytime));
}

void * update_hour(void *arg) {
	while(1) {
		sleep(1);
		rawtime = time(&rawtime);
		mytime = localtime(&rawtime);
		set_time();
	}
}

void * update_min(void *arg) {
	while(1) {
		sleep(1);
		rawtime = time(&rawtime);
		mytime = localtime(&rawtime);
		set_time();
	}
}

void * update_sec(void *arg) {
	while(1) {
		sleep(1);
		rawtime = time(&rawtime);
		mytime = localtime(&rawtime);
		set_time();
	}
}

int main() {
	int err1 , err2 , err3;
	void *value_ptr;

	set_time();

	if((err1 = pthread_create(&hour_thread , NULL , update_hour , NULL)) != 0)
		printf("\n\tError in creating hour thread : %s" , strerror(err1));

	if((err2 = pthread_create(&min_thread , NULL , update_min , NULL)) != 0)
		printf("\n\tError in creating minute thread : %s" , strerror(err2));
		
	if((err3 = pthread_create(&sec_thread , NULL , update_sec , NULL)) != 0)
		printf("\n\tError in creating second thread : %s" , strerror(err3));
	
	pthread_join(hour_thread , &value_ptr);
	pthread_join(min_thread , &value_ptr);
	pthread_join(sec_thread , &value_ptr);

	return(0);
}[/COLOR]


When I run it I get following error:

[COLOR="Red"]/tmp/ccsOiUW1.o: In function `main':
clock.c:(.text+0x13a): undefined reference to `pthread_create'
clock.c:(.text+0x182): undefined reference to `pthread_create'
clock.c:(.text+0x1ca): undefined reference to `pthread_create'
clock.c:(.text+0x203): undefined reference to `pthread_join'
clock.c:(.text+0x218): undefined reference to `pthread_join'
clock.c:(.text+0x22d): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
[/COLOR]

Header file pthread.h gets included successfully,
so why it is not detecting function pthread_join, pthread_create

---

### Post by slavik on 2007-10-22
did you use option -lpthread ?

---

### Post by dwhitney67 on 2007-10-22
It sure would be nice if you learned how to indent your code.  Also, I hope this code will not be used for anything serious.  With multiple threads running, and all using the same variables to stuff data into them, it's a wonder that your program works.

Btw, each thread is calling time(), localtime(), and then set_time().  The function set_time() is then calling time() and localtime().  Isn't this a little redundant?

If you agree, then remove the redundant calls from your threads.  Then move the declarations for rawtime and mytime inside of set_time().  Then look into protecting the code within set_time() with a pthread_mutex.

I should also add that having the hours, minutes, and seconds threads are also redundant in themselves... unless you plan to do something special within each one at a later time.

---

### Post by bunker on 2007-10-22
Also localtime() is not thread-safe.  You're better off using boost's replacement.  Could save you some head-scratching in the future :).

---

### Post by prachijpp on 2007-11-05
Thanks a lot everyone!
I solved the problem. :)

---

