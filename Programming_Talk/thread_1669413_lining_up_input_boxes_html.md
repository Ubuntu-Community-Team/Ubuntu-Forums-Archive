---
title: "lining up input boxes html"
date: 2011-01-17
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-17
like when you look at a google advanced search, they are all neatly placed.
how is that done?
I tried setting up input boxes, but they tend to run all over and spacing with %nbsp and various span but not what I want to see.



>     <form action="<?=$_SERVER['PHP_SELF']?>" method="post">
    <B>Find library results that have...</B><BR><BR>
    all these words: <input type="text" SIZE="80"style="text-align: left" name="andwords"></span><BR>
    exact wording or phrase: &nbsp; &nbsp;&nbsp;  <input type="text" SIZE="80"name="exactphrase"></span><BR>
    one or more of these words: &nbsp; &nbsp; <input type="text" SIZE="80"name="orwords"></span><BR><BR>
    <B>But don't show results that have...</B><BR><BR>
    exclude all of these words:  <span style="padding-left:17px"><input type="text" SIZE="80"name="exwords"></span><BR><BR>
    <input type="submit" name="submit"> <INPUT type="reset">
    </form>

I have a VB6 program that my wife uses at her library that I wrote years ago, and I was thinking of enabling it to work in the browser

---

### Post by The Cog on 2011-01-17
I usually put them all in cells in a table to make them line up.
```
<table>
<tr><td>name</td><td><input type="text"></td></tr>
<tr><td>number</td><td><input type="text"></td></tr>
</table>
```

---

### Post by sdowney717 on 2011-01-17
Thanks, that does work well

---

