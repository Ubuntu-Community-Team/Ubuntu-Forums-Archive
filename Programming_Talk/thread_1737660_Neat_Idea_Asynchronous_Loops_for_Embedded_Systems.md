---
title: "Neat Idea: Asynchronous Loops for Embedded Systems"
date: 2011-04-23
forum: Programming Talk
---

### Post by ve4cib on 2011-04-23
I had to do this for an assignment a few weeks back, but it was a neat enough idea that I figured I'd share it with the rest of you.  It's a way of modifying your standard while-loop in C so that the condition is asynchronously checked, allowing the loop to break out anywhere.

The practical application to this isn't necessarily immediately obvious, so let's look at an example.

Say you have a line-following robot.  It's got a light/dark light sensor pointing down.  The goal is to drive around a white surface until you find a dark line, and the follow that line.

Now let's assume that to find the line initially you want to drive in a spiral pattern.  The first code you might try is something like this:

```
while (! lightSensor.isDark() ) {
    driveSpiral("10ms");
}
followLine();
```

The problem is that the light sensor condition is only checked when the driveSpiral function ends.  You could set the length of time you drive in a spiral before checking to be arbitrarily small, but then you're spending a huge amount of time (relatively-speaking) dealing with pushing and popping parameters from the stack.
The implementation we wound up settling on was kind of interesting though.
You could also check the light sensor inside the driveSpiral function, but that requires return codes, and makes driveSpiral less general-purpose, which leads to less-reusable code.

What we ideally want is for the light sensor to generate an interrupt that we can listen for, and use that to break out of the loop immediately.  Otherwise we might risk driving too far and never actually finding the line we're looking for.


So that's the general idea behind the concept.  But how does one go about implementing it?

Well, conveniently the C standard includes the convenient setjmp and longjmp functions, which can be used to break out of a function and pop all the way back up the stack to wherever setjmp was initially called.  Look up setjmp.h for more details on that.

Before continuing I should mention that this assignment was done as an extension to an embedded realtime operating system developed in our lab over the last several years.  You can download the source-code for an older version [here](http://aalab.cs.umanitoba.ca/index.php?option=com_remository&Itemid=35&func=fileinfo&id=29).  It runs on the Robotis CM-5 boards used in the Bioloid robot kits.

The OS we used has support for running multiple threads and a scheduler to change between them.  Stack space is partitioned between tasks, and a timer interrupt drives the task-switching.

So what I did was to allow the OS to inject a function call on top of the call stack when scheduling a thread.  Basically the scheduler calls this function just before popping the CPU state off the stack and returning to the scheduled thread.  This injected function -- dubbed a "monitor thread" by my prof -- can be scheduled just like a real thread.  The idea is that they're small, fast functions that check something and set a global variable that can be checked by other threads.

But -- and this is the neat part -- if the monitor thread has a True/False return you can use that as the condition in a while loop.  If the function returns false then the loop condition failed, and you can call longjmp to break out of a loop running in the main thread.

Here's an example that might make this a little clearer:

```
 // inside a thread

jmpbuf jmp;
int jmpReturn = setjmp(jmp);
if (jmpReturn == 0) {
    // look for the line
    startMonitorThread( checkLightSensor );
    for(;;) {
        driveSpiral("10ms");
    }
}

// the only way to get here is by calling longjmp to exit the infinite loop
followLine();

____________________________________________

int checkLightSensor() {
    return !lightSensor.isDark();
}

____________________________________________

// inside the task-switcher timer interrupt handler

// push CPU state onto stack
...

// schedule the next thread
...

// get the next monitor thread to execute
struct MonitorThread *monitorThread = nextMonitorThread();
int doLongJmp = monitorThread->execute();

// pop next thread's CPU state off stack
...

if (doLongJmp) {
    longjmp( *(monitorThread -> jmpBuffer) );
}
else {
    // return from interrupt
    ...
}
```


So that's the general idea.  One could probably extend this same logic to a real OS by using pthreads and such.  I thought it was a clever little trick that some other programmer out there might find interesting.

I'm interested to hear what other programmers out there think of this little trick.  Have you ever had to do anything similar?  How would you have gone about solving this problem?

Thanks for reading!

---

