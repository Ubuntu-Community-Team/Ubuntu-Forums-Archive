---
title: "Function binding in Python?"
date: 2009-04-19
forum: Programming Talk
---

### Post by NintenDave on 2009-04-19
I'm trying to make a Mandelbrot fractal by using threads to build different chunks of it

```
	n_cpu = cpu_count()
	threads = []
	
	for i in range( n_cpu ):
		left = ( image_width / n_cpu ) * i
		right = left + ( image_width / n_cpu )
		
		calc_area( ( left, 0, right, image_height ), image_size, pixels )
```
What I want to do, assuming it is possible in Python, is on each iteration to create a thread, and add it to the "threads" list, and I want each thread to execute that call to calc_area. What I would do in C++ is bind that function call, because it feels most natural, and that's what I'd like to do in Python, but I don't know how.

Thanks.

---

### Post by CptPicard on 2009-04-20
In languages that support closures, such as python, you just wrap the call in a lambda and define that somewhere where your desired parameters are lexically visible. After that you can call the lambda at will later on and the parameters remain bound to the values. In functional-programming terms, the operation is called "currying" (esp. when you are doing a partial bind and leaving some parameters free). :) Here's a general "bind" function that does what you want:

```

def bind(func, *args, **kwargs):
    return lambda: func(*args, **kwargs)

def foo(x):
    return x + 3

bar = bind(foo,5)

print bar()

```

Of course, you can simplify this in your code just by looping over the chunks you want to produce and sending for each thread a "lambda: calc_area( ( left,..."

---

### Post by NintenDave on 2009-04-20
Thanks, I used the lamda option, I didn't know that was possible :)
But now I'm getting strange thread activity, probably something simple, so I didn't make a new forum thread for it.
Here's my code:

```
	n_cpu = 1
	threads = []
	
	for i in range( n_cpu ):
		left = ( float(image_width) / n_cpu ) * i
		right = left + ( float(image_width) / n_cpu )
		
		call = lambda: calc_area( ( left, 0, right, image_height ), image_size, pixels )
		thread = threading.Thread( None, call )
		thread.start()
		threads.append( thread )
	
	# Now wait for each thread to join
	for thread in threads:
		thread.join()
```

What I see is that when I run with 1 thread, one core reaches 100% usage and stays there, with the other pretty idle, like I expected. But when I use two threads, they cores seem to use opposite speeds, so the program takes several seconds longer to complete.

Is it a problem with my code? Is the problem not well suited to multi-threading?

PS
I'm running on my laptop, but the power is plugged in, so it couldn't be anything to do with the power manager lowering energy use, could it?

PPS
The graphs are attached. The first one is the profile for the program using 2 threads, the second is the profile for the program using 1 thread.

Thankyou.

---

### Post by Greyed on 2009-04-21
You're laboring under the presumption that Python threads are split across cores.  They aren't.  What you're seeing is Python hopping between cores.

[http://ubuntuforums.org/showthread.php?t=797322](http://ubuntuforums.org/showthread.php?t=797322)

---

