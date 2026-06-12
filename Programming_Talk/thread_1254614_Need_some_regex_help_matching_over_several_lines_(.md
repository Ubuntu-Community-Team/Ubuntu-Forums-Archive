---
title: "Need some regex help matching over several lines (vi / sed)"
date: 2009-08-31
forum: Programming Talk
---

### Post by Keith_Beef on 2009-08-31
I've been handed a slew of 160 or so short HTML files that have gone through some kind of batch import process and have been mangled...

[LIST]
[*]About 75% of the files have a block of 13 lines beginning on line 45.
[*]About 25% of the files have a block of 20 lines beginning on line 46.
[/LIST]
But I can't rule out the possibility of the block sometimes starting elsewhere or being a different number of lines.

What is consistent, is that the block begins:
```
<p class=txt><span style="font-family: Arial; font-size: 10.0pt;">&lt;embed 
```
and ends several lines later with:
```
</span></p>
```

The only lines following the block are:
```
</body>

</html>

```

I can match the beginning of the block with the expression:
```
/<pclass=txt.*\n
```


and match the end of the block with:
```
/<\/span><\/p>$
```

I think that I can do one of the following:[LIST]
[*]match the line at the start of the block, and delete it and all following lines to the end of the file, then add the closing tags to each file,
[*]match the whole block and replace it with a null string.
[/LIST]

The big problem I have is matching over several lines.

Is it even possible to do what I'm attempting?

K.

---

### Post by DaithiF on 2009-08-31
Hi,
If you want to delete between two markers then:
```
sed '/<p class=txt/,/<\/span><\/p>$/d' somefile.html
```

or in vim:
```
:g/<p class=txt/,/^<\/span><\/p>/d
```

---

### Post by Keith_Beef on 2009-08-31
> **DaithiF said:**
> Hi,
If you want to delete between two markers then:
```
sed '/<p class=txt/,/<\/span><\/p>$/d' somefile.html
```

or in vim:
```
:g/<p class=txt/,/^<\/span><\/p>/d
```

Thanks, that was a great help, and you saved me hours of work!

The commands did not quite work, there is what I imagine is a typo in each.

[LIST]
[*]For sed, it should be:
```
sed '/<p class=txt/,/<\/span><\/p>/d' inputfile.htm > outputfile.htm
```
i.e., without the extra $ symbol (which had the effect of deleting to the end of the file),

[*]and for Vim, it should be:
```
:g/<p class=txt/,/^.*<\/span><\/p>/d
```
i.e. allowing any extra characters before the closing span tag (I didn't indicate this in my original post, but there are other things on the line before the tag).
[/LIST]

But your indication of how to set the start and end of the selection was the eye-opener, and allowed me to find the fix in two minutes.

K.

---

