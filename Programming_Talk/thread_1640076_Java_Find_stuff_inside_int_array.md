---
title: "Java: Find stuff inside int array?"
date: 2010-12-07
forum: Programming Talk
---

### Post by fallenshadow on 2010-12-07
How would this be done? :confused:

I have declared my int array but now im kinda lost. I just wanna find a certain number in my int array. Yes I am such a Java noob, im sorry. :D

---

### Post by dwhitney67 on 2010-12-07
Please show us what you have conjured up so far.  Personally I have no desire to write an application from scratch.

---

### Post by lykeion on 2010-12-07
[http://www.java-examples.com/performing-binary-search-java-int-array-example](http://www.java-examples.com/performing-binary-search-java-int-array-example)

---

### Post by Finalfantasykid on 2010-12-07
The naive solution would be to just iterate through the array with a for loop.

```

int number_I_am_looking_for = 42;
for (int i = 0; i < array.length; i++){
   if(array[i] == number_I_am_looking_for){
      return i;
  }
}

```

A much faster solution would be to use a better data structure(An object which stores other objects).  For example of you are accessing this array lots and need to get a certain element quickly, but don't know it's index, then a sorted data structure like a TreeMap, or even a HashMap might be best, although considering you are newer to the language, these might be a little more advanced to grasp the concept(not harder to use, but harder to understand how they work under the hood)

---

### Post by fallenshadow on 2010-12-08
> Please show us what you have conjured up so far. Personally I have no desire to write an application from scratch.

This is what I had written...  :tongue:  :oops:

```
public static void main(String[] args)
     {

       int[] Array = {10, 6, 2, 8, 4, 15};
     }
```

Finalfantasykid: I did try your idea already but it didn't work.

---

### Post by idi0tf0wl on 2010-12-08
> **fallenshadow said:**
> This is what I had written...  :tongue:  :oops:

```
public static void main(String[] args)
     {

       int[] Array = {10, 6, 2, 8, 4, 15};
     }
```

Finalfantasykid: I did try your idea already but it didn't work.

Try this:
```

public static void main(String[] args) {
     //create a new array of ints called "array"
     //containing the following elements
     int[] array=new int[]{
          1,2,3,4,5
     };
     //this will print 1
     System.out.println(array[0]);
}

```

Using array[*] refers to element number * in the array specified (in this case, one called "array").
PM me for a way to get in touch with me for more help. Everyone has to begin. Good luck with Java!

---

### Post by myrtle1908 on 2010-12-08
> **fallenshadow said:**
> This is what I had written...  :tongue:  :oops:

```
public static void main(String[] args)
     {

       int[] Array = {10, 6, 2, 8, 4, 15};
     }
```

Finalfantasykid: I did try your idea already but it didn't work.

The code provided by Finalfantasykid will work.

You are trying to do something incredibly simple.  Frankly, if you cannot figure this much out on your own then you really shouldn't bother with programming at all.

Anyhoo, here's a few pointers to help solve your problem ...

1. Learn about loops.  A *for* loop is fine for your basic problem.  Google for "java for loop example".

2. Learn about comparison operators, specifically for numbers.

If you can understand these two basic concepts then solving your problem will be simple.  Not to mention that Finalfantasykid has already provided an adequate solution.

Good Luck.

---

### Post by fallenshadow on 2010-12-10
I will try the solution by FinalFantasyKid again tonight so. I know its something simple but a simple loop didn't work for me. 

There is no point in telling me I shouldn't do programming at all because Im already quite a good C++ programmer. I only just started Java and I am finding it difficult because my teacher expects me to just learn it on my own somehow. 

Im not good to learn things like that on my own and I need to be shown how to do it initially before I become any bit good at it.

---

### Post by dwhitney67 on 2010-12-10
> **fallenshadow said:**
> 
There is no point in telling me I shouldn't do programming at all because Im already quite a good C++ programmer.
Why? Because you know the syntax?

Java is cake; if you can do something in C++, then doing it in Java should be very similar.

---

### Post by KdotJ on 2010-12-10
I'm sorry but there is no way you can say you're already a good C++ programmer if you can't do this. This has nothing to do with java, or C++, the task you wan to achieve is basic programming. 

Anyway, the code posted for you will 100% work

---

### Post by lykeion on 2010-12-10
Just to show what dwhitney says about the similarities of Java and C++ for basic programming I tried to mockup the C++ code and the Java code for this. I do seem to have too much time on my hands :)
Please forgive my C++ code, it's only the second program I've written in C++ (the first was Hello World).
[PHP]#include <stdio.h>
#include <iostream>
using namespace std;

int main(void) {
	const int arraySize = 5;
	int a[arraySize] = { 2, 4, 6, 8, 10 };
	int pos = -1;
	int number;
	printf("\nEnter number to find: ");
	cin>>number;
	for (int i = 0; i < arraySize; i++ ) 	{
		if (a[i] == number) 
			pos = i;
	}
	if(pos >= 0)
		printf("Found at pos: %d\n", pos);
	else
		printf("Not found\n");
}[/PHP]

And the java code would be something like this:
[PHP]import java.io.Console;

public class Test {
	public static void main(String[] args) {
		
		int[] a = new int[] { 2, 4, 6, 8, 10 };
		int arraySize = a.length;
		int pos = -1;
		int number;
		Console console = System.console();
		String line = console.readLine("\nEnter number to find: ");
		number = Integer.parseInt(line);
		for (int i = 0; i < arraySize; i++ ) {
			if (a[i] == number) 
				pos = i;
		}
		if(pos >= 0)
			System.out.printf("Found at pos: %d\n", pos);
		else
			System.out.printf("Not found\n");
	}
}[/PHP]
Except for the read input part, they are almost identical!!!

---

### Post by KdotJ on 2010-12-10
Indeed, the syntax is practically the same. 

To the OP, here is a method that will do what you need...

```

private boolean search(int[] a, int num) {
    for (int i = 0; i < a.length; i++) { 
        if (a[i] == num)
            Return true;
    }
    return false;
}
```

---

### Post by dwhitney67 on 2010-12-10
Awesome solutions!  Ubuntu Programming Forum == Homework Service Center

---

### Post by myrtle1908 on 2010-12-10
> **dwhitney67 said:**
> Awesome solutions!  Ubuntu Programming Forum == Homework Service Center

Indeed.  Let's hope he/she submits KdotJ's solution as is.  I'm sure you have spotted the error :)

---

### Post by KdotJ on 2010-12-11
> **myrtle1908 said:**
> Indeed.  Let's hope he/she submits KdotJ's solution as is.  I'm sure you have spotted the error :)

Enlighten me... Oh and please dont say the capital R on the first return statement (which would be pointed out a compilation and obvious to fix), iPhone auto-capitalisation is to blame here lol. 

Anyway, I understand what you're both saying about "doing peoples homework", and normally I don't bother helping out with such, but for this particular question, it is so ridiculously simple and can be found over a hundred times by searching google, I though it doesn't really matter

---

### Post by fallenshadow on 2010-12-11
Just to let you all know I wasn't looking for "homework". All I was looking for was a starting point. Think of me like a climber who is pretty good but needs a boost to get started.

The problem is Im doing a Java course but the teacher doesn't even teach us how to program with Java. The teacher just rambles on about theory and expects us to learn how to program with java by ourself. Also I do find Java does things quite differently from C++.

The most I would have taken from anyones code would be the for loop as my starting point. However my final code is quite different and I will PM it to you dWhitney if you don't believe me!!

About the posts saying I might as well not bother with programming:

If every programmer who struggled once took that attitude we wouldn't have alot of programmers now, would we?! :rolleyes:

---

### Post by KdotJ on 2010-12-11
I agree the statement was a bit harsh but maybe it wasn't meant in such a fierce mannor. However, the thing that made me confused is how you said your already good at C++, but apparently haven't ever needed to iterate through an array.  

Regardless, good luck with your learning and course

---

### Post by Finalfantasykid on 2010-12-11
I was sort of rushed when I wrote that snippet of code on the first page (minutes before a class started, c++ class strangely enough O_o).  

So I can clarify a little bit on how it works if that what you can't get to work.

First off since this loop has a return statement it will obviously have to be put into a loop, and will also need a return statement after the for loop in the event that the search doesn't find a result (-1 would be a good return value).  The method should take at least one parameter, the element you are searching for.  Depending on how you have your array being stored(instance variable/static variable/local array) you may also need another parameter for the array.  It might actually be better to just include a second parameter for the array just to be on the safe side.

Next if you didn't realize I am returning the index of the element in the array.

---

### Post by myrtle1908 on 2010-12-11
> **KdotJ said:**
> Enlighten me... Oh and please dont say the capital R on the first return statement (which would be pointed out a compilation and obvious to fix), iPhone auto-capitalisation is to blame here lol.

Of course it was the capital R!  I thought you may have put it there on purpose to "trap" the OP :)

Anyways apologies to OP if I came across harsh.  I do not mean to discourage.  That said, a for loop construct in C/C++ is exactly the same as a for loop in Java.

```
for (init expressions) {
  // do something
}
```

Good Luck

---

### Post by KdotJ on 2010-12-11
> **myrtle1908 said:**
> Of course it was the capital R!  I thought you may have put it there on purpose to "trap" the OP

Haha not quite, no the good old iPhone seems to insist I use captitals all the time lol. That's bad code checking from me... Lol

---

### Post by fallenshadow on 2010-12-12
To be honest I did find that kind of statement a bit insulting. However all apologies are accepted! ;)

One thing that people should take note of is that developers progress at different speeds. I don't progress with something new for quite some time until it "clicks" with me. Until I reach a stage where I am comfortable with it. Right now im not so comfortable with Java as I am with C++. (even though they are similar)

An example here would be Jono Bacon. I used to listen to a podcast he was involved with called LugRadio. On the podcast I distinctly remember a discussion between him and Stuart Langridge. Jono was saying that he just couldn't get/understand programming the same way as Stuart. Jono said he was really struggling with it. Now Jono is programming such important apps as Lernid, it just took time to get to that stage of programming... whatever time he needed. 

So I hope people can be patient until I reach that point, whatever time it will take. When I get to that point it will all be worthwhile!

---

### Post by dwhitney67 on 2010-12-13
> **fallenshadow said:**
> 
So I hope people can be patient until I reach that point, whatever time it will take. When I get to that point it will all be worthwhile!
Will do!

I just hope that in the future that you spend a little time doing basic research before asking ridiculously easy questions on any forum.  If you are in school (university/college level), learning how to perform independent research is paramount to anything else.

Personally, I work as a professional s/w developer (ie I get paid for what I do), and day-in/day-out, it is Linux (or Sun) and C++ that are on the plate.  There are times that I have to peruse code developed by some perturbed developer over a decade ago (before C++ was standardized).  I have to figure out what is going on in the code, fix a bug or two, and then release the s/w.  There's no one to hold my hand during this effort.  If I have a question, I generally perform research on the web or the old fashioned way, by reading through a book.

As for Java, it has been nearly 10 years since I dabbled in it at the student (and professional) level.  Perhaps because of my background, I found the basics of the language to be easy.  But since I do not deal with it on a daily basis, I also keep a bookmark to the [API]("http://download.oracle.com/javase/6/docs/api/index.html?overview-summary.html"), which you might want to consider doing as well.

Good luck with your studies.

---

