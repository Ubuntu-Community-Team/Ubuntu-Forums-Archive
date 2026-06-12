---
title: "(Java) Having a Char variable as opposed to String variable"
date: 2010-01-21
forum: Programming Talk
---

### Post by s3a on 2010-01-21
Here is my unfinished code:
```
import java.util.Scanner;
public class Rectangle
{
	private int x;                             // The x coordinate of this Rectangle.
	private int y;                             // The y coordinate of this Rectangle.
	private int width;                         // The width of this Rectangle.
	private int height;                        // The height of this Rectangle.
**	private char bgchar = ".";**                 // The background char for this Rectangle.
**	private char fgchar = "*";**                // The foreground char for this Rectangle.
	private static final int FRAME_WIDTH = 79; //  The width of the background frame. Fixed and shared by all Rectangle objects
	private static final int FRAME_HEIGHT = 24; // The height of the background frame. Fixed and shared by all Rectangle objects
	
	public Rectangle()
	{
		this.height = 10;
		this.width = 5;
		this.x = 0;
		this.y = 0;
		// "The frame's backround char"
		// "The Rectangle's foreground char"
	}
	public Rectangle(int x, int y, int width, int height/*, char bgchar, char fgchar*/)
	{
		this.x = x;
		this.y = y;
		this.width = width;
		this.height = height;
		//backround
		//foreground
	}
	public void resetAll()
	{
		Scanner kb = new Scanner(System.in);
		
		this.x = kb.nextInt();
		this.y = kb.nextInt();
		this.width = kb.nextInt();
		this.height = kb.nextInt();
		//backround
		//foreground
	}
	// Accessors:
	public int getWidth()
	{
		return width;
	}
	public int getHeight()
	{
		return height;
	}
	public int getX()
	{
		return x;
	}
	public int getY()
	{
		return y;
	}
	/*public int getFgChar()
	{
	}
	public int getBgChar()
	{
	}*/
	// Mutators:
	public void setWidth()
	{
		this.width = width;
	}
	public void setHeight()
	{
		this.height = height;
	}
	public void setX()
	{
		this.x = x;
	}
	public void setY()
	{
		this.y = y;
	}
	/*public void setFgChar()
	{
	}
	public void setBgChar()
	{
	}*/
	public void move(int x, int y)
	{
		this.x = x;
		this.y = y;
	}
	public void rotate(int x, int y)
	{
		this.x = y;
		this.y = x;
	}
	public int area()
	{
		return width * height;
	}
	public int perimeter()
	{
		return (2 * width) + (2 * height);
	}
	public String toString()
	{
		String str = "Width: " + width + "\nWidth: " + width + "\nHeight: " + height + "\nArea: " + this.area() + "\nPerimeter: " + this.perimeter(); // Check if this is correct
		return str;
	}
	/*public draw()
	{
	}*/	
}
```

I realize, that in the bold lines, what I am trying to assign to the variables is causing a syntax error due to the fact that the contents are wrapped in quotation marks (at least I think that's the reason) but, basically, I do not know how to use the char primitive data type. All I know about it is that it is a primitive data type that is used to hold one character (correct me if I am wrong).

I'd appreciate it if someone could tell me how to use it appropriately in this context.

Thanks in advance!

---

### Post by Finalfantasykid on 2010-01-21
Ya so you would have to use the single quotes to remove the syntax error, like you figured.

And you are correct, a char is a primitive type variable not an Object, which means that it neither has a state or any protocol.  In other words, you cannot send methods to the char.  All it is a single byte somewhere in memory, which represents an ASCII character.

So for your setters...
```

public void setFgChar(char newChar)
{
     this.fgchar = newChar;
}

public void setBgChar(char newChar)
{
     this.bgchar = newChar;
}

```

and the getters...

```

public char getFgChar(char newChar)
{
     return this.fgChar;
}

public char getBgChar(char newChar)
{
     return this.bgchar;
}

```

I won't do anything with the other methods since I think it should be pretty obvious how to do it there.

So as you can see, the char works essentially the same way as an int, or double, or float etc.

---

### Post by NovaAesa on 2010-01-21
> **Finalfantasykid said:**
> All it is a single byte somewhere in memory, which represents an ASCII character.

Actually, a char is represented by **two** bytes. The primitive represents a unicode char rather than an ASCII char.

Also if you want to specify a unicode char that is not on the keyboard, you can use the following:

```

char a = '\u89ab';

```

89ab in this example is the code point in unicode of the char to display. You can obviously put any number in there you want between 0x0000 and 0xffff.

---

### Post by Finalfantasykid on 2010-01-21
^I did not know that.  Thanks :D

---

### Post by s3a on 2010-01-21
Thanks to both but, not that it necessarily matters (at least for now), in my course, but; what's the simplistic way of understanding the difference between unicode and ASCII characters? (did I phrase that right?)

@Finalfantasykid:
Thanks for giving me the accessors/mutators. I modified them a bit though as shown in my following (still) incomplete code.
```
import java.util.Scanner;
public class Rectangle
{
	private int x;                             // The x coordinate of this Rectangle.
	private int y;                             // The y coordinate of this Rectangle.
	private int width;                         // The width of this Rectangle.
	private int height;                        // The height of this Rectangle.
	private char bgchar = '.';                 // The background char for this Rectangle.
	private char fgchar = '*';                 // The foreground char for this Rectangle.
	private static final int FRAME_WIDTH = 79; //  The width of the background frame. Fixed and shared by all Rectangle objects
	private static final int FRAME_HEIGHT = 24; // The height of the background frame. Fixed and shared by all Rectangle objects
	
	public Rectangle()
	{
		this.height = 10;
		this.width = 5;
		this.x = 0;
		this.y = 0;
		bgchar = '.';
		fgchar = '*';
	}
	public Rectangle(int x, int y, int width, int height, char bgchar, char fgchar)
	{
		this.x = x;
		this.y = y;
		this.width = width;
		this.height = height;
		this.bgchar = bgchar;
		this.fgchar = fgchar;
	}
	public void resetAll()
	{
		Scanner kb = new Scanner(System.in);
		
		this.x = kb.nextInt();
		this.y = kb.nextInt();
		this.width = kb.nextInt();
		this.height = kb.nextInt();
**		this.bgchar = kb.next();** // Compilation error says it needs a char but this is for strings
**		this.fgchar = kb.next();** // Compilation error says it needs a char but this is for strings
	}
	// Accessors:
	public int getWidth()
	{
		return width;
	}
	public int getHeight()
	{
		return height;
	}
	public int getX()
	{
		return x;
	}
	public int getY()
	{
		return y;
	}
	public char getFgChar()
	{
		 return this.fgchar;
	}

	public char getBgChar()
	{
		 return this.bgchar;
	}
	// Mutators:
	public void setWidth()
	{
		this.width = width;
	}
	public void setHeight()
	{
		this.height = height;
	}
	public void setX()
	{
		this.x = x;
	}
	public void setY()
	{
		this.y = y;
	}
	public void setFgChar(char fgchar)
	{
		 this.fgchar = fgchar;
	}
	public void setBgChar(char bgchar)
	{
		 this.bgchar = fgchar;
	}
	public void move(int x, int y)
	{
		this.x = x;
		this.y = y;
	}
	public void rotate(int x, int y)
	{
		this.x = y;
		this.y = x;
	}
	public int area()
	{
		return width * height;
	}
	public int perimeter()
	{
		return (2 * width) + (2 * height);
	}
	public String toString()
	{
		String str = "Width: " + width + "\nWidth: " + width + "\nHeight: " + height + "\nArea: " + this.area() + "\nPerimeter: " + this.perimeter(); // Check if this is correct
		return str;
	}
	/*public draw()
	{
	}*/
	
	

	
}
```

Before I carry on further. Could you explain why I get compilation errors for the two lines in bold? Also, is my toString() method _logically_ correct? (I still feel a little bit skeptical about writing toString() and equals() methods in my programs and I'm hoping to overcome that :))

---

### Post by Finalfantasykid on 2010-01-21
Well I guess you could do something like this.

```
this.bgchar = kb.next().toCharArray()[0];
```Just be aware that this way could create some problems, like if the person did not enter anything, then it could throw an ArrayOutOfBoundsException.  So you will have to have some way of checking the input that the user enters.

As for your toString method, everything looks fine other than you are putting in the Width twice.

EDIT:  Also I noticed a mistake in your setters for the width, height, x, y.  You have no parameters in those methods.

---

### Post by Axos on 2010-01-21
In a nutshell:

ASCII: barely adequate for the English language
UNICODE: welcomes all the other languages of the world

[http://en.wikipedia.org/wiki/ASCII](http://en.wikipedia.org/wiki/ASCII)
[http://en.wikipedia.org/wiki/Unicode](http://en.wikipedia.org/wiki/Unicode)

---

### Post by samjh on 2010-01-22
> **s3a said:**
> what's the simplistic way of understanding the difference between unicode and ASCII characters?

The ASCII character set is a 7-bit character encoding standard used for the English language and various special characters.

Unicode is a character encoding standard designed to be able to represent characters from multiple languages.  The most common form, UTF-8, uses 8 bits to encode characters and is compatible with the ASCII standard (ie. the 7 least-significant bits in UTF-8 are identical to ASCII).  UTF-16 uses 16 bits to encode characters, and like UTF-8, it is compatible with ASCII.

Java uses UTF-16 for its characters (this is somewhat controversial, as it is one of the reasons for Java's large memory usage).

---

