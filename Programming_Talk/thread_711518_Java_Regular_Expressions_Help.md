---
title: "Java Regular Expressions Help"
date: 2008-02-29
forum: Programming Talk
---

### Post by fuzzyl0g1c on 2008-02-29
Hello everyone!

I'm having some trouble with regular expressions, and I was wondering if any kind soul could give me some guidance. I'm using the Scanner class to read in a text file, and I'm trying to use regular expressions to get the data I want out.

The text file is like this:

-------------------------------
|D|N|O|P|S|N|O|I|T|A|C|A|V|F|X|
-------------------------------
|B|S|E|R|E|N|I|T|Y|N|Z|E|K|Y|I|
-------------------------------
|Z|B|R|E|A|M|O|A|N|A|R|H|E|C|M|

and so on...

The end result I want is to have a 2-d array of all of the characters like so:
D N O P S N O T A C A V F X

The reason it needs to be like this is I'm going to use brute force to search for a bank of words.

Here is my code so far:

```
import java.io.*;
import java.util.Scanner;
import java.util.regex.MatchResult;
import java.util.regex.Matcher;
import java.util.regex.Pattern;
public class WordFind {

	/**
	 * @param args
	 */
	public static void main(String[] args)throws IOException {	
		
		String[][] Word = new String[31][31];
		
		try {
			Scanner sc = new Scanner(new File("cashiers.txt"));
			
			Pattern pattern = Pattern.compile("[A-Z]");
			Matcher matcher = pattern.matcher(sc.next(sc.next()));
			
			System.out.println(matcher.group());

			
		} catch(FileNotFoundException e) {
			System.out.println("This file does not exist.");			
			}
		}
}
```

This is as far as I got because when I run the above I get this:
Exception in thread "main" java.util.InputMismatchException
	at java.util.Scanner.throwFor(Scanner.java:840)
	at java.util.Scanner.next(Scanner.java:1461)
	at java.util.Scanner.next(Scanner.java:1394)
	at WordFind.main(WordFind.java:29)

Can anyone tell me what might be wrong? I'm guessing it can't resolve the dashes to string type, but I'm unsure of what to do. Thanks a lot!
:guitar:

---

### Post by ZylGadis on 2008-02-29
What are you trying to do with sc.next(sc.next()) ? I am almost certain you are trying to do something completely different from what it does. This is the source of your error. Besides, there are much more elegant solutions to what you describe. Did you read the documentation of the Scanner class at all?

[http://java.sun.com/javase/6/docs/api/java/util/Scanner.html]("http://java.sun.com/javase/6/docs/api/java/util/Scanner.html")

---

### Post by coolkid5 on 2008-02-29
With scanner you could use the setDelimeter method which takes a String or Pattern.

setDelimeter("[^A-Z]") would set all non uppercase letters to the delimeter, so that only the letters are returned with the next() method

---

### Post by LittleLORDevil on 2008-02-29
You could take in the line as a string then replaceAll the | characters with "" that should do it.

---

### Post by fuzzyl0g1c on 2008-03-01
Thanks for all the help guys, I appreciate it.

---

