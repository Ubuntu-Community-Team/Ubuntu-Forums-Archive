---
title: "php issue"
date: 2007-02-22
forum: Programming Talk
---

### Post by ncappel1 on 2007-02-22
Hi everyone, I am trying to write a short php page for my sister. 

I need to know is if there is a way to have a list of items with checkboxes that when activated (checked) will produce a short drop down menu with numbers.

ex:
[]activity 1 [dropdown # 1-10]
[]activity 2 [dropdown # 1-10]

to clarify again, the dropdown menus should only be useable when the appropriate activity next to it has been checked. Is this out of the realm of php?

Nicola

---

### Post by kidders on 2007-02-22
Hi there,

> **ncappel1 said:**
> Is this out of the realm of php?It *might* be, depending on how you want to do it, but that's no problem. :-)

**Option 1**
You might be interested in storing the state of the "Activity" checkboxes in a database, a cookie, a file, etc. If so, there would be a page load between (un)checking a box and enabling the appropriate drop-down list. (Does that make sense?)

This option would require (slightly) more PHP work, since you'd be handling twice as many form submissions. It would also work properly in a JavaScript-free environment.

**Option 2**
You mightn't care about the checkbox state information. In this case, you could use a JavaScript to toggle the availability of the drop-down lists, depending on the states of the checkboxes.

The down-side would be that, without JavaScript, the lists would either be always enabled or always disabled.


If you can be a little more specific about exactly how you would like the form to work (and what you'd like to be able to do with the selected values), I'd be happy to make some suggestions.

---

### Post by Mirrorball on 2007-02-22
If the form is submitted after the checkboxes are selected, PHP can generate a dropdown menu at the next request. If the menus have to appear as soon as the checkboxes are selected, you'll have to use Javascript. And then you'll have to think about people who browse with Javascript turned off.

---

### Post by kidders on 2007-02-22
> **Mirrorball said:**
> If the form is submitted after the checkboxes are selected, PHP can generate a dropdown menu at the next request. If the menus have to appear as soon as the checkboxes are selected, you'll have to use Javascript. And then you'll have to think about people who browse with Javascript turned off.

That was *_far_* more succinct! Thanks, Mirrorball.

---

### Post by Mirrorball on 2007-02-22
> **kidders said:**
> That was *_far_* more succinct! Thanks, Mirrorball.
And I thought about your post: "That was far more detailed. I'm so lazy. I ought to write more thorough answers for beginners. He won't understand a thing about what I wrote. Hopefully kidders's post will make everything clear."

---

### Post by ncappel1 on 2007-02-24
Thanks for the input everyone, I did a little more research, and as it turns out, the answer was pretty simple. Since I wanted to drop down menus to appear immediately next to the boxes, I decided to go the java script route. It had excactly what I needed, the option to "unfocus" a certain field. the exact code I added was this:
```

<script language="javascript" type="text/javascript">
	function offon1() {
		if(document.form1.activity1.checked)
{
document.form1.activity1Persons.disabled=false;
}

else
{
document.form1.activity1Persons.disabled=true;
}	
	}

```

which alters the following snippet:
```

<input type="checkbox" name="activity1" value="activity1" onclick="offon1()">Activity1<select name="activity1Persons" disabled="true">
            <option selected value="1">1</option>
            <option value="2">2</option>

```
in this way, when the "activity1" field gets checked, the dropdown menu (which I made disabled by default) changes from "disabled=true" to "disabled=false" thatis, enabled. if the box is unchecked, the status of the dropdown is unchanged.

this was all for a form to gather information on participants in activities my family's business offers to tourists in our area. Which activities are they interested in? check the box, then tell us how many people will be attending. 

thanks to everyone!
viva ubuntu!

---

### Post by Mirrorball on 2007-02-24
Start with disabled="false" for each select and set it to "true" with Javascript, otherwise users that have disabled Javascript won't be able to fill in this form.

---

