---
title: "Form validation in PHP"
date: 2009-09-13
forum: Programming Talk
---

### Post by Nevon on 2009-09-13
I haven't been writing PHP scripts in forever, and I can't recall how to best do form validation. 

Basically I've got a form that looks like this:
[php]<form action="index.php" method="post">
<label for="appname"><span class="red">*</span>Application name:</label>
<input type="text" name="appname" value="" /><br />

<label for="pid">Process ID:</label>
<input type="text" name="pid" value="" /><br />

<label for="appurl">Application website:</label>
<input type="text" name="appurl" value="" /><br />

<label for="name"><span class="red">*</span>Your name:</label>
<input type="text" name="name" value="" /><br />

<label for="email"><span class="red">*</span>Your email:</label>
<input type="text" name="email" value="" /><br />

//Captcha
<?php echo recaptcha_get_html($publickey); ?>

<input type="submit" name="submit" id="submit" value="Submit" />
</form>[/php]
Now I need to check that the ones with a * are not empty, that the email-address seems to be a real email address, and that the "Process ID" consists only of numbers (unless it's empty). After that, I need to check for people trying to delete my database, redirect my visitors, etc. 

If any of the form elements are filled out incorrectly, I need to display error messages to the user. On top of that, I also need the form to "remember" what the user wrote (that is, if the user filled out the form incorrectly, all the values are restored to the form along with the error messages). 

I'm not really asking for code, but I would love it if you had any links to articles outlining the process. I have done it before, and I pretty much know the procedure, it's just that I can't remember all the functions for sanitizing the data, and I can't remember at all how arrays work.

---

### Post by januzi on 2009-09-13
You could use smarty templates. 
As for validation:
```

$not_empty = array( 'x', 'y', 'z' ) ;

// ...

$error = 0 ;
$c = count( $not_empty ) ;
for( $i = 0 ; $i < $c ; $i++ ) {
  $key = $not_empty[$i] ;
  if( empty( trim($_POST[$key]) )) $error = 1 ;
}

```As for type validation (float, int): is_int, is_float => [http://us3.php.net/manual/en/ref.var.php](http://us3.php.net/manual/en/ref.var.php) ($error = 2; )

```

if( $error == 0 ) { 
// insert data into db or something like that

// ...

  header( "Location: complete.php" ) ;
  exit() ;
}
else {
 $smarty->assign( 'error', $error ) ;
 $smarty->assign( $_POST ) ;
}
echo $smarty->fetch( 'page.tpl' ) ;

```In the page.tpl You could put something like:
```

{if $error neq ''} 
  {if $error eq 1}Please fill all required fields
  {elseif $error eq 2}Only numbers allowed
   {/if} 
{/if}
// ...
[COLOR=#000000]<input type="text" name="name" value="{$name}" /><br /> [/COLOR]
// ...

```Plugin for smarty: [http://smartyform.sourceforge.net/](http://smartyform.sourceforge.net/)

Simple form validation: [http://www.php-mysql-tutorial.com/wikis/php-tutorial/form-validation-using-php.aspx](http://www.php-mysql-tutorial.com/wikis/php-tutorial/form-validation-using-php.aspx)

---

### Post by raptor2552 on 2009-09-13
I would use JavaScript to validate on the client side before the form was sent. That way you could popup an alert box to warn of missing or malformed info. Do a Google search for "JavaScript form validation" and you'll find tons of methods on how to handle this.

After getting the data and if you're creating a query into a mysql database use mysql_real_escape_string() to scrub the query built from the submission.

Once you see it I'm sure you won't have any trouble.

---

### Post by Mirge on 2009-09-13
> **raptor2552 said:**
> I would use JavaScript to validate on the client side before the form was sent. That way you could popup an alert box to warn of missing or malformed info. Do a Google search for "JavaScript form validation" and you'll find tons of methods on how to handle this.

After getting the data and if you're creating a query into a mysql database use mysql_real_escape_string() to scrub the query built from the submission.

Once you see it I'm sure you won't have any trouble.

Use Javascript if you want, but don't rely on it as the **only** method of validation... some browsers don't support it, and others can disable it.

---

### Post by Nevon on 2009-09-14
Thank you for your help. I think I've gotten it all working now. I chose not to validate with Javascript simply because I'm even worse at Javascript than PHP, so I figure I'd just do it all on the server-side. What I do is I first run all the values through a method that escapes certain characters, removes excess whitespace, and does all the "anti-hacking" stuff. Then I pass that on to another method that checks that it's all formatted correctly, that the email looks like a real email, etc. Any errors that I encounter are added to an array and all the form data is added to another array, and once everything is done, I check if that array is empty. If it's not, then the user gets thrown back to the form, the form data is restored using the array I created before, and all error messages are displayed from that other array. If there are no errors, the stuff gets added to the database and the users get's a "thank you". 

It really wasn't all that hard. I think it was just me being really rusty.

---

### Post by Johnsie on 2009-09-14
I would use javacript and PHP. Javascript  keeps the user right at entry time and PHP covers anything which may have slipped through the net. The problem with javascript is that different browsers handle it differently and it's also annoying to write because it's hard to root out and fix bugs. However in most cases javascript can help the user get things right before he/she clicks the submit button.

---

### Post by sujoy on 2009-09-14
code igniter has pretty cool form validation functions.

---

### Post by soapytheclown on 2009-09-14
> **Johnsie said:**
> I would use javacript and PHP. Javascript  keeps the user right at entry time and PHP covers anything which may have slipped through the net. The problem with javascript is that different browsers handle it differently and it's also annoying to write because it's hard to root out and fix bugs. However in most cases javascript can help the user get things right before he/she clicks the submit button.

there are loads of javascript frameworks / libraries out there that handle most of the differences between the different browser variations of javascript my prefered one being Mootools since it takes an OO approach to JS but many favor JQuery both have excellent for validation plugins / scripts available for them! the added advantage of using JS being that it saves a request being made to your server by validation on the client side and as already mentioned ALWAYS validate with PHP as they say 'never trust user input'

:)

---

