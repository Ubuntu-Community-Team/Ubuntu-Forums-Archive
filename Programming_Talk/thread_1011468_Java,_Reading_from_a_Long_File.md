---
title: "Java, Reading from a Long File"
date: 2008-12-14
forum: Programming Talk
---

### Post by coolkid5 on 2008-12-14
I'm trying to do things with a file containing a bunch of words, but I'm running into problems accessing all the words in the list...

This code is just supposed to print all the words in the list:


```
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;


public class Test {
	public static void main(String[] args) throws FileNotFoundException{
		Scanner scan = new Scanner(new File("/english-words.95"));
		
		int i = 1;
		while(scan.hasNextLine()){
			String str = scan.nextLine().toUpperCase();
			System.out.println(i + ":" + str);
			i++;
		}
	}
}

```

For some reason it just stops printing the words.  The last few lines of output are:
> 23025:CAFFOLINE
23026:CAFFOY
23027:CAFH
23028:CAFIZ
23029:C

As you can see it stops mid-line on the 23029 word, which should be "CAFOY".  There are thousands more words in the list, and I'm not sure why it is terminating so quickly.  Help would be greatly appreciated :)

---

### Post by jamesstansell on 2008-12-14
Are you running from the command line or from an IDE?  Does it exit by itself, or do you terminate it after it stops printing?  Which version of java is it?

---

### Post by myrtle1908 on 2008-12-14
Is an exception being thrown?  Use a try/catch block.  Perhaps the terminal/shell overflows and cannot display any further?  Maybe try writing the output to a file and see if it stops in the same place.

---

### Post by txcrackers on 2008-12-14
From the Java docs for *nextLine()*:

Since this method continues to search through the input looking for a line separator, it may buffer all of the input searching for the line to skip if no line separators are present. 

I'd check the output of *ioException()*  on each iteration. You may literally be reading from the last position to the end of the file, overflowing the buffer.

---

### Post by HotCupOfJava on 2008-12-14
Yes, definitely use a try/catch block to check for the IOException. You can insert code into the catch block to help you hunt down the bug.

---

### Post by coolkid5 on 2008-12-14
I modified the code to use a try/catch for the IOException:

[PHP]import java.io.File;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.Scanner;


public class Test {
	public static void main(String[] args){
		try{
			Scanner scan = new Scanner(new File("/english-words.95"));

			int i = 1;
			while(scan.hasNextLine()){
				String str = scan.nextLine().toUpperCase();
				System.out.println(i + ":" + str);
				i++;
			}
		}catch(IOException ex){
			ex.printStackTrace();
		}
	}
}[/PHP]

However, no exception is thrown.  I'm using Eclipse as my IDE, and I changed the preferences so that it does not limit the output length, but the same problem occurs.  I also tried running the program from the terminal with the same results.  Also, I am not terminating the program, it terminates itself.
While debugging, I found that the last time it calls scan.nextLine().toUpperCase() it returns just "C" rather than the the whole word "CAFOY".

I still have no idea what's wrong :(

---

### Post by myrtle1908 on 2008-12-14
Code seems fine.  Perhaps you could post the offending file.

---

### Post by HotCupOfJava on 2008-12-15
It is possible that another type of exception is being thrown. Perhaps add another catch block for a generic Exception so you can see if ANY exception is being thrown. There are still too many possibilities for what can be wrong. Perhaps it is overrunning the String buffer somehow. Perhaps it thinks it is at EOF for some reason......

---

### Post by Poyntz on 2008-12-15
[SIZE=1]*As this message went off on a tangent it has been removed by the user*[/SIZE]

---

### Post by myrtle1908 on 2008-12-15
> **Poyntz said:**
> but I'm confused as to why you're initialising i at 1. Shouldn't you be starting i at 0?

'i' is merely being used to display the line number ie. not as an index.

---

### Post by ufis on 2008-12-15
Is there a reason why you are using [FONT="Courier New"]Scanner[/FONT] and not [FONT="Courier New"]FileReader[/FONT]?

Try wrapping the [FONT="Courier New"]FileReader[/FONT] in a [FONT="Courier New"]BufferedReader[/FONT] like (from API docs):
[php]BufferedReader in = new BufferedReader(new FileReader("foo.in"));[/php]

[FONT="Courier New"]BufferedReader[/FONT] has a [FONT="Courier New"]readLine()[/FONT] method that returns the next line, or null if it finds the end of the stream (EOF).

You are using [FONT="Courier New"]Scanner[/FONT] for something it was not created for. Even though it may work, there are tools specifically created for what you want to do: [FONT="Courier New"]FileReader[/FONT].

That said, my next check would be with the input file itself. Especially if it always stops on the same place.

---

### Post by badperson on 2008-12-15
if the file is really large it might be the runtime exception where the heap is too big...I forget what it's called. That's happened to me before. 

Although, you should be able to see that exception in the console, if you're using an ide or just running from a shell. 
bp

---

### Post by PaulM1985 on 2008-12-15
I think the problem you are having may be down to you not closing the buffer.  Have you tried including 

scan.close();

after the while loop?

Paul

---

### Post by achelis on 2008-12-15
There seems to be a bit of confusion as to how exceptions work in Java in this thread.

1) If there is an exception and it is not caught in a try/catch block Eclipse will write the stacktrace in the console.

2) Running it from the console the stacktrace is printed to the console as well, if the exception is not caught.

3) You cannot compile if an Exception is not handled in your code - either by throwing it explicitly or having it in a try/catch. Therefore there is no need to add a "catch Exception" statement at the end of your try/catch. You may however want to catch RuntimeExceptions as the compiler does not require these to be handled.

4) StackOverflow and OutOfMemory are Errors (another type of throwable the superclass for exceptions) and as such (1) and (2) apply to these errors as well. Similar to RuntimeExceptions you are not required to handle Errors.

That said, I'm puzzled why your code doesn't work - can't spot but would like to have a look at it if I could have a copy of the file you're reading.

And while it is not necessary to handle exceptions for small apps like your example I would of course highly recommend making it a habit to properly handle exceptions (closing IO connections in a finally block is generally a good idea :) )

---

### Post by Ragazzo on 2008-12-15
Could be a bug in the virtual machine. I tested your code on the file /usr/share/dict/words and I got the same behaviour as you described (JRE build 1.6.0_10-b33). Then I ran it on another computer and it worked fine (JRE build 1.6.0_01-b06).

Edit: Never mind. scan.ioException() returns MalformedInputException which would indicate a mismatch between character encodings. Change the target file's encoding to UTF-8 and it should work.

---

### Post by coolkid5 on 2008-12-15
Thank you Ragazzo, it was returning a MalformedInputException that couldn't be seen without using ioException.  I changed my word list's encoding to UTF-8 and it works now, but I still don't understand what the problem was exactly.  Could someone explain to me why the character encoding caused this problem?

---

### Post by Ragazzo on 2008-12-15
The documentation for [Scanner]("http://java.sun.com/javase/6/docs/api/java/util/Scanner.html#Scanner(java.io.File)") says:
> 
A scanner can read text from any object which implements the Readable interface. If an invocation of the underlying readable's Readable.read(java.nio.CharBuffer) method throws an IOException then the scanner assumes that the end of the input has been reached. The most recent IOException thrown by the underlying readable can be retrieved via the ioException() method.


There was something in the implementation of the default Reader (sun.nio.cs.StreamDecoder) that Scanner uses that causes problems when the encoding is wrong. To figure out the exact reason you probably have to find the source code for that file. Incidentally, if you use another Reader to do the job, it works fine:
**Scanner scan = new Scanner(new FileReader("/english-words.95"));**

You can of course specify the encoding explicitly too instead of changing the target file:
**Scanner scan = new Scanner(new File("/english-words.95"), "latin1");**

---

### Post by coolkid5 on 2008-12-15
Cool, that explains a lot.

Thanks so much :)

---

