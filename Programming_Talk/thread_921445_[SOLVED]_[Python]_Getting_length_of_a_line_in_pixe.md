---
title: "[SOLVED] [Python] Getting length of a line in pixels, HOW??"
date: 2008-09-16
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-16
I got two points, and a line. The line lays between the two points.
Line's width is 1 pixel. How can I count all pixels in the line?

---

### Post by cb951303 on 2008-09-16
in cartesian geometry the distance between two points is calculated like this:

```

p1(x,y), p2(a,b)
[p1p2] = sqrt((a-x)^2 + (b-y)^2)

```

of course in your case it will give you a floating number which you should round up or down according to situation.

---

### Post by Zugzwang on 2008-09-16
> **crazyfuturamanoob said:**
> I got two points, and a line. The line lays between the two points.
Line's width is 1 pixel. How can I count all pixels in the line?

Making sure that everyone knows what is meant, can you please assure that you want the following: 

Since you want to count the number of pixels *in* the line, you do not want the distance of the two points. Example:

```

*###
#*##
#*##
##*#
##*#
###*

```
This is a line 4 pixels wide and 6 pixels high. The number of pixels in the line is 6. Actually, if you use the standard algorithm for line drawing, then the number of pixels equals the maximum of either the x-length or the y-length.

Using anti-aliasing and such stuff makes the result different. No clue how to compute it then, but that won't be too hard.

---

### Post by crazyfuturamanoob on 2008-09-16
> **Zugzwang said:**
> Making sure that everyone knows what is meant, can you please assure that you want the following: 

Since you want to count the number of pixels *in* the line, you do not want the distance of the two points. Example:

```

*###
#*##
#*##
##*#
##*#
###*

```
This is a line 4 pixels wide and 6 pixels high. The number of pixels in the line is 6. Actually, if you use the standard algorithm for line drawing, then the number of pixels equals the maximum of either the x-length or the y-length.

Using anti-aliasing and such stuff makes the result different. No clue how to compute it then, but that won't be too hard.

Indeed. I want to check for amount of pixels in non-anti-aliased line.

---

### Post by crazyfuturamanoob on 2008-09-20
I made this method for checking the amount of pixels in a line:
```
    [color=#008000]**def**[/color] [color=#0000FF]get_length[/color]([color=#008000]self[/color], p1, p2, screen_size):
        [color=#408080]*# point 1*[/color]
        x1 [color=#666666]=[/color] p1[[color=#666666]0[/color]]
        y1 [color=#666666]=[/color] p1[[color=#666666]1[/color]]
        [color=#408080]*# point 2*[/color]
        x2 [color=#666666]=[/color] p2[[color=#666666]0[/color]]
        y2 [color=#666666]=[/color] p2[[color=#666666]1[/color]]
        [color=#408080]*# test surface*[/color]
        testsurf [color=#666666]=[/color] pygame[color=#666666].[/color]Surface(screen_size)
        testsurf[color=#666666].[/color]fill([color=#666666]0[/color]xffffff)
        [color=#408080]*# draw a black line onto the white test surface*[/color]
        pygame[color=#666666].[/color]draw[color=#666666].[/color]line(testsurf, [color=#666666]0[/color]x000000, (x1, y2), (x2, y2), [color=#666666]1[/color])
        [color=#408080]*# count the black pixels and return the number*[/color]
        pixels [color=#666666]=[/color] [color=#666666]0[/color]
        testrow [color=#666666]=[/color] [color=#666666]0[/color]
        [color=#008000]**for**[/color] row [color=#AA22FF]**in**[/color] [color=#008000]range[/color]([color=#666666]0[/color], screen_size[[color=#666666]1[/color]]):
                testpix [color=#666666]=[/color] [color=#666666]0[/color]
                [color=#008000]**for**[/color] pix [color=#AA22FF]**in**[/color] [color=#008000]range[/color]([color=#666666]0[/color], screen_size[[color=#666666]0[/color]]):
                        [color=#008000]**if**[/color] testsurf[color=#666666].[/color]get_at((testpix, testrow)) [color=#666666]==[/color] ([color=#666666]0[/color], [color=#666666]0[/color], [color=#666666]0[/color], [color=#666666]255[/color]):
                                pixels [color=#666666]+=[/color] [color=#666666]1[/color]
                        testpix [color=#666666]+=[/color] [color=#666666]1[/color]
                testrow [color=#666666]+=[/color] [color=#666666]1[/color]
        pixels [color=#666666]-=[/color] [color=#666666]1[/color]
        [color=#008000]**return**[/color] pixels

```
P1 and p2 are tuples presenting the coordinates of the points. screen_size is also a tuple presenting the width and height of the screen.

This method creates a white surface, then draws a black line onto the surface, and counts all the black pixels on the surface.
Then it returns the amount of black pixels. 

But because python is interpreted language, this method is way too slow. It crashes my programs because it is so slow.
And anyway that method sucks, but I got no idea how else it could work.

I got no idea how to do this faster. Perhaps somebody has already made a faster method?

---

### Post by cb951303 on 2008-09-20
as already stated by Zugzwang for a non-anti aliased line the pixel count is either width or the height of the rectangle.

so

```

dist1 = abs(x2 - x1) + 1
dist2 = abs(y2 - y1) + 1

pixelCount = dist1 if dist1 >= dist2 else dist2

```

---

### Post by Wybiral on 2008-09-20
> **crazyfuturamanoob said:**
> But because python is interpreted language, this method is way too slow. It crashes my programs because it is so slow.

It has nothing to do with Python being slow, it's because you're attempting a brute-force solution when a perfectly fine solution has already been mentioned, max(width, height)

---

