---
title: "HTML table"
date: 2009-01-19
forum: Programming Talk
---

### Post by liorc666 on 2009-01-19
only markup ... but if you can help me out :

im having a table and inside the table i have a <td> :

<td>1<div style="text-align: right">2</div></td>


what i want to achieve :
|1---------------------------2|

what i get :
|1----------------------------|
|----------------------------2|

EDIT: forum system takes off the white spaces so "-" = " "

---

### Post by jespdj on 2009-01-19
That's because a div is a block-level element; it will not be formatted inline (so that it does not come on the same line as the "1").

Try something like this:
```
<td> <span style="float: left;">1</span> <span style="float: right;">2</span> </td>
```

---

### Post by liorc666 on 2009-01-19
<td><div style="float:left">1</div><div style="text-align: right">2</div></td>

thanks :) very useful

---

