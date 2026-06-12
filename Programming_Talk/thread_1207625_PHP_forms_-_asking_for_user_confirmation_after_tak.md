---
title: "PHP forms - asking for user confirmation after taking $_POST from a form"
date: 2009-07-08
forum: Programming Talk
---

### Post by akvino on 2009-07-08
I ran into a problem last night, maybe because I am not too good with processing forms or I need to seriously go over the Static/ Global variables again. All in all I failed to produce desired result so I am asking for help.

Description of the problem in simplified terms:

I have a file1.php that will call via form action=file2.php, where file2.php gets the $_POST data then used to instantiate the object and delete files selected in the form on file1.php from the database.



What I would like to do is add additional radio button call upon selection of the file to be deleted asking user for confirmation - simple YES or NO. Then use the input to either process the deletion or abort. It does not have to be radio button - but for heavens - please give me code snippet and brief info on how is this best done? 

I had the largest problem calling another form once I collected data from the first form, since I failed to use global variable and store the entries. I am working on getting familiar with GLOBAL variable, but in the mean time would like to know the correct way to do it.

---

### Post by CrazyMonkeyFox on 2009-07-08
Show us your code, so we can work with it. We don't know what you have and what you don't. Use the php code tags, when posting your code i.e 
[~php]
Your code here
[~/php]

Without the tilda (~)

---

### Post by Mirge on 2009-07-08
Please don't use register_globals..

---

### Post by akvino on 2009-07-08
My code file1:

[php]

print("<h3>Delete a Band: </h3>");
print ("<hr><br><br>");


function delete_band()
    {
        //calling file with the object handle for MySQL connecting object
        include "connect.php";

        //calling function within connect.php which will return object
        $mysqli=connect();

        //build sql query
        //$sql = "INSERT INTO bands (name) VALUES ('".$bandName."')";
        $sql = "SELECT band_name FROM bands ORDER BY band_name";
        //$res = mysqli_query($mysqli, $sql);
        $res = $mysqli->query($sql, MYSQLI_STORE_RESULT);    

        if ($res)
        {


            //echo ("html");
            echo ("<pre><form action='db_delete_band.php' method='post'>");
            echo ("<p><strong>Select a Band: </strong><br/></p>");
            echo ("<select name='bandfield' size='5' >");

            while($name = $res->fetch_array(MYSQLI_ASSOC))
            {
                $band_name=$name['band_name'];
                //itherating through the option
                echo ("<option value='$band_name'>$band_name</option>");

            }
            echo ("</select><br/>");
            echo ("<p><input type='submit' value='Submit' /></p>");
            echo ("</form></pre>");

        }
        else
        {
            printf("Could not access the record: %s\n", mysqli_error($mysqli));
        }

    }

//echo "<br><h4> List of bands: </h4>";
delete_band();

[/php]


And the second file:
[php]
//include classes library
  include ("classes.php");

  //get the name from the form
  $name=$_POST["bandfield"];

  //create an object with that name
  $band = new Band();

  //set the band name
  $band->setBandName($name);

  $band->delete_band();

  echo "<br/><hr><br/>";
[/php]

---

### Post by akvino on 2009-07-08
That is the working code - what I need to do is when submit on the first file is entered and I got the name of the band captured via $_POST, I need to ask a user for confirmation and then create an object and delete it vie band->delete();.

I just realized PHP is different from all the other OO languages in how it handles globals. I need global variable in order to store what I collect with the $_POST i would assume in order to redirect to the second script.

Ehh I hate processing forms....

---

### Post by smartbei on 2009-07-08
This sounds like something that could either be implemented using Javascript (when the user clicks on the submit button on the form, a confirmation box pops up...) or it could be implemented as another page:
file1 -> confirmation_page -> processing_page (file2)

---

### Post by Reiger on 2009-07-08
I'd say do some JavaScript. Assign an onmousedown event handler (onmousedown="myfunc();") to your various (X)HTML elements that need it...

Then do something like this:

```

function myfunc(action, what) {
  var msg = "Are you sure you want to "+(typeof(action) !='undefined' ? action : "do)+" "+(typeof(what) != 'undefined' ? what: "this")+"?";
  return window.confirm(msg);
}

```

Constructs a message the returns whether or not the user clicks OK (true) in a confirm dialog box. (With the default if no parameters given: "Are you sure you want to do this?", with just action="delete" parameter "Are you sure you want to delete this?", with action="delete" and what="foo.txt" parameters "Are you sure you want to delete foo.txt?"). Usually returning false cancels whatever action the event was supposed to trigger, if not you can of course use JavaScript to de-select the selected item...

---

### Post by akvino on 2009-07-08
> **smartbei said:**
> This sounds like something that could either be implemented using Javascript (when the user clicks on the submit button on the form, a confirmation box pops up...) or it could be implemented as another page:
file1 -> confirmation_page -> processing_page (file2)

I was trying to implement confirmation page, the problem I had (maybe I am not familiar enough with PHP) was how to pass what was collected in the first form to the processing page?

I am not that good with Javascript - would appriciate a little bit more on type of onclick action and how does it abort if 'no' or proceed if 'yes'.

---

### Post by Reiger on 2009-07-08
The thing is that JavaScript gets "first crack" at your form data. It can modify the data you input (or nullify data that is input) via the mechanism of events (DOM events). The topic is quite exhaustive but only mildly complex: because it is been architectured to death but sufficiently nailed down in standards: you can read plenty more than you will need on any half a decent JavaScript tutorial site (w3c schools sprins to mind).

If you want to upload form data you must include a method="[HTTP METHOD]" parameter in your form element. Since you want to address the stuff uploaded as POST data you must require the data be sent using HTTP POST: or in other words use method="post" in your form element.

---

### Post by tturrisi on 2009-07-08
```
<input type="submit" name="submit" value="Submit" onclick="return confirm('Delete this record from database?');">

```
Works in all browsers, standards compliant, gives a Cancel and OK button on the confirm dialog, no neeed for any other javascript code either because "onclick" and "confirm" are built in javascript functions thus no need to write out a separate function script.

Click Cancel and page stays in browser window, click OK and form action is executed.

---

### Post by akvino on 2009-07-08
> **tturrisi said:**
> ```
<input type="submit" name="submit" value="Submit" onclick="return confirm('Delete this record from database?');">

```
Works in all browsers, standards compliant, gives a Cancel and OK button on the confirm dialog, no neeed for any other javascript code either because "onclick" and "confirm" are built in javascript functions thus no need to write out a separate function script.

Click Cancel and page stays in browser window, click OK and form action is executed.

Great I will try it. Can you tell me what happens if 'Cancel' is selected - can I redirect the user to another url or php script?

---

### Post by Mirge on 2009-07-08
> **akvino said:**
> Great I will try it. Can you tell me what happens if 'Cancel' is selected - can I redirect the user to another url or php script?

You'll want to make a function if you want to do that... which, honestly, I probably would have made a function anyway just for clarity.

IE:
```

function ConfirmMessage(msg)
{
    if(confirm(msg) === TRUE) {
        return true;
    } else {
        alert("You clicked cancel.");
        window.location = "http://www.yourname.com/some/other/URL/";
    }
}

```

And then in the <form> tag...
<form onsubmit="return ConfirmMessage('Are you sure you want to remove this record?');" action="some_form_handler.php" method="post">

---

### Post by akvino on 2009-07-08
> **Mirge said:**
> You'll want to make a function if you want to do that... which, honestly, I probably would have made a function anyway just for clarity.

IE:
```

function ConfirmMessage(msg)
{
    if(confirm(msg) === TRUE) {
        return true;
    } else {
        alert("You clicked cancel.");
        window.location = "http://www.yourname.com/some/other/URL/";
    }
}

```

And then in the <form> tag...
<form onsubmit="return ConfirmMessage('Are you sure you want to remove this record?');" action="some_form_handler.php" method="post">

I implemented the Java Script function and call and it works like a charm. One thing I had to do is evade from the php code and make the java script code in HTML. Can someone tell me how to make an HTML call from PHP - from here (this is in php):

echo ("<p><input type='submit' value='Submit' /></p>");

What I did:
?>
<html>
<p><input type="submit" name="submit" value="Submit" onclick="return confirmation();"></p>
</html>
<?php

---

### Post by Mirge on 2009-07-08
> **akvino said:**
> I implemented the Java Script function and call and it works like a charm. One thing I had to do is evade from the php code and make the java script code in HTML. Can someone tell me how to make an HTML call from PHP - from here (this is in php):

echo ("<p><input type='submit' value='Submit' /></p>");

What I did:
?>
<html>
<p><input type="submit" name="submit" value="Submit" onclick="return confirmation();"></p>
</html>
<?php


It probably errored because you forgot to escape your quotes in PHP.

For example:
INVALID:
```

<?php
echo("<input type=_**"**_button_**"**_ value=_**"**_Foobar_**"**_/>");
?>

```VALID:
```

<?php
echo("<input type=\"button\" value=\"Foobar\"/>");
?>

```

If you're going to be spitting out blocks of HTML, I would recommend using a heredoc.
Example:

```

<?php
print <<<EOT
<input type="button" value="Foobar"/>
EOT; // No whitespace before "EOT;" at all...
?>

```

---

### Post by akvino on 2009-07-08
> **Mirge said:**
> It probably errored because you forgot to escape your quotes in PHP.

For example:
INVALID:
```

<?php
echo("<input type=_**"**_button_**"**_ value=_**"**_Foobar_**"**_/>");
?>

```

VALID:
```

<?php
echo("<input type=\"button\" value=\"Foobar\"/>");
?>

If you're going to be spitting out blocks of HTML, I would recommend using a heredoc.
Example:

[code]
<?php
print <<<EOT
<input type="button" value="Foobar"/>
EOT; // No whitespace before "EOT;" at all...
?>

```

Nice, thanks a million will try it tonight... Sup.. Thanks Mirge.

---

### Post by Mirge on 2009-07-08
Not a problem:KS

---

### Post by tturrisi on 2009-07-10
Easiest to just use php end & start tags for blocks of html, then no worries about forgotten escapes and it makes scripting and inline css easier.

---

