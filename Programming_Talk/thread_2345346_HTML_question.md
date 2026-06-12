---
title: "HTML question?"
date: 2016-12-03
forum: Programming Talk
---

### Post by KayeNg on 2016-12-03
Is it ok to ask html questions here?

I'm using bluegriffon to make a website and I need to insert a perl script:

<form style="width: 255px;" action="/cgi-sys/entropysearch.cgi"
                      target="searchwindow"><font color="#333333"><font face="FreeSans, sans-serif"><font
                            style="font-size: 22pt" size="6"> <input name="query"
                              value="" type="text"> <input name="user" value="mywebsi"
                              type="hidden"> <input name="basehref" value="http://mywebsite.org"
                              type="hidden"> <input name="template" value="default"
                              type="hidden"> <input value="Search" type="submit">
<br>
            </font></font></font></form>

The above is a search bar and I want it to be placed beside a series of buttons.

Four example, in a single row, I have home, about us, contact, site map buttons.  To the right of these four buttons, there should be a search bar.  

When I insert the code to where I think it should be, the search bar is placed a row below the row of buttons, instead of being beside them.

help please

---

### Post by kpatz on 2016-12-03
Put the row of buttons inside the <form>.

So, you'd have:
```

<form style="width: 255px;" action="/cgi-sys/entropysearch.cgi"
target="searchwindow">
**<!-- Put code for row of buttons here-->**
<font color="#333333" face="FreeSans, sans-serif" 
style="font-size: 22pt"> <input name="query"
value="" type="text"> <input name="user" value="mywebsi"
type="hidden"> <input name="basehref" value="http://mywebsite.org"
type="hidden"> <input name="template" value="default"
type="hidden"> <input value="Search" type="submit">
<br>
</font></form>

```
Also, if the row of buttons is in a table, I'd add another column (<td>...</td> tag) to the table and put the search bar there.

Also, you can see I consolidated your <font> tags for you as well.  I removed the font size=6 since it's redundant with the font-size: 22pt in the style attribute.

It's more standard nowadays to use CSS for fonts and styles nowadays, but if you're just starting out you can learn that later.

---

### Post by KayeNg on 2016-12-19
Excellent! Thank you!

---

### Post by KayeNg on 2016-12-29
Hey kpatz, I can't seem to change to width of the text box, the box where one types whatever it is he's searching for.

---

### Post by slickymaster on 2016-12-29
*Thread moved to **Programming Talk**.*

---

### Post by SeijiSensei on 2016-12-29
> **KayeNg said:**
> Hey kpatz, I can't seem to change to width of the text box, the box where one types whatever it is he's searching for.

Use CSS:
```

<textarea style='width:500px; height:300px'></textarea>

```

You can use the same method with "<input type='text' ...>".

---

