---
title: "PHP Code not working? I am a little frustrated, works in C++....."
date: 2008-02-22
forum: Programming Talk
---

### Post by thenetduck on 2008-02-22
Hi Guys

I am trying to get good enough with PHP to get a Developer job. Here is the php code that I have written and the error code I get. It doesn't make since to me. 

```


<?php
/*
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
		$active_user = false;
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
		if ($is_locked && !$active_user)
		{
			$message = "not active user, can't put anything in";
			$could_do = false;
		}
		else
		{
			array_push($the_pile, $input); // Add $input to array via push
			$location++; // Increment location
			$message = "you successfully put " . $input . " into location " . 
				$location;  // Display message
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
		if ($is_locked && !$active_user)
		{
			$message = "not active user, can't take anything out"; 
		}
		else
		{
			if ($location <= 0)
			{
				$message = "oops, there is nothing left to take out!"; 
			}
			else
			{
				$location --;// Decrement $location 
				$message = "Successfully took out data"; // Make message
				return array_pop($the_pile); // return poped array.
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
		if ($is_locked)// check to make sure the Cab isn't all ready locked
		{
			$message = "allready locked can can't be locked again!... duh";
		}
		else
		{
			// make active_user true and locked true
			$active_user = true;
			$is_locked = true;   
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
		if (!$is_locked) // Check to if it's not locked
		{
			$message = "you can't unlock because it's not locked!";
		}
		else
		{
			if ($active_user)
			{
				$active_user = false; // After unlocking this is no longer that active
				$is_locked = false; // This then unlocks the Stack.
            $message = "unlock successful";
			}
         else
         {
          	$message = "unlock failed; not active user";
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
		return $message;
	}
}
$user1 = new CabUser();
$user1->putIn(5);
echo $user1->getMessage();
?>


```

the Error code I get in the browser says this: 

> 

Warning: array_push() [function.array-push]: First argument should be an array in /opt/lampp/htdocs/dev/Resume/Cab User/CabUser.php on line 53



What I don't get is, first, why do I have to use the "->" instead of just a " . " to reference to my functions. Second, I put an array into the array_push() function, why isn't it reconizing it? 

Thanks for any help
The Net Duck

---

### Post by melopsittacus on 2008-02-22
Hi, thenetduck!


if you mean this line:
[PHP]
array_push($the_pile, $input); // Add $input to array via push
[/PHP]


you should write instead:
[PHP]
array_push(self::$the_pile, $input); // Add $input to array via push
[/PHP]

The reason is that in PHP, unlike in C++, you always have to explicitly tell that a member variable is part of a class or an object (otherwise the interpreter will treat it as a global variable) You should also include self:: whenever you access static variables of your class, and  $this-> whenever you access dynamic members of your class, throughout your script. (Note that you do not need $ after $this->  , thus you should write $this->message and $this->active_user )


The answer to your other question is that they probably introduced -> instead of ., because . is the string concatenation operator.

---

### Post by thenetduck on 2008-02-22
that was super helpful thank you many times over

---

