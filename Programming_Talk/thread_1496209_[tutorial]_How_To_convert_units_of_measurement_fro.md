---
title: "[tutorial] How To convert units of measurement from one unit or system to another"
date: 2010-05-29
forum: Programming Talk
---

### Post by astkboy2008 on 2010-05-29
Today i will learn you new way to convert units of measurement from one unit or system to another and we will use simple php class
first you should **download** it:[Length Class]("http://www.jooria.com/projects/view?project=987&m=downloads") or **download** the class source code:


[LIST]
[*][convert.php *[1.66  KB]*]("http://www.jooria.com/view/file/509/convert.php")
[*][length.php *[3.07  KB]*]("http://www.jooria.com/view/file/509/length.php")
[*][length.xml *[808  B]*]("http://www.jooria.com/view/file/509/length.xml")
[/LIST]

[FONT=Impact][SIZE=4]now how we can use it?[/SIZE][/FONT]
For example, we can define the relationship between any unit of length  by the number of that length per one meter. 
[PHP]1 m = 100 cm[/PHP]
With this ratio – which we can simply write as 100 – we can easily  convert from meters to the new units. We can also convert from the unit  cm back to meters by inverting the **ratio – 1 / 100**.The length class  makes use of this simple principal. A data file (length.xml) contains  information about each unit of measurement – an abbreviation, a full  name, and this ratio. When the ‘length’ is constructed, it converts it  from the given unit into the SI unit for length – meters.
You can  then easily retrieve this length value in any other defined unit type. 
**[FONT=Impact][SIZE=4]Example Use[/SIZE][/FONT]**

If you download the source code, it comes with a file “convert.php.”  This isn’t part of the class – it just gives you an example of how to  implement the class. Here’s a very simple example to show you the syntax for creating a new  length instance and converting a value starting in centimeters to  inches. [PHP]$len = new length(50, 'cm');
echo $len->getConversion('in') . 'in';[/PHP]
The length constructor takes three arguments – one required and two  optional.  The first argument is the value of your length (50 in this case). The  second parameter is the abbreviation of the unit type (cm). If a unit  is not sent, then it is assumed you’re creating a length in meters. The  last argument is the path/filename to the “length.xml” data file. It’s  assumed to be located in “length.xml” if a path isn’t given.
  The constructor then converts that value into the standard unit –  meters.  getConversion() takes one argument – the new unit type. It takes the  stored value (in meters) and returns it converted to the unit type you  gave.**Extending Length to Include Other Units**The data  file included with the class is by no means intended to be exhaustive.  In fact, it’s pretty limited at the moment. I will probably eventually  update it with a more or less complete list of units.
  However, it was created to be easily adaptable by the user. You could  even make up new imaginary units (for use in a game, maybe).  All you need to do is add a new entry to the xml data file with this  format. 
```
<unit>
    <abbrev>cm</abbrev>
    <ratio>100</ratio>
    <fullName>centimeters</fullName>
</unit>
```

---

### Post by trent.josephsen on 2010-05-29
> **astkboy2008 said:**
> Today i will learn you new way to convert units of measurement from one unit or system to another <snip>

That's "teach", not "learn".

On the whole, your English is not bad, but you need to learn to proofread.  All 15 of your posts exhibit linguistic messiness, not only obscure English grammar mistakes (which are easy to make and will probably be forgiven) but very basic errors like omitting spaces betweenwords and periods at the ends of sentences

I admire your attempts to share knowledge of PHP, but if you want your material to be useful to others, please make an effort to clean it up.  Not only is clearly presented material far more useful than messy stuff, but the care you take in presentation shows your audience how much you care about the topic.  You will more probably be taken seriously if your posts show that you have put effort into them.

---

### Post by gmargo on 2010-05-29
The point of all this is kind of lost on me, especially with a tiny conversion database.

For unit conversion, I prefer the classic unix utility **units(1)**.

[http://packages.ubuntu.com/lucid/units](http://packages.ubuntu.com/lucid/units)

---

### Post by astkboy2008 on 2010-05-30
> **trent.josephsen said:**
> That's "teach", not "learn".

On the whole, your English is not bad, but you need to learn to proofread.  All 15 of your posts exhibit linguistic messiness, not only obscure English grammar mistakes (which are easy to make and will probably be forgiven) but very basic errors like omitting spaces betweenwords and periods at the ends of sentences

I admire your attempts to share knowledge of PHP, but if you want your material to be useful to others, please make an effort to clean it up.  Not only is clearly presented material far more useful than messy stuff, but the care you take in presentation shows your audience how much you care about the topic.  You will more probably be taken seriously if your posts show that you have put effort into them.
this is great advice from big brother;
thank you
and many people told that to me
but not by this method
by saying to me i'm fool and stupid

---

### Post by Reiger on 2010-05-30
Useless. Converting units like that has no purpose, because the result values are almost but not quite human readable. You'll get results like 1.25ft instead of 1ft 3in (12 inch to a foot, IIRC) or 1' 3".

So the only useful application would be in technical calculations; and at that point you really should be using SI end-to-end anyway. Otherwise you end up losing your spacecraft.

---

