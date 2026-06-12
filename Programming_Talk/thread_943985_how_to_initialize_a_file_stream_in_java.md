---
title: "how to initialize a file stream in java"
date: 2008-10-10
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-10-10
Hey All

I'm trying to learn file IO in java but am having some trouble.  I'm writing an application to create password wordlists.  Here's a portion of my code:
```

FileOutputStream dictMaker;
	
	
	// now write a file corresponding to the correct length
	switch (length) {
		
		case 1: 
			// attempt to write to the new file	
			try	{
				
				PrintStream dictionary = new PrintStream(dictMaker);
				dictMaker = new FileOutputStream("alphaLower" + length + ".txt");
				for (char letter = 'a'; letter<='z'; letter++) {
					dictionary.println(letter);				
				} // end for
				
			dictMaker.close(); // close the file
			
			} // end try	
			
			// catch any exceptions
			catch (IOException e) {
				System.out.println("System error.");
			} // end catch
			
			
			break;

```

I'm getting compiler errors that say dictMaker might not have been initialized.  How do I initialize it?
Thanks a lot.  

EDIT:  Sorry for the sloppy formatting in the code block.

---

### Post by patrickballeux on 2008-10-10
Simply declare your variable like this:

FileOutputStream dictMaker = null;

It will not bother you after that.

You sould always assign a value or "Null" to all your declaration.  This way, you know with what you will start with in your process.

Good luck!

---

### Post by the_real_fourthdimension on 2008-10-10
Thanks for the reply.  I did that and it gets rid of the compile-time errors, but it gives me a runtime error:
```

Exception in thread "main" java.lang.NullPointerException: Null output stream
	at java.io.PrintStream.<init>(PrintStream.java:77)
	at java.io.PrintStream.<init>(PrintStream.java:99)
	at java.io.PrintStream.<init>(PrintStream.java:62)
	at DictMaker.alphaLower(DictMaker.java:89)
	at DictMaker.main(DictMaker.java:36)

```

---

### Post by patrickballeux on 2008-10-10
And actually, your output (dictMaker) stream is not initialized with a value.

PrintStream dictionary = new PrintStream(dictMaker);
So it is crashing at this line probably.

You have to assign a value to dickMaker.

Should be something like:
```

dictMaker = new FileOutputStream(new java.io.File("AnOutputFile.txt"));

```

You simply forgot to set an output file in your code...

---

