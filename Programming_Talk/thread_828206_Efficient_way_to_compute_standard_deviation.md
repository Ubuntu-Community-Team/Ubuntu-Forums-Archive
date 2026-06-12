---
title: "Efficient way to compute standard deviation?"
date: 2008-06-13
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-06-13
I am already computing the mean, median, min, max on a set of numbers.  I found out that I also need the standard deviation.  I plan to compute it with the formula here:

[http://en.wikipedia.org/wiki/Standard_deviation](http://en.wikipedia.org/wiki/Standard_deviation)

which involves squaring each number, subtracting the square of the mean from that and then taking the square root.  Does anyone know of a more efficient way or a software library which will do this?  I am programming in C++ and I am looking for something efficient.  I already have the mean, median, min, max implemented efficiently, but I do not see a clean fast way of computing stdev.  Actually, the sum of squares will be huge...anyone know of a good statistical library for this?

---

### Post by bruce89 on 2008-06-13
Simplicity of code is better than speed IMHO.

> **SNYP40A1 said:**
> Actually, the sum of squares will be huge

Why would the size of numbers cause things to be slow?

However, the [GNU Scientific Library]("http://www.gnu.org/software/gsl/") might be of interest.

---

### Post by KingTermite on 2008-06-13
> **bruce89 said:**
> Simplicity of code is better than speed IMHO.
I completely agree.


> **bruce89 said:**
> Why would the size of numbers cause things to be slow?It won't, unless they are sooooo large they need a special data type, not a standard int or double.

---

### Post by bruce89 on 2008-06-13
> **KingTermite said:**
> It won't, unless they are sooooo large they need a special data type, not a standard int or double.

The square of the speed of light needs to be a *long long*.

---

### Post by SNYP40A1 on 2008-06-13
> **bruce89 said:**
> Simplicity of code is better than speed IMHO.



Why would the size of numbers cause things to be slow?

Sorry, that was not correctly stated.  A large double is accessed at the same speed as a small double.  It's actually the operation of squaring that really slows things down.  But I don't see any way around that...

I agree that simplicity of code is better than speed...but in this case, I need speed.  Worst case, I will copy the implementation copied here:

[http://ubuntuforums.org/showthread.php?t=147223](http://ubuntuforums.org/showthread.php?t=147223)

But if something better exists, I would be interested.

---

### Post by bruce89 on 2008-06-13
> **SNYP40A1 said:**
> Sorry, that was not correctly stated.  A large double is accessed at the same speed as a small double.  It's actually the operation of squaring that really slows things down.  But I don't see any way around that...

I agree that simplicity of code is better than speed...but in this case, I need speed.  Worst case, I will copy the implementation copied here:

[http://ubuntuforums.org/showthread.php?t=147223](http://ubuntuforums.org/showthread.php?t=147223)

But if something better exists, I would be interested.

A few milliseconds of difference aren't worth it.

You ought to use assembly if you really want speed.

---

### Post by howlingmadhowie on 2008-06-13
whichever method you use you're looking at a runtime of O(n). if you've already worked out the mean, it's probably quicker to do the mean of the squares minus square of the means thing, because it will save you one subtraction each time.


---edit---

you won't get away from the squaring thing. it's a necessary part of finding the variance (standard deviation). also i'm not sure about the wisdom of using a long long for c^2. do you really need that much accuracy? how accurate are your other values? double would appear to me to be more appropriate (though i don't know exactly what you're doing)

---

### Post by SNYP40A1 on 2008-06-13
I would be taking the standard deviation across about 100 values, doubles in the range of 0 - 15000.

> **howlingmadhowie said:**
> whichever method you use you're looking at a runtime of O(n). if you've already worked out the mean, it's probably quicker to do the mean of the squares minus square of the means thing, because it will save you one subtraction each time.


---edit---

you won't get away from the squaring thing. it's a necessary part of finding the variance (standard deviation). also i'm not sure about the wisdom of using a long long for c^2. do you really need that much accuracy? how accurate are your other values? double would appear to me to be more appropriate (though i don't know exactly what you're doing)

---

### Post by SNYP40A1 on 2008-06-13
> **bruce89 said:**
> A few milliseconds of difference aren't worth it.

You ought to use assembly if you really want speed.

A few ms of difference is not worth it, if that's all it comes out to be.  I think it will be a bit longer than that though.  However, main point is that if there is already optimal code or the best known code for doing this operation, I should use that.  It's about speed, but also robustness, no need to reinvent the wheel.

---

### Post by bruce89 on 2008-06-13
> **SNYP40A1 said:**
> A few ms of difference is not worth it, if that's all it comes out to be.  I think it will be a bit longer than that though.  However, main point is that if there is already optimal code or the best known code for doing this operation, I should use that.  It's about speed, but also robustness, no need to reinvent the wheel.

Doing a few squares and square roots won't take long.

---

### Post by Npl on 2008-06-13
if you really care about performance, you could try using valarray.

```
double[] values; // where you got your values
int valAmount; // amount of values

valarray<double> v(values,valAmount);
double stdvar = sqrt( (v*v).sum() );
double min = v.min();
double max = v.max();
double mean = v.sum()/v.size();
```As valarrays dont like beeing resized you`d need to gather/calculate the list of values in another container. They are supposed to have efficient vector-arithmetic, but I dont know how much faster they are in current implementations of the C++-Library.

---

### Post by bruce89 on 2008-06-13
Even my java test program manages 4 numbers in ~0.1 seconds.

```

import java.util.ArrayList;
import java.util.List;

public class Stdev
{
	List<Double> numbers = new ArrayList<Double>();
	double stdenv;

	public Stdev(List<Double> numbers)
	{
		this.numbers = numbers;

		int size;

		double total = 0.0;

		size = numbers.size();
		for (int i = 0; i < size; i++)
			total += numbers.get(i);
		double mean = total / size;

		List<Double> deviations = new ArrayList<Double>();

		for (int i = 0; i < size; i++)
		{
			double cur = numbers.get(i);
			deviations.add(cur - mean);
		}

		List<Double> squaredDeviations = new ArrayList<Double>();

		for (int i = 0; i < size; i++)
		{
			double cur = deviations.get(i);
			squaredDeviations.add(Math.pow(cur, 2));
		}

		double sum = 0.0;

		for (int i = 0; i < size; i++)
		{
			sum += squaredDeviations.get(i);
		}

		stdenv = Math.sqrt(sum / size);
        }
	
	public double getDeviation ()
	{
		return stdenv;
	}
	
	public static void main (String[] args)
	{
		List<Double> numbers = new ArrayList<Double>();

		if (args.length == 0)
			System.err.println("Not enough arguments");
		else
		{
			for (int i = 0; i < args.length; i++)
				numbers.add (Double.parseDouble(args[i]));
			Stdev stdev = new Stdev(numbers);
			System.out.println(stdev.getDeviation());
		}
	}
}

```

---

### Post by Zebediah49 on 2008-06-13
Can't you just do it as a*a?

```

int x=0;
for(i=0;i<count;i++) {
	x += (col[i]-avg)*(col[i]-avg);
}
stddev = sqrt(x/count);

```

Should be tenable for under a few thousand data points.  It'd probably be fine for a few hundred thousand.

It might be faster to do it distributed out?
(col[i]-avg)*(col[i]-avg) == col[i]*col[i]-2*avg*col[i]+avg*avg

since the sum of all the col[i]'s is your sum, which is your avg*count, that should equal

```

int x= -1*avg*avg*count;
for(i=0;i<count;i++) {
	x += col[i]*col[i];
}
stddev = sqrt(x/count);

```

EDIT: oh yeah, if you can do one operation to an entire array, square each value in the array and then sum it.  That should go quickly.

I'm going to test my method there.

---

### Post by descendency on 2008-06-13
> **KingTermite said:**
> I completely agree.

I don't necessarily. I don't really think you should go out of your way complicate something for microseconds, but when you are talking about a more efficient algorithm that might cut time in half (especially if you are working with enough data that you could be talking 20+ minutes), then you are talking about two different things. 

From a learning standpoint though, I always err on the side of simplicity.

---

### Post by Zebediah49 on 2008-06-13
Yeah, it's not a significant point.  I did my tests with 1,000,000 points...
(java)
```

public static void main(String[] args)

	{

		long sTime = System.nanoTime();

		double[] arr = new double[1000000];

		for(int i=0;i<arr.length;i++) {

			arr[i] = Math.random()*1000;

		}

		System.out.println("Allocated array in "+(System.nanoTime()-sTime));

		sTime  = System.nanoTime();

		double total = 0;

		for(int i=0;i<arr.length;i++) {

			total += arr[i];

		}

		System.out.println("Summed array in "+(System.nanoTime()-sTime)+": "+total);

		sTime  = System.nanoTime();

		double avg = total/arr.length;

		double stdDev1 = 0;

		for(int i=0;i<arr.length;i++) {

			stdDev1 += (arr[i]-avg)*(arr[i]-avg);

		}

		stdDev1 = Math.sqrt(stdDev1/arr.length);

		System.out.println("Did first Standard Deviation in "+(System.nanoTime()-sTime)+": "+stdDev1);

		sTime  = System.nanoTime();

		double stdDev2 = -1*avg*avg*arr.length;

		for(int i=0;i<arr.length;i++) {

			stdDev2 += arr[i]*arr[i];

		}

		stdDev2 = Math.sqrt(stdDev2/arr.length);

		System.out.println("Did second Standard Deviation in "+(System.nanoTime()-sTime)+": "+stdDev2);

		sTime  = System.nanoTime();

	}

```
Gives a result of: (I added commas and size-comments)
```

//1m
Allocated array in 108,359,611
Summed array in 44,375,277: 5.0042642905522627E8
Did first Standard Deviation in 16,997,263: 288.51988721371714
Did second Standard Deviation in 2,775,092: 288.51988721370117

//1m
Summed array in 29,504,104: 4.992879934165966E8
Did first Standard Deviation in 5,628,341: 288.8708968887873
Did second Standard Deviation in 4,225,778: 288.8708968888017

//10m
Allocated array in 1,076,800,797
Summed array in 52,878,518: 4.999995401290787E9
Did first Standard Deviation in 27,917,081: 288.6526045870226
Did second Standard Deviation in 33,545,142: 288.6526045871444

//30m
Allocated array in 3,083,251,206
Summed array in 98,899,210: 1.4997821965846146E10
Did first Standard Deviation in 82,663,331: 288.6495057126215
Did second Standard Deviation in 78,517,595: 288.6495057128009

//30m
Allocated array in 2616247926
Summed array in 108,376,933: 1.4999032270911982E10
Did first Standard Deviation in 85,903,173: 288.67544903651975
Did second Standard Deviation in 77,407,405: 288.67544903657017

```

It seems that my simplified method works a bit better, but that seems sorta arbitrary. But yeah, don't worry about the speed.  I couldn't try 100 million points, since I ran out of memory, but... it took <100 ms to do 30M of them.  It's really not going to be a problem.

---

### Post by Mr.Macdonald on 2008-06-13
The places of possible slowness (word??) would be the average and adding up the numbers.

the way i add large streams of numbers is break them up.

[PHP]1 34 12 67 89 45 32
 35    89   134  32
    124       166
         270[/PHP]
(sorry if my addition is bad)

same with averaging

[PHP]24 62 12 2 8 10 31
 43     7   9   31
    25        20
        22.5[/PHP]


you could apply this to adding and averaging
simply take the array and break it into 4 parts and recursively add those parts

i am no computer scientist but this might make it add faster
[PHP]
long add(int start, long * a, int end) { /* start and end are inclusive */
	if (end==start) {
		return a[start];
	} else if (end-start < 2) {
		return a[start]+a[end];
	}
	
	return add(start, a, start+((int)((end-start)/2))) + add(start+((int)((end-start)/2)))+1, a, end);
}
[/PHP]If i made a mistake please fix it (i didn't test this) and please modify my pointer stuff if i made a mistake

---

### Post by howlingmadhowie on 2008-06-14
> **Mr.Macdonald said:**
> The places of possible slowness (word??) would be the average and adding up the numbers.

the way i add large streams of numbers is break them up.

[PHP]1 34 12 67 89 45 32
 35    89   134  32
    124       166
         270[/PHP]
(sorry if my addition is bad)


yeah, you can do that.

> 

same with averaging

[PHP]24 62 12 2 8 10 31
 43     7   9   31
    25        20
        22.5[/PHP]



but you can't do that (unless you're averaging 1,2,4,8... different data points (as an example, according to your method the average of 8, 10 and 31 is 20)).


> 

you could apply this to adding and averaging
simply take the array and break it into 4 parts and recursively add those parts



it won't help. you will still need to add a total of n-1 times, where n is the number of arguments (number of nodes in a tree is always one more than number of vertices)

> 

i am no computer scientist 

the main thing is that you're trying to learn :)


the things which will slow this down are probably multiplication. on risc machines this will usually take 64 steps to multiply 2 longs. there is however no way to avoid it because it is inherent in the definition of  standard deviation. 

the only simple trick you can do (as i mentioned above) is to separate the sum of the square distances from the mean:

```

standard deviation = sum((xi - mean)^2)/n   // method 1
          = sum(xi^2 -2*xi*mean + mean^2)/n  
          = sum(xi^2)/n - 2 * mean * sum(xi)/n + mean*mean

```
and since mean = sum(xi)/n this reduces to:
```

          =  sum(xi^2)/n - mean^2.   // method 2

```
so what do you win by doing this? well, in the first method you have to perform a subtraction every time, which isn't particularly expensive compared with the square, but nevertheless it can be avoided.

both methods have the advantage of being embarrassingly parallelizable, so you can increase speed linearly with the number of computers working on the problem (in the best case).

---

### Post by SNYP40A1 on 2008-06-16
> **howlingmadhowie said:**
> yeah, you can do that.
it won't help. you will still need to add a total of n-1 times, where n is the number of arguments (number of nodes in a tree is always one more than number of vertices)
[QUOTE]

Actually, I think it would help if you are running on a system with multiple CPUs and you use multi-threading.  That really complicates things though...

[QUOTE]
```

standard deviation = sum((xi - mean)^2)/n   // method 1
          = sum(xi^2 -2*xi*mean + mean^2)/n  
          = sum(xi^2)/n - 2 * mean * sum(xi)/n + mean*mean

```
and since mean = sum(xi)/n this reduces to:
```

          =  sum(xi^2)/n - mean^2.   // method 2

```


It's been a few years since I took a stats course, but I think the eqn above is for variance.  Std dev is the sqrt of the variance.

---

### Post by SNYP40A1 on 2008-06-16
Just to check the consensus, there is no way to find the standard deviation without squaring or taking the log of every member of the standard deviation?  That is the most time consuming part, no way around that?

---

### Post by marialice on 2008-06-16
Wikipedia: [Algorithms for calculating variance](http://en.wikipedia.org/wiki/Algorithms_for_calculating_variance)

I don't think you can get much speed optimization though. Memory is easier: a one-pass algorithm really uses less. But you should always test it, clean code is more important than negligible performance improvements.

---

### Post by DavidBell on 2008-06-16
For what it's worth, this is what I do. There is only one square root, the rest are multiplication and addition. It uses  howlingmadhowies method 2 which is pretty standard (it's also in the original link you posted).
```

double sumX = 0.0;
double sumX2 = 0.0; //sum of squares

for (long i = 0; i < DATASIZE; i++);
    {sumX += data[i];
     sumX2 += data[i] * data[i];
    }

double Mean = sumX / DATASIZE;
double StdDevPop = sqrt (sumX2 - Mean * Mean * DATASIZE) / DATASIZE;  // Population
double StdDevSam = sqrt (sumX2 - Mean * Mean * DATASIZE) / (DATASIZE - 1);  // Sample

```
Arguably you could speed it up a bit using pointers instead of array indicies, but I suspect the compiler does that for you anyway.

PS as howlingmadhowie says, it's very easy to do this in parallel, just split the data into x packets executed in separate threads, combine sums at end for calculations.

---

### Post by howlingmadhowie on 2008-06-16
> **SNYP40A1 said:**
> 
Actually, I think it would help if you are running on a system with multiple CPUs and you use multi-threading.  That really complicates things though...

if you are doing that, you still need to do the addition. you would however have the advantage with the method shown that each addition performed has a minimum number of prerequisite steps, so its parallelizability is better. the expensive part of finding the variance (thank-you for the correction--it was an honest oversight on my part), the square and squareroot thing, is however embarrassingly parallelizable, and there it would certainly be worthwhile writing a method that creates a large number of threads and lets the operating system coordinate it (or if you want to be clever, you can try generating as many threads as you have cores...)

---

