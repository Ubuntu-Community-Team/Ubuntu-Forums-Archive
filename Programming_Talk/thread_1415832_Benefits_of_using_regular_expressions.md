---
title: "Benefits of using regular expressions"
date: 2010-02-25
forum: Programming Talk
---

### Post by dvdhl89 on 2010-02-25
Hi,

I was looking how could I use regular expressions to make parsing easier on C#, so I found this [http://msdn.microsoft.com/en-us/library/ms228595%28VS.80%29.aspx](http://msdn.microsoft.com/en-us/library/ms228595%28VS.80%29.aspx)

So far all I see that it compares strings to find a match with the pattern you define.

Isn't this the same thing that the contains(string) method does? :confused: Sorry if this was a n00b question :S

---

### Post by howlingmadhowie on 2010-02-25
> **dvdhl89 said:**
> Hi,

I was looking how could I use regular expressions to make parsing easier on C#, so I found this [http://msdn.microsoft.com/en-us/library/ms228595%28VS.80%29.aspx](http://msdn.microsoft.com/en-us/library/ms228595%28VS.80%29.aspx)

So far all I see that it compares strings to find a match with the pattern you define.

Isn't this the same thing that the contains(string) method does? :confused: Sorry if this was a n00b question :S

regular expressions can do a lot more, things like:

[abc]{10,11} will match a string which contains a chain of length 10 or 11 containing either a's, b's or c's.

you can also do stuff like:
[^b].*
which will match any word which doesn't begin with a small 'b'

---

### Post by dvdhl89 on 2010-02-25
Oh, thanks I guess I didn't searched well enough, should have looked at the Regex class methods and attributes also. 

Thanks again for the reply

---

### Post by doas777 on 2010-02-25
you can also do transformations and substitutions, and many other things that are over my head...

---

### Post by myrtle1908 on 2010-02-25
No idea if .NET/C# support assertions in regexes, but these are IMO the most powerful and useful beasts available to a decent regex implementation ... [http://www.regular-expressions.info/lookaround.html](http://www.regular-expressions.info/lookaround.html)

---

### Post by doas777 on 2010-02-25
> **myrtle1908 said:**
> No idea if .NET/C# support assertions in regexes, but these are IMO the most powerful and useful beasts available to a decent regex implementation ... [http://www.regular-expressions.info/lookaround.html](http://www.regular-expressions.info/lookaround.html)
.net regex support is pretty strong. it's not dissimilar to java's or python's implementation.
[http://www.regular-expressions.info/dotnet.html](http://www.regular-expressions.info/dotnet.html)

---

