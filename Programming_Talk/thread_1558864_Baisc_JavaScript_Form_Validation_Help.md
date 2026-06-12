---
title: "Baisc JavaScript Form Validation Help"
date: 2010-08-22
forum: Programming Talk
---

### Post by JustChris21 on 2010-08-22
Hey guys my JS code is.. (bear in mind i am a noob)

```

function validate() {
    var errors = false;
    
    if ($('#first').val() == "") {
        alert('All fields MUST be completed to continue');
        return;
    }
    
    if ($('#surname').val() == "") {
        alert('All fields MUST be completed to continue');
        return;
    }
    
    if ($('#email').val() == "") {
        alert('All fields MUST be completed to continue');
        return;
    }
    
    $('#form').submit();
}

```The alert box pops up fine if a field is not filled in but once you press 'ok' on the alertbox it processes the form and doesn't let you fill in the details iyswim.

Any help appreciated.

---

### Post by Compyx on 2010-08-23
There's not a lot of context to determine what could be wrong, but I'll give it a shot.

Normally when doing client-side form validation with Javascript, you use the 'onsubmit' event of the form to run the validation function. Such a function is expected to return false if the form didn't validate and return true if everything validated. When returning false, the form doesn't submit, when returning true, the form submits.

Since you don't show any HTML code which references your validate function or Javascript which sets up event listeners, so there isn't a lot I can say to help you with your code. You could try returning false after each alert() call in your function. But since you seem to be using jQuery, there might be another way, I personally have never used jQuery, so I can't help you there.

Posting the HTML code of the form would probably help in identifying the problem.

---

### Post by JustChris21 on 2010-08-23
Right this is what I have done for the HTML

[HTML] 
<form id="form" action="contactscript.php" method="post">
               <fieldset id="field">
                  <legend id="legend">PHP Email Contact Form</legend>
                 <label for="cname">First Name:</label>   <input class="input" id="first" name="first" type="text" size="26"><br /><br />
                  <label for="cname">Surname:</label>       <input class="input" id="surname" name="surname" type="text" size="26"><br /><br />
                  <label for="cname">Email:</label>        <input class="input" id="email" name="email" type="text" size="26"><br /><br />
                 <label for="cname">Message:</label>     <textarea id="textarea" name="message" class="input" rows="10" cols="30">Please Type Your Message Here</textarea><br /><br />
                 <input id="submit" class="input" type="submit" value="Send!" onclick="validate();">
                                                                          
               </fieldset>
            </form>[/HTML]

And the Javascript is in an externel file which is loaded in the 'Head' part of my html so when the submit buttin is clicked it runs to function 'validate()'.

Its my first go at doing validation mind!

---

### Post by Compyx on 2010-08-25
What you should do is remove onclick="validate();" from the submit button, and add onsubmit="validate();" to the <form> tag.
And the validate() function should look something like this:
```

function validate() {
    
    if ($('#first').val() == "") {
        alert('All fields MUST be completed to continue');
        return false;
    }
    
    if ($('#surname').val() == "") {
        alert('All fields MUST be completed to continue');
        return false;
    }
    
    if ($('#email').val() == "") {
        alert('All fields MUST be completed to continue');
        return false;
    }
    
    return true;
}

```

When the handler (in this case, the validate() function) for the 'submit' event of the form returns true, the form is submitted, when the handler returns false, the form does not submit.

In your case, you had the validate() function connected to the 'click' event of the submit button, which triggered the validation function but also triggered the submit event, regardless of the code in your function.

You could change the type of the submit button to a normal button, that way the validate() function only triggers the submit event when all fields validate. But people who have javascript disabled will never be able to submit the form. The way I described lets people with javascript disabled still submit the form, although there's no validation.

But to be honest, I consider client-side validation with javascript as a little extra service for the user; real validation happens on the server-side.

---

### Post by Hellkeepa on 2010-08-27
HELLo!

Actually, you'll need to use the following in the form-tag, to make sure the form isn't submitted in case of a missing field:
```
onsubmit="return validate();"
```
That way, the return status bubbles up to the browser, which will either stop or continue with the submission, depending upon the bool retrieved.

Happy codin'!

---

