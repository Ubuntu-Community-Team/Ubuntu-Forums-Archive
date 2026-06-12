---
title: "Python text file to image"
date: 2008-11-27
forum: Programming Talk
---

### Post by tdrusk on 2008-11-27
So far I've got
```

file=raw_input('what is the name of the file?')
print file

f = open(file)
for s in f:
    s = s.strip("\n")
f.close
print len (s)

    
# creates a 50x50 pixel black box with hello world written in white, 8 point Arial text
import Image, ImageDraw, ImageFont

i = Image.new("RGB", (25,25))
d = ImageDraw.Draw(i)
f = ImageFont.truetype("Arial.ttf", 12)
d.text((0,0), s, font=f)
i.save(open("helloworld.png", "wb"), "PNG")

```Now this prints just one line in the picture. If the line is longer than 140 characters I want it to go to the next line. How can I do this?

---

### Post by kaivalagi on 2008-11-27
You could use the textwrap functions: [http://docs.python.org/library/textwrap.html](http://docs.python.org/library/textwrap.html)

But the width used would be in characters, so based on the font used, you may want to have a function to determine width in chars based on pixel width and font type....

interesting problem, maybe someone has a more suitable solution...?

---

### Post by tdrusk on 2008-11-27
> **kaivalagi said:**
> You could use the textwrap functions: [http://docs.python.org/library/textwrap.html](http://docs.python.org/library/textwrap.html)

But the width used would be in characters, so based on the font used, you may want to have a function to determine width in chars based on pixel width and font type....

interesting problem, maybe someone has a more suitable solution...?
Sweet. I'll look into it. Looks like it should work. I originally wanted to do this in java, but python makes it easier I think... I know more about java though.

I know the proper dimensions/font size, so that's not a problem.

---

