---
title: "javascript data validation question"
date: 2010-08-08
forum: Programming Talk
---

### Post by badperson on 2010-08-08
Hi,
I have a simple html form page...I have a date input field, and a radio button group. 

When the user clicks submit, I have some java script that makes sure that a) one of the radio buttons is checked and b) that the date parses against a regex. 

If one of those matches fails, however...the user is returned to a blank form. Is there anyway to preserve what was in the other fields?
thanks, 
bp

---

### Post by lkjoel on 2010-08-08
> **badperson said:**
> Hi,
I have a simple html form page...I have a date input field, and a radio button group. 

When the user clicks submit, I have some java script that makes sure that a) one of the radio buttons is checked and b) that the date parses against a regex. 

If one of those matches fails, however...the user is returned to a blank form. Is there anyway to preserve what was in the other fields?
thanks, 
bp
Could show me the source code of the javascript file?

---

### Post by badperson on 2010-08-08
oh man...I walked away from this without posting the code....:(
here's the js:
```
<script type="text/javascript">


	function validateData(){
	ratingIsSelected();
	validateDate();
	
	}

	function ratingIsSelected(){
	var numChecked = 0;
	//alert('test ' + document.brewEntryForm.rating.length);	
		for(i=0;i<document.brewEntryForm.rating.length;i++){
			if(document.brewEntryForm.rating[i].checked){
			numChecked++;
			}
		}
		
		if(numChecked==0){
		alert('select a rating');
		}
	}
	
	
	function validateDate(){
	var dateText = document.brewEntryForm.brewDate.value;
	var dateExpression = /\d{4}-\d{2}-\d{2}/;
	//alert(dateExpression.exec(dateText));	
		if(dateExpression.exec(dateText)==null){
		alert('please enter a date in format: yyyy-dd-mm');
		}
	}

</script>
```


and the button that calls it:

```
<input type="submit" value="enter" onclick="validateData()"/>
```

---

### Post by jflaker on 2010-08-08
> **badperson said:**
> Hi,
I have a simple html form page...I have a date input field, and a radio button group. 

When the user clicks submit, I have some java script that makes sure that a) one of the radio buttons is checked and b) that the date parses against a regex. 

If one of those matches fails, however...the user is returned to a blank form. Is there anyway to preserve what was in the other fields?
thanks, 
bp

When I began programming, my mentor told me "assume the user is full of crap, and go from there".  In other words, never EVER trust user input.  For a calendar, you will see 2/31/2010 and the user will argue it is valid (at least wit the computer).  Where and when possible, use some sort of prompting (ajax comes in handy here) to get the form filled in correctly

Parsing a date becomes troublesome.  Add the text field with a tag onfocus="blur()", which will input inhibit the text field...then add a java popup calendar picker which will add a date text that is absolutely valid.........The point is to keep validation simple...Javascript checks for SOMETHING in the field and you know it is correct...if something is in the field, then it checks out.

Keeps your job simple and ensures all data is valid.

here is a google search for a java popup calendar
[http://www.google.com/search?client=ubuntu&channel=fs&q=calendar+popup+javascript&ie=utf-8&oe=utf-8]("http://www.google.com/search?client=ubuntu&channel=fs&q=calendar+popup+javascript&ie=utf-8&oe=utf-8")

Just my $0.02

---

### Post by lkjoel on 2010-08-12
> **badperson said:**
> oh man...I walked away from this without posting the code....:(
here's the js:
```
<script type="text/javascript">


    function validateData(){
    ratingIsSelected();
    validateDate();
    
    }

    function ratingIsSelected(){
    var numChecked = 0;
    //alert('test ' + document.brewEntryForm.rating.length);    
        for(i=0;i<document.brewEntryForm.rating.length;i++){
            if(document.brewEntryForm.rating[i].checked){
            numChecked++;
            }
        }
        
        if(numChecked==0){
        alert('select a rating');
        }
    }
    
    
    function validateDate(){
    var dateText = document.brewEntryForm.brewDate.value;
    var dateExpression = /\d{4}-\d{2}-\d{2}/;
    //alert(dateExpression.exec(dateText));    
        if(dateExpression.exec(dateText)==null){
        alert('please enter a date in format: yyyy-dd-mm');
        }
    }

</script>
```
and the button that calls it:

```
<input type="submit" value="enter" onclick="validateData()"/>
```
The problem is here:
```
<input type="submit" value="enter" onclick="validateData()"/>
```
try:
```
<button onclick="validateData()">Enter</button>
```

---

### Post by Hellkeepa on 2010-08-12
HELLo!

Actually, I'd recommend firing the JavaScript function "onsubmit", on the forum tag. That way, it does not require the user to actually click on the button to run the validation, but it would also support the user hitting "enter" while on an input field.
In other words: Remove the "onclick" bit on the submit-button, and add the following to the form-tag:
```
onsubmit="return validateData()"
```
Have the function return "false" if the validation fails, or "true" if it succeeds, and the form will only be submitted if the validation succeeds.

PS: Remember that this is no replacement for proper validation on the server, as the user can easily circimvent the validation by simply turning off JS (or not supporting it at all). Even by circumventing the form in its entierty, and posting the data from a completely different page/method.

Happy codin'!

---

