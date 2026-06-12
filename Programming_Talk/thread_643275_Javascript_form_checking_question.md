---
title: "Javascript form checking question"
date: 2007-12-17
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-17
I've never used any javascript (mainly just PHP), but I'm trying to do some client side checking before submitting to a MySQL database.

I've found this:

[php]
/* This script and many more are available free online at
The JavaScript Source!! http://javascript.internet.com
Created by:  |  */

function validate(){
var invalid = " "; // Invalid character is a space

if (document.submitform.filename.value.indexOf(invalid) > -1) {
alert("Sorry, spaces are not allowed.");
return false;
}
else {
return true;
   }
}
[/php]

but I'm wondering if that will work on a form with multiple entries, aka

[php]
echo '<p><object><form action="'. $_SERVER["PHP_SELF"] . '" method="post" name="inputForm" onSubmit="return validate()>';
// echo "<form method=\"post\" action=\"enter_it.php\">";
echo "<label for=\"alignment\">Item Name :</label> <input type=\"text\" name=\"name\" /><br />";
echo "<label for=\"alignment\">Key Number :</label> <input type=\"text\" name=\"id\" /><br />";
echo "<label for=\"alignment\">Picture URL :</label> <input type=\"text\" name=\"pic\" /><br />";
echo "<label for=\"alignment\">Page URL :</label> <input type=\"text\" name=\"link\" /><br />";
echo "<label for=\"alignment\">Description :</label> <input type=\"text\" name=\"description\" /><br />";
echo "<label for=\"alignment\">Type :</label> <input type=\"text\" name=\"type\" /><br />";
echo "<label for=\"alignment\">Price :</label> <input type=\"text\" name=\"price\" /><br />";
echo "<input type=\"submit\" name=\"submit\" value=\"submit\" />";
echo "</form></object></p>";
[/php]

I've tested the Javascript and it does work on a form with a single input, but I have yet to get it to work on one with multiple entries.

Thanks!

---

### Post by LaRoza on 2007-12-17
[php]
window.onload = function()
{
    var formChecked = document.getElementsByTagName("form")[0];
    if (formChecked)
    {
        formChecked.onsubmit = function()
        {
            var items = this.getElementsByTagName("input");
            for (var i=0; i < items.length; i++)
            {
                 if (item[i].value == " ")
                 {
                      return false;
                 }
            } 
            return true;
        }
    }
}

[/php]

Just link to that in an external file, and it should mostly work, tweak as you will.

It has many flaws, the number one is that will end at the first field that is empty, in real life, it should alert the user to each one that is empty, which is easy to do, but I don't have my scripts in front of me.

---

### Post by DouglasAWh on 2007-12-17
my post was a little misleading.  I don't want to do the same thing in each entry, so the loop won't work.  One time I want to check for character length and the next time I want to check for spaces, and such.

---

### Post by LaRoza on 2007-12-17
> **DouglasAWh said:**
> my post was a little misleading.  I don't want to do the same thing in each entry, so the loop won't work.  One time I want to check for character length and the next time I want to check for spaces, and such.

Instead of the loop, you can give each input an id (which is the same as the name), and use the document.getElementById() method, and check its value.
```

<div>
<form method="post" action="enter_it.php">
<label for="alignment">Item Name :</label> <input type="text" name="name" id="name" /><br />
<label for="alignment">Key Number :</label> <input type="text" name="id" id="id" /><br />
<label for="alignment">Picture URL :</label> <input type="text" name="pic" id="pic" /><br />
<label for="alignment">Page URL :</label> <input type=\"text" name="link" id="link" /><br />
<label for="alignment">Description :</label> <input type="text" name="description" id="description" /><br />
<label for="alignment">Type :</label> <input type="text" name="type"  id="type" /><br /> 
<label for="alignment">Price :</label> <input type="text" name="price" id="price" /><br />
<input type="submit" value=\"submit\" />"; 
</form></div> 

```

[php]
window.onload = function() 
{ 
    var formChecked = document.getElementsByTagName("form")[0]; 
    if (formChecked) 
    { 
        formChecked.onsubmit = function() 
        { 
            var returnValue = true;
            var ID = document.getElementById("id");
            //Add the rest

            //Add the check and test for each one, with each rule you need
            if (ID && ID.value = " ")
            {
                 this.style.backgroundColor == "#FF0000";
                 returnValue = false;
            }
            return returnValue;
        } 
    } 
} 
[/php]

---

### Post by DouglasAWh on 2007-12-17
> **LaRoza said:**
> 
[php]
            var returnValue = true;
            var ID = document.getElementById("id");
            //Add the rest

            //Add the check and test for each one, with each rule you need
            if (ID && ID.value = " ")
            {
                 this.style.backgroundColor = "#FF0000";
                 returnValue = false;
            }
            return returnValue;

[/php]

What exactly is the role of returnValue here?  Does the form just know not to submit if it is false?

---

### Post by LaRoza on 2007-12-17
> **DouglasAWh said:**
> What exactly is the role of returnValue here?  Does the form just know not to submit if it is false?

Line by line:

[php]
window.onload = function()  //Page loads, then the following is run
{  
    var formChecked = document.getElementsByTagName("form")[0];  //This is the first form on the page,
    if (formChecked)  //Make sure the form exists
    {  
        formChecked.onsubmit = function()  //when the form is submitted, run the following function
        {  
            var returnValue = true; //The default return value
            var ID = document.getElementById("id"); //The ID field
            //Add the rest 

            //Add the check and test for each one, with each rule you need 
            if (ID && ID.value = " ") 
            { 
                 this.style.backgroundColor = "#FF0000"; 
                 returnValue = false; //Resets returnValue
            } 
            return returnValue; //If at any point a field is in violation of its condition, returnValue will be false.
                                           //Remember, if you return false from an event, it never happened, so the
                                           //will not be submitted
        }  
    }  
} 
[/php]
Line by line:

(

---

### Post by michaelzap on 2007-12-17
I used to reinvent the wheel for every project also. And test and debug my reinvented wheel as well. Now I use jQuery plugins for just about everything, and I have a little more time to live my life.

Try this: [http://plugins.jquery.com/project/validate](http://plugins.jquery.com/project/validate)

Of course JavaScript form validation is no substitute for server-side validation, but it can be a boost to general usability.

---

### Post by LaRoza on 2007-12-18
> **michaelzap said:**
> I used to reinvent the wheel for every project also. And test and debug my reinvented wheel as well. Now I use jQuery plugins for just about everything, and I have a little more time to live my life.

Try this: [http://plugins.jquery.com/project/validate](http://plugins.jquery.com/project/validate)

Of course JavaScript form validation is no substitute for server-side validation, but it can be a boost to general usability.

I just typed that script up quickly, for my sites, I have my own scripts already made and tested.

---

### Post by michaelzap on 2007-12-18
> **LaRoza said:**
> I just typed that script up quickly, for my sites, I have my own scripts already made and tested.

I still do a bit of custom JavaScript myself as needed, so I didn't mean to suggest that you shouldn't or your script was somehow inferior. But man am I happy that I discovered jQuery. It's unbelievably powerful and easy-to-use, so when I end up writing JavaScript now it's usually more complex or specialized scripts because jQuery has made all of the usual stuff work without even trying.

---

### Post by LaRoza on 2007-12-18
> **michaelzap said:**
> I still do a bit of custom JavaScript myself as needed, so I didn't mean to suggest that you shouldn't or your script was somehow inferior. But man am I happy that I discovered jQuery. It's unbelievably powerful and easy-to-use, so when I end up writing JavaScript now it's usually more complex or specialized scripts because jQuery has made all of the usual stuff work without even trying.

I looked into it, but I still like to write my own. Perhaps it is because I like doing it, and it is a hobby.

---

### Post by michaelzap on 2007-12-18
> **LaRoza said:**
> I looked into it, but I still like to write my own. Perhaps it is because I like doing it, and it is a hobby.

Think what you could do if you started with jQuery instead of from scratch, though.

---

### Post by LaRoza on 2007-12-18
> **michaelzap said:**
> Think what you could do if you started with jQuery instead of from scratch, though.

I like starting from scratch. 

I agree, being a programmer means knowing what to write, and what to reuse, but since I do this as a hobby, and do it for fun, my from scratch scripts which I build on are perfect for me.

-EDIT (Looking at the jQuery documentation and source, I see that is a very useful tool, and would speed up development considerably on projects)

---

### Post by DouglasAWh on 2007-12-18
> **michaelzap said:**
> 
Of course JavaScript form validation is no substitute for server-side validation, but it can be a boost to general usability.

There are a few database side limits, like field length, but the site is password protected, so in this case I don't think I need a lot.  This will be "production" use, but it'll just be me using it so I don't have to think about the MySQL syntax each time.  Mostly though, I'm trying to teach myself javascript through something I'll actually use.

Thanks for the help!  I haven't gotten it to work yet, but I'm going to work on it now!

---

### Post by DouglasAWh on 2007-12-29
> **LaRoza said:**
> 
[php]

            //Add the check and test for each one, with each rule you need
            if (ID && ID.value = " ")
[/php]

Firebug says "invalid assignment left-hand side" on the above line.  What does that mean?  I'm looking into it.  Thanks!

---

### Post by LaRoza on 2007-12-29
> **DouglasAWh said:**
> Firebug says "invalid assignment left-hand side" on the above line.  What does that mean?  I'm looking into it.  Thanks!

Common bug, use "==" instead of "=".

Fixed my original.

---

