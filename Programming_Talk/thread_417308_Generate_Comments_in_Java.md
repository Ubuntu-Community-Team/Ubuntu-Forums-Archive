---
title: "Generate Comments in Java"
date: 2007-04-21
forum: Programming Talk
---

### Post by upidivl on 2007-04-21
Is there a way to auto generate javadoc comments for a java source file?

I know one can do this very easily with Eclipse, but I'm hoping there is a command line based solution.  (Maybe some option with the javadoc command, but I can't find anything.)

---

### Post by Tomosaur on 2007-04-21
Not as far as I'm aware. The whole point of javadoc is to make your code / api understandable and ease development. Javadoc doesn't understand anything about what your software is for, and while it's theoretically possible to auto-generate a very bare javadoc comment by parsing the code, the resulting documentation will be far from useful. The best practice is to just do it yourself - bad documentation is just as bad as no documentation.

---

### Post by upidivl on 2007-04-21
So, you're calling me lazy?  :-)

That's a good point though, it should be on my shoulders to get the comments going.  I did mean the bare comments only, not everything - obviously that is quite impossible.  I like how Eclipse can make the bare javadoc and let me fill in the rest, but really, that isn't too hard or time consuming.

---

### Post by Tomosaur on 2007-04-21
> **upidivl said:**
> So, you're calling me lazy?  :-)

That's a good point though, it should be on my shoulders to get the comments going.  I did mean the bare comments only, not everything - obviously that is quite impossible.  I like how Eclipse can make the bare javadoc and let me fill in the rest, but really, that isn't too hard or time consuming.

Lazy!

Nah - what I meant was, computers are stupid. There may well be a tool out there to do what you describe, but I don't know of it. It just seems to me that writing the comments by hand is the best way to do it. It could be an interesting project anyway - get on with it! :P

---

### Post by pmasiar on 2007-04-22
Comment should explain parts which are not obvious from code: *why* you doing stuff, what are the *unstaed assumtions*, and maybe what *other* ways were tried and discarded (and why they do not work). It is impossible to generate this info from code - it is not there.

---

### Post by upidivl on 2007-04-22
All I want is what Eclipse can do - generate the header of a method with the correct @ parts.  I would then fill in the rest of the needed information.  Check out the generate javadoc option (or whatever) in Eclipse and you'll see what I mean.

I'm well aware that there is no solution for generate *all* my comments and that I need to specify the strict details myself - I do that as it is.

---

### Post by Wybiral on 2007-04-22
> **pmasiar said:**
> Comment should explain parts which are not obvious from code: *why* you doing stuff, what are the *unstaed assumtions*, and maybe what *other* ways were tried and discarded (and why they do not work). It is impossible to generate this info from code - it is not there.

I agree... If it's obvious enough for a computer to generate comments for it... Then it doesn't need commenting. Save the comments for a chunk of code that needs it. If it's just typical code that the average programmer can pick up on... Don't waste your time.

BAD:
```

// Use "i" to iterate from 0 to 99
for(i=0; i<100; ++i)

```

GOOD:
```

// Find dot product of 3d vectors "a" and "b"
d = a[0]*b[0] + a[1]*b[1] + a[2]*b[2];

```

But really, you should aim for as few comments as possible, because you should write your code clear enough not to need comments...

BETTER:
```

dot_product = vec_a[0] * vec_b[0] + vec_a[1] * vec_b[1] + vec_a[2] * vec_b[2];

```

EDIT:

Ooops, I see you need it to produce comments for a documentation system... Sorry for missing that. But, same rule applies, don't waste time documenting obvious code.

---

### Post by eisenklopf on 2008-06-22
'javadoc *.java' should work after you cd into the directory and if you comment your code well enough it's not lazy at all.

---

### Post by LaRoza on 2008-06-22
> **eisenklopf said:**
> 'javadoc *.java' should work after you cd into the directory and if you comment your code well enough it's not lazy at all.

But it won't make comments will it?

---

### Post by geirha on 2008-06-22
Not sure why no one seems to understand what you're asking, but I do (I think). Check out [http://docwiz.sf.net](http://docwiz.sf.net) . It's old, but should do the trick. Seems it has a gui to let you add comments as well as command-line options for adding comment-templates to java-files.

---

### Post by Can+~ on 2008-06-22
> **eisenklopf said:**
> 'javadoc *.java' should work after you cd into the directory and if you comment your code well enough it's not lazy at all.

So you replied a month old topic for.. that?

---

### Post by LaRoza on 2008-06-22
> **geirha said:**
> Not sure why no one seems to understand what you're asking, but I do (I think). Check out [http://docwiz.sf.net](http://docwiz.sf.net) . It's old, but should do the trick. Seems it has a gui to let you add comments as well as command-line options for adding comment-templates to java-files.

Necromancing will make it hard to help the OP...

---

### Post by themusicwave on 2008-06-23
In order for the Javadoc command to work properly you need to comment according to a specific style.

Give this a read:
[http://java.sun.com/j2se/javadoc/writingdoccomments/]("http://java.sun.com/j2se/javadoc/writingdoccomments/")

A short summary is that javadoc comments start with a /** and end with an */

To specifiy a parameter you say @param <TYPE> <INFO>
To specify a return type you say @return <INFO>

Example:

/**This function calculates the area of a square
@param float length The length of the square
@param float width The width of the squar
@return The area of the square.

private float computeArea(float length, float width){
           return length * width;
}

There are many more flags than these, and some IDEs such as Netbeans create all the Java doc for you from teh code.  You just have to fill it in.

When you run that code through javadoc it will make a nice set of HTML pages for you.  The Java API at [http://java.sun.com/javase/6/docs/api/]("http://java.sun.com/javase/6/docs/api/") was created using this tool.  It gives great and helpful documentation output.

The guide explains it much better than this, but is also very long.

---

