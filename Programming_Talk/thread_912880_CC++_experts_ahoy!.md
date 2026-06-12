---
title: "C/C++ experts ahoy!"
date: 2008-09-07
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-07
I tried to translate [_this_](http://www.planetxot.com/gml_is_clockwise.htm) and [_this_](http://www.planetxot.com/gml_lines_intersect.htm) into python:
```
def xor(a, b):
	if a == b:
		return True
	elif a != b:
		return False

def is_clockwise(x0, y0, x1, y1, x2,y2):
	"""
	Usage:
	      clockwise = is_clockwise(x0, y0, x1, y1, x2, y2);

	  Description:
	      Given a sequence of three 2D points, return whether or not
	      the sequence is in clockwise or counter-clockwise order.

	  Arguments:
	      x0, y0    coordinate pair for the first point
	      x1, y1    coordinate pair for the second point
	      x2, y2    coordinate pair for the third point

	  Returns:
	      TRUE if the points are in clockwise order,
	      FALSE if the points are in counter-clockwize order,
	      or (-1) if there is no solution.
	      
	  copyright (c) 2006, John Leffingwell
	  www.planetxot.com
	"""
	clockwise = -1
	if ((x0 != x1) or (y0 != y1)):
		if (x0 == x1):
			clockwise = xor((x2 < x1), (y0 > y1))
		else:
			m = ((y0 - y1) / (x0 - x1))
			b = (y0 - m * x0)
			clockwise = xor((y2 > (m * x2 + b)), (x0 > x1))
	return clockwise

def lines_intersect(x0, y0, x1, y1, x2, y2, x3, y3):
	"""
	  Usage:
	      intersection = lines_intersect(x0, y0, x1, y1, x2, y2, x3, y3);
	
	  Description:
	      Determines if two given lines intersect.
	
	  Arguments:
	      x0, y0    1st coordinate pair for the first line
	      x1, y1    2nd coordinate pair for the first line
	      x2, y2    1st coordinate pair for the second line
	      x3, y3    2nd coordinate pair for the second line
	
	  Returns:
	      TRUE when the lines intersect,
	      or FALSE otherwise.
	
	  Dependences:
	      is_clockwise()
	
	  copyright (c) 2006, John Leffingwell
	  www.planetxot.com
	"""
	return ((is_clockwise(x0, y0, x1, y1, x2, y2) != is_clockwise(x0, y0, x1, y1, x3, y3)) \
	and (is_clockwise(x2, y2, x3, y3, x0, y0) != is_clockwise(x2, y2, x3, y3, x1, y1)))
```
Did I do it correctly? Correct this if it is wrong.

---

### Post by Zugzwang on 2008-09-07
Don't know. Normally you would write some tests to see if if works (at least before posting).

However, at least your "xor" function looks incorrect. You are actually implementing XNOR, but that might already be a mistake in the original implementation.

---

### Post by Martin Witte on 2008-09-07
> **Zugzwang said:**
> Don't know. Normally you would write some tests to see if if works (at least before posting).


You could consider the [unit test module ]("http://docs.python.org/lib/minimal-example.html") to write testcases for this code, it is tailor made for a test like this

---

### Post by Wybiral on 2008-09-07
Are you just trying to translate the logic, or make it Pythonic as well? Also, that's not C or C++ (notice the lack of static types) the site says it's GML script (for game maker). If you're going to implement it in Python, you might want to wrap it in a simple class for handling 2d points (a line class doesn't hurt either). I imagine whatever you're using this for, you'll need more point and line methods, so this is just the logical way to go about it.

BTW, Python has an XOR, it's the '^' operator (just like C/C++).

```
[color=#008000]**def**[/color] [color=#0000FF]clockwise[/color](a, b, c):
    [color=#008000]**if**[/color] (a[color=#666666].[/color]x [color=#666666]!=[/color] b[color=#666666].[/color]x) [color=#AA22FF]**or**[/color] (a[color=#666666].[/color]y [color=#666666]!=[/color] b[color=#666666].[/color]y):
        [color=#008000]**if**[/color] a[color=#666666].[/color]x [color=#666666]==[/color] b[color=#666666].[/color]x:
            [color=#008000]**return**[/color] (c[color=#666666].[/color]x [color=#666666]<[/color] b[color=#666666].[/color]x) [color=#666666]^[/color] (a[color=#666666].[/color]y [color=#666666]>[/color] b[color=#666666].[/color]y)
        [color=#008000]**else**[/color]:
            m [color=#666666]=[/color] (a[color=#666666].[/color]y [color=#666666]-[/color] b[color=#666666].[/color]y) [color=#666666]/[/color] (a[color=#666666].[/color]x [color=#666666]-[/color] b[color=#666666].[/color]x)
            [color=#008000]**return**[/color] (c[color=#666666].[/color]y [color=#666666]>[/color] (m [color=#666666]*[/color] c[color=#666666].[/color]x [color=#666666]+[/color] (a[color=#666666].[/color]y [color=#666666]-[/color] m [color=#666666]*[/color] a[color=#666666].[/color]x))) [color=#666666]^[/color] (a[color=#666666].[/color]x [color=#666666]>[/color] b[color=#666666].[/color]x)
    [color=#008000]**else**[/color]:
        [color=#008000]**raise**[/color] [color=#D2413A]**ValueError**[/color]([color=#BA2121]"No solution possible!"[/color])


[color=#008000]**class**[/color] [color=#0000FF]**Point**[/color]:

    [color=#008000]**def**[/color] [color=#0000FF]__init__[/color]([color=#008000]self[/color], x, y):
        [color=#008000]self[/color][color=#666666].[/color]x [color=#666666]=[/color] x
        [color=#008000]self[/color][color=#666666].[/color]y [color=#666666]=[/color] y


[color=#008000]**class**[/color] [color=#0000FF]**Line**[/color]:

    [color=#008000]**def**[/color] [color=#0000FF]__init__[/color]([color=#008000]self[/color], a, b):
        [color=#008000]self[/color][color=#666666].[/color]a [color=#666666]=[/color] a
        [color=#008000]self[/color][color=#666666].[/color]b [color=#666666]=[/color] b

    [color=#008000]**def**[/color] [color=#0000FF]intersects[/color]([color=#008000]self[/color], other):
        a [color=#666666]=[/color] clockwise([color=#008000]self[/color][color=#666666].[/color]a, [color=#008000]self[/color][color=#666666].[/color]b, other[color=#666666].[/color]a)
        b [color=#666666]=[/color] clockwise([color=#008000]self[/color][color=#666666].[/color]a, [color=#008000]self[/color][color=#666666].[/color]b, other[color=#666666].[/color]b)
        c [color=#666666]=[/color] clockwise(other[color=#666666].[/color]a, other[color=#666666].[/color]b, [color=#008000]self[/color][color=#666666].[/color]a)
        d [color=#666666]=[/color] clockwise(other[color=#666666].[/color]a, other[color=#666666].[/color]b, [color=#008000]self[/color][color=#666666].[/color]b)
        [color=#008000]**return**[/color] (a [color=#666666]!=[/color] b) [color=#AA22FF]**and**[/color] (c [color=#666666]!=[/color] d)

[color=#408080]*# a*[/color]
[color=#408080]*# |\*[/color]
[color=#408080]*# b-c*[/color]
[color=#008000]**print**[/color] clockwise(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]))

[color=#408080]*# a*[/color]
[color=#408080]*# |\*[/color]
[color=#408080]*# c-b*[/color]
[color=#008000]**print**[/color] clockwise(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]))

[color=#408080]*# a0  b1*[/color]
[color=#408080]*#   \/*[/color]
[color=#408080]*#   /\*[/color]
[color=#408080]*# b0  a1*[/color]
a [color=#666666]=[/color] Line(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]))
b [color=#666666]=[/color] Line(Point([color=#666666]1[/color], [color=#666666]0[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]))
[color=#008000]**print**[/color] a[color=#666666].[/color]intersects(b)

[color=#408080]*# a0  b0*[/color]
[color=#408080]*#  |  |*[/color]
[color=#408080]*#  |  |*[/color]
[color=#408080]*# a1  b1*[/color]
a [color=#666666]=[/color] Line(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]))
b [color=#666666]=[/color] Line(Point([color=#666666]1[/color], [color=#666666]0[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]))
[color=#008000]**print**[/color] a[color=#666666].[/color]intersects(b)

```

---

### Post by mssever on 2008-09-07
> **Wybiral said:**
> ```
[COLOR=#008000]**def**[/COLOR] [COLOR=#0000ff]clockwise[/COLOR](a, b, c):
```<off-topic>@Wybiral, I noticed that you have correct syntax highlighting without abusing the [noparse][php][/noparse] tags. Apparently, you pasted highlighted code in. How did you accomplish that? I've often found the [noparse][php][/noparse] tags to be inadequate.</off-topic>

---

### Post by Wybiral on 2008-09-07
> **mssever said:**
> I've often found the [noparse][php][/noparse] tags to be inadequate.

Me too (and language-biased, might I add!) so I added this to my site: [http://www.challenge-you.com/bbcode](http://www.challenge-you.com/bbcode)

---

### Post by mssever on 2008-09-07
> **Wybiral said:**
> Me too (and language-biased, might I add!) so I added this to my site: [http://www.challenge-you.com/bbcode](http://www.challenge-you.com/bbcode)
Awesome. Bookmarked.

---

### Post by LaRoza on 2008-09-07
> **Wybiral said:**
> Me too (and language-biased, might I add!) so I added this to my site: [http://www.challenge-you.com/bbcode](http://www.challenge-you.com/bbcode)

Cool.

---

### Post by Kadrus on 2008-09-07
[PostMarkup]("http://code.google.com/p/postmarkup/")

---

### Post by Sinkingships7 on 2008-09-07
> **mssever said:**
> Awesome. Bookmarked.

+1
Thanks Wybiral.

---

### Post by nvteighen on 2008-09-08
Great!

But here's a very subtle "bug" in Scheme:

```
([color=#008000]**define **[/color]([color=#0000FF]a[/color] [color=#19177C]i[/color])
    ([color=#0000FF]a[/color] ([color=#008000]+ [/color][color=#19177C]i[/color] [color=#666666]1[/color])))

```

WARNING: Don't execute this, it's an infinite loop!

The + should have the **same** color as the a, as all procedures are of the same kind, no matter whether primitive or user-defined... at least, that's what Emacs's scheme-mode does.

---

### Post by crazyfuturamanoob on 2008-09-08
> **Wybiral said:**
> Are you just trying to translate the logic, or make it Pythonic as well? Also, that's not C or C++ (notice the lack of static types) the site says it's GML script (for game maker). If you're going to implement it in Python, you might want to wrap it in a simple class for handling 2d points (a line class doesn't hurt either). I imagine whatever you're using this for, you'll need more point and line methods, so this is just the logical way to go about it.

BTW, Python has an XOR, it's the '^' operator (just like C/C++).

```
[color=#008000]**def**[/color] [color=#0000FF]clockwise[/color](a, b, c):
    [color=#008000]**if**[/color] (a[color=#666666].[/color]x [color=#666666]!=[/color] b[color=#666666].[/color]x) [color=#AA22FF]**or**[/color] (a[color=#666666].[/color]y [color=#666666]!=[/color] b[color=#666666].[/color]y):
        [color=#008000]**if**[/color] a[color=#666666].[/color]x [color=#666666]==[/color] b[color=#666666].[/color]x:
            [color=#008000]**return**[/color] (c[color=#666666].[/color]x [color=#666666]<[/color] b[color=#666666].[/color]x) [color=#666666]^[/color] (a[color=#666666].[/color]y [color=#666666]>[/color] b[color=#666666].[/color]y)
        [color=#008000]**else**[/color]:
            m [color=#666666]=[/color] (a[color=#666666].[/color]y [color=#666666]-[/color] b[color=#666666].[/color]y) [color=#666666]/[/color] (a[color=#666666].[/color]x [color=#666666]-[/color] b[color=#666666].[/color]x)
            [color=#008000]**return**[/color] (c[color=#666666].[/color]y [color=#666666]>[/color] (m [color=#666666]*[/color] c[color=#666666].[/color]x [color=#666666]+[/color] (a[color=#666666].[/color]y [color=#666666]-[/color] m [color=#666666]*[/color] a[color=#666666].[/color]x))) [color=#666666]^[/color] (a[color=#666666].[/color]x [color=#666666]>[/color] b[color=#666666].[/color]x)
    [color=#008000]**else**[/color]:
        [color=#008000]**raise**[/color] [color=#D2413A]**ValueError**[/color]([color=#BA2121]"No solution possible!"[/color])


[color=#008000]**class**[/color] [color=#0000FF]**Point**[/color]:

    [color=#008000]**def**[/color] [color=#0000FF]__init__[/color]([color=#008000]self[/color], x, y):
        [color=#008000]self[/color][color=#666666].[/color]x [color=#666666]=[/color] x
        [color=#008000]self[/color][color=#666666].[/color]y [color=#666666]=[/color] y


[color=#008000]**class**[/color] [color=#0000FF]**Line**[/color]:

    [color=#008000]**def**[/color] [color=#0000FF]__init__[/color]([color=#008000]self[/color], a, b):
        [color=#008000]self[/color][color=#666666].[/color]a [color=#666666]=[/color] a
        [color=#008000]self[/color][color=#666666].[/color]b [color=#666666]=[/color] b

    [color=#008000]**def**[/color] [color=#0000FF]intersects[/color]([color=#008000]self[/color], other):
        a [color=#666666]=[/color] clockwise([color=#008000]self[/color][color=#666666].[/color]a, [color=#008000]self[/color][color=#666666].[/color]b, other[color=#666666].[/color]a)
        b [color=#666666]=[/color] clockwise([color=#008000]self[/color][color=#666666].[/color]a, [color=#008000]self[/color][color=#666666].[/color]b, other[color=#666666].[/color]b)
        c [color=#666666]=[/color] clockwise(other[color=#666666].[/color]a, other[color=#666666].[/color]b, [color=#008000]self[/color][color=#666666].[/color]a)
        d [color=#666666]=[/color] clockwise(other[color=#666666].[/color]a, other[color=#666666].[/color]b, [color=#008000]self[/color][color=#666666].[/color]b)
        [color=#008000]**return**[/color] (a [color=#666666]!=[/color] b) [color=#AA22FF]**and**[/color] (c [color=#666666]!=[/color] d)

[color=#408080]*# a*[/color]
[color=#408080]*# |\*[/color]
[color=#408080]*# b-c*[/color]
[color=#008000]**print**[/color] clockwise(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]))

[color=#408080]*# a*[/color]
[color=#408080]*# |\*[/color]
[color=#408080]*# c-b*[/color]
[color=#008000]**print**[/color] clockwise(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]))

[color=#408080]*# a0  b1*[/color]
[color=#408080]*#   \/*[/color]
[color=#408080]*#   /\*[/color]
[color=#408080]*# b0  a1*[/color]
a [color=#666666]=[/color] Line(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]))
b [color=#666666]=[/color] Line(Point([color=#666666]1[/color], [color=#666666]0[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]))
[color=#008000]**print**[/color] a[color=#666666].[/color]intersects(b)

[color=#408080]*# a0  b0*[/color]
[color=#408080]*#  |  |*[/color]
[color=#408080]*#  |  |*[/color]
[color=#408080]*# a1  b1*[/color]
a [color=#666666]=[/color] Line(Point([color=#666666]0[/color], [color=#666666]0[/color]), Point([color=#666666]0[/color], [color=#666666]1[/color]))
b [color=#666666]=[/color] Line(Point([color=#666666]1[/color], [color=#666666]0[/color]), Point([color=#666666]1[/color], [color=#666666]1[/color]))
[color=#008000]**print**[/color] a[color=#666666].[/color]intersects(b)

```

I don't care about the code as long as it does exactly what was it's original purpose.

---

### Post by mssever on 2008-09-08
> **nvteighen said:**
> But here's a very subtle "bug" in Scheme:
And here's one in the Ruby irb highlighter. Here's the out-of-the box irb: 
```
[COLOR=#000080]**irb(main):001:0> **[/COLOR]a [COLOR=#666666]=[/COLOR] [COLOR=#666666][[/COLOR][COLOR=#666666]1[/COLOR],[COLOR=#666666]2[/COLOR],[COLOR=#666666]3[/COLOR][COLOR=#666666]][/COLOR]
[COLOR=#808080]=> [1, 2, 3]
[/COLOR][COLOR=#000080]**irb(main):002:0> **[/COLOR][COLOR=#008000]**def**[/COLOR] [COLOR=#0000ff]b[/COLOR](a)
[COLOR=#000080]**irb(main):003:1> **[/COLOR]  [COLOR=#19177c]@foo[/COLOR] [COLOR=#666666]=[/COLOR] a
[COLOR=#000080]**irb(main):004:1> **[/COLOR][COLOR=#008000]**end**[/COLOR]
[COLOR=#808080]=> nil
[/COLOR][COLOR=#000080]**irb(main):005:0> **[/COLOR]b [COLOR=#008000]%w[q w e r t y][/COLOR]
[COLOR=#808080]=> ["q", "w", "e", "r", "t", "y"]
[/COLOR][COLOR=#000080]**irb(main):006:0> **[/COLOR][COLOR=#19177c]@foo[/COLOR]
[COLOR=#808080]=> ["q", "w", "e", "r", "t", "y"]
irb(main):007:0>
[/COLOR]
```And here's the same thing with the option [COLOR=#880000]IRB[/COLOR][COLOR=#666666].[/COLOR]conf[COLOR=#666666][[/COLOR][COLOR=#19177c]:PROMPT_MODE[/COLOR][COLOR=#666666]][/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#19177c]:SIMPLE[/COLOR] set (which is how I run irb since the prompts are much cleaner:
```
[COLOR=#808080]>> a = [1,2,3]
=> [1, 2, 3]
>> def b(a)
>>   @foo = a
>> end
=> nil
>> b %w[q w e r t y]
=> ["q", "w", "e", "r", "t", "y"]
>> @foo
=> ["q", "w", "e", "r", "t", "y"]
>> 
[/COLOR]
```I'm sure that this is actually a bug in whatever library you're using. And I'm not sure why the first irb example is incompletely highlighted.

---

### Post by Wybiral on 2008-09-08
[Pygments]("http://pygments.org/") is the library I used, it does seem to have some oddities, but it still beats PHP highlighting :)

---

### Post by Wybiral on 2008-09-08
> **crazyfuturamanoob said:**
> I don't care about the code as long as it does exactly what was it's original purpose.

What I posted does... But you don't care what the code looks like, at all?

---

### Post by mssever on 2008-09-08
> **Wybiral said:**
> [Pygments]("http://pygments.org/") is the library I used, it does seem to have some oddities, but it still beats PHP highlighting :)
Duly noted. [Bug reported]("http://dev.pocoo.org/projects/pygments/ticket/363").

---

### Post by crazyfuturamanoob on 2008-09-10
Is this correct? It should return True if a point is inside a triangle:
```
[color=#008000]**def**[/color] [color=#0000FF]point_in_triangle[/color](x0, y0, x1, y1, x2, y2, x3, y3):
	[color=#BA2121][i]"""
	  Usage:
	      inside = point_in_triangle(x0, y0, x1, y1, x2, y2, x3, y3);
	
	  Description:
	      Determines if a given point lays within a given triangle.
	
	  Arguments:
	      x0, y0    1st coordinate pair for the triangle
	      x1, y1    2nd coordinate pair for the triangle
	      x2, y2    3rd coordinate pair for the triangle
	      x3, y3    Coordinate pair of the test point
	
	  Returns:
	      TRUE when the test point is inside of the given triangle,
	      or FALSE otherwise.
	"""[/i][/color]
	[color=#008000]**return**[/color] ([color=#AA22FF]**not**[/color] clockwise(x0,y0,x1,y1,x3,y3) [color=#AA22FF]**and**[/color] [color=#AA22FF]**not**[/color] clockwise(x1,y1,x2,y2,x3,y3) \
	[color=#AA22FF]**and**[/color] [color=#AA22FF]**not**[/color] clockwise(x2,y2,x0,y0,x3,y3))

```
And that colorthing is AWESOME!

---

### Post by mssever on 2008-09-10
> **crazyfuturamanoob said:**
> Is this correct?Why not use a tuple (or a custom point object) to represent a point. In other words, instead of having x0, y0, x1, y1, etc, do ```
x = (0,0)
y = (42,0)
z = (0,42)
```
Then your function could begin: ```
def point_in_triangle(x,y,z):
```This would make for more readable code.

---

### Post by crazyfuturamanoob on 2008-09-11
> **mssever said:**
> Why not use a tuple (or a custom point object) to represent a point. In other words, instead of having x0, y0, x1, y1, etc, do ```
x = (0,0)
y = (42,0)
z = (0,42)
```
Then your function could begin: ```
def point_in_triangle(x,y,z):
```This would make for more readable code.
But it is not in 3d!

---

### Post by mssever on 2008-09-11
> **crazyfuturamanoob said:**
> But it is not in 3d!
Which is why I used 2D points. 3D points would be a 3-tuple like (1,4,54). I was just simplifying the points in point_in_triangle(). On re-reading it, I see that it takes four points as arguments. So do: ```
def point_in_triangle(point1, point2, point3, test):
```where each argument is a 2-tuple like I explained above.

---

### Post by crazyfuturamanoob on 2008-09-12
> **mssever said:**
> Which is why I used 2D points. 3D points would be a 3-tuple like (1,4,54). I was just simplifying the points in point_in_triangle(). On re-reading it, I see that it takes four points as arguments. So do: ```
def point_in_triangle(point1, point2, point3, test):
```where each argument is a 2-tuple like I explained above.
I was just thinking what might that z argument be, but now I get it, the third corner of the triangle.

---

