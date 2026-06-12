---
title: "javascript is confusing..."
date: 2008-04-09
forum: Programming Talk
---

### Post by lapubell on 2008-04-09
hello my dearest friends...
I'm working with some javascript that is really confusing me.  I have a form that allows you to choose from a drop down list, or if you want, put new values into text boxes.  however I don't want them to be able to do both.  I am trying to make it so that when you choose an item from the drop down box the text fields go back to the default values, and when you type in the text boxes, the select box goes back to its default value.  I've read some online docs and did the normal google search, but I'm not getting any results.  Any javascript gurus out there want to point me in the right direction or help me out?

I know I can count on my favorite programmers out there.

---

### Post by LaRoza on 2008-04-09
> **lapubell said:**
> hello my dearest friends...
I'm working with some javascript that is really confusing me.  I have a form that allows you to choose from a drop down list, or if you want, put new values into text boxes.  however I don't want them to be able to do both.  I am trying to make it so that when you choose an item from the drop down box the text fields go back to the default values, and when you type in the text boxes, the select box goes back to its default value.  I've read some online docs and did the normal google search, but I'm not getting any results.  Any javascript gurus out there want to point me in the right direction or help me out?

I know I can count on my favorite programmers out there.

You can do this several ways.

[list]
[*] Make a checkbox for each form element, only one checkbox can be checked, so when you get the data, only use the element associated with the checkbox
[*] Disable the other form element, by setting the attribute disabled to disabled. formElementToDisable.setAttribute("disabled","disabled");
[*] Add a custom option to the select. See [http://laroza.freehostia.com/home/apps/styleTester/index.php](http://laroza.freehostia.com/home/apps/styleTester/index.php)
[/list]

In that last example, the page is full of select boxes, but many of them allow the user to select a value not there ("specify"), try it.

---

### Post by lapubell on 2008-04-09
that page you wrote is going to be helpful, but I'm still confused.  This is obnixous.  I'll keep working on it but i just wanted to say thanks.

---

### Post by LaRoza on 2008-04-09
> **lapubell said:**
> that page you wrote is going to be helpful, but I'm still confused.  This is obnixous.  I'll keep working on it but i just wanted to say thanks.

Perhaps you could show some of the code? If the form is simple enough I could write something up for you.

---

### Post by lapubell on 2008-04-09
ok... here is what I have been sruggling with.

pseudo code:
<form action="whatever.php" method="post" name="add">
<select name=""><option name... value... /><option name... value... /><option name... value... />
</select> <!-- this is the select that I want to change the values of some of the inputs below back to their default values...-->

<input type='text' name='newCourse' value="" />
<input type='text' name='newCourse' value="" />
<input type='text' name='newCourse' value="" />
<input type='text' name='newCourse' value="" />
<!-- any of these input boxes, onclick sets the select back to the first option... -->

</form>
end of pseudo code.

I have two different options that I want the user to be able to choose from.  But in case the user changes their mind in the middle of filling out the form, I don't want the select box to have an option besides the first one AND have data besides the defaults in those input boxes.  So if there is any option besides number one selected on the drop down, all those input boxes go back to the defaults, and if they start typing in the input boxes, the select goes back to option 1.  See what I mean?

You are a life saver.  :)

---

### Post by LaRoza on 2008-04-09
> **lapubell said:**
> ok... here is what I have been sruggling with.

pseudo code:
<form action="whatever.php" method="post" name="add">
<select name=""><option name... value... /><option name... value... /><option name... value... />
</select> <!-- this is the select that I want to change the values of some of the inputs below back to their default values...-->

<input type='text' name='newCourse' value="" />
<input type='text' name='newCourse' value="" />
<input type='text' name='newCourse' value="" />
<input type='text' name='newCourse' value="" />
<!-- any of these input boxes, onclick sets the select back to the first option... -->

</form>
end of pseudo code.

I have two different options that I want the user to be able to choose from.  But in case the user changes their mind in the middle of filling out the form, I don't want the select box to have an option besides the first one AND have data besides the defaults in those input boxes.  So if there is any option besides number one selected on the drop down, all those input boxes go back to the defaults, and if they start typing in the input boxes, the select goes back to option 1.  See what I mean?

You are a life saver.  :)

I am not sure what you are trying to do, could you post the actual form code?

---

### Post by lapubell on 2008-04-09
it might be kinda confusing.  It's all mixed in with php to generate the select options...

---

### Post by lapubell on 2008-04-09
real code:

```
<form action="includes/addScore.php" method="post" name="add">
<table style="font-size: 8pt;" cellspacing="10px">
<tr>
	<td valign="middle"><span class='headline2'>Course:</span></td>
	<td valign="middle"><select name="courses"><option value="none">Select a Course</option><option value='Hillsboro Terrace-White'>Hillsboro Terrace - White Tees</option
</select>

<div id="newCourse" style="display: none; padding-top: 12px;">
<input type="text" name="newCourse" style="width: 100px; font-style: italic;" value="Course Name" onblur="if(this.value.length == 0) this.value='Course Name';" onclick="if(this.value == 'Course Name') this.value='';" />&nbsp;&nbsp;&nbsp;

<input type="text" name="newTee" style="width: 90px; font-style: italic;" value="Tee Color" onblur="if(this.value.length == 0) this.value='Tee Color';" onclick="if(this.value == 'Tee Color') this.value='';" />&nbsp;&nbsp;&nbsp;

<input type="text" name="newRating" style="width: 40px; font-style: italic;" value="Rating" onblur="if(this.value.length == 0) this.value='Rating';" onclick="if(this.value == 'Rating') this.value='';" />&nbsp;&nbsp;&nbsp;

<input type="text" name="newSlope" style="width: 40px; font-style: italic;" value="Slope" onblur="if(this.value.length == 0) this.value='Slope';" onclick="if(this.value == 'Slope') this.value='';" />
</div>
```

the input text boxes need to set the select to option "Select a Course" and the drop down, when clicked, needs to set the input boxes to their default values...
hope this clears up what I am trying to do.

---

### Post by LaRoza on 2008-04-09
> **lapubell said:**
> 
the input text boxes need to set the select to option "Select a Course" and the drop down, when clicked, needs to set the input boxes to their default values...
hope this clears up what I am trying to do.

I am kind of pressed for time.

That code is really sloppy, and invalid. It mixes style, deprecated attributes, behavior and weird code. 

I am not able to alter it as it is. Perhaps all style could be moved to an external stylesheet and all the scripting could be removed. (Note, my code has no mixing of such aspects of web development. Looking at the markup for that style tester and you will see)

---

### Post by lapubell on 2008-04-09
you are right.  that code is generated by my php, which is a combo of hand written code and code output from dream weaver which my graphic designer is using.  I usually clean everything up after it works, which is probably not the right way to do things, but I'm new to this.  here is some cleaned up code.  please don't think I'm trying to waste your time, I'm just really stuck here.  I have been reading your wiki and the W3C javascript pages while waiting...

```
<form action="includes/addScore.php" method="post" name="add">
Course:
<select name="courses">
   <option value="none">Select a Course</option>
   <option value='Hillsboro Terrace-White'>Hillsboro Terrace - White Tees</option>
</select>

<input type="text" name="newCourse" value="Course Name"  />
<input type="text" name="newTee" value="Tee Color" />
<input type="text" name="newRating" value="Rating" />
<input type="text" name="newSlope" value="Slope" />
</form>

```

no rush on your time, please don't feel pressured by me...

one last time so anyone new to this thread knows what is going on, the select "courses" has many different options generated by php, and when any is chosen I want to set the values for the text inputs to their default values (this way if they were changed by the user, they go back to what they were).

also, if the user types into the boxes, the select goies back to the "Select a course" option.  This way I can't have the form submitted with both a drop down choice (the default option is ignored) and new text in those boxes (the default text is ignored).

---

### Post by wrightee on 2008-04-10
The simple answer to all pita problems with javascript is Jquery!

```
$('#courseSelect').bind("change",function(){resetMyText()});

function resetMyText(){
$('#texfield1').val("");
..etc
}

```

---

