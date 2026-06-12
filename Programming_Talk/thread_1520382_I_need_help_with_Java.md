---
title: "I need help with Java"
date: 2010-06-29
forum: Programming Talk
---

### Post by smdawson on 2010-06-29
I am trying to understand how to read a file of two number columns into two arraylists. One column in each arraylist.
(i.e)
 
1 2
3 1 
9 23
-1 -1
 
The double "-1"s are in each file to denote the end of list. How can I get the scanner to end on the double -1's, read the numbers into the arraylist, and what does printStackTrace() do? I realize I need 'catch' after 'try' to handle exceptions, but the rest is a little fuzzy.
 
My compiler says that comparing strings using == or != is a bad idea. I thought to use hasNextLine() but then I have to get rid of the double -1's. (The code doesn't work that way either though)
 
This is what most of my code looks like.
```
 
....
ArrayList arry1 = new ArrayList();
ArrayList arry2 = new ArrayList();
 
try
{
Scanner scan = new Scanner(new File("Numbers.txt"));
while (scan.nextLine() != "-1 -1")
   {
   arry1.add(scan.nextInt());
   arry2.add(scan.nextInt());
   }
} catch (FileNotFoundException e)
 {
 e.printStackTrace();
 }
 
 

```

---

### Post by burton247 on 2010-06-29
not 100% but.

Firstly you should compare strings using the .equals() method.

Secondly i'd turn the int to a string, so I would try:

while (!scan.nextLine().toString().equals("-1 -1"))

---

### Post by trent.josephsen on 2010-06-29
@burton247:  nextLine returns a String.

The Scanner nextLine method will discard the line it reads, so you won't be reading the integers from the line that you compared to "-1 -1".  Read the integers first and then compare them to -1, or else store the line and pick the numbers out of it later.

Furthermore, put only the code that can cause an exception into the try block.  That's the new Scanner(...) invocation.

---

### Post by burton247 on 2010-06-29
opps, got confused with nextLine and nextInt.

Didn't think about the other point though. Is there not a cleaner way to do this though?

---

### Post by smdawson on 2010-06-29
Alright. I ended up doing this. It may not be the most effecient way, but it reads all the numbers and takes off the -1's at the end. 
 
@trent.josephsen. Are you mistaken about the placement of the brackets around the scanner? I tried what you said and I could not compile. However, I am successfully running the program with the brackets where I had them.
 
 
```
 
do {
ary1.add(scanner.nextInt());
ary2.add(scanner.nextInt());
 
    } while (scanner.hasNextInt());
 
ary1.remove(ary1.size() -1);
ary2.remove(ary2.size() -1);

```

---

### Post by smdawson on 2010-06-29
So ArrayList's .get() method doesn't return as type int, so I cannot use that to compare the values of my arraylists....any alternatives?

---

### Post by Queue29 on 2010-06-29
this hasn't been run through a compiler, but it's the right idea.

```

try {
	Scanner inFile = new Scanner(new File("Nums.txt"));
	while(inFile.hasNextInt())
	{
		int n1 = inFile.nextInt();
		int n2 = inFile.nextInt();
		if(n1 == n2 == -1)
			break;
		arrayList1.add(n1);
		arrayList2.add(n2);
	}
}catch(Exception e)


```

Actually the while loop could just be:
```
 while(true) 
```
since we're assuming your input file is perfectly formatted anyway (as in there are an even number of numbers, and ends on "-1 -1". )

---

### Post by Yes on 2010-06-29
The ArrayList is returning an Integer, so to compare two values in an ArrayList you'll need to use Integer's toInt method:

```
if (listOne.get (1).toInt () == listTwo.get(1).toInt ()) {}
```

---

### Post by Some Penguin on 2010-06-29
Perhaps I'm old-school, but I wouldn't use Scanner at all.  *shrug*

I'd use BufferedReader's readLine method to pull in a string, use trim() to create a version without leading or trailing whitespace, and either use String's split() method or the Pattern/Matcher combo to find the two string-separated bits.

The Integer class then has methods like parseInt that'll throw informative exceptions on parse failure.

---

### Post by Queue29 on 2010-06-29
> **Some Penguin said:**
> Perhaps I'm old-school, but I wouldn't use Scanner at all.  *shrug*

I'd use BufferedReader's readLine method to pull in a string, use trim() to create a version without leading or trailing whitespace, and either use String's split() method or the Pattern/Matcher combo to find the two string-separated bits.

The Integer class then has methods like parseInt that'll throw informative exceptions on parse failure.

Or we could just use scanner to pick out the ints for us. Your method is extremely error prone, and is a terrible idea when proven-to-be-correct libraries are available.

---

### Post by endotherm on 2010-06-29
a stacktrace is a message describing what the computer was doing at the time the execution happened, in a way that you can determine what call lead to what call lead to the exception. 
here is some advice about how to read a stacktrace. 
[http://java.sun.com/developer/technicalArticles/Programming/Stacktrace/](http://java.sun.com/developer/technicalArticles/Programming/Stacktrace/)

---

### Post by trent.josephsen on 2010-06-29
> **smdawson said:**
> 
@trent.josephsen. Are you mistaken about the placement of the brackets around the scanner? I tried what you said and I could not compile. However, I am successfully running the program with the brackets where I had them.

I don't know what issue you encountered, but I can guess.  You need to declare the Scanner variable first so it doesn't go out of scope when you fall out of the try block.

```
// WRONG -- scan goes out of scope
try {
    Scanner scan = new Scanner(new File("Numbers.txt"));
} catch(FileNotFoundException e) {
    e.printStackTrace();
}
// do something with scan

```

```
// RIGHT -- declare scan beforehand
Scanner scan;
try {
    scan = new Scanner(new File("Numbers.txt"));
} catch(FileNotFoundException e) {
    e.printStackTrace();
}
// do something with scan

```

Do you understand why?

---

### Post by Some Penguin on 2010-06-29
Dubious distinction.  Either "do something with scan" should be inside the try() block in which case the scope is fine, or the catch() clause should either return or e.g. return a scanner from another input source.   Printing the stack trace is a diagnostic, not an error handling mechanism.

(and often not a terribly useful one compared to using e.g. org.apache.log4j.Logger appenders, as stdout is not necessarily being read and not necessarily exclusively belonging to the thread with the exception.  It's a good idea to get used to Logger.)

---

### Post by trent.josephsen on 2010-06-29
> **Some Penguin said:**
> Dubious distinction.  Either "do something with scan" should be inside the try() block in which case the scope is fine, or the catch() clause should either return or e.g. return a scanner from another input source.   Printing the stack trace is a diagnostic, not an error handling mechanism.

I just copied the OP's code; it didn't occur to me that the catch block didn't fix that (although you are obviously right).  The point was that the try block should generally be as small as possible, containing only the code that can generate an interesting exception.  That was the only line that could throw a FileNotFound exception; hence, the only line that you should be trying to catch one from.

---

### Post by KdotJ on 2010-06-29
> **Some Penguin said:**
> Perhaps I'm old-school, but I wouldn't use Scanner at all.  *shrug*

I'd use BufferedReader's readLine method to pull in a string, use trim() to create a version without leading or trailing whitespace, and either use String's split() method or the Pattern/Matcher combo to find the two string-separated bits.

The Integer class then has methods like parseInt that'll throw informative exceptions on parse failure.

I'm with you here...
I would of gone for something like

```

BufferedReader br = new BufferedReader(new FileReader("file.txt"));

while (true) {
    String next = br.readLine().trim();
    if (next.equals("-1 -1")) {break;}
    String[] values = next.split(" ");
    try {
        ary1.add(Integer.parseInt(values[0]));
        ary2.add(Integer.parseInt(values[1]));
    }
    catch (NumberFormatException e) {
        //Handle exception here
    }
}
```

---

### Post by smdawson on 2010-06-30
> **trent.josephsen said:**
>  
Do you understand why?
 
Yes...Becasue you have to create the Scanner 'scan' before you try to use it to open the file. Right?
 
 
@Queue29 - Thanks for the logic! It does what I want without making me format the end of the ArrayList. However, is 'break' effecient?  
 
I only ask becasue my Java textbook says under "Language Coding Guidelines" to "...avoid the break or continue statements..." to avoid nonlinear control flow.
 
 
@Yes - Thanks for the .toInt() method. That will help a lot.

---

### Post by smdawson on 2010-06-30
> **Some Penguin said:**
> Dubious distinction. Either "do something with scan" should be inside the try() block in which case the scope is fine, or the catch() clause should either return or e.g. return a scanner from another input source. Printing the stack trace is a diagnostic, not an error handling mechanism.
 
(and often not a terribly useful one compared to using e.g. org.apache.log4j.Logger appenders, as stdout is not necessarily being read and not necessarily exclusively belonging to the thread with the exception. It's a good idea to get used to Logger.)
 
 
...ok, so printing stack trace does not handle the error, can you explain how to handle the error? Is Logger an error-handling method or a diagnostic?

---

### Post by KdotJ on 2010-06-30
It depend what you wan to happen when an exception is caught. For example, your program could print out an error message and then terminate, it could print an error message and continue to read the file (if the error is not FileNotFound for example).  It's up to you the programmer to decide what happens and how to handle the exception, inside that catch block

---

### Post by endotherm on 2010-06-30
> **smdawson said:**
> ...ok, so printing stack trace does not handle the error, can you explain how to handle the error? Is Logger an error-handling method or a diagnostic?
if you can't handle the execption, throw it, so that the calling code can determine a fallback. if all else fails, log the error, display a message and exit (though that is the sloppy way out). since you are processing user input, reprompting for good input is a good bet, or if it;s from a file, and the file is missing or corrupt, ask the user to supply a new file.

---

### Post by smdawson on 2010-07-02
Ok. What is the efficient way to catch the exception, prompt the user to enter the new/correct file, and then continue? I'm googling the heck out of this, but I cannot seem to find a good explanation.
 
I know in VB I would have something like 'On Error GoTo NoFileHandler' and then have NoFileHandler prompt for the new file name and 'Resume Next' in the code at where it left off. Is it similar to that..?

---

### Post by wkhasintha on 2010-07-03
hi

---

### Post by Some Penguin on 2010-07-03
> **smdawson said:**
> Ok. What is the efficient way to catch the exception, prompt the user to enter the new/correct file, and then continue? I'm googling the heck out of this, but I cannot seem to find a good explanation.
 
I know in VB I would have something like 'On Error GoTo NoFileHandler' and then have NoFileHandler prompt for the new file name and 'Resume Next' in the code at where it left off. Is it similar to that..?


Looping constructs.  For instance, use a while() loop, handle any exceptions inside it, and decide whether to loop or not based on what happens.  This is something you should be able to simply reason out, not Google.

---

