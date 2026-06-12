---
title: "Looking for suggestions"
date: 2013-12-10
forum: Programming Talk
---

### Post by amir2 on 2013-12-10
I am looking for a way to send an array of objects into a randomly generated function and get data back like this

data = randomFunction(data); 

The random Function needs to be generated at runtime. My first idea was to just use a function pointer(C++) to point at a char[], but after thinking about it, running random programs in C++ can cause some problems, and I need a way to kill the function if it gets stuck in a loop. 

I am open to any language.

---

### Post by neural_adapter on 2013-12-11
I am a little puzzled about your question. In general it is not possible to determine if a program is stuck in a loop (i.e. won't terminate) or is running normally. This problem is a different version of the famous undecidable Halting problem.

It might be possible to kill the execution of the function by using a timer though.

If you would provide some more details about what you are trying to do, it will be easier for people here to help you.

---

### Post by trent.josephsen on 2013-12-11
What does it mean for a function to be "randomly generated"?

What does it mean for a "randomly generated function" to have an argument?

Must a "randomly generated function" terminate?

If it does terminate, does it have a meaningful return value or side effects?

If it doesn't terminate, is it even a function?

What do you hope to learn from this exercise?

---

### Post by amir2 on 2013-12-11
I guess I need to explain it more...

Your can pass anything into any random binary file and call it a function(99% of the time it will loop endless, overflow stack give meaningless  results).  The idea is to create a function, that is not optimized, and compare; take that function, give it an input, time it, and then give the generated function(which will start as simply 0) the same input. If the output is the same and it done it faster, repeat for every possible input; if it fails(too much time or wrong results), 1 to there function and repeat. There needs to be way to kill a function that goes over it's time. 

In theory it works, in practice it is hard to do; the processes becomes exponentially harder, so even a supercomputer couldn't do more than a simple function,and the other problem is that there are many that will kill your computer hidden in there. For example, you  WILL run into this exact code and many others like it

myObject hello()
{
   char *bye = 0; 
   while(1)
   {
        bye* = 0;
        bye++; 
   }

   return 1/0; 

}


If you don't have experience with c++, that will crash your computer faster than window 8.

---

### Post by ofnuts on 2013-12-12
And what do you expect from this, except participating to the global planet warming by overheating your CPU? How many runnable (I won't even say "useful") programs fit in 10 bytes? and with 10 bytes you can generate 2^80 programs (which is more or less 10^24).

---

### Post by trent.josephsen on 2013-12-12
Perhaps amir2 works for D-Wave.

Ctrl-C should take care of any infinite loops you encounter, unless your "function" goes so far as to register a SIGINT handler, but that's such a vanishingly small probability as to be not worth considering. Even then you can take care of it with kill -9. Unless it turns out to be a forkbomb, but that probably won't happen before the heat death of the Universe, so I wouldn't worry about it.

---

### Post by nidzo732 on 2013-12-12
Do you realy expect that you can randomly generate a valid function. The machine language is simple but it has it's rules.
A random stream of bytes probably wouldn't be a valid function.
It would have to generate proper opcodes, addresses (even if you get lucky with opcodes, there is little chance of avoiding segfaults) and it would have to generate proper code for getting arguments and returning values, not to mention the stack management.
If you run it a billion times you might get lucky and it might generate a working program.

---

