---
title: "python question"
date: 2011-11-04
forum: Programming Talk
---

### Post by abraxas334 on 2011-11-04
I have 50 files, all in the same sort of format, which I would like to read into arrays in python.

The files look like this:
xa  "\t" xb "\" trapX "\t" ext "\t" absolute   
:           :            :             :             :
:           :            :             :             :
:           :            :             :             :
N         N           N           N            N
There is a title line and then all other entries are doubles, separated by a tab delimeter
So what I want is an array for each of the entries in the file, like:

xa[50][0-N]
xb[50][0-N]
trapX[50][0-N] and so forth
the entreis should ideadlly be numpy duoubles.
The N, ie number of rows in each file may vary, but there is the same amount of data for each observable. 
Files have names as: file.1.dat, file.2.dat  etc

What is the best way of extracting the data out of these files? This will have to be done in python. 

Thanks

---

### Post by ofnuts on 2011-11-04
> **abraxas334 said:**
> I have 50 files, all in the same sort of format, which I would like to read into arrays in python.

The files look like this:
xa  "\t" xb "\" trapX "\t" ext "\t" absolute   
:           :            :             :             :
:           :            :             :             :
:           :            :             :             :
N         N           N           N            N
There is a title line and then all other entries are doubles, separated by a tab delimeter
So what I want is an array for each of the entries in the file, like:

xa[50][0-N]
xb[50][0-N]
trapX[50][0-N] and so forth
the entreis should ideadlly be numpy duoubles.
The N, ie number of rows in each file may vary, but there is the same amount of data for each observable. 
Files have names as: file.1.dat, file.2.dat  etc

What is the best way of extracting the data out of these files? This will have to be done in python. 

ThanksLooks like homework? each file can be read into an array with a one-liner using a "comprehension" and string::split().

---

### Post by abraxas334 on 2011-11-04
> Looks like homework? each file can be read into an array with a one-liner using a "comprehension" and string::split().

I wish it was home work, coz that would mean someone is actually teaching me python. 
What I am actually trying to do is write an automatic data analysis script, which is calling a python function.

What does a "comprehension" mean. The split bit I get, it just separates the "columns".

I was going to do something like this:
[PHP]

print "reading in traces...."
for i in range(ntraces)
	f=open(filepath+str(i)+".dat", 'r')
	lines = f.readlines();
	f.close()

[/PHP]

So i guess my main problem is how do I define the size of the array for the second entry. i.e if I have XA[50][n], where n varies for each trace. In c++ I would just use a vector object or something like that. 
This is really what I want to do: trace_trapX[] = numpy.zeros([ntraces], numpy.float32), but I cannot do that in the for loop as the array is then only definied within that loop is that correct?

---

### Post by ofnuts on 2011-11-04
> **abraxas334 said:**
> I wish it was home work, coz that would mean someone is actually teaching me python. 
What I am actually trying to do is write an automatic data analysis script, which is calling a python function.

What does a "comprehension" mean. The split bit I get, it just separates the "columns".

I was going to do something like this:
[PHP]

print "reading in traces...."
for i in range(ntraces)
    f=open(filepath+str(i)+".dat", 'r')
    lines = f.readlines();
    f.close()

[/PHP]So i guess my main problem is how do I define the size of the array for the second entry. i.e if I have XA[50][n], where n varies for each trace. In c++ I would just use a vector object or something like that. 
This is really what I want to do: trace_trapX[] = numpy.zeros([ntraces], numpy.float32), but I cannot do that in the for loop as the array is then only definied within that loop is that correct?Variable scoping is simpler in Pythin that in most language. There is no "block scope", only function scope. The variable you use in a loop can be used outside the loop.

Comprehensions are described there: [http://docs.python.org/tutorial/datastructures.html#list-comprehensions](http://docs.python.org/tutorial/datastructures.html#list-comprehensions)
The one-liner I would use for one file is:
```

data=[line.split('\t') for line in open(***filename***).read().splitlines()]

```That reads the file to a list of lists of strings, but if your contents are numbers, you can use a "map" to convert them on the fly and obtain a list of list of ints or floats:
```

nums=[map(float,row) for row in data]

```

The list are dynamically build, if you need to specify sizes to build numpy arrays, use ***len()*** (above, len(nums) gives the number of rows, and len(nums[0]) gives the number of columns)

---

### Post by abraxas334 on 2011-11-04
> **ofnuts said:**
> Variable scoping is simpler in Pythin that in most language. There is no "block scope", only function scope. The variable you use in a loop can be used outside the loop.

Comprehensions are described there: [http://docs.python.org/tutorial/datastructures.html#list-comprehensions](http://docs.python.org/tutorial/datastructures.html#list-comprehensions)
The one-liner I would use for one file is:
```

data=[line.split('\t') for line in open(***filename***).read().splitlines()]

```That reads the file to a list of lists of strings, but if your contents are numbers, you can use a "map" to convert them on the fly and obtain a list of list of ints or floats:
```

nums=[map(float,row) for row in data]

```

The list are dynamically build, if you need to specify sizes to build numpy arrays, use ***len()*** (above, len(nums) gives the number of rows, and len(nums[0]) gives the number of columns)

That's great! It makes more sense now. Thank you so much!

---

### Post by cgroza on 2011-11-04
The functions map and filter are deprecated because their tasks can be easily replaced by list comprehensions.
Use the itertools.imap, it returns an iterator and can work on infinite sequences.

---

