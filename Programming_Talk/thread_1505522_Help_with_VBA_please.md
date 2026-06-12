---
title: "Help with VBA please"
date: 2010-06-09
forum: Programming Talk
---

### Post by smdawson on 2010-06-09
Previously all of my questions about C++ have been answered very helpfully (@dwhitney67 & @MadCow108). Hopefully you guys know VBA as well ;)
 
For a project at my summer-internship I need to know how to split a 16b binary line into two arrays(or vectors?) of 4b and 12b, using VBA. I am not familiar with VBA and have trouble following the syntax at this point. 
 
(i.e.) 1111111111110000 >>(split into 2 arrays somehow)
array1(12b) = 111111111111
array2(4b) = 0000
 
After this I will perform some simple binary calculations with the two pieces of information.
 
If you could point out any VBA reference material as helpful as cplusplus.com and learncpp.com is, that would be appreciated!

---

### Post by rrashkin on 2010-06-09
VBA isn't something that pertains to LINUX at all in my experience but I do use it at work.

Take a number, [COLOR="Red"]n[/COLOR].
Convert it to a hex string: [COLOR="Red"]h=hex(n)[/COLOR]
Note that this may require adding on the analysis package, at least for Excel, you don't say what application you're using.
Now, here's a function I wrote to convert a hex string to a binary string:
```
Function h2b(hstr)
'convert hex string to binary string
    cnvarr = Array("0000", "0001", "0010", "0011", "0100", 0101", "0110", "0111", "1000", "1001", "1010", "1011", "1100", "1101", "1110", "1111")
    bstr = ""
    For i = 1 To Len(hstr)
        hdgt = Mid(hstr, i, 1)
        cix = CInt("&H" & hdgt)
        bstr = bstr & cnvarr(cix)
    Next
    h2b = bstr
End Function
```

But you didn't ask about any of that. You're starting with a 16-character binary string, s.

The 1st 12 characters are [COLOR="Red"]left(s,12)[/COLOR]
The last 4 characters are [COLOR="Red"]right(s,4)[/COLOR]
To convert a string to an array or list, you have to loop through the string one character at a time:
```
for i = 1 to len(s)
    a(i)=mid(s,i,1)
next
```

where a was defined to be an array:[COLOR="Red"]dim a(len(s))[/COLOR]

I have to say, though, that VBA is a poor choice for this unless you need to work within an application.  This sort of thing is just what Python was made for (the string is already a list).

---

