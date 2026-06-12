---
title: "Problem with Programming Threads"
date: 2005-10-02
forum: Programming Talk
---

### Post by skyboy on 2005-10-02
Hi, I have a problem with a thread. I have a thread that listen to the console input during runtime of an application, I can set the console using termio library to the right environment but at the end of the tread when I want to put the console back to normal settings, it doesn't work. The same program when not in a thread works perfectly.
What can be the problem ??

Here is the Code :

#include <sys/types.h>  /* for getppid    */
#include <unistd.h>     /* for getppid    */
#include <pthread.h>    /* for threads    */
#include <stdio.h>      /* for perror etc */
#include <stdlib.h>     /* for exit       */
#include <sys/ioctl.h>
#include <termio.h>
#include <iostream>
#include <fstream>


int flag = 0;

void *keyboard(void*){
    struct termio t1, t2;
    unsigned char in[2];
    int len;

    ioctl(0, TCGETA, &t1);
    t2 = t1;

    t1.c_lflag = 0;
    t1.c_iflag = 0;
    t1.c_cc[VMIN] = 1;
    t1.c_cc[VTIME] = 0;
    ioctl(0, TCSETA, &t1);

    while(1)
    {
        len = read(0, in, 1);
        if (len < 1)
        {
            printf("\nError during read !!\007");
            return(0);
        }
        *in &= 0xFF;
 
        if (*in == 'a')
        {
            printf(" Splicing asked \t");
	    flag = 1;
	//Set watchVariable to 'a'
            return(0);
        }
        if (toupper(*in) == 'Q')
        {
            printf(" Bye bye \t");
            ioctl(0, TCSETA, &t2);
            flag = 2;
            return(0);
        }
        else
        {
            printf(" Splicing NOT asked \t");
	    flag = 0;
	//Set watchVariable to 'a'
            return(0);
        }

	return(0);


    }
}

int main(){
pthread_t tid;

while(1) {
pthread_create(&tid, NULL, keyboard, NULL);
pthread_join(tid, NULL);
if(flag==0) {
	printf("splicing has NOT been asked\n");
	} 
if(flag==1) {
	printf("splicing has been asked\n");
	} 
if(flag==2) {
	printf("Exit the program\n");
	exit(0);
	} 
} 
exit(0);

}

#########################
without thread
 ########################

/* getchar example : typewriter */
#include <stdio.h>
#include <sys/ioctl.h>
#include <termio.h>
#include <iostream>
#include <fstream>

int main (void)

{
    struct termio t1, t2;
    unsigned char in[2];
    int len;

    ioctl(0, TCGETA, &t1);
    t2 = t1;

    t1.c_lflag = 0;
    t1.c_iflag = 0;
    t1.c_cc[VMIN] = 1;
    t1.c_cc[VTIME] = 0;
    ioctl(0, TCSETA, &t1);

    while(1)
    {
        len = read(0, in, 1);
        if (len < 1)
        {
            printf("\nError during read !!\007");
            return(1);
        }
        *in &= 0xFF;
 
        if (*in == 'a')
        {
            printf(" Splicing asked");
	//Set watchVariable to 'a'
        }
        printf("\n");

        if (toupper(*in) == 'Q')
        {
            ioctl(0, TCSETA, &t2);
            return(0);
        }
    }
}

---

### Post by thumper on 2005-10-02
Firstly I would ask you to surround code blocks with the ```
 tags.

I can not really follow what your program is trying to do at all.  Can you explain it?
What is the purpose of the ioctl calls?

Also I am curious, what do you expect [code]*in &= 0xFF;
``` to do?  Because I don't think it does anything given that *in is an unsigned char.

Now my C is a little rusty as I do mostly C++ but have you checked the docs on ioctl?

---

### Post by skyboy on 2005-10-02
Ok, I'll try to be more clear:
I just start a thread that listen to keybord input, key pressed by user, and simply print a message on the screen.
I'm just wondering why the code doesn't work the same way when embedded in a thread !! What doens't work is that 
line " ioctl(0, TCSETA, &t2);" .

here is the code cleaned :)

```

#include <sys/types.h>  /* for getppid    */
#include <unistd.h>     /* for getppid    */
#include <pthread.h>    /* for threads    */
#include <stdio.h>      /* for perror etc */
#include <stdlib.h>     /* for exit       */
#include <sys/ioctl.h>
#include <termio.h>
#include <iostream>
#include <fstream>


int flag = 0;

void *keyboard(void*){
    struct termio t1, t2;
    unsigned char in[2];
    int len;
    ioctl(0, TCGETA, &t1);
    t2 = t1;
    t1.c_lflag = 0;
    t1.c_iflag = 0;
    t1.c_cc[VMIN] = 1;
    t1.c_cc[VTIME] = 0;
    ioctl(0, TCSETA, &t1);

    while(1)
    {
        len = read(0, in, 1);

        if (*in == 'a')
        {
            printf(" Splicing asked \t");
	    flag = 1;
            return(0);
        }
        if (toupper(*in) == 'Q')
        {
            printf(" Bye bye \t");
            ioctl(0, TCSETA, &t2);
            flag = 2;
            return(0);
        }
        else
        {
            printf(" Splicing NOT asked \t");
	    flag = 0;
            return(0);
        }
	return(0);
    }
}

int main(){
pthread_t tid;

while(1) {
pthread_create(&tid, NULL, keyboard, NULL);
pthread_join(tid, NULL);
if(flag==0) {
	printf("splicing has NOT been asked\n");
	} 
if(flag==1) {
	printf("splicing has been asked\n");
	} 
if(flag==2) {
	printf("Exit the program\n");
	exit(0);
	} 
} 
exit(0);

}

```

---

### Post by thumper on 2005-10-02
Well so much for keeping the indentation...

Am I right in assuming that the ioctl with TCGETA is trying to set the standard input to be asynchronous for gets?  In which case why do this if running a separate thread for reading the input.  One of the reasons for putting it in another thread is so you can treat local funciton calls in a synchronous manner.

---

### Post by skyboy on 2005-10-02
> Am I right in assuming that the ioctl with TCGETA is trying to set the standard input to be asynchronous for gets? In which case why do this if running a separate thread for reading the input. One of the reasons for putting it in another thread is so you can treat local funciton calls in a synchronous manner.
No, this is done so that you don't have the hit enter after pressing a key.

---

### Post by thumper on 2005-10-02
Why not use something like getc or getchar?

---

### Post by skyboy on 2005-10-02
because those function freeze the execution of the program till a key is pressed.

---

### Post by thumper on 2005-10-02
But if it is on a different thread, why worry?

---

### Post by LordHunter317 on 2005-10-02
You're returning from the keyboard() function prematurely.  Why are you using return when it looks like you want continue?

---

### Post by skyboy on 2005-10-03
> You're returning from the keyboard() function prematurely. Why are you using return when it looks like you want continue?

Thanks for your answer but return() is done just to gain speed in the process.
```
printf(" Bye bye \t");
ioctl(0, TCSETA, &t2);
flag = 2;
return(0);
```

The point here is that the ```
ioctl(0, TCSETA, &t2);
``` doens't execute or if it does, it doesn't have the same effect when it is executing in the tread than in a normal environment. It doesn't give my console the correct settings back.

---

### Post by cactus on 2005-10-03
Well, it looks like the thread is not effecting the parent environment for some reason. I would suggest you simply place your ioctl command before your main app exit, instead of at the end of the thread. Then you won't have to deal with any potential thread/environment/scope issues.

---

### Post by thumper on 2005-10-03
[QUOTE=skyboy]Thanks for your answer but return() is done just to gain speed in the process.[/QUOTE]Perhaps you are using return where you should be using continue?
I was looking at your function again and I agree with **LordHunter317** in that you have four return statements in the function and you only reset ioctl at one of those return points.
This is what I think may have been intended based on your initial post:
```
void *keyboard(void*) {
struct termio t1, t2;
unsigned char in[2];
int len;
ioctl(0, TCGETA, &t1);
t2 = t1;
t1.c_lflag = 0;
t1.c_iflag = 0;
t1.c_cc[VMIN] = 1;
t1.c_cc[VTIME] = 0;
ioctl(0, TCSETA, &t1);
while(1)
{
len = read(0, in, 1);
/* you removed your len check */
if (toupper(*in) == 'Q')
{
printf(" Bye bye \t");
flag = 2;
break;
}
if (*in == 'a')
{
printf(" Splicing asked \t");
flag = 1;
}
else
{
printf(" Splicing NOT asked \t");
flag = 0;
}
}
ioctl(0, TCSETA, &t2);
return(0);
}

```
This follows the single exit point idiom, which I don't necessarily think is useful everywhere, but adds readability to this.
BTW I looks as if the **code** blocks are no longer preserving spaces.  That's a real fubar!

---

### Post by thumper on 2005-10-03
[QUOTE=cacti]Well, it looks like the thread is not effecting the parent environment for some reason. I would suggest you simply place your ioctl command before your main app exit, instead of at the end of the thread. Then you won't have to deal with any potential thread/environment/scope issues.[/QUOTE]
Given the main waits for the started thread to finish, it would be sufficient to do the ioctl prior to returning from that thread.  Problem was he wasn't.

---

### Post by skyboy on 2005-10-03
Thanks guys but none of the advices worked better.
Sure, Thumper you add clarity to the code and made it more logical, but even so it is obvious that before returning it should set back the original mode of the console, still it doesnt work.
Even if I try to set up the console mode before the thread starts, in the main() environment, same things happen.
By the way, try to run it, you will see it by yourself.
compile with the -pthread flag.
thanks anyway for your help. It is great.

---

### Post by thumper on 2005-10-03
OK, found your problem (well at least the one your are talking about).

Change the **exit(0)** in the main while loop to a **break**, and move the initial ioctl to the start of main, and the setting it back to the end of main before the last exit.

I noticed several things while compiling and using your code however.  Firstly you are compiling as C++ not C, this is apparent by your use (or non use) of <iostream> and <fstream>.  Have you tried:
```
char c;
std::cin >> c;
```

Also you are starting and stopping threads with no real purpose.  I think that what you really want is to start up the thead once, not every time through the main while loop, and change your inter-thread communication.  I suggest you look at conditions or semaphores.  Conditions would probably suit you better though.

I can recommend the book "Programming with POSIX Threads".  It is all C, but can easily be wrapped with some classes, or look at something like boost threads.

---

### Post by skyboy on 2005-10-03
Thanks for the tips. But I still can't manage the get back the console in normal mode. Just in case I didn't really get what you said, coulp you please copy paste the code that is working for you.
I also know about the c/c++ code, but I found that function in c, and tried to make it worked in c++. of course, the example I used now is just for learning purpose not for anything definite. :) but true, looks like bad programming :D
```
char c;
std::cin >> c;
```
this is good too but you have to hit enter to validate the key pressed.
if you know how to do it more easily so that I can just press a letter without having to hit enter, I am opened to the suggestion.

Thanks very much for your great help

---

### Post by skyboy on 2005-10-03
I am now using the  cin<<c; function. it is more simple and at least don't get those nasty behaviour of the console.
But if you know how to be able to get a key press without having to hit enter, I would be happy with it :)

thanks again

---

### Post by thumper on 2005-10-03
[QUOTE=skyboy]I am now using the  cin<<c; function. it is more simple and at least don't get those nasty behaviour of the console.
But if you know how to be able to get a key press without having to hit enter, I would be happy with it :)
thanks again[/QUOTE]
How about you tell us what you are really trying to accomplish and why you need non-buffered input?

---

### Post by thumper on 2005-10-03
[QUOTE=skyboy]Just in case I didn't really get what you said, coulp you please copy paste the code that is working for you.[/QUOTE]
Here you go (skipped headers and global flag):

```

void *keyboard(void* arg){
   unsigned char in[2];
   int len;
   
   while(1)
   {
      len = read(0, in, 1);
      if (len < 1)
      {
         printf("\nError during read !!\007");
         return(0);
      }
      if (*in == 'a')
      {
         printf(" Splicing asked \t");
         flag = 1;
         //Set watchVariable to 'a'
         return(0);
      }
      if (toupper(*in) == 'Q')
      {
         printf(" Bye bye \t");
         flag = 2;
         return(0);
      }
      else
      {
         printf(" Splicing NOT asked \t");
         flag = 0;
         //Set watchVariable to 'a'
         return(0);
      }
      
      return(0);
   }
}

int main(){
   struct termio t1, t2;
   
   ioctl(0, TCGETA, &t1);
   t2 = t1;
   
   t1.c_lflag = 0;
   t1.c_iflag = 0;
   t1.c_cc[VMIN] = 1;
   t1.c_cc[VTIME] = 0;
   ioctl(0, TCSETA, &t1);

   pthread_t tid;
   
   while(1) {
      pthread_create(&tid, NULL, keyboard, NULL);
      pthread_join(tid, NULL);
      if(flag==0) {
         printf("splicing has NOT been asked\n");
      }
      if(flag==1) {
         printf("splicing has been asked\n");
      }
      if(flag==2) {
         printf("Exit the program\n");
         break;
      }
   }

   ioctl(0, TCSETA, &t2);

   exit(0);
}
```

---

### Post by skyboy on 2005-10-03
:D
it is for a real time MPEG2TS splicing tool that can splice 2 mpeg2ts streams. I want to interact and give command to the splicer so that when I press 's' for example, it is splicing the streams.
Is your curiousity satified :D (kidding)

Non buffered input is just nicer than buffered one. That is the main point :rolleyes: 

thanks

---

### Post by skyboy on 2005-10-03
Your code is working pretty well, I have to admit :D
Thanks

But still if you figure out easier way, I would be very happy.
thanks again for your help

---

### Post by thumper on 2005-10-03
It is not C++ that is buffering your input, but the terminal I/O.  You still need to set the ioctl commands to control the terminal even in C++.

Here is a small C++ bits that works
```
#include <termio.h>
#include <iostream>

int main()
{
   char c = 0;

   struct termio t1, t2;
   
   ioctl(0, TCGETA, &t1);
   t2 = t1;
   
   t1.c_lflag = 0;
   t1.c_iflag = 0;
   t1.c_cc[VMIN] = 1;
   t1.c_cc[VTIME] = 0;
   ioctl(0, TCSETA, &t1);

   while (std::cin >> c) {
      if ('Q' == ::toupper(c)) {
         std::cout << "Done\n";
         break;
      }
      if ('a' == c) {
         std::cout << "Splicing asked\n";
      }
      else {
         std::cout << "Splicing NOT asked\n";
      }
   }
   ioctl(0, TCSETA, &t2);
   // EOF, fail or bad gets here
   return 1;
}

```

---

### Post by thumper on 2005-10-03
It seems as if the parsing of the **code** blocks is different for the quick reply, hence the nice indenting now ;-)

---

### Post by thumper on 2005-10-03
Should be ```
return 0;
``` but that bit was a carry over from earlier test bits which didn't need to reset the terminal I/O.

---

### Post by thumper on 2005-10-03
A more C++ version:
```
#include <termio.h>
#include <iostream>

class TerminalControl
{
   public:
      TerminalControl()
      {
         termio curr;
         ::ioctl(0, TCGETA, &curr);
         old_ = curr;

         curr.c_lflag = 0;
         curr.c_iflag = 0;
         curr.c_cc[VMIN] = 1;
         curr.c_cc[VTIME] = 0;
         ::ioctl(0, TCSETA, &curr);
      }
      ~TerminalControl()
      {
         ::ioctl(0, TCSETA, &old_);
      }
   private:
      termio old_;
};

int main()
{
   // destructor nicely handles cancelling
   TerminalControl set_unbuffered_input;
   char c = 0;

   while (std::cin >> c) {
      if ('Q' == ::toupper(c)) {
         std::cout << "Done\n";
         // destructor resets terminal control
         return 0;
      }
      if ('a' == c) {
         std::cout << "Splicing asked\n";
      }
      else {
         std::cout << "Splicing NOT asked\n";
      }
   }
   // EOF, fail or bad gets here
   return 1;
}

```

---

### Post by thumper on 2005-10-03
Here, try this one.  It has the threads...
```
#include <termio.h>
#include <iostream>
#include <pthread.h>

class TerminalControl
{
   public:
      TerminalControl()
      {
         termio curr;
         ::ioctl(0, TCGETA, &curr);
         old_ = curr;

         curr.c_lflag = 0;
         curr.c_iflag = 0;
         curr.c_cc[VMIN] = 1;
         curr.c_cc[VTIME] = 0;
         ::ioctl(0, TCSETA, &curr);
      }
      ~TerminalControl()
      {
         ::ioctl(0, TCSETA, &old_);
      }
   private:
      termio old_;
};

struct Params
{
      Params() : splice(false), ok(true) {}
      volatile bool splice;
      volatile bool ok;
};

void* keyboard(void* arg)
{
   Params& params = *(reinterpret_cast<Params*>(arg));
   char c = 0;
   while (std::cin >> c) {
      if ('Q' == ::toupper(c)) {
         params.ok = false;
         break;
      }
      if ('a' == c) {
         params.splice = true;
      }
      else {
         params.splice = false;
      }
   }
   return 0;
}

int main()
{
   // destructor nicely handles cancelling
   TerminalControl set_unbuffered_input;
   Params params;
   
   pthread_t id = 0;
   pthread_create(&id, 0, keyboard, &params);

   while (params.ok) {
      std::cout << (params.splice ? "Busy splicing\n" : "Busy not splicing\n");
      // do the actual work instead of sleeping
      ::sleep(1);
   }
   // don't really need to join the thread...
   pthread_join(id, 0);

   // main is the one function you don't really need to specify a return for.
}

```
Questions welcome... even from **LordHunter317** 8)

---

### Post by thumper on 2005-10-03
Can you tell I'm a bit bored at work? 8)

---

### Post by skyboy on 2005-10-03
Thanks for that very nice C++ code. Nevertheless, I will have to still use a thread for catching the key press event but that isn't difficult.
Thanks very much.

---

### Post by skyboy on 2005-10-03
Ok, you are way faster than me :)
thanks for the thread one !!
Shall I forward my work to you :D ??

---

### Post by thumper on 2005-10-03
You could always post a reference to it when you have it done.

---

### Post by skyboy on 2005-10-03
hehe,
The splicing tool is done already and work nicely. This was just to make usability nicer. If you want to I can send you the code, it's GPL and uses Live.com library.

---

### Post by skyboy on 2005-10-03
here is my code is a way I can use it.
But something strange happen ; the first key press take awhile to be detected, after that it is really fast, do you know why ??
```
#include <termio.h>
#include <iostream>
#include <pthread.h>

bool flag = false;

class TerminalControl
{
   public:
      TerminalControl()
      {
         termio curr;
         ::ioctl(0, TCGETA, &curr);
         old_ = curr;

         curr.c_lflag = 0;
         curr.c_iflag = 0;
         curr.c_cc[VMIN] = 1;
         curr.c_cc[VTIME] = 0;
         ::ioctl(0, TCSETA, &curr);
      }
      ~TerminalControl()
      {
         ::ioctl(0, TCSETA, &old_);
      }
   private:
      termio old_;
};

struct Params
{
      Params() : splice(false), ok(true) {}
      volatile bool splice;
      volatile bool ok;
};

void* keyboard(void* arg)
{
   Params& params = *(reinterpret_cast<Params*>(arg));
   char c = 0;
   while (std::cin >> c) {
      if ('Q' == ::toupper(c)) {
         params.ok = false;
         break;
      }
      if ('s' == c) {
        params.splice = true;
	flag = true;
      }
      else {
         params.splice = false;
	 flag = false;
      }
}
   return 0;
}

int main()
{
   // destructor nicely handles cancelling
   TerminalControl set_unbuffered_input;
   Params params;
   
   pthread_t id = 0;
   pthread_create(&id, 0, keyboard, &params);

   while (params.ok) {
	if(flag == true){
	      std::cout << (params.splice ? "Busy splicing\n" : "Busy not splicing\n");
	}
	else {
	      std::cout << (params.splice ? "Busy splicing\n" : "Busy not splicing\n");
	}
      // do the actual work instead of sleeping
      //::sleep(1);
   }
   // main is the one function you don't really need to specify a return for.
}

```

---

### Post by thumper on 2005-10-03
The initial pause is the starting of the keyboard reading thread.

Also why use the global flag?  What is what params.splice is for.

---

### Post by skyboy on 2005-10-03
the Global Flag is a mistake :D I actually use the params.splice

---

### Post by skyboy on 2005-10-03
the forum really has trouble with posting CODE

---

### Post by LordHunter317 on 2005-10-03
**Thumper**:
Your code is fine, despite it's lack of error checking on the ioctl calls.
It could be written (and probably should be written) as a simple non-member function, that performs the call, calls the function it's passed as a pointer, then restores the terminal state.
In this case, the choice is really a wash, except that the syntax for the non-member function is more compact, and it's more in line with the C++ standard.  So IOW, I would do something like:```
#include <termio.h>

template <typename Func>
void
unbuffered_io_call(Func f) {
	termio curr, old;
	::ioctl(0, TCGETA, &curr);
	old = curr;

	curr.c_lflag = 0;
	curr.c_iflag = 0;
	curr.c_cc[VMIN] = 1;
	curr.c_cc[VTIME] = 0;	
	::ioctl(0, TCSETA, &curr);

	f();

	::ioctl(0, TCSETA, &old_);
}
```Or similar (untested, still needs error code ;)).  This is more STL-like, which is why I prefer it.  Either solution can be trivally extended to operate on any FD 
The really clever solution of course would be to write iostream mainpulators to perform this, but it would be iostreams-implementaion dependent, unless you did a lot of extra, painful work.

---

### Post by thumper on 2005-10-03
[QUOTE=LordHunter317]Your code is fine, despite it's lack of error checking on the ioctl calls.
[/QUOTE]
Pot... Kettle... Black  :???:

---

### Post by LordHunter317 on 2005-10-03
What?  That was in jest, and not meant to be taken seriously.  Apologies if you were upset.

---

### Post by thumper on 2005-10-03
No, seriously, I don't have a problem with this.  I just find it funny.

I understand your approach to the code and I agree that it is valid.  I would like you to try to write the code that uses your approach though.

The use of constructors and destructors for this type of control is a standard C++ idiom (acquisition is initialisation) that is also used for things like mutexs.  Simple objects on the stack then contol resource return, in this case the resetting of the terminal settings.  

Providing a templated function such as the one you demonstrated is a more functional approach.  No less wrong than what I did, just different.  I am curious however to see how much more clear it makes the code 8)

---

### Post by LordHunter317 on 2005-10-03
[QUOTE=thumper]I would like you to try to write the code that uses your approach though.[/quote]If you really want, I'll write a copy of the program that uses that function, but it's pretty obvious.  It's no different from using any STL algorithm function that takes a function argument: e.g., std::for_each.

> The use of constructors and destructors for this type of control is a standard C++ idiom (acquisition is initialisation) that is also used for things like mutexs.Yes, but actual objects are used so operator-overloading can be providing to make the resource management types more like the primitive types.  In this case, there's no reason to do that, so an actual class has little advantage.

If all you need to do is run fixed code before and after a function, a non-member function is preferable because it's less prone to misuse, and it's a better form of encapsulation: a user can't mistakenly instantiate the code, or have any scoping issues of any sort.  

> I am curious however to see how much more clear it makes the code 8)Mostly because it looks like a STL algorithm function, which means it's much more consistent with the standard.  This is by far the biggest and most importance difference. It doesn't require the user to declare an instance of the object, which means it's more memory efficent and eaiser to use because there's no way to have scoping issues.  Both issues are small, admittedly.

---

### Post by thumper on 2005-10-04
[QUOTE=LordHunter317]If you really want, I'll write a copy of the program that uses that function, but it's pretty obvious.  It's no different from using any STL algorithm function that takes a function argument: e.g., std::for_each.[/QUOTE]
I know how I would do it.  What I am interested in is how *you* would do it.  Also to demonstrate to our readers :)

[QUOTE=LordHunter317]If all you need to do is run fixed code before and after a function, a non-member function is preferable because it's less prone to misuse, and it's a better form of encapsulation: a user can't mistakenly instantiate the code, or have any scoping issues of any sort.[/QUOTE]
I don't follow.  How is it less prone to misuse and how do you mistakenly instantiate the code?  Why do you believe that it is a *better* form of encapsulation.  Having an object to record state, update state in the ctor and revert state in the dtor encapsulates the data and function calls, so how can a non-member function encapsulate it better?

[QUOTE=LordHunter317]Mostly because it looks like a STL algorithm function, which means it's much more consistent with the standard.  This is by far the biggest and most importance difference. It doesn't require the user to declare an instance of the object, which means it's more memory efficent and eaiser to use because there's no way to have scoping issues.  Both issues are small, admittedly.[/QUOTE]
I'm not sure why making the functionality live in a templated non-member function is so important.  C++ is a multi-paradigm language and the generic programming is just one of the paradigms that it supports, so why is that more important than a simple object?

Also the whole intent of the object is to be controlled by the scope.  That is why it is done that way 8)

---

### Post by LordHunter317 on 2005-10-04
> **thumper]I don't follow.  How is it less prone to misuse and how do you mistakenly instantiate the code?[/quote]Consider something of the form:```
void
my_io_func() {
   TerminalControl control said:**
> Why do you believe that it is a *better* form of encapsulation.More is hidden, which is the whole point.

> so how can a non-member function encapsulate it better?Because quite literally, more is hidden.  Even if I used an object internally in the non-member function, the client never has to deal with it, which is better encapsulation.

> I'm not sure why making the functionality live in a templated non-member function is so important.Because it's best way to make the interface easy for a client to use, and hard to break.  Even in subtle, nonobvious ways.

> Also the whole intent of the object is to be controlled by the scope.  That is why it is done that way 8)But it fails at doing that.  The programmer must explictly figure out the correct scope, and bugs can occur if he's wrong.  With the non-member function, the scope is forced upon him and is constant.   The latter is much harder to create errors with.

---

### Post by thumper on 2005-10-05
[QUOTE=LordHunter317]Consider something of the form:```
void
my_io_func() {
TerminalControl control;
for(i=0; i<20; i++) {
char foo = get_terminal_char();  // Where terminal char gets a single character.
}
}
```Obviously, all calls are done asynchronously.   But lets say some comes along later and modifies my_io_func():```
void
my_io_func() {
TerminalControl control;
for (i=0; i<20; i++) {
char foo = get_terminal_char();
}
func_that_can_only_be_used_synchronously  // XXX: Bug introduced due to scoping of TerminalControl.
}
```Obviously, this is easy to fix: move TerminalControl inside the for loop, or into a scope block surronding the for loop to fix the scoping problem.
But with my solution, the scoping problem cannot exist in the first place.  Modification to the existing code, except what is called by unbuffered_io_func() which your code also has a problem with, will not introduce any bugs due to the terminal being left in an asynchronous state when it shouldn't be.   Your code has the potential to introduce subtle bugs because it requires an explicit object instaniation.
[/QUOTE]
Well that just doesn't make sense.  The function my_io_func, which you might have called through your template function could still be altered by to include the func_that_can_only_be_used_synchronously and you **still** have the problem that the function is called with I/O in the wrong state, except now there is no info in the my_io_func that says it is all async.

Yours is just another approach, but I don't think it is "better".

---

### Post by LordHunter317 on 2005-10-05
> **thumper]Well that just doesn't make sense.  The function my_io_func, which you might have called through your template function could still be altered by to include the func_that_can_only_be_used_synchronously and you **still** have the problem that the function is called with I/O in the wrong state, except now there is no info in the my_io_func that says it is all async.[/quote]Yes, you're correct.  Your approach has the same problem though, so it's irrelevant.  There's no way to prevent (trivially) someone from passing a function to unbuffered_io_func() that can't be used in that context.  Not unless you come up with a concept or traits check for I/O calls, which isn't really germane.

However, let's consider the most obvious approach using my method:```
void
my_io_func() {
	for (i=0 said:**
> Yours is just another approach, but I don't think it is "better".Many books agree with me, specifically *Effiective C++, Third Edition.*  Mr. Myers goes as far to say that non-member, non-friend functions should be preferred whenever possible:> Prefer non-member non-friend functions to member fuctions.  Doing so increases encapsulation, packaging flexibility, and functional extensibility.

The STL also agrees with me as well, as most everything that can be reasonably defined as a non-member, non-friend function is.

---

### Post by thumper on 2005-10-06
The fundamental comes down to this:

Is the terminal I/O state a resource that needs to be managed?

If it is, then an object to control the resource is the best way, c.f. smart pointers,  std::vector, et al.

---

### Post by LordHunter317 on 2005-10-06
[QUOTE=thumper]The fundamental comes down to this:

Is the terminal I/O state a resource that needs to be managed?

If it is, then an object to control the resource is the best way, c.f. smart pointers,  std::vector, et al.[/QUOTE]Do the words false dichotomy mean anything to you?

You've provided **no** proof as to why that's the best way in C++, and I've provided multiple explanations as to why it isn't.

I would generally agree with you that an object is the best way to control the lifetime of another **object**.

But we're not controlling **objects** are we?  No, we simply want to run some code before and after **some other code**.  Last I checked, functions in C++ aren't first-class, so this case doesn't decompose into the above case.   

If this was C# with it's using construct, or any functional language with objects (e.g., CLOS, Javascript, etc.) then I'd agree with your form.

But this is C++, and functions aren't first class.  Therefore, there's a difference declaring an object that performs something when it leaves scope, and declaring a function that performs a fixed set of actions and then calls another function.  The differences is that latter's actions have fixed scope: they will always occur before the call to passed function is made and after the passed function is returned.  There is no way around that.  In the case of the former, that's not true.  It's only true when the **programmer** declares the object before making the call to the "passed function", and makes sure the object leaves scope immediately after the passed function.

Only, it's possible for the programmer to get that wrong. 

And that's ignoring the entire convention argument, to which you have no defense.

---

### Post by thumper on 2005-10-06
Let's not get too uptight now...

> we simply want to run some code before and after some other code
Isn't that what you are doing to close a file or delete memory?  All programs are just running code.

I'm more interested in the semantics and efficiency.  Calling setting and resetting code every time in a loop (as your example does) goes against the general coding guideline of "Don't pessimize prematurely".  Use scope as it is designed.

There are many parts of the standard library that use RAII as the main idiom, so saying a templated function is "more standard" is a load of bollocks.  

If we are going to quote Meyers, how about:
> Item 13: Use objects to manage resources

You can't stop bad programmers from breaking code, full stop.  No come back to that one.

---

### Post by LordHunter317 on 2005-10-06
[QUOTE=thumper]Isn't that what you are doing to close a file or delete memory?[/quote]No.  In that case, we want to run some code on **object destruction**.   That's not the same as running some code before/after some arbitrary function f().

> I'm more interested in the semantics and efficiency.My code has clearer semantics and is no less efficent.

> Calling setting and resetting code every time in a loop (as your example does) goes against the general coding guideline of "Don't pessimize prematurely".So you factor the loop into the I/O function, or a function that calls it, which is trivial enough.  It's not like it's something you don't have to do for the STL *anyway*, so I'm not sure how valid of an argument this is.

> Use scope as it is designedThe prinicpal purpose of scope is to  control **lifetime** issues, and my solution does that **better** than yours.  Meaning, I'm using scope more correctly.

> There are many parts of the standard library that use RAII as the main idiom,Demonstrate a **single** STL member that uses RAII in the manner you do, because none do.  They use it to manage **resources** only. 

There is no resource to manage here, so RAII makes no sense by definition.  You can't acquire or initialize a resource when no resource exists.

We don't have any state to maintain, unless we artifically create it.  We want to perform an single asynchronous I/O operation or set thereof.  After they're done, we want to go back to synchronous mode.  No resource there.   

As such, we want the interface that forces that behavior to occur in the most situations, which is mine.

> so saying a templated function is "more standard" is a load of bollocks. No, it isn't.  Non-member functions are preferred wherever practical.  You've yet to show why a class should be preferred over a non-member function in this case, except for claiming RAII, which is a non-sequitur.  That idiom doesn't fit here. 

>  Item 13: Use objects to manage resourcesWonderful, no show the resource.  The problem here is that there is no resource.

> You can't stop bad programmers from breaking code, full stop.Yes, but you can make it **difficult**, which is worthwhile to do so.

> No come back to that one.Then why the suggestion: "Make interfaces easy to use, and hard to break,".  By you reasoning, that suggestion shouldn't make any sense, yet it's the standard mantra for class designers in C++.

---

### Post by thumper on 2005-10-06
You are missing my entire point.

The I/O state **is** (or can be thought of as) a resource that is managed.

---

### Post by LordHunter317 on 2005-10-06
[QUOTE=thumper]The I/O state **is** (or can be thought of as) a resource that is managed.[/QUOTE]Yes, but not in the context of a traditional resource managing object.

Resource managing objects perform an action at the creation of **another** object, and then when the resource manging object is destroyed, it performs another action.

This is true of std::auto_ptr, boost::shared_ptr, etc.  

Now, where is the other object?  There isn't one, which is why a resource-manging class doesn't fit.  Unless you had it take a function object or override operator(), either of which makes it **equivalent** to my solution.

[edit]In otherwords, a resource manager is a container object.  Your object isn't containing anything, so it doesn't fit the design.  And if you modified it to contain something, it would become identical to my solution, except requiring explict instantiation, leading to the class of bugs I noted above.

You still haven't addressed the fundamental scoping flaw with your solution, though you keep trying to dodge it.  **In the face of the class of bugs your solution has that mine does *not*, how is yours *better***?

---

### Post by thumper on 2005-10-06
I'm not trying to dodge it, I was trying to see if you would come to the realisation as I did.

What happens to this code when f() throws?
```
template <typename Func>
void
unbuffered_io_call(Func f) {
	termio curr, old;
	::ioctl(0, TCGETA, &curr);
	old = curr;

	curr.c_lflag = 0;
	curr.c_iflag = 0;
	curr.c_cc[VMIN] = 1;
	curr.c_cc[VTIME] = 0;	
	::ioctl(0, TCSETA, &curr);

	f();

	::ioctl(0, TCSETA, &old_);
}
```
That's why we use objects with destructors.

---

### Post by LordHunter317 on 2005-10-06
Trivial to correct, you use an object internally, and wrap it's existence in the function.  Then you return to syncrhonous mode in all cases, and you get correct scoping.

Yes, that was a bug in my code.  However, it's correctable.  The scoping issues with your solution **are not** correctable, without turning your code into my code.   They're a **design**, not an implementation flaw.

---

### Post by LordHunter317 on 2005-10-06
To be fair, that flaw does make my code near identical to yours.

However, I still prefer my form, because unlike wrapping someting in a std::auto_ptr, TerminalControl is not inoccuous.  It has potential side effects on any function call, while the only side-effect of having a std::auto_ptr wrapped object in scope longer than necessary is excessive memory utilization.

However, it won't break your code.  Having TerminalControl is scope longer than necessary will likely break your code (in non-subtle ways, non-obvious ways) so providing a non-member function to control it is worthwhile, as the scope is absolutely critical here.

---

