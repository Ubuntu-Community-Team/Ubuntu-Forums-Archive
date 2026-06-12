---
title: "[PHP] find numbers inbetween"
date: 2008-05-27
forum: Programming Talk
---

### Post by ELD on 2008-05-27
Basically i am creating a php game where i need to let the players always have someone to fight.

So if i have people at levels 1,10,56,400 well none of them are probably going to have anyone to fight all at wierd levels.

I have this at the moment:
```

$numbers = array( range( $lower_level, $higher_level+(round( rand(1,8)/2 ) ) ) ); 

```

But that gives me all the numbers :(

---

### Post by Lau_of_DK on 2008-05-27
> **ELD said:**
> Basically i am creating a php game where i need to let the players always have someone to fight.

So if i have people at levels 1,10,56,400 well none of them are probably going to have anyone to fight all at wierd levels.

I have this at the moment:
```

$numbers = array( range( $lower_level, $higher_level+(round( rand(1,8)/2 ) ) ) ); 

```

But that gives me all the numbers :(

Could you rephrase the question so even a simpleton from Denmark gets it?

What range of numbers exactly are you looking to produce?

/Lau

---

### Post by ELD on 2008-05-27
> **Lau_of_DK said:**
> Could you rephrase the question so even a simpleton from Denmark gets it?

What range of numbers exactly are you looking to produce?

/Lau

Say if i have 1,34,500

I wish to know all the numbers inbetween 1-34 and 34-500, but i don't want those numbers as well.

---

### Post by Lau_of_DK on 2008-05-27
> **ELD said:**
> Say if i have 1,34,500

I wish to know all the numbers inbetween 1-34 and 34-500, but i don't want those numbers as well.

Alright, so how about this

[php]
$numbers_i_want = []
$numbers_i_dont_want = [5, 4, 3, 2, 1]
for ($i = 1; i <= 100; i++) {
   if !($i isin $numbers_i_dont_want) {
      $numbers_i_want[] = $i
   }
}
[/php]

/Lau

---

### Post by ELD on 2008-05-27
> **Lau_of_DK said:**
> Alright, so how about this

[php]
$numbers_i_want = []
$numbers_i_dont_want = [5, 4, 3, 2, 1]
for ($i = 1; i <= 100; i++) {
   if !($i isin $numbers_i_dont_want) {
      $numbers_i_want[] = $i
   }
}
[/php]

/Lau

Unfortunaly i get this:
> 
Fatal error: Cannot use [] for reading in /home/prxainfo/public_html/bruce-o-matics.php on line 9


---

### Post by Lau_of_DK on 2008-05-27
Argh :( Sorry, I've not installed my Apache server since updating to 8.04, so I didnt test the code. Try this, its tweaked a little:

[php]
$numbers_i_want = array();
$numbers_i_dont_want = array(5, 4, 3, 2, 1);
for ($i = 1; i <= 100; i++) {
   if !($i isin $numbers_i_dont_want) {
      $numbers_i_want[] = $i;
   }
}  
[/php]

If for some reason Php doesn't allow an empty initialization of an array (line 1), then change to = array(0);.

Hope it works now ;)

/Lau

---

### Post by ELD on 2008-05-27
> **Lau_of_DK said:**
> Argh :( Sorry, I've not installed my Apache server since updating to 8.04, so I didnt test the code. Try this, its tweaked a little:

[php]
$numbers_i_want = array();
$numbers_i_dont_want = array(5, 4, 3, 2, 1);
for ($i = 1; i <= 100; i++) {
   if !($i isin $numbers_i_dont_want) {
      $numbers_i_want[] = $i;
   }
}  
[/php]

If for some reason Php doesn't allow an empty initialization of an array (line 1), then change to = array(0);.

Hope it works now ;)

/Lau

```

$lower_level = 1;
$higher_level = 10;

$numbers = array( range( $lower_level, $higher_level+200 ) ); 

$numbers_i_want = $numbers;
$numbers_i_dont_want = array(5, 4, 3, 2, 1);
for ($i = 1; i <= 100; i++) {
  if !($i isin $numbers_i_dont_want) {
     $numbers_i_want[] = $i;
  }
}

```

error:: Parse error: syntax error, unexpected T_INC, expecting ')' in /home/prxainfo/public_html/bruce-o-matics.php on line 9

---

### Post by Lau_of_DK on 2008-05-27
> **ELD said:**
> Unfortunaly i get this:


Then you need to do some bug-hunting. I gave you 5 lines of code, but you report an error on line 9, specifically that php cannot read from [] - So what goes on in line 9? 

/Lau

---

### Post by ELD on 2008-05-28
This is line 9:

"for ($i = 1; i <= 100; i++) {"

I would figure it out but i really don't know what it is heh.

---

### Post by Lau_of_DK on 2008-05-28
> **ELD said:**
> This is line 9:

"for ($i = 1; i <= 100; i++) {"

I would figure it out but i really don't know what it is heh.

Its just me being an idiot - I think I've learned from this thread not to post code in languages I dont use, when I cant test the code locally - but oh well.

As you can see, PHP wants all variables to be prefixed with "$". Meaning a variable called i, should always be written as $i. In the code above I've only prefixed the first i, so changed the last 2 to $i.

```

for ($i = 1; $i <= 100; $i++)

```

and what it means is "for (starting value, condition while running, increment). 

So for ($i = 5; $i <= 50; $i += 25) would start with 5, increment by 25 (ie next value 30, then 55) and stop when $i is no longer below or equal to 50.

I appologize for the confusion,
/Lau

---

### Post by ELD on 2008-05-28
I now have this which almost works perfectly:
```

$lower_level = 1;
$higher_level = 10;

$numbers = array( range( $lower_level, $higher_level+200 ) ); 

$numbers_i_want = $numbers;
$numbers_i_dont_want = array(20,5, 4, 3, 2, 1);

for ($i = 1; $i < 100; $i++) {
  if (!in_array($i, $numbers_i_dont_want)) {
     $numbers_i_want[] = $i;
  }
}

foreach ($numbers_i_want as $number)
{
	echo $number . '<br />';
}

```

But it doesn't actually respect the numbers i want, for example "$higher_level+200" so the highest number should be "210". But the foreach loop gives me this:

> 
Array
6
7
8
9
..........

..all the way up to 99

When it should respect "$highest_number+200" so the highest should be 210?

Also why does it echo the word array?

---

### Post by wdaniels on 2008-05-28
> **ELD said:**
> $numbers = array( range( $lower_level, $higher_level+200 ) );

This will create a nested array, what you want is just:

```
$numbers = range( $lower_level, $higher_level+200 );
```

You're not getting the range you wanted because the loop only runs between 1 and 100:

```
for ($i = 1; $i < 100; $i++) {
```

You need something more like:

```
$lower_level = 1;
$higher_level = 10;

$numbers_i_want = $numbers;
$numbers_i_dont_want = array(5, 4, 3, 2, 1);
for ($i = $lower_level; $i <= $higher_level+200; $i++) {
  if (!in_array($i, $numbers_i_dont_want)) {
     $numbers_i_want[] = $i;
  }
}
```

---

### Post by ELD on 2008-05-28
> **wdaniels said:**
> This will create a nested array, what you want is just:

```
$numbers = range( $lower_level, $higher_level+200 );
```

You're not getting the range you wanted because the loop only runs between 1 and 100:

```
for ($i = 1; $i < 100; $i++) {
```

You need something more like:

```
$lower_level = 1;
$higher_level = 10;

$numbers_i_want = $numbers;
$numbers_i_dont_want = array(5, 4, 3, 2, 1);
for ($i = $lower_level; $i <= $higher_level+200; $i++) {
  if (!in_array($i, $numbers_i_dont_want)) {
     $numbers_i_want[] = $i;
  }
}
```

That now rightly echos out the numbers, but it doesn't take into account the numbers i don't want anymore?
Heres updated code:

```

$lower_level = 1;
$higher_level = 10;

$numbers = range( $lower_level, $higher_level+200 );

$numbers_i_want = $numbers;
$numbers_i_dont_want = array(20,5, 4, 3, 2, 1);

for ($i = $lower_level; $i <= $higher_level+200; $i++) {
  if (!in_array($i, $numbers_i_dont_want)) {
     $numbers_i_want[] = $i;
  }
}

foreach ($numbers_i_want as $number)
{
	echo $number . '<br />';
}

```

---

### Post by wdaniels on 2008-05-28
$numbers_i_want needs to be empty, not initialised to the range you want to test - that part happens in the loop.

---

### Post by wdaniels on 2008-05-28
i.e.

```
$lower_level = 1;
$higher_level = 10;

$numbers_i_dont_want = array(20,5, 4, 3, 2, 1);
for ($i = $lower_level; $i <= $higher_level+200; $i++) {
  if (!in_array($i, $numbers_i_dont_want)) {
     $numbers_i_want[] = $i;
  }
}

foreach ($numbers_i_want as $number)
  echo $number . '<br />';

```

or explicitly:

```
$lower_level = 1;
$higher_level = 10;

$numbers_i_want = array();
$numbers_i_dont_want = array(20,5, 4, 3, 2, 1);
for ($i = $lower_level; $i <= $higher_level+200; $i++) {
  if (!in_array($i, $numbers_i_dont_want)) {
     $numbers_i_want[] = $i;
  }
}

foreach ($numbers_i_want as $number)
  echo $number . '<br />';

```

---

### Post by ELD on 2008-06-05
Thank you so much that works great!

Now i just need a way to find out the numbers i don't want automatically.

Something like where there are more than 6 at a level count that number as one of the ones i don't want to use?

---

### Post by ELD on 2008-06-09
Still having a minor issue:

[php]
<?php
/*
Thanks to help from people on the Ubuntu Linux message board!
*/
include('../includes/dbconnect.php');

function make_brucie($level)
{
	$type_rand = rand(1,3);
		
	if ($type_rand == 1)
	{
		$type = 'S';
	}
		
	else if ($type_rand == 2)
	{
		$type = 'M';
	}
		
	else if ($type_rand == 3)
	{
		$type = 'A';
	}
		
	echo $type;
} 

// find the highest level player
$sql1 = "SELECT `level` FROM `pdm_stats` ORDER BY `level` DESC LIMIT 1";
$query1 = mysql_query($sql1) or die(mysql_error());
$highest_player = mysql_fetch_array($query1);

// the lowest players level
$lower_level = 1;

// the highest players level
$higher_level = $highest_player['level'];

// the numbers
$numbers_i_want = array();

// find the actual numbers needed
for ($i = $lower_level; $i <= $higher_level+50; $i++) 
{
	$numbers_i_want[] = $i;
}

// test
foreach ($numbers_i_want as $number)
{
	echo $number . '<br />';
	
	make_brucie($number);
}
?>
[/php]

For some reason the first number has no letter and when it gets to the final number there is a letter after it...example:

> 
1
M2
S3
M4
S5
S6
A7
A8
....more numbers...
M52
A53
A


I have no idea how to fix?

---

### Post by altonbr on 2008-06-09
Its because you're echoing the number, creating a line break and then creating the letter, so the first one will always be a number.

---

### Post by ELD on 2008-06-09
Oops my bad, cheers.

---

### Post by altonbr on 2008-06-09
I sort of messed with your code to make it more extenable, but if you're making a game, you may want to check out Object-oriented Programming. It is all preference however.

```
<?php

function make_brucie($level)
{
    switch($type_rand = rand(1,3))
    {
    	case 1:
    		return 'S';
    		break;
    	case 2:
    		return 'M';
    		break;
    	case 3:
    		return 'A';
    		break;
    	default:
    		exit(); // something went wrong
    }
} 

// the lowest players level
$lower_level = 1;

// the highest players level
$higher_level = 50;

// the numbers
$numbers_i_want = array();

// find the actual numbers needed
for ($i = $lower_level; $i <= $higher_level+50; $i++) 
{
    $numbers_i_want[] = $i;
}

// test
foreach ($numbers_i_want as $number)
{
    echo make_brucie($number).$number.'<br />';
}

?>
```
> A1
A2
S3
M4
M5
...

---

### Post by altonbr on 2008-06-09
Object oriented programming looks like this:
```
<?php

/**
 *  Class: Pet
 *	@attrib:  name
 *	@methods:  
 *		- __construct()
 *		- eat()
 *		- go_to_sleep()
 *		- play()
 */

class Pet {

	// Declare the attributes:
	public $name;

	// Constructor assigns the pet's name:
	function __construct($pet_name)
	{
		$this->name = $pet_name;
		self::go_to_sleep();
	}
	
	// Pets can eat
	function eat()
	{
		echo '<p>'.$this->name.' is eating</p>';
	}
	
	// Pets can sleep
	function go_to_sleep()
	{
		echo '<p>'.$this->name.' is sleeping</p>';
	}

	// Pets can play
	function play()
	{
		echo '<p>'.$this->name.' is playing</p>';
	}
	
	// Pets can parish :(
	function __destruct()
	{
		echo '<p>'.$this->name.' passed away :(</p>';
	}

} // End of Pet class


/**
 * Cat class extends Pet
 * Cat overrides play()
 */
class Cat extends Pet
{
	function play()
	{
		// Call the Pet::play() method
		parent::play();
		
		echo '<p>'.$this->name.' is climbing</p>';
		
	}
} // End of Cat class


/**
 * Dog class extends Pet
 * Dog overrides play()
 */
class Dog extends Pet
{
	function play()
	{
		// Call the Pet::play() method
		parent::play();
		
		echo '<p>'.$this->name.' is fetching</p>';
	}
} // End of Dog class

// Create a dog:
$dog = new Dog('Satchel');

// Create a cat:
$cat = new Cat('Bucky');

// Create an unknown type of pet:
$pet = new Pet('Rob');

// Feed
$dog->eat();
$cat->eat();
$pet->eat();

// Sleep
$dog->go_to_sleep();
$cat->go_to_sleep();
$pet->go_to_sleep();

// Play
$dog->play();
$cat->play();
$pet->play();

// Delete the objects:
unset($dog, $bucky, $pet);

?>
```

> Satchel is sleeping

Bucky is sleeping

Rob is sleeping

Satchel is eating

Bucky is eating
...

---

### Post by ELD on 2008-06-10
I know what OOP is and i use quite a bit of it, this is merly a script that will be used by cpanels crons, hence why i want to keep it simple.

---

### Post by altonbr on 2008-06-10
> **ELD said:**
> I know what OOP is and i use quite a bit of it, this is merly a script that will be used by cpanels crons, hence why i want to keep it simple.

You said you were programming a game and saw you programming in procedural, so I figured it was a fair warning :)

---

### Post by ELD on 2008-06-10
That is only a snippet of one page.

Besides i will not OOP program for the sake of OOP, when it is not needed, it's not.

---

### Post by altonbr on 2008-06-10
> **ELD said:**
> That is only a snippet of one page.

Besides i will not OOP program for the sake of OOP, when it is not needed, it's not.

That's great. I never use OOP, it was just a suggestion, thanks.

---

