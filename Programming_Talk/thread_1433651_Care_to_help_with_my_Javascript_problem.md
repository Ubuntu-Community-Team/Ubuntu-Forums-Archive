---
title: "Care to help with my Javascript problem?"
date: 2010-03-19
forum: Programming Talk
---

### Post by skymera on 2010-03-19
I'm a JavaScript noob and we're just starting to learn some at college.

I've created a web page which has a feedback form, a series of drop downs and text input boxes.
I've added validation to each of these so if they're blank or left empty, the submit button will not submit, an alert box will show.

If everything is done correct, the submit button will allow the data to be sent.

Now, my problem.
When the submit button is clicked, IF everything is correct, I'd like a separate page to load which just says "thanks" it's called Submit.HTML.

But if something is unanswered, i don't want the Submit.HTML to load.

I've been coding this in Notepad++ though i'm going to continue with gEdit.

Anyone know how to do this?

---

### Post by raffaele181188 on 2010-03-19
Form validation always requires server-side validation (it could even be an AJAX transaction but it's uncommon). When you specifcy <form action="serverscript.ext"> you are telling the browser to send every input collected from the user to that URL. Javascript and serverside validation have nothing to do with each other. Javascript validation is just a more skilled way of preliminary controlling what the user typed, but then you NEED to perform that serverside control. So your action is always submit.php (for example, if you user PHP), then in your submit.php you have something like
[php]
if (validate($_POST)) {
  header("Location: submitok.html"); // or maybe echo (...)
} else {
  reoutput_your_form(); // to let the user resend his data
}
[/php]

---

### Post by roccivic on 2010-03-19
If I turn off JS in my browser (about 10% of internet users do this) I will be able to submit your form empty. You wouldn't fancy this, would you?

You need to learn a server-side scripting language.

---

### Post by skymera on 2010-03-19
> **roccivic said:**
> If I turn off JS in my browser (about 10% of internet users do this) I will be able to submit your form empty. You wouldn't fancy this, would you?

You need to learn a server-side scripting language.

Wouldn't bother me since this is just some college work and it forwards to a dud server :P

But yes, in reality this is a silly design.

---

### Post by roccivic on 2010-03-19
Off the top of my head:
```
<form name="myForm" action="otherPage.html">
  1:<input id="field1" type="text"><br>
  2:<input id="field2" type="text"><br>
  3:<input id="field3" type="text"><br>
  <input type="button" onclick="javascript:validate();" value="Submit">
</form>
<script type="text/javascript">
function validate() {
  if ( !document.getElementById('field1').value || !document.getElementById('field2').value || !document.getElementById('field3').value ) {
    alert("Doh! Must fill in all fields...");
  }
  else {
    document.myForm.submit()
  }   
}
</script>

```

---

### Post by skymera on 2010-03-19
thanks for replies :)

---

### Post by Compyx on 2010-03-19
> **roccivic said:**
> Off the top of my head:
```
<form name="myForm" action="otherPage.html">
  1:<input id="field1" type="text"><br>
  2:<input id="field2" type="text"><br>
  3:<input id="field3" type="text"><br>
  <input type="button" onclick="javascript:validate();" value="Submit">
</form>
<script type="text/javascript">
function validate() {
  if ( !document.getElementById('field1').value || !document.getElementById('field2').value || !document.getElementById('field3').value ) {
    alert("Doh! Must fill in all fields...");
  }
  else {
    document.myForm.submit()
  }   
}
</script>

```

This way if a user has javascript disabled he/she will never be able to submit the form.

It's better to have the validate() function return true if the data is correct and false if it isn't and register the validate function with the 'onsubmit' event of the <form> element.
That way if the user has javacript enabled the form won't submit unless the data is valid, and if the user has javascript disabled, there won't be any client-side validation but at least he/she can still submit the form without having to enable javascript just to submit some form data.

But the correct way to handle form-data is on the server side: assume the user is evil/stupid and rigorously check the sumbitted data. Client-side validation is nice but should not be used alone, server-side validation should always be performed too.

---

### Post by Hellkeepa on 2010-03-19
HELLo!

**raffaele181188**: Remember to always have "die ()" after the "header ('Location')" call. Otherwise the script will continue to parse the code, until the first bit of output was echo'd.

**Compyx**: Who says I have to use the form exactly as it is written? Opera for one makes it very simple to circumvent "protections" like these, by enabling me to edit the source code of the active site, via the source code view. That's not even taking into the consideration of recreating the page on another server/locally, or writing a script to simulate a browser posting the contents.

So you're completely correct in your closing paragraph: Server side validation is a must, and client side is just a "nicety" (and not secure).

**skymera**: You've gotten the script to work as intended?

Happy codin'!

---

### Post by Slim Moe on 2010-03-19
> **roccivic said:**
> If I turn off JS in my browser (about 10% of internet users do this) I will be able to submit your form empty. You wouldn't fancy this, would you?

You need to learn a server-side scripting language.

Not if the submission button uses JavaScript, too :p

---

