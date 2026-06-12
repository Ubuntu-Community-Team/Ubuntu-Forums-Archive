---
title: "PHP price quote generator"
date: 2010-08-10
forum: Programming Talk
---

### Post by caspertk on 2010-08-10
I'm new to php. I'm writing a script to read the multiple inputs (drop down menus) from a form, convert them to int, add them together and display the price. I'm having trouble with the converting part though. I'm not sure exactly how to do it. I tried writing if statements for each variable, but that just displayed syntax errors, so I dropped that. So I'm kinda at a lost at what to do now. 

```
      
      <section id="quote">
        <header>
          <h1>Free Price Quote Generator</h1>
        </header>
        <p>This utility is used to help you find the package that's right for you. Answer the questions below to help us determine which package you should choose. All fields are required.</p>
	<?php
	if(isset($_POST['submit'])){
	    $logo   = $_POST['logo'];
	    $content   = $_POST['content'];
            $pages   = $_POST['pages'];
	    $maint   = $_POST['maint'];
	    $drop   = $_POST['drop'];
	    $forms   = $_POST['forms'];
            // Convert values into ints
            function convertToInt($_POST['submit']){
            foreach {
                // Where I'm stuck
                }
	    }
        } 
	?>
	<form method="post" action="quote.php">
          Do you have a finished logo?<br />
          <select name="logo" value="<?php echo $logo; ?>">
            <option>Yes</option>
            <option>No</option>
          </select><br />
          Do you have finished content?(images)<br />
          <select name="content" value="<?php echo $content; ?>">
            <option>Yes</option>
            <option>No</option>
          </select><br />
          How many pages do you estimate your site to be?<br />
          <select name="pages" value="<?php echo $pages; ?>">
            <option>1 - 10</option>
            <option>10 - 20</option>
            <option>20 or More</option>
          </select><br />
          Would you like site maintenance?<br />
          <select name="maint" value="<?php echo $maint; ?>">
            <option>Yes</option>
            <option>No</option>
          </select><br />   
          Would you like drop down navigation?<br />
          <select name="drop" value="<?php echo $drop; ?>">
            <option>Yes</option>
            <option>No</option>
          </select><br />   
          Would you like any forms such as contact forms?<br />
          <select name="forms" value="<?php echo $forms; ?>">
            <option>Yes</option>
            <option>No</option>
          </select><br />     
	  <input type="submit" name="submit" value="Submit">
	</form>        
      </section>
```

I thought maybe I could use a foreach code to go through the variables and convert each one to replace all the if statements. But I can't figure out how to get it to work. I'm not asking for you to rewrite my code for me. Just want some help in which direction to go with it, maybe some simple examples, and tutorial links are always appreciated :D

Thanks in advance for any help!

---

### Post by v8YKxgHe on 2010-08-10
Why do you think you need to convert them to integers? Simply give the HTML 'option' elements a 'value' attribute and use those.

Also, strings can add up just well:

```
$ php -r 'var_dump( "4" + "3" );'
int(7)

```

---

### Post by iMisspell on 2010-08-10
Dont have the time to test, but im pretty sure you can not put a 'Function' inside in IF condition like you are trying.

Nomaly you would write the function by-itself and then inside your IF you would call the function, it makes your code easyer to understand.

For your "multiple inputs (drop down menus)" i would suggest you define values in them (like AlexC_ said).

[html]
          How many pages do you estimate your site to be?<br />
          <select name="pages" value="<?php echo $pages; ?>">
            <option value="10">1 - 10</option>
            <option value="20">10 - 20</option>
            <option value="30">20 or More</option>
          </select><br />

[/html]

_

---

### Post by caspertk on 2010-08-12
> **AlexC_ said:**
> Why do you think you need to convert them to integers? Simply give the HTML 'option' elements a 'value' attribute and use those.

Also, strings can add up just well:

```
$ php -r 'var_dump( "4" + "3" );'
int(7)

```

When I return the value how do I get rid of the '(int)' part and return only the number?

---

### Post by caspertk on 2010-08-12
Nevermind I figured it out myslef :) Thanks for everyones help! I really appreciate it. That's straight from the heart of a nub.

---

### Post by Hellkeepa on 2010-08-12
HELLo!

If you post the solution that you got here, we might be able to suggest an alternative/better way of accomplishing that. If nothing else, it'd probably help you write better code. ;-)

Happy codin'!

---

