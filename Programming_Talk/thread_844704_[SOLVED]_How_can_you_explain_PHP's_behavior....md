---
title: "[SOLVED] How can you explain PHP's behavior..."
date: 2008-06-29
forum: Programming Talk
---

### Post by raxz on 2008-06-29
I was recently asked by a co-worker why the following code produces the same result when the "refresh" button is hit but when typing/just hitting the the address bar again clears all output...(ie the "names" are no longer visible)

[PHP]		
		<?php
		
		
			if(isset($_POST['submit'])){
				
				echo "<br />Hello ".$_POST['fname']." ".$_POST['mname']." ".$_POST['lname']." <br />";
				echo "your e-mail address is ".$_POST['email']."<br />";
				echo "your gender is ".$_POST['gender'."<br />";
				
				if($_POST['age'] >= 18){
					echo "<b>you are of legal age</b>";
				}else{
					echo "<b>you are not yet of legal age</b>";
				}  
				[/PHP]

I cannot for the life of me just say "that's really how PHP works"..can someone explain the difference between the refresh button and manually typing the URL in PHP.

does it have something to do with cache/headers?

Also is there a way to clear the output when a page is refreshed..I tried unset() still nothing.

---

### Post by Jordanwb on 2008-06-29
When a form is submitted using the post method $_POST['submit'] is set so it will be true. When you hit refresh you resend the form data, causing it to be true again. Simply typing in the url does not send post data so it is false.

As for clearing output, use something like 

[php]
$_SESSION['form_submitted'] = true;
[/php]

also for that you'd need either start_session () or session_start (). I can't remember which.

---

### Post by Thirtysixway on 2008-06-29
Don't forget to sanitize those inputs!

---

### Post by Jordanwb on 2008-06-29
> **Thirtysixway said:**
> Don't forget to sanitize those inputs!

That's some good advice there. Never trust user input.

---

### Post by raxz on 2008-06-29
> **Jordanwb said:**
> When a form is submitted using the post method $_POST['submit'] is set so it will be true. When you hit refresh you resend the form data, causing it to be true again. Simply typing in the url does not send post data so it is false.

As for clearing output, use something like 

[php]
$_SESSION['form_submitted'] = true;
[/php]

also for that you'd need either start_session () or session_start (). I can't remember which.

hmm...ok so the keyword to remember is post data. the code was just a sample to better demonstrate what behavior I was talking about.

erm could you elaborate on that "$_SESSION['form_submitted']"?

:lolflag:

---

### Post by Thirtysixway on 2008-06-29
> **raxz said:**
> hmm...ok so the keyword to remember is post data. the code was just a sample to better demonstrate what behavior I was talking about.

erm could you elaborate on that "$_SESSION['form_submitted']"?

:lolflag:

You would set [php]$_SESSION['form_submitted'] = true;[/php] on the page with the form.  Then on the page that handles the input (the code posted here) it would check to see if it was set to true, then set it [php]$_SESSION['form_submitted'] = false;[/php] so if it was refreshed, the session would be false and it would display the form again or show an error.  This works because the session is not set based on submitting data.

---

### Post by raxz on 2008-06-29
> **Thirtysixway said:**
> You would set [php]$_SESSION['form_submitted'] = true;[/php] on the page with the form.  Then on the page that handles the input (the code posted here) it would check to see if it was set to true, then set it [php]$_SESSION['form_submitted'] = false;[/php] so if it was refreshed, the session would be false and it would display the form again or show an error.  This works because the session is not set based on submitting data.


but what if I want to just have one page where both the form and the PHP are in?

---

### Post by Jordanwb on 2008-06-29
For that I do something like this:

[php]
$form_submitted = isset ($_POST['submit']);
$show_form = true;

if ($form_submitted)
{

}
if ($show_form)
{

}
[/php]

Also for the bit about the $_SESSION variable you could generate a random number, make it a hidden field in the form. When the form is submitted save the number in a $_SESSION variable. When the form is resubmitted check the value. If it is the same ignore the post data. If you want an example I'll make one.

---

### Post by Thirtysixway on 2008-06-29
> **raxz said:**
> but what if I want to just have one page where both the form and the PHP are in?

You could have like
[php]
<?php
if(!$_POST['myform']){
	//We haven't submitted the form yet!

	echo("<form method=post name=myform>
		First Name:<br><input type=text name=fname><br><br>
		Middle Name:<br><input type=text name=mname><br><br>
		Last name:<br><input type=text name=lname><br><br>
		Email Address:<br><input type=text name=email><br><br>
		Gender:<br><input type=text name=gender><br><br>
		<input type=submit name=submit value=Submit!></form>
		");

	$_SESSION['form_submitted'] = true;
}else{
	//The form HAS been submitted!

	if($_SESSION['form_submitted'] == true){
		//the user came from our form!

		echo "<br />Hello ".$_POST['fname']." ".$_POST['mname']." ".$_POST['lname']." <br />";
		echo "your e-mail address is ".$_POST['email']."<br />";
		echo "your gender is ".$_POST['gender'."<br />";
                
		if($_POST['age'] >= 18){
			echo "<b>you are of legal age</b>";
		}else{
			echo "<b>you are not yet of legal age</b>";
		}

		$_SESSION['form_submitted'] = false;

	}else{
		//the user didn't come from our form!

		echo("Please hit back and re enter your data.");
		$_SESSION['form_submitted'] = false;
	}
}
?>
[/php]

 I haven't tested it but it should work.

---

### Post by Jordanwb on 2008-06-29
One look and I saw right away that there would be a bug:

[php]if($_SESSION['form_submitted'] = true){ [/php]

should be

[php]if($_SESSION['form_submitted'] == true){[/php]

or

[php]if($_SESSION['form_submitted']){[/php]

but that would work. Albeit a bit messy (at least for me).

---

### Post by Thirtysixway on 2008-06-29
Whoops, sorry about that!  I've updated my post with that fix, thanks Jordanwb.

---

### Post by Jordanwb on 2008-06-29
No prob. We're all here to help each other. Besides everyone has made that mistake before.):P

---

### Post by raxz on 2008-06-29
@ Thirtysixway - tried(*read copy pasted) your code...no output was generated.

@ Jordanwb - hmm  the code you gave should it look something like this:

[PHP]
$form_submitted = isset ($_POST['submit']);
		$show_form = true;

		if ($form_submitted){
				echo "<br />Hello ".$_POST['fname']." ".$_POST['mname']." ".$_POST['lname']." <br />";
					
					echo "your e-mail address is ".$_POST['email']."<br />";
					echo "your gender is ".$_POST['gender']."<br />";
					
					if($_POST['age'] >= 18){
						echo "<b>you are of legal age</b>";
					}else{
						echo "<b>you are not yet of legal age</b>";
					}  
					
			$show_form=false;//


[/PHP]




interesting idea about the random numbers never thought about it like that. will try it out.

---

### Post by Jordanwb on 2008-06-29
Yeah that's how I write forms and stuff like that. Makes it easier for me to display error messages about input and stuff like that.

> **raxz said:**
> @ Thirtysixway - tried(*read copy pasted) your code...no output was generated.

It should. Change the form output part to:

[php]

    echo('<form method="post" name="myform">
        First Name:<br><input type="text" name="fname"><br><br>
        Middle Name:<br><input type="text" name="mname"><br><br>
        Last name:<br><input type="text" name="lname"><br><br>
        Email Address:<br><input type="text" name="email"><br><br>
        Gender:<br><input type="text" name="gender"><br><br>
        <input type=submit name="submit" value="Submit!"></form>
        ');

[/php]

because the other dude didn't put any quotes around property values the browser may be confused.

---

### Post by raxz on 2008-06-29
I mean when you hit the "submit" button nothing is displayed

---

### Post by Jordanwb on 2008-06-29
That's weird. It should. I'll try it on my server.

[edit]

Right after "<?php" put "session_start ();" (minus the quotes)

but it works for me.

---

### Post by raxz on 2008-06-29
[PHP]<?php session_start();

if(!$_POST['myform']){
//We haven't submitted the form yet!

	echo("<form method=post name=myform>
	First Name:<br><input type=text name=fname><br><br>
	Middle Name:<br><input type=text name=mname><br><br>
	Last name:<br><input type=text name=lname><br><br>
	Email Address:<br><input type=text name=email><br><br>
	Gender:<br><input type=text name=gender><br><br>
	<input type=submit name=submit value=Submit!></form>");

$_SESSION['form_submitted'] = true;

}else{

	echo "this should work here";//this should show after submit
	
//The form HAS been submitted!
		if($_SESSION['form_submitted'] == true){
			//the user came from our form!
			
			echo "<br />Hello ".$_POST['fname']." ".$_POST['mname']." ".$_POST['lname']." <br />";
			                echo "your e-mail address is ".$_POST['email']."<br />";
			                echo "your gender is ".$_POST['gender']."<br />";
			                
			                if($_POST['age'] >= 18){
			                    echo "<b>you are of legal age</b>";
			                }else{
			                    echo "<b>you are not yet of legal age</b>";
			                }
			$_SESSION['form_submitted'] = false;
		}else{
			//the user didn't come from our form!
			echo("Please hit back and re enter your data.");
			$_SESSION['form_submitted'] = false;
		}
} 


[/PHP]


I have no idea why this does not work...:(

---

### Post by Jordanwb on 2008-06-29
Oh I forgot that I changed something else. Change 

[php]if(!$_POST['myform']){[/php]

to

[php]if(!isset($_POST['submit'])){[/php]

---

### Post by raxz on 2008-06-29
worked!

I thought&#12288;fixed it when I changed it to this:

[PHP]<?php session_start();

if(!$_POST['myform']){
//We haven't submitted the form yet!

	echo("<form method=post name=myform>
	First Name:<br><input type=text name=fname><br><br>
	Middle Name:<br><input type=text name=mname><br><br>
	Last name:<br><input type=text name=lname><br><br>
	Email Address:<br><input type=text name=email><br><br>
	Gender:<br><input type=text name=gender><br><br>
	<input type=submit name=submit value=Submit!></form>");

$_SESSION['form_submitted'] = true;

//var_export($_SESSION['form_submitted']);

}

if($_SESSION['form_submitted']){

	echo "this should work here";
	
//The form HAS been submitted!
		if($_SESSION['form_submitted'] == true){
			//the user came from our form!
			
			echo "<br />Hello ".$_POST['fname']." ".$_POST['mname']." ".$_POST['lname']." <br />";
			                echo "your e-mail address is ".$_POST['email']."<br />";
			                echo "your gender is ".$_POST['gender']."<br />";
			                
			                if($_POST['age'] >= 18){
			                    echo "<b>you are of legal age</b>";
			                }else{
			                    echo "<b>you are not yet of legal age</b>";
			                }
			$_SESSION['form_submitted'] = false;
		}else{
			//the user didn't come from our form!
			echo("Please hit back and re enter your data.");
			$_SESSION['form_submitted'] = false;
		}
} 


[/PHP]


but yeah that is another way of doing it. anyway thanks and I will have to remember the key word again is "post data" :lolflag:

---

