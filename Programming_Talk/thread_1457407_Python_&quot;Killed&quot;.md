---
title: "Python &quot;Killed&quot;"
date: 2010-04-18
forum: Programming Talk
---

### Post by imaginaryfruit on 2010-04-18
What does it mean if I get the message "Killed" after hitting Ctrl+C whilst running a Python script? 

Usually hitting Ctrl+C gives the message "KeyboardInterrupt", but when running my program for a slightly larger integer I got the message "Killed" instead. Does this mean that the numbers became to large to cope with?

I tried googling but wasn't successful, so explanation would much appreciated -- even a link to a useful webpage would help.

Thanks!

---

### Post by OgreProgrammer on 2010-04-18
It would depend on what you were doing, but it almost sounds like it was a cleaner interrupt than a regular keyboard interrupt. 

Normally keyboard interrupt means "stop NOW" while a killed process does a proper clean up and exit. A little bit different than organic kills.

---

### Post by Cracauer on 2010-04-18
Hold on a sec.

I think you mean to say if you run your program with "a larger integer" (you realize that's useless info here, right), then you get the "killed" message *without* you hitting Control-C.

Is that correct?

---

### Post by imaginaryfruit on 2010-04-18
Sorry, "a larger integer" was indeed unhelpful. I'm trying to find the decomposition groups of polynomials mod p for various values of p. For one polynomial, p=37 gave an answer within a few seconds (and if interrupted by Ctrl+C, gave the KeyboardInterrupt message I'm used to). For the same polynomial, p=43 gave no response for several minutes, and when Ctrl+C is pressed, gives the "Killed" message.

Could it be that the process has already been killed by the time I press Ctrl+C, but simply hasn't yet printed the message? And what sort of problem causes Python to decide to kill a process?

Thanks for the replies!

---

### Post by azagaros on 2010-04-18
You were doing a mathematical algorithm without bounds checking....

"Integer too Large" is one thought... 64 bit integer signed is 63 bits with 1 bit for sign...

if the math crosses into the 65th bit it will cause a interrupt on the processor.  App will be killed instantly.

---

### Post by Cracauer on 2010-04-18
> **imaginaryfruit said:**
> Sorry, "a larger integer" was indeed unhelpful. I'm trying to find the decomposition groups of polynomials mod p for various values of p. For one polynomial, p=37 gave an answer within a few seconds (and if interrupted by Ctrl+C, gave the KeyboardInterrupt message I'm used to). For the same polynomial, p=43 gave no response for several minutes, and when Ctrl+C is pressed, gives the "Killed" message.

Could it be that the process has already been killed by the time I press Ctrl+C, but simply hasn't yet printed the message? And what sort of problem causes Python to decide to kill a process?

Thanks for the replies!

Hmmm, that's a little weird.

If you had said you die without Control-C and a message "killed", then I would have replied with that your program probably ran out of swapspace system-wide and the kernel decided to kill the python process when it had to pick something. That would match both the error message and the fact that you are doing some exponential problem.

Are you doing recursion there? Any chance you can describe in more detail what is going on inside the program?

Are you on a 32 bit OS and how much swap do you have? Does the swap get filled up when you run with the large value?

It could still what I say above and either as you say a delayed message, or that the Python interpreter tried to deal with an out-of-memory condition (or stack overflow) during this time.

---

### Post by Cracauer on 2010-04-18
> **azagaros said:**
> You were doing a mathematical algorithm without bounds checking....

"Integer too Large" is one thought... 64 bit integer signed is 63 bits with 1 bit for sign...

if the math crosses into the 65th bit it will cause a interrupt on the processor.  App will be killed instantly.

I don't think Python has integer overflow checking once you run out of "long" and even if they did, why wouldn't they throw an exception?

The processor itself does not throw an interrupt (exception in CPU speech) on integer overflow or underflow. It sets a bit that is ignored by C, C++, Java etc but read by many other languages to either fall back to a bignum (or floating point in the case of same naive languages) or to raise an exception (language exception, not CPU exception).

---

### Post by imaginaryfruit on 2010-04-18
I tried some different polynomial-prime combinations, and one did indeed give me MemoryError, so presumably that was the problem all along -- though I don't know why it didn't give me that message for the earlier examples. 

I checked my program, and realised that while I'd found a way to avoid using huge polynomials, I hadn't removed the statements defining them. I removed those and it works fine now.

What is swap? (I'm new to programming, as you may have guessed.)

Thanks for all the help!

---

### Post by ssam on 2010-04-18
are you using an external library that might catch the keyboard interrupt and give its one message?

when i run long simulations i usually have some sort of progress output to that i can see that its still working. suppose you have something that loops a million times, then use
```

for x in xrange(1e6):
  if (x%1e4 == 0): print x, "% done"
  ...

```
to watch progress.

PS: are you using numpy/scipy. if you are doing mathematical things you should have a look at them.

---

### Post by Cracauer on 2010-04-18
> **imaginaryfruit said:**
> I tried some different polynomial-prime combinations, and one did indeed give me MemoryError, so presumably that was the problem all along -- though I don't know why it didn't give me that message for the earlier examples. 

I checked my program, and realised that while I'd found a way to avoid using huge polynomials, I hadn't removed the statements defining them. I removed those and it works fine now.

What is swap? (I'm new to programming, as you may have guessed.)

Thanks for all the help!

Assuming that my knee-jerk assessment that you were facing an out-of memory condition is correct, you ran out of backing storage for read/write memory pages.

The total amount of read/write memory pages all your programs can have is RAM + paging space (minus kernel internal things, of course). Plus readonly file mappings which are mostly "free" since they don't need backing space.

Use `free` and `cat /proc/swaps` to monitor swapspace. If the assumption is correct you'll see how it gets all eaten up and then the kernel kills your memory hog.

ssam, he's not getting the same behavior when he's using the same program with a different upper bound. If he would be using a library that catches signals he would get the same behavior with the smaller upper bound.

---

### Post by soltanis on 2010-04-18
> **Cracauer said:**
> I don't think Python has integer overflow checking once you run out of "long" and even if they did, why wouldn't they throw an exception?


Python would throw an exception if you were overflowing something, but it seems that whenever Integers get too big, python automatically transitions them to bignums (and these don't seem to have a limit beyond the size of your available memory).

> 
The processor itself does not throw an interrupt (exception in CPU speech) on integer overflow or underflow. It sets a bit that is ignored by C, C++, Java...

When you overflow an integer in C, the result is implementation-dependent and undefined. There is no exception that is thrown. This is the cause of many silent errors (or, in the case you were using that integer to do memory operations, quite noisy errors that usually involve "Segmentation fault").

EDIT:
And to answer the original concern, Linux has something called the OOM killer which automatically kills processes that are consuming too many system resources (see man getrlimit and setrlimit to see how Linux sets resource limits). When the system's resource limits are exceeded by a program, the process is sent certain signals, which, if it ignores those signals, it will be sent SIGKILL, which has two effects:
1) Immediately terminates the running process with no prior notification to that process; so in fact, the process has absolutely no opportunity to flush its buffers or finish writing data to files. This can be bad.
2) Sends the message "Killed" to the tty the process is on.

I invite you to observe this effect by opening two terminals, and in one of them, running the following command:
```

yes

```

Then go to the other terminal, and type
```

pkill -9 yes

```

You should see the "Killed" message, and yes will stop its output completely.

---

