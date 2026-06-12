---
title: "[Java] Reading Text File"
date: 2008-03-30
forum: Programming Talk
---

### Post by TreeFinger on 2008-03-30
I have a text file I am trying to make some String objects from.
The format of the text file is this..

```

I need this entire string to be copied
thisIs1String thisIsAnotherString thisWillAlsoBe andThis
Here is another line I need
4more seperateTokens downHere andSoon..

```

My current program gets the first set of things just fine
But when going to the second line I need to copy it just copies the new line character as that string

```

public static void main (String[] args) throws IOException
	{
		Scanner fileScan;
		fileScan = new Scanner (new File("questions.txt")); 
		String question, correctAnswer, wrongAnswer1, wrongAnswer2, wrongAnswer3;
		
		boolean anotherQuestion = true;
		
		while ( fileScan.hasNext() == true ) 
		{
			question = fileScan.nextLine();
			correctAnswer = fileScan.next();
			wrongAnswer1 = fileScan.next();
			wrongAnswer2 = fileScan.next();
			wrongAnswer3 = fileScan.next();
		
			System.out.println (question);
			System.out.println (correctAnswer);
			System.out.println (wrongAnswer1);
			System.out.println (wrongAnswer2);
			System.out.println (wrongAnswer3);
		
			anotherQuestion = fileScan.hasNext();
		
			if ( anotherQuestion == true ) {
				System.out.println ("Create another question object here");
			}
			else {
				System.out.println ("No More Questions to load, Start asking the questions to user");
			}
		}
	}

```

---

### Post by Heril on 2008-04-04
The issue is the nature of the next() method..

When you use the nextLine() method, the scanner is advanced to the end of the next newline character and then reads everything it skipped into the scanner.

However when you use the next() method it does the same thing(assuming you don't define a delimiter) except for a space character, however this does not include the newline character.

There are a couple of ways to fix this problem. You could arbitrarily execute the next() method again at the end of every set of answers. Another option would be to use nextLine() for the last answer in every set.

However, the implementation I would use is to define a delimiter for the scanner, which will define how next() behaves. Using this you can define it to consider any whitespace and newlines as the delimiter for it, while nextLine() will still behave the same way. 

To learn more on how to do this, look at the Java API for [Scanner]("http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html") and [Pattern]("http://java.sun.com/j2se/1.5.0/docs/api/java/util/regex/Pattern.html").

---

