---
title: "OOo basic: reverse array order?"
date: 2009-03-22
forum: Programming Talk
---

### Post by dhysk on 2009-03-22
as lame as it sounds I thought this would be simple and strait forward however no luck searching the help or google.

This is my first program ever other than the lame "hello world" that is everyone's 'first' program.  Anyway, i can't find how to reverse my array order for instance.

change MyArray(-2,-1,0,1,) into MyArray(2,1,0,-1,)
the array size isn't known and although always in either ascending or descending order it isn't known which one.

I found in visual basic all you have to do is 
```
Array.reverse(MyArray)
```
no luck in OOo basic though ;(.  So I tried to do this
```
	tmp = MyArray
	for x =  LBound(MyArray) to UBound(MyArray)
		MyArray(x) = tmp(UBound(MyArray) - x)
		next x
```

I only go threw it one time however what i get for an output is MyArray(1,0,0,1) and here is the odd part I also get tmp(1,0,0,1)

again originally MyArray(-2,-1,0,1) and without the for loop I verified both arrays are (-2,-1,0,1).  however no matter what the array is it always repeats the 0,0 in the middle and then mirrors the other side.  for example (-30,-29,....0,...,29,30) ill get (29,28,....0,0,....28,29)

---

### Post by Xiong Chiamiov on 2009-03-23
What language is this?  OOo to mean means OpenOffice.org, which is most certainly *not* a programming language.

---

### Post by lisati on 2009-03-23
> **Xiong Chiamiov said:**
> What language is this?  OOo to mean means OpenOffice.org, which is most certainly *not* a programming language.
I think the OP is referring to a version of BASIC.

> **dhysk said:**
> as lame as it sounds I thought this would be simple and strait forward however no luck searching the help or google.

This is my first program ever other than the lame "hello world" that is everyone's 'first' program.  Anyway, i can't find how to reverse my array order for instance.

change MyArray(-2,-1,0,1,) into MyArray(2,1,0,-1,)
the array size isn't known and although always in either ascending or descending order it isn't known which one.

I found in visual basic all you have to do is 
```
Array.reverse(MyArray)
```
no luck in OOo basic though ;(.  So I tried to do this
```
	tmp = MyArray
	for x =  LBound(MyArray) to UBound(MyArray)
		MyArray(x) = tmp(UBound(MyArray) - x)
		next x
```

I only go threw it one time however what i get for an output is MyArray(1,0,0,1) and here is the odd part I also get tmp(1,0,0,1)

again originally MyArray(-2,-1,0,1) and without the for loop I verified both arrays are (-2,-1,0,1).  however no matter what the array is it always repeats the 0,0 in the middle and then mirrors the other side.  for example (-30,-29,....0,...,29,30) ill get (29,28,....0,0,....28,29)

You might want to try something like this:
```
	for x =  LBound(MyArray) to UBound(MyArray)/2
		tmp = MyArray(x)
                MyArray(x) = MyArray(UBound(MyArray) - x)
                MyArray(Ubound(MyArray) - x) = tmp
	next x
```
Note: my example isn't perfect and will probably need a little refinement, "left as an exercise for the reader". (the ubount(...)-x bit works best if the lbound function equates to 0, in other situations it's an error)

---

### Post by dhysk on 2009-03-23
Thanks lisati.  I will try that tonight.  On a side apparently you have to dl and 'install' the Array.Reverse(ArrayName) in visual basic and I couldn't do that.  However on Visual basic my original code worked like a charm.  I still would like to get it to work in Open Office Calc, so I will try your idea. 

Oh and ya OOo Basic referred to Open Office's version of Basic, sorry for the confusion.

---

