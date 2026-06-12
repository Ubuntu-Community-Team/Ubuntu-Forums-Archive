---
title: "Python PIL Image.show() does nothing!"
date: 2007-05-17
forum: Programming Talk
---

### Post by cisforcojo on 2007-05-17
Hey all,

I'm working through the Python Challenge and Image.show() does nothing. I feel like this command could be very useful but I always have to create new files and then load them in GIMP or something to view the pictures.


SPOILER WARNING!!!  SPOILER WARNING!!! SPOILER WARNING!!! 
(Level 11 Solution)
import urllib, Image
from cStringIO import StringIO
def splitOE(source):
    results = []
    width, height = source.size
    results = [Image.new(source.mode, (width//2, height//2))
               for dummy in range(4)]
    for x in range(width):
        for y in range(height):
            target = results[x%2 + (y%2<<1)]
            target.putpixel((x//2, y//2), source.getpixel((x, y)))
    return results
url = 'http://huge:file@www.pythonchallenge.com/pc/return/cave.jpg'
odd_even = splitOE(Image.open(StringIO(urllib.urlopen(url).read())))
for result in odd_even:
    result.show()

This is my code. It doesn't give me any errors, but also doesn't show() the picture.

Thanks!

---

### Post by WW on 2007-05-17
Check your [previous thread]("http://ubuntuforums.org/showthread.php?t=409111"). :)

---

