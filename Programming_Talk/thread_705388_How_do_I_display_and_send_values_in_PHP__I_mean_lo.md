---
title: "How do I display and send values in PHP ? I mean logic wise?"
date: 2008-02-23
forum: Programming Talk
---

### Post by thenetduck on 2008-02-23
Sorry for the blane subject header... this is what I mean.

I have this Class I created in PHP that is OOP and its called "CabUser.php" you can create a new user via 

```

$user1 = new CabUser();

```

Then call it's member functions etc.... 
I would like to be able to have a graphic page that lets a person create a new user, then a couple of buttons that call the member function to do stuff and also lets that page display a message that the class makes via 

```

$user1->getMessage();

```

My question is:
How can I create a page that does this? for Instance, if the page doesn't start off with any users, and after "they" (being whom ever is using this) clicks add new Cab User, I would like that user to appear under a drop down box so they can select that user and "act" as that user. 

My idea was that there would be three files, a Display for my graphics, a Control to handle data flow and of course my CabUser.php class file. Is this the right way? 

How would I do this, I mean, I know that I can post data to my control file, but after I post that data to that file, it automatically takes me to the control file and I wanna get back to my display file, plus I need the control file to send information back to my display file. Very confused on how I can do this. Any would is wonderful, Thank you so much for all the help that has been give so far.

The Net Duck

---

### Post by xlinuks on 2008-02-23
> I would like to be able to have a graphic page that lets a person create a new user, then a couple of buttons that call the member function to do stuff and also lets that page display a message
By clicking on buttons the user won't get to access a member function of your class since the user is on the client side and your php class is on the server side.
I think the first thing you might need to learn is how to use "sessions" to be able to "distinguish" users (sesssion IDs).
Next, you gotta figure out what the user did and act correspondingly on your server side by calling the corresponding function of your php class.. "Figuring out" implies analysing submitted (hidden) requests (throught "get" or "post" ).

---

### Post by thenetduck on 2008-02-23
I have created an object like this: 

```


$_SESSION['user_tim'] = new CabUser();

```

The problem is, every time I leave the page and come back, it auto dumbs the info and then creates a new users, deleting all of the static info that object has. Is there a way to do something like : static $_SESSION['user_tim'] = new CabUser(); or something? Everything will work if the object will just remain static. ...

Thanks 

The Net Duck

---

### Post by winch on 2008-02-23
Use [isset]("http://php.net/isset") to make sure the variable is not set before assigning a new object to it.

[php]
if (!isset($_SESSION['user_tim']))
{
    $_SESSION['user_tim'] = new CabUser();
}
[/php]

---

### Post by lnostdal on 2008-02-24
you use sessions, like i explained here: [http://ubuntuforums.org/showthread.php?t=704131](http://ubuntuforums.org/showthread.php?t=704131)

..store the object/instance in a session-variable..

edit: by the way -- if you re-use your threads instead of creating new ones it will be easier to keep things in context and understand "your background" while working on this

---

### Post by thenetduck on 2008-02-24
Your that man... or woman or .... your cool.

Thanks 

The Net Duck

---

### Post by LaRoza on 2008-02-24
Threads merged to keep it together.

---

### Post by thenetduck on 2008-02-24
Ok ..... I am still having problems. Here are the three files and I working with. 

Filename: index.php

```

<?php
session_start();
$disMessage = $_SESSION['display'];
/*
* This was created by Sterling Cobb. 
*/
// Create the heading
$head =<<<HED
<hmtl>
<title> Resume Sample Code </title>
	<head> 
	<center>
	<h1> Welcome, thank you for using </h1>		
	</center>	
	<p> Please forgive the design, I am terrible at css but still think is cool.
	</p>
</html>
HED;
// display heading
echo $head;

// lists the users with Radio buttions :)
$users =<<< USE
	<input type='radio' value = 'Jim' name = 'user_name'> Jim
	</br >
	<input type = 'radio' value = 'Bob' name = 'user_name'> Bob
	</br >
	<input type = 'radio' value = 'Mary' name = 'user_name'> Mary
	</br >
	<input type = 'radio' value = 'Liam' name = 'user_name'> Liam
	</br >
USE;

// Creates all the actions that can be made.
$actions =<<< ACT
<input type = 'text' name = 'push_amount' value=0>
<input type = 'submit' name = 'button' value = 'push'>
</br >
<input type = 'submit' name = 'button' value = 'pop'>
</br >
<input type = 'submit' name = 'button' value = 'lock'>
<input type = 'submit' name = 'button' value = 'unlock'>
ACT;

// display body, sent from control.php
$body = <<<BOD
<center>
<form method = 'post' action = 'control.php'>
<table width = 80%>
<tr>
	<td>$users</td>
	<td>$actions</td>
	<td valign = top><h4>Display Message</h4> </br > 
	$disMessage
	</td>
</tr>
</table>
</form>
</center>
BOD;
echo $body;
?>


```

Filename: CabUser.php

```


<?php
Summary: This program is an example using OOP concepts with PHP5. This is a 
simulation of a file cabinet. When you create a new FileCab it's like create a
new user. They all use the same File Cab. It's using a Stack type input/output.
Two bools are used to run everything. A static bool that says "the cab is
locked by some user" and bool that says "I am the active_user". 
*/

class CabUser
{
	private static $message; 
	private $active_user;
	
	// ----------Static Stuff-----------//
	private static $the_pile = array();
	private static $is_locked = false;
	private static $location = 0; // Location, in reference to the array.
	/*
	* Summary: Make sure that then a new user is created, it is not the active
	* Process: 
	*			set active_user to false
	*/
	function __construct()
	{
		$this->active_user = false;
		self::$message = "Users Successfuly created!";
	}
	
	/*
	* Summary: This will allow a data type to be put into the stack. It will 
	* check to see if the Cab is locked. If it is locked then if you are the 
	* the active user you can put something into it else you can't put anything 
	* into it.
	* Process: 
	* 			Check to see if not active user... display message if not
	*			if Active user: add data to pile, inc. location and set message
	*			return true if success.
	*/
	public function putIn($input)
	{
		if (self::$is_locked && !$this->active_user)
		{
			self::$message = "not active user, can't put anything in";
			$could_do = false;
		}
		else
		{
			array_push(self::$the_pile, $input); // Add $input to array via push
			self::$location++; // Increment location
			self::$message = "you successfully put " . $input . " into location " . 
				self::$location;  // Display message
			$could_do = true; 
		}
		return $could_do;
	}
	
	/*
	* Summary: This uses the same logic as the "putIn()" function but instead of 
	* putting somthing into the stack, you are taking something out. It also
	* checks to make sure that you don't cross over the end of the stack by 
	* trying to take more out than you can. 
	* Process: 
	* 			if not active user, set message to be displayed
	*			if active, make sure something can be taken out, if possible
	*				Decrement location, set display message and return the poped 
					array. 
	*/
	public function takeOut()
	{
		if (self::$is_locked && !$this->active_user)
		{
			self::$message = "not active user, can't take anything out"; 
		}
		else
		{  
			if (self::$location <= 0)
			{
				self::$message = "oops, there is nothing left to take out!"; 
			}
			else
			{
				
				$poped_data = array_pop(self::$the_pile);
				self::$message = "Successfully took out " . $poped_data .
					" from location " . self::$location; // Make message
				self::$location --;// Decrement $location 
				return $poped_data; // return poped array.
			}
		}
	}
	
	/*
	* Summary: It locks the Cab that will only let the user that locked it add 
	* things and unlock it. It also checks to make sure the the stack isn't all 
	* ready locked and if it is locked, this user is the active user.
	* Process: 
	*			Check if this user can do anything
	*			If it can, make this user as active and set locked as true
	*/
	public function lock()
	{
		if (self::$is_locked)// check to make sure the Cab isn't all ready locked
		{
			self::$message = "allready locked can can't be locked again!... duh";
		}
		else
		{
			// make active_user true and locked true
			$this->active_user = true;
			self::$is_locked = true;   
			self::$message = "successfully locked cab!";
		}

	}

	/*
	* Summary: This will unlock the Cab. You must be the active user to unlock 
	* it so it will check that first. It will also make sure the Cab is all ready
	* locked because it wouldn't make sense to unlock something that isn't locked
	* Process: 
	*/
	public function unLock()
	{
		if (!self::$is_locked) // Check to if it's not locked
		{
			self::$message = "you can't unlock because it's not locked!";
		}
		else
		{
			if ($this->active_user)
			{
				$this->active_user = false; // After unlocking this is no longer that active
				self::$is_locked = false; // This then unlocks the Stack.
            self::$message = "unlock successful";
			}
         else
         {
          	self::$message = "unlock failed; not active user";
         }
		}
	}
	
	/* 
	* Summary: This will return the message the Cab puts out
	* Process: 
	*			Return message
	*/
	public function getMessage()
	{
		return self::$message;
	}
}
?>
```

Filename: control.php

```

<?php
session_start();
/*
* Summary: The Control will call on classes and use information posted to it 
* from the index page to display information correctly. 
*/

include 'CabUser.php';
if (!isset($_SESSION['user_jim']))
{
	// create users
	$_SESSION['user_jim'] = new CabUser();
	$_SESSION['user_bob'] = new CabUser();
	$_SESSION['user_mary'] = new CabUser();
	$_SESSION['user_liam'] = new CabUser();
}
// determin the user
switch ($_POST['user_name'])
{
	case Jim:
		doAction($_SESSION['user_jim']);		
	break;
	case Bob:
		doAction($_SESSION['user_bob']);	
	break;
	case Mary:
		doAction($_SESSION['user_mary']);	
	break;
	case Liam: 
		doAction($_SESSION['user_liam']);	
}

function doAction($sessionUser)
{
// Determin button pressed and do that action
	switch ($_POST['button'])
	{
		case push:
			$sessionUser->putIn($_POST['push_amount']);
		break;
		case pop:
			$sessionUser->takeOut();
		break;
		case lock:
			$sessionUser->lock();
		break;
		case unlock:
			$sessionUser->unLock();
	}
	$_SESSION['display'] = $sessionUser->getMessage();
}
header("Location: index.php");

?>

```


I have tried to do some kind of Autoload function? but that didn't seem to work. I am confused on why the isset isn't working correctly. 

Can anyone understand why it is failing to do what I want it to do? 

Thanks
The Net Duck

---

