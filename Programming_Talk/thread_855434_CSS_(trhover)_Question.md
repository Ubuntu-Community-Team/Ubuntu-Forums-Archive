---
title: "CSS (tr:hover) Question"
date: 2008-07-10
forum: Programming Talk
---

### Post by JohnSearle on 2008-07-10
Hello all,

I'm looking to highlight multiple cells using *CSS/html only*, but have failed to find any information on how to do this.

I have gotten single cells to highlight within a row by using the following code:

CSS:
```
.rhigh td:hover {background-color: red;}
```

HTML:
```
<tr class="rhigh">
<td> ... </td>
<td> ... </td>
</tr>
```

I've attempted to use the same code - changing td to tr - to change the entire row at once, but I get no effect in Firefox 3.0.

Any suggestions?

Thanks,

- John

---

### Post by Mickeysofine1972 on 2008-07-10
You might try this in another browser like ff2 or Opera, if get the same result its not the new browser at fault.

I notice that ff3 doesn't deal with css the same as even ff2, for better or worse so give that a try.

You could also try wrapping the <tr> in a <div> of that class instead.

Hope this helps 

Mike

---

### Post by odyniec on 2008-07-10
This should work:
```
tr.rhigh:hover { background-color: red; }
```

---

### Post by JohnSearle on 2008-07-10
Thanks for the reply guys!

> **odyniec said:**
> This should work:
```
tr.rhigh:hover { background-color: red; }
```

This worked like a charm. Is there any explanation behind why it couldn't have been written the way I was attempting? 

- John

---

### Post by odyniec on 2008-07-10
> **JohnSearle said:**
> This worked like a charm. Is there any explanation behind why it couldn't have been written the way I was attempting?
You didn't post the actual code, so I'm not sure what it was, but, assuming you only replaced "td" with "tr", I guess it looked like this:
```
.rhigh tr:hover {background-color: red;}
```
If written this way, this rule is applied to a hovered tr element, which is a descendant of a class="rhigh" element. This does not match your HTML code, as it's the tr element itself having the "rhigh" class, not its ancestor. So the correct rule should match a tr element that has the "rhigh" class, and is hovered.

---

