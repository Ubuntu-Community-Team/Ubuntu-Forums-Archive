---
title: "calculate with bash"
date: 2018-04-01
forum: Programming Talk
---

### Post by cazz on 2018-04-01
Hi I try to do something easy and have use this page to make it a script that calculate the time left of a job
[https://www.shell-tips.com/2010/06/14/performing-math-calculation-in-bash/](https://www.shell-tips.com/2010/06/14/performing-math-calculation-in-bash/)

That I have is a script that run every 45 min until x and y are the same

x is the ending value so before I start run the script I set a value inside, example 20
y is the count of the script so everytime the script have run it add it to it self with start of 0 so next is 1, after that 2 and so on.

I know the script is going to take 45 min so first I did try to add everything in one single line

countdown=$(expr x-y \* 45 /60)

That I trying to do is multiply 45 with how many time the script have left to run (that why I need to use x-y so it countdown)
That give me value of minute but I like to make it easy so I divide it with 60 so I get whole hours (maybe is a good way to make it more nice to look at)

But I get the wrong value of the countdown so I have to do something wrong.

I did try to split the code to make it easy but have not so good luck in that.

I just want to make it look nice like 4:15 (four hours and 15 min)

---

### Post by TheFu on 2018-04-01
Before bash, we used expr to do calculations.  Bash has math built-in, so no need to use the external program expr anymore.  Spawning a separate process when unnecessary is inefficient.

Anything on the right side of the = needs to be a variable, number or operator.  x and y are neither.

```
countdown=$((  ($x-$y) * 45 / 60 ))
```
is probably what you want.

```
countdown=$((  (10-5 ) * 45 / 60 )); echo $countdown
``` works.

There are ways in bash to do date math and time math based on seconds.  Unix systems use seconds since 1/1/1970 internally. Getting any time into seconds is relatively easy. In 2038, a 32-bit seconds will roll over, however.  It won't be an issue on 64-bit OSes, but 32-bit ones will likely be impacted, somehow similar to the Y2K stuff.

---

### Post by #&amp;thj^% on 2018-04-01
> **TheFu said:**
> Before bash, we used expr to do calculations.  Bash has math built-in, so no need to use the external program expr anymore.  Spawning a separate process when unnecessary is inefficient.

is probably what you want.

```
countdown=$((  (10-5 ) * 45 / 60 )); echo $countdown
``` works.

There are ways in bash to do date math and time math based on seconds.  Unix systems use seconds since 1/1/1970 internally. Getting any time into seconds is relatively easy. In 2038, a 32-bit seconds will roll over, however.  It won't be an issue on 64-bit OSes, but 32-bit ones will likely be impacted, somehow similar to the Y2K stuff.
+1 Brilliant! ;)


And not to over complicate or add confusion here, there was a script that I used back in 2008 written by "Justin Ellison", and I believe it to still work now.
Found here: [https://github.com/justintime/progress.sh/blob/master/progress.sh](https://github.com/justintime/progress.sh/blob/master/progress.sh)
The link I posted is valid, I just checked! :)
Back when I needed this it would show something along the lines of this:
```
Current=.13/sec TotalAvg=.13/sec Total=4/600 0% 1.27 hrs left
Current=.33/sec TotalAvg=.23/sec Total=14/600 2.00% 42.46 mins left
Current=.33/sec TotalAvg=.26/sec Total=24/600 4.00% 36.92 mins left
Current=.33/sec TotalAvg=.28/sec Total=34/600 5.00% 33.69 mins left
Current=.33/sec TotalAvg=.29/sec Total=44/600 7.00% 31.95 mins left
Current=.33/sec TotalAvg=.29/sec Total=54/600 9.00% 31.37 mins left
Current=.33/sec TotalAvg=.30/sec Total=64/600 10.00% 29.77 mins left
```
My old Notes show my example:
The one-liner script that echoes two log lines to a file once every 3 seconds for 30 minutes. Before hitting the enter key, open up another terminal, and run this in it:
```
./progress.sh 'grep -c SUCCESS test.out' 600
```
Watch your quoting on the first argument. If you&#8217;re doing complex pipelines, you will likely need to escape some characters.
Anyway I hope it helps you if not just kindly disregard.

---

### Post by cazz on 2018-04-01
> **TheFu said:**
> Before bash, we used expr to do calculations.  Bash has math built-in, so no need to use the external program expr anymore.  Spawning a separate process when unnecessary is inefficient.

Anything on the right side of the = needs to be a variable, number or operator.  x and y are neither.

```
countdown=$((  ($x-$y) * 45 / 60 ))
```
is probably what you want.

```
countdown=$((  (10-5 ) * 45 / 60 )); echo $countdown
``` works.

There are ways in bash to do date math and time math based on seconds.  Unix systems use seconds since 1/1/1970 internally. Getting any time into seconds is relatively easy. In 2038, a 32-bit seconds will roll over, however.  It won't be an issue on 64-bit OSes, but 32-bit ones will likely be impacted, somehow similar to the Y2K stuff.

Thanks but have you any idea how I get with two decimal?

I was trying with ```
"%.2f\n"
``` but I guess the calculate round it up

---

### Post by TheFu on 2018-04-01
I don't think expr or bash to scalar math.  They do interger math, right?  Don't believe me. Verify it yourself.

```
$ expr 3 / 2
1

$ echo $(( 3 / 2 ))
1
```

Scalar math is different.  **bc** is the command off the top of my head. I tend to use perl by that point.

---

### Post by cazz on 2018-04-01
ok, well is ok I can use this anyway, is better then nothing :)

---

### Post by sisco311 on 2018-04-01
Check out:
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression) and
[http://mywiki.wooledge.org/BashFAQ/022](http://mywiki.wooledge.org/BashFAQ/022)

I would convert everything to seconds, do the math and when its needed convert the result back to days/hours/minutes.

But you can also simply multiply the dividend by 100:
```

[sisco@asrock ~]$ a=$((4 * **100 **/ 3))
[sisco@asrock ~]$ echo $a
133
[sisco@asrock ~]$ echo ${a:0:-2}.${a:(-2):2}
1.33

```

---

### Post by TheFu on 2018-04-02
Using seconds for all time/date calculations is how professionals do it, if we aren't being clear. Staying with integer math as much as possible is faster almost always.

---

