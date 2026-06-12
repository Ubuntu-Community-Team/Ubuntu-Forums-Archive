---
title: "(Java) Need help with a not so easy nested for loop"
date: 2010-01-23
forum: Programming Talk
---

### Post by s3a on 2010-01-23
This is what I need to be able to do with my nested for loops (the formatting is slightly off):

> **********.....................................................................

**********.....................................................................

**********.....................................................................

**********.....................................................................

**********.....................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

...............................................................................

x coordinate: 0

y coordinate: 0

width:        10

height:       5

background:   .

forground:    *

area:         50.0

perimeter:    30.0


Here is my Rectangle class (I made this):
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
	private static final int FRAME_WIDTH = 79; //  The width of the background frame. Fixed and shared by all Rectangle objects.
	private static final int FRAME_HEIGHT = 24; // The height of the background frame. Fixed and shared by all Rectangle objects.

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
		this.bgchar = kb.next().charAt(0); // Reads a string and extracts the first character.
		this.fgchar = kb.next().charAt(0); // Reads a string and extracts the first character.
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
	public void rotate()
	{
		int temp = height; // Stores the height variable's contents into the temp variable
		this.height = width; // Stores the width variable's contents into the height variable
		this.width = temp; // Stores the temp variable's contents which is the former height variable's contents into the width variable.
	}
	public int area()
	{
		return width * height;
	}
	public int perimeter()
	{
		return (2 * width) + (2 * height);
	}
	public String toString() // Add things like backround and foreground for example, as well as x and y coordinates (=4 things that need to be added)
	{
		String str = "\nWidth: " + width + "\nHeight: " + height +
		"\nArea: " + this.area() + "\nPerimeter: " + this.perimeter()
		+ "\nBackround: " + bgchar + "\nForeground: " + fgchar + 
		"\nx-coordinate: " + x + "\ny-coordinate: " + y;

		return str;
	}
	public void draw() // Still needs work
	{
		for(int h = 1; h <= FRAME_HEIGHT; h++) // 24
		{
			for(int w = 1; w <= FRAME_WIDTH; w++) // 79
			{
				if(w <= width)
					System.out.print(fgchar);
				else if(w > width && w <= FRAME_WIDTH)
					System.out.print(bgchar);
			}
		if(h <= height)
			System.out.print(fgchar);
		else if(h > width && h < FRAME_HEIGHT)
			System.out.print(bgchar);
		}
	}
}
```

Here is the code that my teacher made in order to test our programs:
```
public class RectangleDemo
{
	public static void main(String[] args)
	{
		// 1st Code Fragment
		Rectangle r1 = new Rectangle();
		r1.draw();
		System.out.println(r1);

		// 2nd Code Fragment
		//r1.move(45, 10);
		//r1.draw();
		//r1.rotate();
		//r1.draw();

		// 3rd Code Fragment
		//Rectangle r2 = new Rectangle(30, 10, 7, 11, '-', '+');
		//r2.draw();
		//r2.move(45, 3);
		//r2.draw();

		// 4th Code Fragment
		//r2.rotate();
		//r2.draw();

		// 5th Code Fragment
		//r2.resetAll();
		//r2.draw();
		//System.out.println(r2);

		// 6th Code Fragment
		//Rectangle r3 = new Rectangle(20, 5, 15 , 10, 'o', 'X');
		//r3.draw();
		//r3.move(-5, -5); //
		//r3.draw();
	}
}
```

I am testing the 1st code fragment and do not get the desired result. Here is what I get when running off the terminal:

> java RectangleDemo
*****..........................................................................******..........................................................................******..........................................................................******..........................................................................******..........................................................................******..........................................................................******..........................................................................******..........................................................................******..........................................................................******..........................................................................******...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****...........................................................................*****..........................................................................
Width: 5
Height: 10
Area: 50
Perimeter: 30
Backround: .
Foreground: *
x-coordinate: 0
y-coordinate: 0

When I run it the normal way in geany (my IDE/text editor), I get a more rectangular looking set of stars which is not what I the terminal or above shows but I pasted it anyways since it could be important. This is the last thing I can't do and I'll have finished this program if someone could please help me with the nested for loop. I AM capable of doing basic nested for loops ...

Example:
```
public class nested
{
	// 10x10 "Square" (Looks like a Rectangle though because of spacing)
	public static void main(String[] args)
	{
		for(int width = 1; width <= 10; width ++)
		{
			for(int height = 1; height <= 10; height++)
			{
				System.out.print("+");
			}
		System.out.println();
		}
	}
}
```
... but I need help in this case.

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by rogue_0111 on 2010-01-23
--

Check out:

[http://www.dreamincode.net/forums/showtopic90878.htm](http://www.dreamincode.net/forums/showtopic90878.htm)

And they have live help.

--

---

### Post by DougB1958 on 2010-01-23
Here's a thought (well, OK, a couple of questions that might help you see what's wrong): a printed rectangle consists of several lines of text. How do you tell when one line is finished and the next should start? What Java statement(s) would end the current output line and start a new one?

---

### Post by mess110 on 2010-01-24
```

void draw() {
  for (int j = 0; j < FRAME_HEIGHT; j++) {
    for (int i = 0; i < FRAME_WIDTH; i++) {
      if ((x <= i && i < width + x) && (y <= j && j < height + y)) {
        System.out.print("#");
      } else {
        System.out.print(".");
      }
    }
    System.out.println();
  }
}

```

One possible solution is to check each frame position, one by one, if it is a rectangle or not.

---

