---
title: "Need a little Java help.."
date: 2007-09-28
forum: Programming Talk
---

### Post by LPomfrey on 2007-09-28
I've got to..
> # Write a "void" method called "timer()" using a "while" loop that will run for 1.0 seconds and will print to the screen every time 100 more loops have been run. Change the code so that it only writes to the screen every 10000 loops. What does this tell you ? For this task you may wish to use the following :

    * The following code determines the current time to the nearest msec since January 1st 1970 : "long timeNow = System.currentTimeMillis();"
    * Recall the use of the remainder operator, which returns the remainder when "ia" is divded by "ib" : "int iremainder = ia % ib;"
For a programming course I'm taking as part of a physics course at uni.

What I have so far is:
```
	public void timer() {
		boolean time;
		long starttime = System.currentTimeMillis();
		int y = 0;
		time = true;
		while ( time ){
			int i = 0;
			while (i < 100) {
				long timenow = System.currentTimeMillis();
				long diff = timenow - starttime;
				long tremainder = diff % 1000;
				if ( tremainder == 0 ) {
					i++;
				}
			}
			
			int wait = 100;
			int iremainder = i % wait;
			if ( iremainder == 0 ) {
				y++;
				int howlong = y * wait;
				System.out.println(howlong);
			}

		}
			
	}
```
Which doesn't seem to be working at all (well, it's counting up in 100's but not every hundred seconds.) 

I know this should be simple but I can't get my head around it. 

Any help would be much appreciated.

---

### Post by Ramses de Norre on 2007-09-29
How I understand your question: your loop should run for 1000s, so I've put **(System.currentTimeMillis()-time)<1000** in the while statement with time being the time when the loop starts.
You then want every 100 loops to be written to screen, so in the easiest case you'd set one if statement:
```
if(loops%100==0)
{
    System.out.println("A loop has passed!");
}
```

And now one extra: you should only write data once every 1000 loops, so instead of directly printing the string I'd append them to a StringBuilder (which is faster than a plain string for this purpose).
You then use a similar if statement as the one for detecting the 100 loops event and print the builder to the screen. And because (loops%1000) can only be true if (loops%100) is also true, you can put the second if statement inside the first one (so you'll run less tests and your code will be faster).

The method:
```
public void timer()
{
    long time=System.currentTimeMillis();
    int loops=0;
    StringBuilder out=new StringBuilder("");
    while((System.currentTimeMillis()-time)<1000)
    {
        if(loops%100==0)
        {
            out.append("100 loops have passed!\n");
            if(loops%1000==0)
            {
                System.out.println(out);
            }
        }
        loops++;
    }
}
```

---

### Post by LPomfrey on 2007-09-29
> **Ramses de Norre said:**
> How I understand your question: your loop should run for 1000s, so I've put **(System.currentTimeMillis()-time)<1000** in the while statement with time being the time when the loop starts.
You then want every 100 loops to be written to screen, so in the easiest case you'd set one if statement:
```
if(loops%100==0)
{
    System.out.println("A loop has passed!");
}
```

And now one extra: you should only write data once every 1000 loops, so instead of directly printing the string I'd append them to a StringBuilder (which is faster than a plain string for this purpose).
You then use a similar if statement as the one for detecting the 100 loops event and print the builder to the screen. And because (loops%1000) can only be true if (loops%100) is also true, you can put the second if statement inside the first one (so you'll run less tests and your code will be faster).

The method:
```
public void timer()
{
    long time=System.currentTimeMillis();
    int loops=0;
    StringBuilder out=new StringBuilder("");
    while((System.currentTimeMillis()-time)<1000)
    {
        if(loops%100==0)
        {
            out.append("100 loops have passed!\n");
            if(loops%1000==0)
            {
                System.out.println(out);
            }
        }
        loops++;
    }
}
```

Thanks a lot. :) 
The only problem now is that it seems to be printing out constantly, rather than waiting for 100 seconds.

```
public void timer() {
		boolean time;
		time = true;
		while( time ){
			long starttime = System.currentTimeMillis();
			int i = 0;
			int printevery = 100;
			StringBuilder out=new StringBuilder("");
			while ( (System.currentTimeMillis() - starttime) < 1000 ){
				if(i % printevery == 0)
				{
					out.append("The set number of loops have passed!\n");
		            if(i % 1000 == 0)
		            {
		                System.out.println(out);
		            }
		        }
		        i++;

			}
		}	
	}
```

---

### Post by Ramses de Norre on 2007-09-29
Why do you make a boolean time that is set to true, then put while(time) and never change the boolean again? Your algorithm runs infinite?

And what do you mean by waiting 100s? You mean that after 0 loops a line gets printed? Thats easily circumvented:
```
public void timer()
{
    long time=System.currentTimeMillis();
    int loops=0;
    StringBuilder out=new StringBuilder("");
    while((System.currentTimeMillis()-time)<1000)
    {
        if(loops!=0 && loops%100==0)
        {
            out.append("100 loops have passed!\n");
            if(loops%1000==0)
            {
                System.out.println(out);
            }
        }
        loops++;
    }
}
```

Your coding style is pretty hard to read, it makes no sense to make a variable (in casu printevery) to be read out only once and "i" is less descriptive as "loops".

---

### Post by LPomfrey on 2007-09-29
> **Ramses de Norre said:**
> Why do you make a boolean time that is set to true, then put while(time) and never change the boolean again? Your algorithm runs infinite?

And what do you mean by waiting 100s? You mean that after 0 loops a line gets printed? Thats easily circumvented:
```
public void timer()
{
    long time=System.currentTimeMillis();
    int loops=0;
    StringBuilder out=new StringBuilder("");
    while((System.currentTimeMillis()-time)<1000)
    {
        if(loops!=0 && loops%100==0)
        {
            out.append("100 loops have passed!\n");
            if(loops%1000==0)
            {
                System.out.println(out);
            }
        }
        loops++;
    }
}
```

Your coding style is pretty hard to read, it makes no sense to make a variable (in casu printevery) to be read out only once and "i" is less descriptive as "loops".

Yea, it's got to run forever, as I understand what I've been asked.

The loop needs to run itself for 1 second, then after it's run 100 times (so 100 seconds), it needs to print out. Then 100 seconds later it should print out again, and so on and so forth.

As for my coding style, it's just how I'm used to doing things I guess.:)

---

### Post by Ramses de Norre on 2007-09-29
How do you define "The loop needs to run itself for 1 second" ?
If you need to do what you described in your first post, my code will do exactly that (except for me typing 1000 instead of 10000, I just noticed that).

---

### Post by LPomfrey on 2007-09-29
> **Ramses de Norre said:**
> How do you define "The loop needs to run itself for 1 second" ?
If you need to do what you described in your first post, my code will do exactly that (except for me typing 1000 instead of 10000, I just noticed that).

I mean that there should be a while loop that runs for a total of 1 second (which it will in this case), then after it's run 100 times it needs to print to screen.

The only problem is that instead of printing every 100 seconds, in this case it seems to be printing constantly.

---

### Post by CptPicard on 2007-09-29
I and Ramses are understanding your exercise so that your top-level while loop runs for one second *total*. Then, while it is running during that one second total time, it counts how many times it's being run and prints to screen at specific intervals... so roughly...

```

int count = 0;
while (not yet run for one second) {
  count++;
  if (count % somenumber)
     print
}

```

As far as I understand, the "moral" of this is to see how many loops you can do within one second... which is quite a lot :)

---

### Post by LPomfrey on 2007-09-29
> **CptPicard said:**
> I and Ramses are understanding your exercise so that your top-level while loop runs for one second *total*. Then, while it is running during that one second total time, it counts how many times it's being run and prints to screen at specific intervals... so roughly...

```

int count = 0;
while (not yet run for one second) {
  count++;
  if (count % somenumber)
     print
}

```

As far as I understand, the "moral" of this is to see how many loops you can do within one second... which is quite a lot :)
Got it. I guess I just didn't understand what I was being asked as well as I thought. :oops:

Thanks, for the help guys. :)

---

### Post by Ramses de Norre on 2007-09-29
Running through a loop 100 times doesn't take long... My code prints blocks of 100 lines once every 10000 runs of the loop.
The printing can look pretty constant though, but it isn't.

My code runs 1 sec (the while loop), builds blocks of 100 lines (so every 100th loop one line is added) and after 10000 loops the block is printed and the StringBuilder is reset.

I've added the reseting, I forgot about that before.

```
public void timer()
{
    long time=System.currentTimeMillis();
    int loops=0;
    StringBuilder out=new StringBuilder("");
    while((System.currentTimeMillis()-time)<1000)
    {
        if(loops!=0 && loops%100==0)
        {
            out.append("100 loops have passed!\n");
            if(loops%10000==0)
            {
                System.out.println(out);
                out.setLength(0);
            }
        }
        loops++;
    }
}
```

---

### Post by LPomfrey on 2007-09-29
> **Ramses de Norre said:**
> Running through a loop 100 times doesn't take long... My code prints blocks of 100 lines once every 10000 runs of the loop.
The printing can look pretty constant though, but it isn't.

My code runs 1 sec (the while loop), builds blocks of 100 lines (so every 100th loop one line is added) and after 10000 loops the block is printed and the StringBuilder is reset.

I've added the reseting, I forgot about that before.

```
public void timer()
{
    long time=System.currentTimeMillis();
    int loops=0;
    StringBuilder out=new StringBuilder("");
    while((System.currentTimeMillis()-time)<1000)
    {
        if(loops!=0 && loops%100==0)
        {
            out.append("100 loops have passed!\n");
            if(loops%10000==0)
            {
                System.out.println(out);
                out.setLength(0);
            }
        }
        loops++;
    }
}
```

Thanks.

I think my main problem is that I was coming at it from the point of view of somehow the loop should actually take a second to do 1 iteration, then it should print out every 100 of those (so every 100 seconds) rather than what it should have been.


Out of interest what is the benefit of using StringBuilder?

---

### Post by Ramses de Norre on 2007-09-29
In Java, Strings are immutable and string concatenation (the "+" operator) actually creates a new object, which is pretty memory inefficient when using a lot of concatenation. So instead you can use StringBuilder, which is an implementation of CharSequence, to build up strings by adding or inserting. Your algorithm will be a lot faster when adding 100 strings to a StringBuilder than when concatenating 100 strings (and thus creating 100 objects).
You can see a StringBuilder as an efficient, mutable string,

---

