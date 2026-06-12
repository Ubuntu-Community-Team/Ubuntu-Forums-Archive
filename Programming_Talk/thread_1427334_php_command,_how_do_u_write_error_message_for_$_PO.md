---
title: "php command, how do u write error message for $_POST"
date: 2010-03-11
forum: Programming Talk
---

### Post by w0296094 on 2010-03-11
hello, i am using bluefish and i have a question

I have a webpage named search.html, which connects with viewcourseinformation.php.

Search is solely made for a for that has two search criteria, one is department, and the other is credit hours.
It looks something like this 

Drop down menu: (You choose between department or credit hours)

Box where you can fill stuff in(i.e.: if you are looking for economics, type economics)

the submit button, when you click it, it accesses viewcourseinformation.php, which uses the $_POST method for accessing my database and putting the information from the form.

My question is this, every time i put wrong information in the field(for instance, if for department i put 3, instead of eeconomics, or in credit hours i put economics instead of 3) i get the following message

Array (     [searchtype] => department     [searchterm] => 3     [days] =>  ) 

how can i setup my webpage so that instead of showing a message of array, that it will show an error message saying "invalid entry" or somthing along those lines

---

### Post by Hellkeepa on 2010-03-11
HELLo!

This depends quite a lot upon the logic of the tests you'd like to run, and how the rest of the code is written. Personally, I use a template engine, and an include script to create this kind of functionality.
For an example, you can have a look at this: [http://norskwebforum.no/pastebin/11105](http://norskwebforum.no/pastebin/11105)

"Validate ()" is just a wrapper function for my [validation functions](http://norskwebforum.no/pastebin/7609), that uses the template-engine to fetch the correct input label string to add to the "$message" variable.

Happy codin'!

---

### Post by w0296094 on 2010-03-11
thanx for the input. In other words what you are saying is that i should write the messages of the results i want to show, in a text file. Once that is set,

i should make an argument that will hel screen results (using true, ''), Once that is set,

i'm not sure what this woud do:
[FONT=monospace]
[/FONT]$Comments = Validate ('string', 'comments', 'COMMENTS', 'FORM_COMMENTS', $Check, $Message);[FONT=monospace]

[/FONT]$Name = Validate ('name', 'name', 'NAME', 'FORM_NAME', $Check, $Message);


can you help me on that?

---

### Post by w0296094 on 2010-03-11
what i  want to see on my webpage is this

if department: economics or marketing, then show the results from the database

otherwise, i need an error message that says: incorrect department name.


or 


if credit hours: 3, then show the results from the database


otherwise, i need an error message that says: incorrect credit hour name

---

### Post by Xyro on 2010-03-11
Since you've given far too little information, this may be of no use.

Why don't you check the input sanity before you feed it into the database query script (if that is what you're doing). Something like:

[php]
<?php

...

  if ( $_POST['dropMenu'] == "department" )
  // 'Department' was selected.
  {
    if ( $_POST['input'] == "economics" )
      // Do economics stuff.
    else if ( $_POST['input'] == "other department" )
      // Do other department stuff.
    else
      echo "You've entered an invalid department!";
  }
  else
  // Assuming 'credit hours' was selected.
  {
    if (  is_numeric( $_POST['input'] ) )
      // Do credit hour stuff.
    else
      echo "You've entered an invalid credit hours!";
  {

...

?>
[/php]

---

### Post by w0296094 on 2010-03-16
thanks that gave me an idea that led to the solution i appreciate it and i'm sorry if i didnt provide enough info

---

### Post by Hellkeepa on 2010-03-16
HELLo!

Sorry about late reply, been a bit busy.
Anyway, what the "validate ()" function does, is to act as a wrapper for the validate funtions I linked to. Combining them with the Template engine, to automatically create the error messages in the correct locale, if the validation should fail.
In other words, the pseudo-code looks like something like this:
[php]funtion Validate ($function, $index, $field, $text, &$check, &$message) {
    if not exist $function (), return error.
    if not $validated = val_$function ($_POST[$index]):
        $Template->FORM_FIELD_.$field = htmlspecialchars ($_POST[$index])
        $message .= "Validation failed for ".$Template->$text
        $check = false;
        return false;
    $Template->FORM_FIELD_.$field = htmlspecialchars ($validated)
    return $validated
}[/php]
"$Template->FORM_FIELD_.$field" is used to repopulate the form, if the validation should fail. That way the user does not have to fill in everything anew.

I'm not saying that you should create a text file with the error messages, just explaining the way I've done it so that it supports a multi-language site in an easy manner. You can create the error messages in any manner of your choosing, including writing them directly into the code.
However, what I was intending to show, was the flow of the programming. How you can easily add error messages to a form, and still display the form, in an elegant manner. Notice how I've used the function "Write_Comments ()", and why. (Hint: "return" is a big reason.)

Happy codin'!

---

