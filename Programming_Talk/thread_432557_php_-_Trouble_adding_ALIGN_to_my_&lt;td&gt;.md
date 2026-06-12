---
title: "php - Trouble adding ALIGN to my &lt;td&gt;"
date: 2007-05-04
forum: Programming Talk
---

### Post by jingo811 on 2007-05-04
I'm experimenting with a multiplication table and part of the code I can align the numbers to the right by doing so.
```
print"<td align='right'>" . $col*$row . "</td>";
```

But I've been told to style the header part of the multiplication table by doing so.
```
print"<td style='color:white;background:black'><b>" . $col . "</b></td>";
```

Now all the numbers on my main multiplication table is aligned RIGHT but the header indexing numbers are still in default how do I properly add the ALIGN=RIGHT property to my <td>?

I tried doing it like so but it didn't change anything need help plz?
> print"<td style='color:white;background:black;[color=red]align='right'[/color]'><b>" . $col . "</b></td>";

---

### Post by WW on 2007-05-04
Use the attribute **text-align** instead of align, e.g. **text-align: right;**

---

### Post by jingo811 on 2007-05-04
Hey it worked tnx dude :)

---

