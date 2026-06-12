---
title: "Inconsistent (and wrong) output using boost::thread"
date: 2008-12-28
forum: Programming Talk
---

### Post by Fox5 on 2008-12-28
Alright, I'm trying to learn some basic threading and this is a problem I've been banging my head up against for a while.
I'm doing some image manipulation using boost::numeric::ublas::matrix, which I believe is supposed to be thread safe, but as soon as more than 1 concurrent thread is involved I get radically different results on every execution.
I believe my algorithms should be order independent (or close to it).

My first bit of calling code looks like:
```

do
{

	n = 0;
	
	
	for (int structNum = 0; structNum < 8; structNum++)
	{
		for (int x = 0; x < numthreads; x++)
		{
			
			tg.create_thread(boost::bind(&decompose::octagon,d,boost::ref(M),boost::ref(copy),x,structNum, boost::ref(n), boost::ref(bar)));
		}
		//d->octagon(M,copy,0,structNum,n);
		
		bar.wait();
		
		tg.join_all();
		
		
		d->copy(copy,M);

	}
	if (n == 0)
		break;
	numLoops ++;

}while(n);

```

And it's calling:
```

void decompose::octagon(matrix4D &M, matrix4D &copy, int threadNum, int structNum, int &n, boost::barrier &bar)

```

I have two copies of my matrices, an original and a copy. For each call to octagon, the original is only used as read only while the copy has its corresponding values modified. I send the function what thread number this is (a global variable stores the number of threads) and the general algorithm through the matrix is:

```

	for (x = threadNum; x < (h); x += num)
	{
		for (y = threadNum; y < (w); y+= num)

```
Where threadnum is the current thread number, and num is the total number of concurrent threads. As such, no threads should ever operate on the same element in the matrix object (unless I'm wrong about matrix being thread safe).

I expected tg.join_all() to cause each thread to finish execution before program flow would continue. I wasn't sure if it wasn't doing that, so I tried adding a barrier condition (bar) with a count of 3, though that doesn't seem to make a difference. Still, each thread calls bar.wait() upon finishing, and so does main after creating both threads. Also, join_all doesn't seem to destroy threads, so threadgroup tg ends up containing hundreds of threads by the end of the program execution. I assume that they're mostly all just idle, but I suppose it could be a problem.

Am I missing something major with my threading design?

---

### Post by Cracauer on 2008-12-29
I didn't review your code line by line, but the first thing that comes to mind is that if they say that these functions are "thread-safe", then that means while they operate on different matrices, on entirely separate arguments.

---

### Post by Fox5 on 2008-12-29
Why can't they access different elements of the same matrix? They lie in different locations in memory, right, so long as the matrix is not resized?

---

### Post by Cracauer on 2008-12-29
I can't look more into it right now, but they might share per-matrix control elements?

---

### Post by catchmeifyoutry on 2008-12-29
> **Fox5 said:**
> 
```

		/* ... */
		for (int x = 0; x < numthreads; x++)
		{
			/* ... */	

tg.create_thread(boost::bind(&decompose::octagon,d,boost::ref(M),boost::ref(copy),x,structNum, boost::ref(n), boost::ref(bar)));
			/* ... */
		}
		/* ... */

```

And it's calling:
```

void decompose::octagon(matrix4D &M, matrix4D &copy, int threadNum, int structNum, int &n, boost::barrier &bar)

```

...
I send the function what thread number this is (a global variable stores the number of threads) and the general algorithm through the matrix is:

```

	for (x = threadNum; x < (h); x += num)
	{
		for (y = threadNum; y < (w); y+= num)

```
Where threadnum is the current thread number, and num is the total number of concurrent threads. As such, no threads should ever operate on the same element in the matrix object (unless I'm wrong about matrix being thread safe).


I find this confusing, maybe you can explain. Is the num variable in the decompose::octagon function the same (value) as numthreads in the loop? I.e. is num the total number of threads in the whole program, or the number of threads for each decompose::octagon() call? If this is a program wide global, why does it have a different name at both lines, of it isn't global shouldn't you pass numthreads some where to the decompose::octagon() function? And why do you pass structNum, what does that count? Also, what does the outer structNum loop do? Do you change the matrix M somewhere in that loop?

---

### Post by Fox5 on 2008-12-29
Num is an object variable indicating the total number of threads.
Numthreads is the same thing, but in main().
StructNum is which masking element is being applied on that iteration. I have 8 different arrays each with a different orientation, and structNum just keeps track of which one I'm using.

I figured out the problem though, it's with my inner loop with for (y = threadNum; y < (w); y+= num). By incrementing both x and y by the number of threads each time, I'm missing elements, and probably wreaking all sorts of havok on some of the algorithms.
I've got it sorted out now. Boy, it's one of those annoying things that just seems so simple when you finally get it.

---

### Post by dribeas on 2008-12-29
Believing that it is thread safe and knowing that it is are complete different matters. I did not find any thread safety guarantee in the docs but then again I only gave it a few seconds.

ublas::matrix is a wrapper around both dense and sparse matrices. While I don't know the library and I don't have experience in the domain, I can but assume that dense matrices will be stored in n-dimensional arrays, while sparse matrices will probably have some space optimizations.

With n-dimensional arrays, there should be no problem with more than one thread accessing different parts of the array, or if more than one thread access in a read-only way. But if the internal representation changes it might just happen that those operations are not thread safe.

I would go ahead and ask in boost mailing list.

---

