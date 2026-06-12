---
title: "parsing xml"
date: 2010-11-05
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-05
I want to create xml definitions that I can use to define 2D graphics with my iterators for recursive data structures.

e.g. attached is a picture of a recursive triangle, but instead of writing code to create the structure I want to read it from an XML file and have some fun with "fractal" images.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=174604&stc=1&d=1288931364[/IMG]
I know XML can handle hierarchical data no problem but how would I handle the cyclic (recursive) links placing the images themselves within themselves?

I was hoping someone has experience with XML who knows how to do that perhaps ?

---

### Post by Reiger on 2010-11-05
You would create provisions for elements to link to themselves. It's as simple or as difficult as you want it to be because you create the XML format.

A simple enough way would be to define an ID type attribute/element and define a continue/recursion REFID type attribute/element.

So a fractal could be defined to look like this:
```

<fractal limit="300"> <!-- limit to recursion depth of 300 -->
<!-- create a triangle with equal sides -->
<triangle id="base">
  <param name="x"/> <!-- x coord of top of triangle -->
  <param name="y"/> <!-- y coord of top of triangle -->
  <param name="u"/> <!-- vector from top to base of triangle (x) -->
  <param name="v"/> <!-- vector from top to base of triangle (y) -->
  <!-- call base again with new x, y values -->
  <apply refid="base">
    <with-param name="x" value="..."/>
    <with-param name="y" value="..."/>
    <with-param name="u" value="..."/>
    <with-param name="v" value="..."/>
  </apply>
</triangle>
</fractal>

```

---

### Post by worksofcraft on 2010-11-05
> **Reiger said:**
> You would create provisions for elements to link to themselves. It's as simple or as difficult as you want it to be because you create the XML format.

A simple enough way would be to define an ID type attribute/element and define a continue/recursion REFID type attribute/element...

Thanks for that idea Reiger :)
I see XML really is very flexible and it's hard to decide when to make something an attribute of a tag, or to make it into a property tag within the body of something. Having an "id" attribute is a good way to make references and I see they do that in XHTML.

I think XHTML is probably quite a well thought out pattern to emulate so I'll even borrow the idea of having a "class" attribute to determine the appearance of things (I was going to call it layers, but aiming for consistency with existing structures can't be a bad thing. OTOH I don't know why they use css files that are not themselves an XML syntax :confused:

Right from the start I could define coordinates (points) in many different ways:
```

<coord id="top1"><x>10</x><y>20</y></coord>
<!-- or -->
<coord id="top2" x="10" y="20">but then what to put in here?</coord>
<!-- and transformed coordinates -->
<coord><rotate angle="30">
      <value name="top1" />
</rotate></coord>

```

There is a big danger that it becomes hideously verbose and an inefficient way to store and process even trivial diagrams. So now I suppose I need to find some guidelines on systematic and consistent way to convert a data structure into XML :popcorn:

---

### Post by Arndt on 2010-11-05
> **worksofcraft said:**
> Thanks for that idea Reiger :)
I see XML really is very flexible and it's hard to decide when to make something an attribute of a tag, or to make it into a property tag within the body of something. Having an "id" attribute is a good way to make references and I see they do that in XHTML.

I think XHTML is probably quite a well thought out pattern to emulate so I'll even borrow the idea of having a "class" attribute to determine the appearance of things (I was going to call it layers, but aiming for consistency with existing structures can't be a bad thing. OTOH I don't know why they use css files that are not themselves an XML syntax :confused:

Right from the start I could define coordinates (points) in many different ways:
```

<coord id="top1"><x>10</x><y>20</y></coord>
<!-- or -->
<coord id="top2" x="10" y="20">but then what to put in here?</coord>
<!-- and transformed coordinates -->
<coord><rotate angle="30">
      <value name="top1" />
</rotate></coord>

```

There is a big danger that it becomes hideously verbose and an inefficient way to store and process even trivial diagrams. So now I suppose I need to find some guidelines on systematic and consistent way to convert a data structure into XML :popcorn:

For representing any particular structure, XML doesn't give you anything that you couldn't have got with a much simpler format, so think about why you need XML. There may be many good reasons, or none.

Inefficient it may be, but I wouldn't worry about the efficiency for trivial diagrams.

---

### Post by worksofcraft on 2010-11-05
> **Arndt said:**
> For representing any particular structure, XML doesn't give you anything that you couldn't have got with a much simpler format, so think about why you need XML. There may be many good reasons, or none.

Inefficient it may be, but I wouldn't worry about the efficiency for trivial diagrams.

Indeed... I did ask myself that question. I mean I could just dump the data out in binary records, but then I would get problems with byte ordering and how to represent pointers and machines with different word sizes etcetera :shock:

Thus my first reason for choosing XML is because it is a portable text based format and if need be can be edited with a text editor.

My second reason is that I don't want to reinvent things that have already been thought out, tried tested and refined based on real experience unless I have a good reason to avoid it. My biggest concern with XML is exactly how verbose it is.

My third reason is that XML has become industry standard and so there software libraries and tools available for processing XML. e.g. you can open one with Firefox and even if it doesn't know what application it is for it displays a nicely colored nested tree structure with expand/contract tabs.

I suppose I won't really get a feel for it until I start using it so I better go find a tutorial on libexpat or whatever that XML parser library is called. :)

---

### Post by myrtle1908 on 2010-11-05
A bit left-field but have you considered SVG?  Perhaps coupled with Raphael?  This way you could easily use the more lightweight JSON data format.  SVG provides for all the rotation etc and drawing triangles and the like is a cakewalk with Raphael.

Anyhoo, just a thought if you don't mind javascript.

[http://raphaeljs.com/](http://raphaeljs.com/)

---

### Post by worksofcraft on 2010-11-05
> **myrtle1908 said:**
> A bit left-field but have you considered SVG?  Perhaps coupled with Raphael?  This way you could easily use the more lightweight JSON data format.  SVG provides for all the rotation etc and drawing triangles and the like is a cakewalk with Raphael.

Anyhoo, just a thought if you don't mind javascript.

[http://raphaeljs.com/](http://raphaeljs.com/)

Yes, awesome! [SVG]("http://www.w3.org/TR/SVG11/") is exactly the kind of standard I wanted to start with :)

I do have some interesting ideas for this that are probably not in the standard... yet ;)
oh and I've already spotted some interesting ideas in the standard that I haven't quite fathomed why do it that way... like here is one - why use a 3D vector for 2D graphics :confused:
```

current transformation matrix (CTM)
    Transformation matrices define the mathematical mapping from one coordinate
    system into another using a 3x3 matrix using the equation:
    [x' y' 1] = [x y 1] * matrix.
    The current transformation matrix (CTM) defines the mapping from the user coordinate
    system into the viewport coordinate system...

```

Admittedly I'll not be using javascript because one of my objectives is to explore developing proper GUI apps in C++ and also find out a bit more about the lower levels of graphics rendering on X windows based systems and I don't want to tie into any specific SVG processing libraries because I want to be able to explore possibilities of extending and adapting SVG capabilities :guitar:

p.s. my immediate concern is atm to use Gtk builder and Glade to manage the user interface and make double buffering work with Cairo graphics in the application window. Proof of concept code is to get all those recursive triangles rotating smoothly, and then get on to SVG based storage :shock:

---

### Post by myrtle1908 on 2010-11-05
Might be something useful here [http://antigrain.com/about/index.html](http://antigrain.com/about/index.html)

---

### Post by worksofcraft on 2010-11-05
> **myrtle1908 said:**
> Might be something useful here [http://antigrain.com/about/index.html](http://antigrain.com/about/index.html)

Yes, yet another awesome discovery :)
I'm not sure yet how much it overlaps with Cairo graphics functionality but it says it works with X11. Gdk does give me direct access to them.

---

### Post by Reiger on 2010-11-06
> **worksofcraft said:**
>  why use a 3D vector for 2D graphics

Not that I'm particularly knowledge-able about these kinds of things, but 3x3 matrices are used in affine transforms. Then it makes sense to use a 3d vector because relations (concatenated transforms) can be expressed in terms of matrix multiplication.

The Java SE API features a convenience class for implementing affine transforms which has some hints on how it's done: [http://download.oracle.com/javase/1.4.2/docs/api/java/awt/geom/AffineTransform.html](http://download.oracle.com/javase/1.4.2/docs/api/java/awt/geom/AffineTransform.html)

---

### Post by worksofcraft on 2010-11-06
> **Reiger said:**
> Not that I'm particularly knowledge-able about these kinds of things, but 3x3 matrices are used in affine transforms. Then it makes sense to use a 3d vector because relations (concatenated transforms) can be expressed in terms of matrix multiplication.

The Java SE API features a convenience class for implementing affine transforms which has some hints on how it's done: [http://download.oracle.com/javase/1.4.2/docs/api/java/awt/geom/AffineTransform.html](http://download.oracle.com/javase/1.4.2/docs/api/java/awt/geom/AffineTransform.html)

Yes that's weird... I implemented mine with 2x2 matrix... Seems to be working in my [animated "test3"]("http://code.google.com/p/schematrix/"): all the triangle placements rotating within each other... I wonder what I'm missing :confused:

---

