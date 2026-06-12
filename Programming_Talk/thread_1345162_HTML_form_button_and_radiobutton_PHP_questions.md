---
title: "HTML form button and radiobutton PHP questions"
date: 2009-12-03
forum: Programming Talk
---

### Post by dmillerw on 2009-12-03
What I'm attempting is to have a HTML form submit button that when clicked, creates a javascript dialog box that will allow the user to continue or cancel the action, is this possible?

Secondly, is there a way to have a radio button's default be a value in a MySQL database?

---

### Post by korvirlol on 2009-12-03
> **dmillerw said:**
> What I'm attempting is to have a HTML form submit button that when clicked, creates a javascript dialog box that will allow the user to continue or cancel the action, is this possible?


here is an example:
[php]
<script>
function trysubmit(){
     var submit = confirm("are you sure you want to continue?");

     if(!submit){
          return false;
     }

     document.yourform.submit();
}
</script>

<form action = '' method = '' name = 'yourform'>

form stuff

<input type = 'button' value = '' onclick = 'trysubmit()'>
</form>[/php]you can have any form element be whatever value from your database from a query. Note that radiobuttons are either checked, or not checked. You can "check" the radio button when your page loads by using the attribute "checked":

```
<input type = 'radio' checked>
```

---

### Post by dmillerw on 2009-12-03
> **korvirlol said:**
> here is an example:
[php]
<script>
function trysubmit(){
     var submit = confirm("are you sure you want to continue?");

     if(!submit){
          return false;
     }

     document.yourform.submit();
}
</script>

<form action = '' method = '' name = 'yourform'>

form stuff

<input type = 'button' value = '' onclick = 'trysubmit()'>
</form>[/php]you can have any form element be whatever value from your database from a query. Note that radiobuttons are either checked, or not checked. You can "check" the radio button when your page loads by using the attribute "checked":

```
<input type = 'radio' checked>
```
I tried that code, but it executes the form whether I press OK or Cancel

---

### Post by dmillerw on 2009-12-04
Anyone

---

### Post by CyberJack on 2009-12-04
This sould work for the submitting part.
Now if javascript is disabled your form will still be submitted. This means that you have to check your input of the processing side (always highly advisable).

[HTML]
<html>
<head>
	<script type="text/javascript">
		function trysubmit()
		{
			var submit = confirm("are you sure you want to continue?");
			if(!submit)
				return false;
			return true;
		}
	</script>
<head>
</body>
	<form action='' method='' name='yourform' onsubmit="return trysubmit();">
	<input type='submit'>
	</form>  
</body>
</html>
[/HTML]

The automatically checking of a radiobutton depends on you html style.(so does the code above).
If you use html 4.01 you can you the example from korvirlol.
If you use xhtml use this code:

[HTML]
<input type="radio" value="" name="" checked="checked" />
[/HTML]

---

### Post by korvirlol on 2009-12-04
> **dmillerw said:**
> Anyone

The very simply example I posted works.

perhaps you should post the code you used. It would be more beneficial then simply posting it doesnt work.

---

### Post by dmillerw on 2009-12-05
My bad, but CyberJacks code worked, thanks.

---

