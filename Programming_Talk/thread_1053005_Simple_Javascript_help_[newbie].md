---
title: "Simple Javascript help? [newbie]"
date: 2009-01-28
forum: Programming Talk
---

### Post by aktiwers on 2009-01-28
I am trying to create a simple javascript that checks how many checkboxes that has been checked and then returns one string
 if there is 5 or above checked and another string if there is 4 or below. 

Here is the HTML:
[php]
<script type="text/javascript" src="checkboxCounter.js"></script>

<form method="post" name=playlist>
1<input type=checkbox name=ckbox>
<br>2<input type=checkbox name=ckbox>
<br>3<input type=checkbox name=ckbox>
<br>4<input type=checkbox name=ckbox>
<br>5<input type=checkbox name=ckbox>
<br>6<input type=checkbox name=ckbox>
<br>7<input type=checkbox name=ckbox>
<br>8<input type=checkbox name=ckbox>
<br>9<input type=checkbox name=ckbox>
<p><input type=button value="Count Checkboxes" onClick="anyCheck(this.form)">
</form>
[/php]and here is the Javascript [checkboxCounter.js]
[php]
function anyCheck(form) {
var total = 0;
var max = form.ckbox.length;
for (var idx = 0; idx < max; idx++) {
if (eval("document.playlist.ckbox[" + idx + "].checked") == true) {
    total += 1;
   }
}
if (total < 5) 
{
document.write("<b>Goodbye World</b>");
{
else
{
document.write("Helloworld");
}

[/php]For some reason this works very well without the ELSE statement, but now it does not?

What I'm I missing? 

All help would be great!

---

### Post by jespdj on 2009-01-28
> **aktiwers said:**
> For some reason this works very well without the ELSE statement, but now it does not?
Because you have a { before the else statement which should have been a }.

And this:
[php]if (eval("document.playlist.ckbox[" + idx + "].checked") == true) {[/php]
is much more complex than it needs to be, just do this instead:
[php]if (form.ckbox[idx].checked) {[/php]
There's no need for the 'eval' and '== true'.

---

### Post by aktiwers on 2009-01-28
Thanks Jespdj.
But it is still not working out for me?

It now looks like this:
[php]


function anyCheck(form) {
var total = 0;
var max = form.ckbox.length;
for (var idx = 0; idx < max; idx++) {
if (form.ckbox[idx].checked) {  
    total += 1;
   }
}
if (total < 5) 
{
document.write("<b>Goodbye World</b>");
}
else
{
document.write("Helloworld");
}

[/php]Any ideas? And thanks a lot for you reply :)

---

### Post by sujoy on 2009-01-28
dude, you are still missing the closing brace of the function

---

### Post by matmatmat on 2009-01-28
You need this code:
[PHP]
function anyCheck(form) {
var total = 0;
var max = form.ckbox.length;
for (var idx = 0; idx < max; idx++) {
if (form.ckbox[idx].checked) {  
    total += 1;
   }
}
if (total < 5) 
{
document.write("<b>Goodbye World</b>");
}
else
{
document.write("Helloworld");
}  
}//added closing brace
[/PHP]

---

### Post by aktiwers on 2009-01-28
Oh my god..  haha

Thanks a lot..! :) 
Really, I had not seen that

---

### Post by myrtle1908 on 2009-01-28
[http://www.jslint.com/](http://www.jslint.com/) will help you find errors in your javascript.

---

### Post by jespdj on 2009-01-29
Note: If you indent your code properly, instead of starting every line in the leftmost column, it's much easier to see the structure of your code and you'd immediately see mistakes like this.
[php]
function anyCheck(form) {
    var total = 0;
    var max = form.ckbox.length;
    for (var idx = 0; idx < max; idx++) {
        if (form.ckbox[idx].checked) {  
            total += 1;
        }
    }
    if (total < 5) 
    {
        document.write("<b>Goodbye World</b>");
    }
    else
    {
        document.write("Helloworld");
    }  
}//added closing brace  
[/php]

---

