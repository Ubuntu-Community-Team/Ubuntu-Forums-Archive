---
title: "Java: Can't print character like &quot;newline&quot; or &quot;tab&quot; on strings (\n, \t, etc...)"
date: 2009-03-28
forum: Programming Talk
---

### Post by VotaVader on 2009-03-28
Hi. I'm programming the scanner for a compiler in a course assignment, and I just have to fix this one little bug that I can't figure out why it happens.
The program basically scans a text file, and returns a bunch of "tokens", strings that represent parts of code (like operators, int literals, strings, parenthesis, etc). Anyway, my scanner returns all tokens alright except for some string literals. The problem with them is that instead of applying such characters as the newline (\n) and tab (\t) to the output, it prints them out literally on the strings.

Seems a bit tangled, so I'll show an example:
For a certain string-literal token, the output (on the console) of my scanner is this:

```
Kind = 37 [<string-literal>], spelling = "\n\n\tI \t Fibonacci(I) \n\t=====================\n", position = 15(17)..15(69)
```

and what I should be getting, is this:

```
Kind = 37 [<string-literal>], spelling = "

	I 	 Fibonacci(I) 
	=====================
", position = 15(17)..15(69)
```

So it's basically the same thing, except in my output doesn't have the spacings properly implemented. Now, I'm no java expert, but doesn't the compiler automatically transform these characters into indentation when found in strings?
Maybe there's something I've missed in the code. So here are the methods.
This is the method that creates the string that is printed to the console. I didn't implement this; it came with the skeleton, I just input the "spelling" variable.

```
  public String toString() {
    return "Kind = " + kind + " [" + spell(kind) + 
          "], spelling = \"" + spelling + "\", position = " + position;
  }
```

Now here's the part of the method that creates the "spelling" variable. It basically just keeps adding the characters to the string until it reaches the end of the string (the final "). I didn't include the whole thing, but just the core of what it does.

```

// ...
case '"': // for string literal
    	accept();
    	tokenString = "";
    	while(currentChar != '"'){    		
    		tokenString += currentChar;
    		accept(); // updates currentChar to next char on the file
    	}
    	spelling.append(tokenString);
    	accept();
    	return Token.STRINGLITERAL;
// ...

```

Hope you guys can help, because it's the last glitch I have to correct to have it working perfectly! Thanks!

---

### Post by AsoSako on 2010-03-13
Sorry for posting on an old thread, but I have noticed this as well.  It seems that when trying to use the newline character \n for example r even the system class with System.getProperty("line.separator") Java and Ubuntu do not really get the point across.  What is the newline or tab character for strings in Ubuntu.  Is in different because it is usually \n \t or Linux machines?  Anyone have any idea?!?

---

### Post by kahumba on 2010-03-14
I always use \n and it never failed on Linux nor windows. What's your actual problem, can you give us an example that compiles that we can test your problem?

---

### Post by AsoSako on 2010-03-14
Nothing more then a regular tooltip as such
```
JButton jbutton = new JButton(startIcon);
jbutton.setToolTipText("Something\nSomethingelse");
```

---

### Post by GregBrannon on 2010-03-14
Try ("Something" + \n + "Somethingelse") instead.

---

### Post by GregBrannon on 2010-03-14
> Try ("Something" + \n + "Somethingelse") instead.

Sorry.  I was being a 'tard.  (Just woke up.)  That won't work.  The \n character should be included in the quotes, and it should work fine that way, unless there's something special about button labels.

What output do you get?

---

### Post by AsoSako on 2010-03-14
All of it is just clumped up together in one straight line.   And I have tried the +"\n"+ i also tried + System.getProperty("line.separator")+ which should pull the system line separator symbol.  Maybe it's just something related to tooltips themselves, and I would need to extend the class and modify it?

---

### Post by kahumba on 2010-03-14
The tooltip doesn't support new lines, hence all new line characters are ignored. There's a "workaround" however by using HTML, like in JLabel when you want fancy stuff, except that the sole purpose of HTML in this case is to get multi-line support:

[PHP]
jComponent.setToolTipText("<html>tip line one<br>tip line two</html>");
[/PHP]

For more info Google "java multiline tooltip".

---

### Post by kahumba on 2010-03-14
Forgotten to attach result.

---

