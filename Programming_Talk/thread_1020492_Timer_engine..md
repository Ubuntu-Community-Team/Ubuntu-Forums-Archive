---
title: "Timer engine."
date: 2008-12-24
forum: Programming Talk
---

### Post by Thesuperchang on 2008-12-24
Hi, I'm creating a timer engine for some future programs. I've come a little bogged down in the optimisation phase. Initially this engine was hopeless, however I'm now squeezing some required speed out of it. My first approach was to use pretest loops, however speed was dismal;
real	0m12.019s
user	0m3.760s
sys	0m8.261s
This yielded results 20% slower then the target mark. The most alarming of this was the 82% CPU time used on system function calls. I'd imagine this is from the [PHP]clock()[/PHP] function call.

The code was reworked and changed to mostly post-test loops. This yielded more appeasing results;
real	0m10.013s
user	0m3.008s
sys	0m7.000s
Appeasing as it looks, I hit my target time. However the sys time is stupidly large. This code is still as slow as a turtle. To run this engine alone would require 70% of the CPU time which is not feasible for anything worth timing accurately.

Current version of my timer engine.
[PHP]#include <time.h>
#include <stdbool.h>

#define BREAKDOWN 1	// The breakdown of instructions x OPTIME per second
#define OPTIME	  1 	// Amount of instructions per second's/breakdown

#define RUNTIME	  10	// TESTING PURPOSES ONLY. This defines how long the program will be executed for.

int main(void) {
	clock_t init;
	int timeCount;
	
	int i = 0;	// TESTING PURPOSES ONLY.
// - *** TIMING *** -
	for(;;) {
		init = clock();
		timeCount = 0;
/* TESTING */	if(i++ >= RUNTIME * BREAKDOWN) break; // TESTING PURPOSES ONLY. After every iteration here, there should be a 1 second time difference.
		do {
			if((timeCount++ < OPTIME)) { // Amount of iterations per breakdown time.
// - *** TIMING *** -

				/* Instruction
				 Executable statement
				 Executable statement
				 Executable statement
				*/

// - *** TIMING *** -
			}
		} while( ((clock() - init) < CLOCKS_PER_SEC/BREAKDOWN)); // Rather then spending valuable time doing a pre check, a post check will drain buffered time. Idealy buffer time should be plentyfull.
	}
// - *** TIMING *** -

	return 0;
}[/PHP]

From what I can see, the idea is to process the engine mechanics in the time I buy for myself via fast execution of the instructions. (Buffered time) To do this I move all possible checks to after the execution of the instructions if possible.

My second idea for major optimisation is to eliminate the need to call the [PHP]clock()[/PHP] function. To successfully do this, I intend to calculate the average iterations of the loop that occurs within the intended loop time. This could be achieved by using one resource demanding loop every 4 seconds or so and then applying the statistics for the next 3 seconds of runtime.

Another optimisation I had in mind was the use of recursion rather then the do while loop. I was thinking that perhaps the instructions could be enclosed inside a function. The function is then to be declared as inline or static and recursion is used for X amount of cycles (BREAKDOWN). By using inline I'll avoid the chaos of building and gutting the stack. This method would also rid the copious amounts of comparison checks.

As you can see, the code is in its infancy and will require quite a bit of optimising before it can be of any use to me. I was hoping that perhaps someone could give me a few pointers on what could be done as well as if my ideas are feasible or not.

Oh yeah, and merry Christmas.

Thanks in advance,
C. Anderson

---

### Post by dwhitney67 on 2008-12-24
What is a "timer engine"?  I'm fluent in English, C, and C++, however I haven't a clue what your trying to accomplish.  Google didn't yield an answer either.

Could you please elaborate a little more?  You wrote that you are trying to optimize your program.  It doesn't get more optimized than this:
[php]
int main()
{
  /* Instruction
     Executable statement
     Executable statement
     Executable statement
   */
}
[/php]
All kidding aside, I can only gather from the code you posted, you are trying to delay the execution of critical code by wrapping it up in collection of for/do loops, thus governing how often the program acquires the use of the CPU.  If this is correct, for what purpose are you doing this?

---

### Post by Thesuperchang on 2008-12-24
The idea is to slow down the execution of the CPU. An example of this would be in the implementation of an emulator. My CPU is clocked @ 1GHz per core, however a system I may want to emulate may be clocked at say 33MHz. This code is designed to run code at a speed of whatever the program requests by changing the constants. Timer engine was a name I assigned it by myself.

---

### Post by catchmeifyoutry on 2008-12-25
So you want to delay the execution of the main loop if it goes to fast.
I would keep it simple, and define a target speed as number of milliseconds per iteration. Then, measure time every iteration, see how much time passed since the previous iteration, and if it is too much pass the rest of the time idle. Normally, you could use sleep(uint) to pass time with an idle CPU, but that would happen in terms of seconds. Probably your application would require sub-second control. I believe you could use usleep() instead to stay idle for a given amount of microseconds. A quick google gave me this: [http://www.faqs.org/faqs/unix-faq/faq/part4/section-6.html](http://www.faqs.org/faqs/unix-faq/faq/part4/section-6.html)
Success

---

### Post by dwhitney67 on 2008-12-25
usleep() is now considered to be an obsolete system call (i.e. it could be deprecated at some point in the future).

The preferred system call to use (nowadays) is nanosleep().

---

