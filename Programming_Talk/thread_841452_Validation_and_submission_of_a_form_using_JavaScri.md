---
title: "Validation and submission of a form using JavaScript"
date: 2008-06-26
forum: Programming Talk
---

### Post by Palu on 2008-06-26
Need: I have a form. When the user clicks "submit", I need a dialog box to say "Are you finished?" Then I need the Yes/OK button to submit and No/Cancel button to do nothing. Eventually I'll add more validation, but I can handle everything other than how submission would be controlled in a JavaScript environment.

My guess: I'll probably have to add a button to the form that says "submit" (but no actual submit button anywhere). The onclick would call a function containing (pseudo code) *if (confirm("text...) submit form xyz, else nothing*

Please let me know if I'm on the right track and how to submit the form via JavaScript. If instead I need to include a submit button, let me know how I would be able to "interrupt" it if the user clicked cancel. :-) Thanks.

---

### Post by WW on 2008-06-27
Disclaimer: I'm no javascript guru, so don't count on this suggestion as being a great design...

In a form that I created, I have a submit button, and I used the **onSubmit** attribute in the form, e.g.
```

<form name="FormName" method="get"
  action="http://...your_url_here..." 
  onSubmit="return validate_form();" >

```
The javascript function **validate_form()** checks the input fields, and if they are all OK, it return true.  Then the browser actually submits the form.  If any of the input fields are incorrect, validate_form() pops up an alert, and returns false, which prevents the browser from submitting the form.  Something like that might work for you; perhaps you could validate your data, and if it is OK, give the user one more chance to cancel with a confirm() dialog.  That is, if the data is not valid, have validate_form() return false after letting the user know why.  If the data is good, have validate_form() return the result of the confirm() dialog.

---

### Post by stevescripts on 2008-06-27
Briefly, the actual submission of the form, is handled by the script that is called by the "action=" value, eg

```

<form name="myform" action="/cgi-bin/parseinput.cgi" method="post">

```

Where parseinput.cgi might be, say a PERL script. (or whatever language floats your boat ;) )
There are lots of links out there that give examples of javascript form validation.  

Beware, however, that relying on  javascript alone, to validate user input is **not safe**.  The script that actually handles the submission to the server needs to parse out dangerous user input.

Hope this helps a bit.

Steve

---

