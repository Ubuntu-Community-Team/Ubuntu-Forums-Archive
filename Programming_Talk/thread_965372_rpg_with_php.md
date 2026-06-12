---
title: "rpg with php"
date: 2008-10-31
forum: Programming Talk
---

### Post by rtoot3 on 2008-10-31
hi, im trying to make an rpg, somewhat like [kingdom of loathing]("http://kingdomofloathing.com/"), using php. so to kinda learn a little bit more about php i made this little mini rpg where you type something, and it says "you 'whatever you typed' your cow". theres a few things that say something else when you type them and one of them is "fight a dragon". this is where im having problems. when you type fight a dragon, i tried to make a battle with trogdor where you choose your attack and try to kill him, and it keeps going until somone dies. the whole thing was working before i tried to make a battle. i was wondering if somone could help me out with this. heres the code:

cowrpg.html:
```
<html>
<head>
</head>
<body bgcolor="black">
<br /><font color="white">
<form action="cowrpg.php" method="post">
You are a brave adventurer with a cow. What would you like to do with your cow?
<br />
Type action here: <input type="text" name="action" />
<input type="submit" />
</form></font>
</form>
</body>
</html>

```

cowrpg.php:
```
<html>
    <head>
    </head>
    <body bgcolor="black"><br />
<font color="white"> 
<?php
$troghealth=10;
$yourhealth=10;
function battle()
{
echo "you wander around with your cow and find the mighty trogdor!<br />
choose your attack!<br />
trogdors health:" . $troghealth . "<br />your health:" . $yourhealth ."
<br />
<form action="cowbattle.php" method="post">
<input type="radio" name="attack" value="slice"/> slice
<br>
<input type="radio" name="attack" value="throw"/> throw
<input type="submit" />
</form>";
}
if ($_POST['action']=='kill')
echo "way to go, you killed your cow and lost the game stupid.";
elseif ($_POST['action']=='kick')
echo "you kick your cow,<br />poor cow.";
elseif ($_POST['action']=='eat')
echo "you eat your cow,<br />well, i guess you were hungry...";
elseif ($_POST['action']=='fight a dragon')
battle();
else
echo "you " . $_POST['action'] . " your cow.";
?>
  <br /><br /><a href="cowrpg.html" target="1">play again?</a>
  </font>
    </body>
</html>

```

cowbattle.php:
```
<html>
    <head>
    </head>
    <body bgcolor="black"><br />
<font color="white"> 
<?php
if ($_POST['attack']=='slice')
$troghealth-=2
$yourhealth-=5
echo "
you slice trogdor with your cow dealing 2 damage<br />
you were too close to trogdor and he burninates you dealing 5 damage<br />
choose your attack!<br />
trogdors health:" . $troghealth . "<br />your health:" . $yourhealth ."
<br />
<form action="cowbattle.php" method="post">
<input type="radio" name="attack" value="slice"/> slice
<br>
<input type="radio" name="attack" value="throw"/> throw
<input type="submit" />
</form>";
elseif ($_POST['attack']=='throw')
$troghealth-=2
echo "
you make sure to keep you distance and you throw your cow at trogdor dealing 2 damage<br />
your to far away for trogdor to burninate you<br />
choose your attack!<br />
trogdors health:" . $troghealth . "<br />your health:" . $yourhealth ."
<br />
<form action="cowbattle.php" method="post">
<input type="radio" name="attack" value="slice"/> slice
<br>
<input type="radio" name="attack" value="throw"/> throw
<input type="submit" />
</form>";
else if ($troghealth==0)
you win!<br /><br /><a href="cowrpg.html" target="1">play again?</a>
?>
else if ($yourhealth==0)
you lose!<br /><br /><a href="cowrpg.html" target="1">play again?</a>
?>
</font>
    </body>
</html>
```

its very simple, the attacks do have the same result every time, basicly to win you just keep throwing the cow so you dont get close enough for trogdor to burninate you
im not sure if its a simple mistake, of if im way off
you can see a working version without the battle [here]("http://rtoot3.com/?p=92")

---

### Post by Delever on 2008-10-31
Basic scheme to handle such game in php:

[header html]

[get user state (before fighting, after fighting, etc)]

[handle user actions based on what state he is in]

[change state based on actions]

[display html for state]

[display any other html]

---

### Post by rtoot3 on 2008-10-31
> **Delever said:**
> Basic scheme to handle such game in php:

[header html]

[get user state (before fighting, after fighting, etc)]

[handle user actions based on what state he is in]

[change state based on actions]

[display html for state]

[display any other html]

could you maybe show me what the code would be?
sorry, im really new to this

---

### Post by Delever on 2008-10-31
> **rtoot3 said:**
> could you maybe show me what the code would be?
sorry, im really new to this

There is no fun if I do it :) So I won't do it :).

** goes to write simple example **

Ermm... ok, you owe me a beer :D

[PHP]
<?php
/* header */

session_start();
?>
<html>
<head>
</head>
<body style="background: black; color: white">
<br />
<form id="form_main" action="index.php" method="post">

<!-- get user state -->
<?php

$first_time = False;

if (isset($_SESSION["state"]))
{
	$state = $_SESSION["state"];
} else {
	$state = "start";
	$first_time = True;
}

?>

<!-- handle user actions based on what state he is in, change state based on actions -->
<?php

if ($_POST["restart"] == "1")
{
	$state = "start";
	$first_time = True;
}

$state_selected = False;

if ($state == "start")
{
	if ($_POST['action'] == "kill")
	{
		$state = "cow dead"; $state_selected = True;
	} 
	elseif ($_POST['action'] == "eat")
	{
		$state = "cow eaten"; $state_selected = True;
	}
}
else if ($state == "cow dead")
{
	
}

if ($state_selected == False && !$first_time)
{
	echo "That action was not possible<br />";
}

$_SESSION["state"] = $state; // write it back to session variable

?>

<!-- display html for state -->

<?php
if ($state == "start") {
?>

You are a brave adventurer with a cow. What would you like to do with your cow?
<br />
Type action here: <input type="text" name="action" />
<input type="submit" />

<?php
} elseif ($state == "cow dead") {
?>

Now it is dead. How are you gonna live now?
<br />
Type action here: <input type="text" name="action" />
<input type="submit" />

<?php
} elseif ($state == "cow eaten") {
?>

Why you had to do it? Game over!

<?php
}
?>

<br />
<br />
<input type="hidden" name="restart" value="0" />
<input type="button" value="Restart" onclick="restart.value = 1; document.getElementById('form_main').submit();" />

</form>
</body>
</html>
[/PHP]

This, however, does not solve your problem. But you can create buttons for different actions like I did with button "restart". And now it is easy to expand game to infinity... almost.

---

### Post by rtoot3 on 2008-10-31
thank you very much, but i still need to solve the battle system

---

### Post by Delever on 2008-10-31
Something like this:
[PHP]
<?php
} elseif ($state == "cow fight") {
?>

Fight is intense! You:
<br />
<input type="hidden" name="fightaction" value="" />
<input type="button" value="Bash" onclick="fightaction.value = 'bash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Smash" onclick="fightaction.value = 'smash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Slash" onclick="fightaction.value = 'slash'; document.getElementById('form_main').submit();" /> 
[/PHP]

then handle it by checking $_POST['fightaction'] variable and change state as necessary.

You can also store numbers in $_SESSION["any_name_you_want"].
Just remember to clear those numbers when player restarts the game.

---

### Post by drubin on 2008-10-31
You might also want to take a look at ajax and xhtml as the php side

<font> tags are deprecated and should not be used. 
ajax so that the users experience is much more enhanced as waiting for the page to re-load completely every time would remove from some of the user experience.

---

### Post by eviltang on 2008-10-31
If I were to recommend a solution, which I am not sure I quite understand your question, I would say look into php sessions.

You could (in theory) add session variables to keep track of the health or position of your character.  So, everytime they did an action, the dragon could advance so eventually he would be close enough to burn them.

Although, now that I think about it, you could implement it like it was suggested, use a series of buttons for different attacks, whenever a button is pushed, have the dragons position change.

Just a thought.

---

### Post by drubin on 2008-10-31
> **eviltang said:**
> If I were to recommend a solution, which I am not sure I quite understand your question, I would say look into php sessions.

You could (in theory) add session variables to keep track of the health or position of your character.  So, everytime they did an action, the dragon could advance so eventually he would be close enough to burn them.

Although, now that I think about it, you could implement it like it was suggested, use a series of buttons for different attacks, whenever a button is pushed, have the dragons position change.

Just a thought.

Session vars would not be a great option for this encase of a disconnect from the internet you would loose all statistics about your player. You would have to take a look at some sort of backend db for storage of the data. 

This is a completly different way of thinking coming from an application development back ground. you need to use the DB as "a sort of memory management type thing", and just store some stuff in sessions to make the retrieval faster for things accessed often and only enough so you can retrive the correct(updated) info from the db.

---

### Post by eviltang on 2008-10-31
> **drubin said:**
> Session vars would not be a great option for this encase of a disconnect from the internet you would loose all statistics about your player. You would have to take a look at some sort of backend db for storage of the data. 

This is a completly different way of thinking coming from an application development back ground. you need to use the DB as "a sort of memory management type thing", and just store some stuff in sessions to make the retrieval faster for things accessed often and only enough so you can retrive the correct(updated) info from the db.

Understood, and thank you.  I was not sure what the OP was looking for.  Just trying to offer different ways to observe it.  I am by no means a programmer. lol!

---

### Post by rtoot3 on 2008-10-31
oh well the thing is with my first code, when you typed something it just went blank, now ive got a better code, and only one file instead of three.
but now when you press one of the buttons it doesnt work, you can test the new version at [http://rtoot3.com/test.php](http://rtoot3.com/test.php)
here is the code 

test.php
```
<?php

if ($_POST["restart"] == "1")
{
    $state = "start";
    $first_time = True;
}

$state_selected = False;

if ($state == "start")
{
    if ($_POST['action'] == "kill")
    {
        $state = "cow dead"; $state_selected = True;
    } 
    elseif ($_POST['action'] == "eat")
    {
        $state = "cow eaten"; $state_selected = True;
    }
    elseif ($_POST['action'] == "cook")
    {
        $state = "cow cooked"; $state_selected = True;
    }
    elseif ($_POST['action'] == "kick")
    {
        $state = "cow kicked"; $state_selected = True;
    }
    elseif ($_POST['action'] == "punch")
    {   
        $state = "cow punched"; $state_selected = True;
    }
    elseif ($_POST['action'] == "fight")
    {   
        $state = "cow fight"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "bash")
    {   
        $state = "cow bashed"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "smash")
    {   
        $state = "cow smashed"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "slash")
    {   
        $state = "cow slashed"; $state_selected = True;
    }
}
else if ($state == "cow dead")
{
    
}

if ($state_selected == False && !$first_time)
{
    echo "That action is not possible<br />";
}

$_SESSION["state"] = $state; // write it back to session variable

?>

<!-- display html for state -->

<?php
if ($state == "start") {
?>

You are a brave adventurer with a cow. What would you like to do with your cow?
<br />
Type action here: <input type="text" name="action" />
<input type="submit" />

<?php
} elseif ($state == "cow dead") {
?>

you kill your cow<br />
great... you killed your cow and lost the game, stupid.

<?php
} elseif ($state == "cow cooked") {
?>

you cook your cow into a well done steak,<br />
then you eat it.<br />
you lose.

<?php
} elseif ($state == "cow eaten") {
?>

you eat your cow<br />
wow, you really are stupid. you should have at least cooked it first!
<br />you lose.

<?php
} elseif ($state == "cow kicked") {
?>

you kick your cow<br />
poor cow

<?php
} elseif ($state == "cow punched") {
?>

you punch your cow<br />
poor cow

<?php
} elseif ($state == "cow bashed") {
?>

you bash your cow<br />
poor cow

<?php
} elseif ($state == "cow smashed") {
?>

you smash your cow<br />
poor cow

<?php
} elseif ($state == "cow slashed") {
?>

you slash your cow<br />
poor cow

<?php
} elseif ($state == "cow fight") {
?>

Fight is intense! You:
<br />
<input type="hidden" name="fightaction" value="" />
<input type="button" value="Bash" onclick="fightaction.value = 'bash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Smash" onclick="fightaction.value = 'smash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Slash" onclick="fightaction.value = 'slash'; document.getElementById('form_main').submit();" /> 
<input type="submit" />

<?php
}
?>

<br />
<br />
<input type="hidden" name="restart" value="0" />
<input type="button" value="Restart" onclick="restart.value = 1; document.getElementById('form_main').submit();" />

</form>
</body>
</html>
```

anyone know what happened?

---

### Post by drubin on 2008-10-31
> **eviltang said:**
> Understood, and thank you.  I was not sure what the OP was looking for.  Just trying to offer different ways to observe it.  I am by no means a programmer. lol!

I just post as I see things because other people might see them think it is a great (complete) solution and then sit for days trying to work out if they are disconnected they loose their info. 

But sessions are defiantly the way to go with storing "who" the correct logged in user is maybe a username or something just make sure it is all stored some were in persistent memory (like a DB).

Think of a session as your RAM, and DB as your hard drive, you would not to be editing your thesis in your favorite editor it is all fine on the screen and your PC crashes with out having saved it to your hard drive?

---

### Post by drubin on 2008-10-31
> **rtoot3 said:**
> oh well the thing is with my first code, when you typed something it just went blank, now ive got a better code, and only one file instead of three.
but now when you press one of the buttons it doesnt work, you can test the new version at [http://rtoot3.com/test.php](http://rtoot3.com/test.php)
here is the code 
....

anyone know what happened?

Firstly the if this is the first experience with coding all the more reason to learn as much as you can :)

Start with this.[http://www.php.net/manual/en/session.examples.php](http://www.php.net/manual/en/session.examples.php) then  [http://ubuntuforums.org/showthread.php?p=5520180#post5520180](http://ubuntuforums.org/showthread.php?p=5520180#post5520180) 

But you need to be telling php to start the session some where. (See examples and links)

Another minor issues is the $state is never set any where. (But I assume you haven't gotten to it yet)

---

### Post by Delever on 2008-10-31
> **drubin said:**
> Firstly the if this is the first experience with coding all the more reason to learn as much as you can :)

Start with this.[http://www.php.net/manual/en/session.examples.php](http://www.php.net/manual/en/session.examples.php) then  [http://ubuntuforums.org/showthread.php?p=5520180#post5520180](http://ubuntuforums.org/showthread.php?p=5520180#post5520180) 

But you need to be telling php to start the session some where. (See examples and links)

Another minor issues is the $state is never set any where. (But I assume you haven't gotten to it yet)

That's not full code you see. Look at my example which he is using as base, there is session_start();

> but now when you press one of the buttons it doesnt work

It works, you simply need the code which reacts to the changes you did.

[PHP]
if ($state == "start")
{
 // this code reacts to commands when state == start
} 
else if ($state == "cow fight")
{
 // here you can put code which is active when state is actual fight
 // like this
 // because only in this state there exists such thing like fightaction
 // now, don't create too many states, because you need code for every new state you make
 // instead, you better create state "game over"
    if ($_POST['fightaction'] == "bash")
    {   
        $state = "game over"; $state_selected = True;
        // and asign message to new variable which exists only in this state
        $gameover_message = "blah blah blah";
    }
    elseif ($_POST['fightaction'] == "smash")
    {   
        $state = "game over"; $state_selected = True;
        $gameover_message = "blah blah blah2";
    }
    elseif ($_POST['fightaction'] == "slash")
    {   
        $state = "game over"; $state_selected = True;
        $gameover_message = "blah blah blah3";
    }
}
[/PHP]

<...>

...so you can print that message in game over state

[PHP]
<?php
} elseif ($state == "game over") {

echo $gameover_message;

}
?>
[/PHP]

Remember, that's one of the million ways to do it... :) Don't take it for granted. You can create functions to simplify repetitive tasks, create cow object to store cow health, anything you want.

---

### Post by Delever on 2008-10-31
> **drubin said:**
> I just post as I see things because other people might see them think it is a great (complete) solution and then sit for days trying to work out if they are disconnected they loose their info. 


Yeah, session is temporary way to track the user, and as soon as you close browser window (let's say so), session ends.

I specifically haven't said anything about databases - because it complicates code even more, and no way I was going to write example with that - I just wanted to help getting started.

Mind you - databases are not hard, but it is one more language (SQL) and one more tool (MySQL).

---

### Post by rtoot3 on 2008-10-31
thank you so much everyone for helping me. i currently dont have the time to check if what all you guys said is working, but please come back tomorrow to see if i got it working.
thanks

---

### Post by drubin on 2008-10-31
> **Delever said:**
> Yeah, session is temporary way to track the user, and as soon as you close browser window (let's say so), session ends.

I specifically haven't said anything about databases - because it complicates code even more, and no way I was going to write example with that - I just wanted to help getting started.

Mind you - databases are not hard, but it is one more language (SQL) and one more tool (MySQL).

This is the HUGE problem with webdevelopment. I think ALL users should start with basic (static) html, add css, then work out some basic javascript, from then work on a server side scripting lang. then add database support.

This is more often then not never the case because of time constraints and not being able to make something productive with out the inclusion of all 6 completely separate langs that have completly different syntax makes this type of development harder.

---

### Post by Delever on 2008-11-01
> **rtoot3 said:**
> thank you so much everyone for helping me. i currently dont have the time to check if what all you guys said is working, but please come back tomorrow to see if i got it working.
thanks

I haven't posted complete working solution, I suggest you to experiment with what you have to get good understanding what is going on. Use "echo" to print variable values or additional info just for debugging, put more into $_SESSION variable to make game smarter, etc. Read on internet what exactly $_POST, $_GET, $_SESSION, $_SERVER is for, how they work.

---

### Post by rtoot3 on 2008-11-01
i guess im just really bad at this at the moment, but heres my code now

test.php:
```
<?php
/* header */

session_start();
?>
<html>
<head>
</head>
<body style="background: black; color: white">
<br />
<form id="form_main" action="test.php" method="post">

<!-- get user state -->
<?php

$first_time = False;

if (isset($_SESSION["state"]))
{
    $state = $_SESSION["state"];
} 
else 
{
    $state = "start";
    $first_time = True;
}

?>

<!-- handle user actions based on what state he is in, change state based on actions -->
<?php

if ($_POST["restart"] == "1")
{
    $state = "start";
    $first_time = True;
}

$state_selected = False;

if ($state == "start")
{
    if ($_POST['action'] == "kill")
    {
        $state = "cow dead"; $state_selected = True;
    } 
    elseif ($_POST['action'] == "eat")
    {
        $state = "cow eaten"; $state_selected = True;
    }
    elseif ($_POST['action'] == "cook")
    {
        $state = "cow cooked"; $state_selected = True;
    }
    elseif ($_POST['action'] == "kick")
    {
        $state = "cow kicked"; $state_selected = True;
    }
    elseif ($_POST['action'] == "punch")
    {   
        $state = "cow punched"; $state_selected = True;
    }
    elseif ($_POST['action'] == "fight")
    {   
        $state = "cow fight"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "bash")
    {   
        $state = "cow bashed"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "smash")
    {   
        $state = "cow smashed"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "slash")
    {   
        $state = "cow slashed"; $state_selected = True;
    }
}
else if ($state == "cow dead")
{
    
}

if ($state_selected == False && !$first_time)
{
    echo "That action is not possible<br />";
}

$_SESSION["state"] = $state; // write it back to session variable

?>

<!-- display html for state -->

<?php
if ($state == "start") {
?>

You are a brave adventurer with a cow. What would you like to do with your cow?
<br />
Type action here: <input type="text" name="action" />
<input type="submit" />

<?php
} elseif ($state == "cow dead") {
?>

you kill your cow<br />
great... you killed your cow and lost the game, stupid.

<?php
} elseif ($state == "cow cooked") {
?>

you cook your cow into a well done steak,<br />
then you eat it.<br />
you lose.

<?php
} elseif ($state == "cow eaten") {
?>

you eat your cow<br />
wow, you really are stupid. you should have at least cooked it first!
<br />you lose.

<?php
} elseif ($state == "cow kicked") {
?>

you kick your cow<br />
poor cow

<?php
} elseif ($state == "cow punched") {
?>

you punch your cow<br />
poor cow

<?php
} elseif ($state == "cow fight") {
?>

Fight is intense! You:
<br />
<input type="hidden" name="fightaction" value=""/>
<input type="button" value="Bash" onclick="fightaction.value = 'bash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Smash" onclick="fightaction.value = 'smash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Slash" onclick="fightaction.value = 'slash'; document.getElementById('form_main').submit();" /> 
<input type="submit" />
<?php 
} if ($state == "cow bashed") {
?>

    you bash your cow<br />
    poor cow


<?php 
} elseif ($state == "cow smashed") {
?>

you smash your cow<br />
poor cow


<?php 
} elseif ($state == "cow slashed") {
?>

you slash your cow<br />
poor cow
?>
<?php
}
?>

<br />
<br />
<input type="hidden" name="restart" value="0" />
<input type="button" value="Restart" onclick="restart.value = 1; document.getElementById('form_main').submit();" />

</form>
</body>
</html>
```
you can still try it at rtoot3.com/test.php
but when you type fight, it works. but then when you press either of the three buttons it displays "this action is not possible" which is only suposed to happen when the variable $state_selected is false. but for all three of the actions in the code it makes $state_selected true.

---

### Post by Delever on 2008-11-01
> **rtoot3 said:**
> 
but when you type fight, it works. but then when you press either of the three buttons it displays "this action is not possible" which is only suposed to happen when the variable $state_selected is false. but for all three of the actions in the code it makes $state_selected true.

but all these three actions are surrounded by

```

if ($state == "start")
{

}

```

and state is no longer "start", it's fight.

Refer to my previous post for more detail.

---

### Post by rtoot3 on 2008-11-01
:( what did i break now?
test.php:
```
<?php
/* header */

session_start();
?>
<html>
<head>
</head>
<body style="background: black; color: white">
<br />
<form id="form_main" action="test.php" method="post">

<!-- get user state -->
<?php

$first_time = False;

if (isset($_SESSION["state"]))
{
    $state = $_SESSION["state"];
} 
else 
{
    $state = "start";
    $first_time = True;
}

?>

<!-- handle user actions based on what state he is in, change state based on actions -->
<?php

if ($_POST["restart"] == "1")
{
    $state = "start";
    $first_time = True;
}

$state_selected = False;

if ($state == "start")
{
    if ($_POST['action'] == "kill")
    {
        $state = "cow dead"; $state_selected = True;
    } 
    elseif ($_POST['action'] == "eat")
    {
        $state = "cow eaten"; $state_selected = True;
    }
    elseif ($_POST['action'] == "cook")
    {
        $state = "cow cooked"; $state_selected = True;
    }
    elseif ($_POST['action'] == "kick")
    {
        $state = "cow kicked"; $state_selected = True;
    }
    elseif ($_POST['action'] == "punch")
    {   
        $state = "cow punched"; $state_selected = True;
    }
    elseif ($_POST['action'] == "fight")
    {   
        $state = "cow fight"; $state_selected = True;
    }
    
}
else if ($state == "cow dead")
{
    
}
else if ($state == "cow fight")
{
if ($_POST['fightaction'] == "bash")
    {   
        $state = "cow bashed"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "smash")
    {   
        $state = "cow smashed"; $state_selected = True;
    }
    elseif ($_POST['fightaction'] == "slash")
    {   
        $state = "cow slashed"; $state_selected = True;
    }
}
if ($state_selected == False && !$first_time)
{
    echo "That action is not possible<br />";
}

$_SESSION["state"] = $state; // write it back to session variable

?>

<!-- display html for state -->

<?php
if ($state == "start") {
?>

You are a brave adventurer with a cow. What would you like to do with your cow?
<br />
Type action here: <input type="text" name="action" />
<input type="submit" />

<?php
} elseif ($state == "cow dead") {
?>

you kill your cow<br />
great... you killed your cow and lost the game, stupid.

<?php
} elseif ($state == "cow cooked") {
?>

you cook your cow into a well done steak,<br />
then you eat it.<br />
you lose.

<?php
} elseif ($state == "cow eaten") {
?>

you eat your cow<br />
wow, you really are stupid. you should have at least cooked it first!
<br />you lose.

<?php
} elseif ($state == "cow kicked") {
?>

you kick your cow<br />
poor cow

<?php
} elseif ($state == "cow punched") {
?>

you punch your cow<br />
poor cow

<?php
} elseif ($state == "cow bashed") {
?>

you bash your cow dealing 2 damage

<?php
} elseif ($state == "cow slashed") {
?>

you slash your cow dealing 2 damage

<?php
} elseif ($state == "cow smashed") {
?>

you smash your cow dealing 2 damage

<?php
} elseif ($state == "cow fight") {
?>

Fight is intense! You:
<br />
<input type="hidden" name="fightaction" value=""/>
<input type="button" value="Bash" onclick="fightaction.value = 'bash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Smash" onclick="fightaction.value = 'smash'; document.getElementById('form_main').submit();" /> 
<input type="button" value="Slash" onclick="fightaction.value = 'slash'; document.getElementById('form_main').submit();" /> 
<input type="submit" />
<?php 

<?php
}
?>

<br />
<br />
<input type="hidden" name="restart" value="0" />
<input type="button" value="Restart" onclick="restart.value = 1; document.getElementById('form_main').submit();" />

</form>
</body>
</html>
```

now when you go to it, its just blank
rtoot3.com/test.php

---

### Post by rtoot3 on 2008-11-01
wow i cant believe im so bad at this that theres 2 full pages of people helping me.

---

### Post by drubin on 2008-11-01
Firstly if you ever get a plank page it "mostly" means that the php code did not execute(ie bad syntax error)

best place to look
```
tail -f /var/log/apache2/error.log
``` This is handy for when you are developing to have a terminal with that command running and you will be able to see all the errors that appear in your scripts.

OR 

Change the way your server [reports the errors]("http://www.php.net/error-reporting") and put them on the screen.  NB this is not recommended for production servers as it gives other users valuable information  about your webserver/code layout. (But should be fine for home testing)

---

### Post by rtoot3 on 2008-11-01
i dont run it from the terminal, i just upload it to my website every time i do something. how can i make it so i can run php files from my computor instead of my website so that i can see error messages? that would really help.

---

### Post by drubin on 2008-11-01
> **rtoot3 said:**
> i dont run it from the terminal, i just upload it to my website every time i do something. how can i make it so i can run php files from my computor instead of my website so that i can see error messages? that would really help.

Take a look at my sig for installing and setting up PHP (it is very simple ) and then work on a local test environment and when you are ready to upload the files to your server go a head :)

Also I knew you did not run these via CLI but I thought the website was on your own local machine. So this might be a problem because you more then likely do not have access to ssh and the logfiles.

---

### Post by rtoot3 on 2008-11-02
i still cant figure out why its blank:(

---

### Post by drubin on 2008-11-02
> **rtoot3 said:**
> i still cant figure out why its blank:(

Did you look in the logs, did you try adding the error reporting stuff to your scripts?

---

### Post by Delever on 2008-11-02
Install apache server and php5 on your computer:

```

apache2 php5 libapache2-mod-php5

```

copy your "test.php" into "/var/www" (you will need write rights, for example, you can run nautilus with sudo (gksudo nautilus) to access that directory).

Access your page by going to [http://localhost/test.php](http://localhost/test.php)

Be default, you should see errors printed instead of blank page.

---

### Post by rtoot3 on 2008-11-04
yes! thank you for showing me how to run it from my computor! its so much better when it tells you whats wrong! write now theres nothing wrong with it cause i fixed it all, but please check back to see how im doing.
thanx.

---

### Post by rtoot3 on 2008-11-04
ive decided to completly rewrite the code my own way to see if i could do it again by myself...
i cant :(
i wrote this code, but when you run it, all it says is "cow rpg" and nothing else. what happened?

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Cow RPG</title>
</head>

<body style="background-color: black; color: white;">
<!-- starting variables -->
<?php 
$action = "type";
$just_started = True;
?>
<!-- the form function -->
<?php
function usr(){?>
<form id="tehform" name="tehform" action="cowrpg.php" method="post">
Type action here: <input type="text" name="action" />
<input type="submit" />
</form>
<?php }?>
<!-- the choices -->
<?php if (action == "type"){
echo "you are a brave adventurer with a cow!\nwhat would you like to do with your cow?";
usr();} ?>
<?php
if ($_POST["action"] == kick)
{
$action = "kick"; $just_started = False;
}
?>
<!-- the users input -->

<?php 
echo "Cow RPG";
?>
<br />
<br />

<!-- the results -->
<?php
if (action == "kick"){
echo "you kick your cow";}

elseif (action == "type"){
usr();}
?>
<?php if ($just_started == False){ ?>
<input type="button" value="Bash" onclick="tehform.value = 'type'; document.getElementById('tehform').submit();" />
<?php } ?>
</body>
</html>
```

---

### Post by Delever on 2008-11-05
action == "type"

should be

$action == "type"

you are welcome to feel embarrassed now :lolflag:

---

### Post by drubin on 2008-11-05
> **rtoot3 said:**
> ive decided to completly rewrite the code my own way to see if i could do it again by myself...
i cant :(
i wrote this code, but when you run it, all it says is "cow rpg" and nothing else. what happened?


Did you look at the log files? /var/log/apache2/error_log


> **Delever said:**
> you are welcome to feel embarrassed now :lolflag:

That is not appropriate. I do not appreciate people laughing at other peoples mistakes. The OPP is more then welcome to laugh at his mistake but you aren't

---

### Post by Delever on 2008-11-05
> **drubin said:**
> 
That is not appropriate. I do not appreciate people laughing at other peoples mistakes. The OPP is more then welcome to laugh at his mistake but you aren't

I am very sorry, I tried to do it in friendly way, because I saw that he is getting better at php. God knows how many times I forgot to add $ before php variable too. I hope this does not discourage OP to ask for more help - I had no such intention.

---

### Post by drubin on 2008-11-05
> **Delever said:**
> I am very sorry, I tried to do it in friendly way, because I saw that he is getting better at php. God knows how many times I forgot to add $ before php variable too. I hope this does not discourage OP to ask for more help - I had no such intention.

I just did it so that others don't read your post and think it is appropriate to laugh all the time. And yes we all make those mistakes but some of us are new to it and making these types of mistakes weren't silly but par of the learning proccess

Yes the OP is improving. keep it up

---

### Post by rtoot3 on 2008-11-05
i dont really mind. i could tell delever was being nice about it, also thanx, i should have seen that one. lol

---

### Post by drubin on 2008-11-05
> **rtoot3 said:**
> i dont really mind. i could tell delever was being nice about it, also thanx, i should have seen that one. lol

I am glad this came from you as well :) keep up the work man, programming is all about persistence.

---

### Post by rtoot3 on 2008-11-06
whats wrong with my sessions, i get the following error when i try to play it:
```
Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /var/www/cowrpg.php:10) in /var/www/cowrpg.php on line 12

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /var/www/cowrpg.php:10) in /var/www/cowrpg.php on line 12
```

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Cow RPG</title>
</head>

<body style="background-color: black; color: white;">
<!-- starting variables -->
<?php 
$action = "start";
session_start(); 
$_SESSION['cowhealth'] = 10;
?>
<!-- the choices -->
<?php if ($action == "type"){
echo "you are a brave adventurer with a cow!\nwhat would you like to do with your cow?";
} ?>
<?php
if ($_POST["action"] == kick)
{
$action = "kick"; $_SESSION['cowhealth'] -= 2;
}
elseif ($_POST["action"] == punch)
{
$action = "punch"; $_SESSION['cowhealth'] -= 2;
}
?>
<!-- the users input -->

<?php 
echo "Cow RPG!";
?>
<br /><br />
<?php 
echo "cowhealth: " . $_SESSION['cowhealth'];
?>
<!-- the form function -->
<form id="tehform" name="tehform" action="cowrpg.php" method="post">
Type action here: <input type="text" name="action" />
<input type="submit" />
</form>

<!-- the results -->
<?php
if ($action == "kick"){
echo "you kick your cow";}
elseif ($action == "punch"){
echo "you punch your cow";}
?>
</body>
</html>
```

---

### Post by rtoot3 on 2008-11-06
nvm, found out session start has to go to the very top
but now the variable cowhealth still restarts to 10 every time you type something in again, and it doesnt show an error message or anything

```
<?php session_start(); ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Cow RPG</title>
</head>

<body style="background-color: black; color: white;">
<!-- starting variables -->
<?php 
$action = "start"; 
$_SESSION['cowhealth'] = 10;
?>
<!-- the choices -->
<?php if ($action == "type"){
echo "you are a brave adventurer with a cow!\nwhat would you like to do with your cow?";
} ?>
<?php
if ($_POST["action"] == kick)
{
$action = "kick"; $_SESSION['cowhealth'] -= 2;
}
elseif ($_POST["action"] == punch)
{
$action = "punch"; $_SESSION['cowhealth'] -= 2;
}
?>
<!-- the users input -->

<?php 
echo "Cow RPG!";
?>
<br /><br />
<?php 
echo "cowhealth: " . $_SESSION['cowhealth'];
?>
<!-- the form function -->
<form id="tehform" name="tehform" action="cowrpg.php" method="post">
Type action here: <input type="text" name="action" />
<input type="submit" />
</form>

<!-- the results -->
<?php
if ($action == "kick"){
echo "you kick your cow";}
elseif ($action == "punch"){
echo "you punch your cow";}
?>
</body>
</html>
```

---

### Post by drubin on 2008-11-07
Read this [http://ubuntuforums.org/showpost.php?p=5498327&postcount=2](http://ubuntuforums.org/showpost.php?p=5498327&postcount=2)
Also you might want to take a look at the whole thread it might help you.

---

### Post by rtoot3 on 2008-11-07
somehow im still not getting it.

---

### Post by drubin on 2008-11-07
> **rtoot3 said:**
> somehow im still not getting it.

Basically it says that it needs to be at the top of the script so that NOTHING is outputted to the screen.

---

### Post by rtoot3 on 2008-11-07
> **drubin said:**
> Basically it says that it needs to be at the top of the script so that NOTHING is outputted to the screen.

it is though, look at the top of this code.

```
**<?php session_start(); ?>**
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Cow RPG</title>
</head>

<body style="background-color: black; color: white;">
<!-- starting variables -->
<?php 
$action = "start"; 
$_SESSION['cowhealth'] = 10;
?>
<!-- the choices -->
<?php if ($action == "type"){
echo "you are a brave adventurer with a cow!\nwhat would you like to do with your cow?";
} ?>
<?php
if ($_POST["action"] == kick)
{
$action = "kick"; $_SESSION['cowhealth'] -= 2;
}
elseif ($_POST["action"] == punch)
{
$action = "punch"; $_SESSION['cowhealth'] -= 2;
}
?>
<!-- the users input -->

<?php 
echo "Cow RPG!";
?>
<br /><br />
<?php 
echo "cowhealth: " . $_SESSION['cowhealth'];
?>
<!-- the form function -->
<form id="tehform" name="tehform" action="cowrpg.php" method="post">
Type action here: <input type="text" name="action" />
<input type="submit" />
</form>

<!-- the results -->
<?php
if ($action == "kick"){
echo "you kick your cow";}
elseif ($action == "punch"){
echo "you punch your cow";}
?>
</body>
</html>
```

---

### Post by Delever on 2008-11-07
Imagine your code like this:

Every time you refresh your page (by clicking link or button), your script is executed. So, every time value 10 is assigned to $_SESSION['cowhealth'].

Basically, any variable is lost as soon as page is printed out for user. Except those variables you store in session.

To learn more about session, here are some useful links to tutorials:

[http://php.about.com/od/advancedphp/ss/php_sessions.htm](http://php.about.com/od/advancedphp/ss/php_sessions.htm)
[http://www.tizag.com/phpT/phpsessions.php](http://www.tizag.com/phpT/phpsessions.php)

> **rtoot3 said:**
> nvm, found out session start has to go to the very top
but now the variable cowhealth still restarts to 10 every time you type something in again, and it doesnt show an error message or anything


With your cow health, you need to solve a problem (thats what programming is, problem solving): how to set cow health to 10 only the first time, and for any subsequent requests use value you set previously.

---

### Post by rtoot3 on 2008-11-07
ok i understand now, i got it so the cows health doesnt reset over and over by using two files

file cowrpg.php
```
<?php session_start(); ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Cow RPG</title>
</head>

<body style="background-color: black; color: white;">
<!-- starting variables -->
<?php 
$_SESSION['action'] = "start"; 
$_SESSION['cowhealth'] = 10;
?>
<!-- the choices -->
<?php if ($_SESSION['action'] == "type"){
echo "you are a brave adventurer with a cow!nwhat would you like to do with your cow?";
} ?>

<?php 
echo "Cow RPG!";
?>
<br /><br />
<?php 
echo "cowhealth: " . $_SESSION['cowhealth'];
?>
<!-- the form function -->
<form id="tehform" name="tehform" action="cowrpg2.php" method="post">
Type action here: <input type="text" name="action" />
<input type="submit" />
</form>
</body>
</html>
```

file cowrpg2.php
```
<?php session_start(); ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Cow RPG</title>
</head>

<body style="background-color: black; color: white;">
<!-- starting variables -->
<!-- the choices -->
<?php if ($_SESSION['action'] == "type"){
echo "you are a brave adventurer with a cow!nwhat would you like to do with your cow?";
} ?>
<?php
if ($_POST["action"] == kick)
{
$action = "kick"; $_SESSION['cowhealth'] -= 2;
}
elseif ($_POST["action"] == punch)
{
$action = "punch"; $_SESSION['cowhealth'] -= 2;
}
?>
<!-- the users input -->

<?php 
echo "Cow RPG!";
?>
<br /><br />
<?php 
echo "cowhealth: " . $_SESSION['cowhealth'];
?>
<!-- the form function -->
<form id="tehform" name="tehform" action="cowrpg2.php" method="post">
Type action here: <input type="text" name="action" />
<input type="submit" />
</form>

<!-- the results -->
<?php
if (action == "kick"){
echo "you kick your cow";}
elseif ($action == "punch"){
echo "you punch your cow";}
elseif ($_SESSION['cowhealth'] == 0){
echo "dude, you gotta stop beating down your cows, you just killed it and lost the game, here, ill give you a new cow"; $_SESSION['cowhealth'] = 0;}
?>
</body>
</html>
```

thank you so much! im so close to being done, but when cow health gets to 0, i want it to say

"dude, you gotta stop beating down your cows, you just killed it and lost the game, here, ill give you a new cow"

it does that correctly, but i also want it to reset cow health to 10, but for some reason it just keeps going down to negitives.

---

### Post by Delever on 2008-11-07
Game seems simple, but you actually need to check a lot of things.

I will give you an example how it can be done; read comments, then read them again. I suggest you to improve your version by taking bits and pieces you want from mine - that way you can learn more quickly.

In my version, I used some new things: like array to store player's data and array to store cow's data. Those arrays are $player and $opponent.

My version is not "best way to do it" - there is no "best" way, what should be important that it works.

And, in case I forgot - read comments. You will find many answers there.

---

### Post by rtoot3 on 2008-11-09
thank you so much! i understand so much more about php now from this simple little project! by the way, since you basicaly made whole the last version of this game, its your work. and i was wondering if i could put it on my website?

---

### Post by Delever on 2008-11-09
> **rtoot3 said:**
> thank you so much! i understand so much more about php now from this simple little project! by the way, since you basicaly made whole the last version of this game, its your work. and i was wondering if i could put it on my website?

Yeah, but I would be glad if you tried to improve it, since it is very basic :)

---

### Post by drubin on 2008-11-09
> **rtoot3 said:**
> thank you so much! i understand so much more about php now from this simple little project! by the way, since you basicaly made whole the last version of this game, its your work. and i was wondering if i could put it on my website?

best way to learn is to download some opensource projects ie phpbb3 and read the code there. Also reading programming guidelines can help with formating of your code and making code easier to maintain.

---

### Post by rtoot3 on 2008-11-29
lol, Im back with another problem, i tried to do it with cookies instead of sessions. heres the code
```


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<link rel="stylesheet" type="text/css" href="style.css"/>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
<title>Placelandia</title>
</head>
<body>
<?php include('tabbar.php'); ?><br /><br />
<?php include('header.php'); ?>
<br />
<div id="page">
<?php include('sidebar.php'); ?>
<div id="content">
<form id="tehform" name="tehform" action="index.php" method="post">

<!-- we have to create this input field, so that when we set value TO it
it will be sent inside $_POST['action'] variable after page is reloaded -->
<input type="hidden" id="action" name="action" value="" />

<?php
 $inTwoMonths = 60 * 60 * 24 * 60 + time(); 
 setcookie('player', $player, $inTwoMonths);
 setcookie('opponent', $opponent, $inTwoMonths);
// when we recieve action to "restart" the game, we simply clear session value
if ($_POST['action'] == 'restart')
{
	echo 'Restarting the game.<br /><br /><br />';
	unset($_COOKIE['player']);
	// thats all, everything is cleared (except the oponent, it will be cleared anyway)
}

if (isset($_COOKIE['player'])) // check if we have player variable stored in session
{
	// if yes, asign it to local variable
	null;

	// load oponent too
} else { // if we don't have player stored in session, it means player is new or he have just restarted the game
	// so we create new player
	
	$player = array(
		'max_health' => 100,
		'health' => 100,
		'strength' => 20, // just example, you can add any number of variables
		'state' => 'alone', // our first state is alone, that means player is not doing anything special
		'enemies_slayed' => 0,
		'cows_saved' => 0,
		);
	
	// it also means no other game options are initialized
	$opponent = null;
}

// this function returns random number between 0 and 100
function Chance()
{
	return rand(0, 100);
}

// this function prints button
// this button does three things:
// 1. draws a button with $name text written on it
// 2. that button, when clicked, changes <input name="action" /> field's value to $action
// 3. after doing that, button calls submit(), which reloads page and sends all <input> field
// values as $_POST variables to this script.
function MakeButton($name, $action)
{
	?>
	<input type="button" value="<?php print($name); ?>"	 onclick="document.getElementById('action').value = '<?php print($action); ?>';document.getElementById('tehform').submit();" />
	<?php
}

// function to increase player health
// & before variable means that changed value must be preserved when function finishes
// You can pass array as "$character", the only requirement is that it must have
// "health" and "max_health" items. So we can use this function to heal both
// player and opponent, because both have those values
function Heal($how_much, &$character)
{
	if ($character['health'] + $how_much <= $character['max_health']) // if increased health will be less than max health
	{
		$character['health'] += $how_much; // increase health
	} else { // if increased health will be more than max health
		$character['health'] = $character['max_health']; // set health to max health
	}
}

// & before variable means that changed value must be preserved when function finishes
function GiveDamageTo($how_much, &$character)
{
	if ($character['health'] - $how_much >= 0) // if decreased health will be more then 0
	{
		$character['health'] -= $how_much; // decrease health
	} else { // if decresed health will be less than 0
		$character['health'] = 0; // set health to 0
	}
}

// this function returns random item from array; look below how it is used
function OneOf($array)
{
	// input is array like this: array("cow" => 20, "dragon" => 30)
	// it means: "item" => "probability it will be chosen"
	
	// first sum up all those probability values
	$sum_of_values = 0;
	foreach ($array as $key => $value)
	{
		$sum_of_values += $value;
	}
	// then take random value between min and max
	$random_value = rand(1, $sum_of_values);
	// then iterate over elements again and find which one $random_value represents
	$cur_value = 0;
	foreach ($array as $key => $value)
	{
		$cur_value += $value;
		if ($random_value <= $cur_value)
		{
			return $key;
		}
	}
	// if all fails return last array key
	$keys = array_keys($array);
	return $keys[count($array) - 1];
}

// this function handles player traveling anywhere
// & before variable means that changed value must be preserved when function finishes
function Travel(&$player, &$opponent)
{
	// we have 70 percent chance to meet someone or something
	if (Chance() < 70)
	{
		// now we need to choose random oponent, with probability values
		// the higher value after =>, the higher probability it will be chosen
		// see OneOf function above for details
		$opponent_name = OneOf(array('Cow' => 40, 'Wolf' => 30, 'Radscorpion' => 7, 'Hobo' => 20, Stick Figure => 25)); // right now I added three options
		if ($opponent_name == 'Cow')
		{
			echo 'You meet a cow. It seems friendly.<br />'; 
			// now asign that to variable, which will be written to session
			// so what we met is preserved
			$opponent = array(
				'name' => $opponent_name,
				'max_health' => 10,
				'health' => 10,
				'strength' => 1, // just example, you can add any number of variables
				);
			// and player state no longer can be "alone"
			// because when he is "alone", he can only travel and wait, and we want
			// him to interact with oponent
			$player['state'] = 'with_oponent'; // i am just inventing it as I go
		} 
		else if ($opponent_name == 'Wolf')
		{
			echo 'You meet a wolf. It seems it hasn\'t eaten any cows lately. You will do until it finds a cow.<br />'; 

			$opponent = array(
				'name' => $opponent_name,
				'max_health' => 50,
				'health' => 50,
				'strength' => 23,
				);
				
			$player['state'] = 'fight'; // wolf starts fighting right away
		}
		else if ($opponent_name == 'Hobo')
		{
			echo 'Somehow you find yourself in a dark alley with a hobo. "oh no magical squirrel, your not stealing my pixie  				sticks again!" he says drunkenly. He breaks the bottom of his beer bottle on the ground and prepares to fight!
			<br />'; 

			$opponent = array(
				'name' => $opponent_name,
				'max_health' => 50,
				'health' => 40,
				'strength' => 19,
				);
				
			$player['state'] = 'fight';
		}
		else if ($opponent_name == 'Radscorpion')
		{
			echo 'You meet a radscorpion. You have no chances! Probably.<br />'; 

			$opponent = array(
				'name' => $opponent_name,
				'max_health' => 90,
				'health' => 90,
				'strength' => 30,
				);
				
			$player['state'] = 'fight'; // radscorpion also starts fighting right away
		}
else if ($opponent_name == 'Stick Figure')
		{
			echo '<img src="images/stickfigure.png" width="100" height="100"/><br />Holy Crap! Its a friggin '.$opponent_name.'!!! Just look at those muscles! How will you ever defeat that?<br />'; 

			$opponent = array(
				'name' => $opponent_name,
				'max_health' => 90,
				'health' => 90,
				'strength' => 30,
				);
				
			$player['state'] = 'fight'; // radscorpion also starts fighting right away
		}
	} else {
		$opponent = null;
	}
}

// handle actions which happen when user clicks some button
// notice that we handle actions AFTER we load values from session
// because action handling happens after page reload
if ($player['state'] == 'alone') // state alone or with_oponent means player is doing nothing special
{
	if ($_POST['action'] == 'travel') // if state is alone, we can react to such actions like travel and wait, however, if state is another, like "fight", these actions can not be ececuted; and that's good, because we don't want player to be able to travel when fighting or talking
	{
		// what travel means - it means that we look what oponents
		// player has, decide what to print with player leaving them
		// then remove the oponent, and based on random number thange oponent
		// to null (that would mean player has not found anything)
		// or change it to another one
		
		// first, every time player travels we increse his health a little bit
		Heal(2, $player);
		
		// execute travel function, which will modify our player and maybe opponent
		Travel($player, $opponent);
	} 
	else if ($_POST['action'] == 'wait')
	{
		// when player waits, he regenerates health quickly
		Heal(30, $player);
	}
} 
else if ($player['state'] == 'with_oponent')
{
	if ($_POST['action'] == 'travel')
	{
		Heal(2, $player);
		
		if ($opponent['name'] == 'Cow') // if that was cow, and we travel past it
		{
			$player['cows_saved'] += 1; // increse count of saved cows
		}
		
		Travel($player, $opponent);
	}
	else if ($_POST['action'] == 'wait')
	{
		Heal(30, $player);
	}
	else if ($_POST['action'] == 'start_fight') // in state "with_oponent" we have one more action
	{
		$player['state'] = 'fight'; // wich changes state into fight
	}
}
else if ($player['state'] == 'fight')
{
	if ($_POST['action'] == 'hard_slash') 
	{
		// hard slash has lower chance to hit, but deals more damage
		if (Chance() < 45)
		{
			$damage = $player['strength'] * 1.5; // calculate how much damage player can give
			GiveDamageTo($damage, $opponent);
			echo 'You hit '.$opponent['name'].' and give '.$damage.' damage.<br />';
		} else {
			echo 'You miss.<br />';
		}
	} 
	else if ($_POST['action'] == 'hit') 
	{
		// simple hit has high chance to hit, but deals less damage
		if (Chance() < 92)
		{
			$damage = $player['strength'] * 1; // calculate how much damage player can give
			GiveDamageTo($damage, $opponent);
			echo 'You hit '.$opponent['name'].' and give '.$damage.' damage.<br />';
		} else {
			echo 'You miss.<br />';
		}
	}
	if ($opponent['health'] == 0)
	{
		echo 'You killed the '.$opponent['name'].'!<br />';
		$player['enemies_slayed'] += 1; // increse count of slayed enemies
		$player['state'] = 'with_oponent'; // change state
	}
}

if ($opponent == null) // there is not much to do when there is no oponent
{
	echo 'You stand alone in the middle of nowhere.<br />';
	// now we can use button function to print button
	// it much easier than doing it again and again
	echo '<hr />'; // draw line
	MakeButton('Travel','travel');
	MakeButton('Wait','wait');
} else { // otherwise
	if ($player['state'] == 'with_oponent')
	{
		echo 'You are with '.$opponent['name'].'.<br />';
		if ($opponent['health'] > 0) // it is alive
		{       
			if (Chance() < 70)
			{
				echo 'Both standing, and looking at each other calmly.<br />';
			} else {
				echo 'It wonders why you are staring so long.<br />';
			}
			MakeButton('Start fighting','start_fight');
		} else { // it is dead
			echo 'And it is dead.<br />';
		}
		MakeButton('Move along','travel');
		MakeButton('Wait','wait');
	} else if ($player['state'] == 'fight') {
		echo 'You are fighting with '.$opponent['name'].'.<br />';
		// if state is fight, oponent tries to hit after every turn
		// however, it also has chance to miss
		if (Chance() < 70) // cow and wold could have different "accuracy" or whatever to be different in this case, but I am not doing it
		{
			$damage = $opponent['strength']; // in case of enemies, they deal the same damage as the strength they have
			GiveDamageTo($damage, $player);
			if ($player['health'] > 0)
			{
				echo $opponent['name'].' hits you and gives you '.$damage.' damage.<br />';
			}
			else
			{
				echo $opponent['name'].' killed you!<br />';
			}
		} else {
			echo $opponent['name'].' missed.<br />';
		}
		echo $opponent['name'].' has '.$opponent['health'].' health.<br />';
		
		if ($player['health'] > 0)
		{
			MakeButton('Hit '.$opponent['name'],'hit');
			MakeButton('Try to hit harder','hard_slash');
			MakeButton('Do nothing',''); // just reload the page
		} else {
			$player['state'] = 'dead';
			MakeButton('Oh My God!',''); // we just need to reload page, action is not important
		}
	} 
	else if ($player['state'] == 'dead') 
	{
		echo 'Here lies the corpse of mighty traveler, who wasted all his life on the Internet.<br />';
		echo 'Killed by some random '.$opponent['name'].', he has no story to tell.<br />';
		echo '<br /><br />';
		echo 'Enemies slayed: '.$player['enemies_slayed'].'<br />';
		echo 'Cows saved: '.$player['cows_saved'].'<br />';
	}
}

echo '<hr />'; // draw line

MakeButton("Restart", "restart");
// at the end, always put all variables back into session
// so that changes are preserved when use reloads the page

?>

</form>
</div>
</div>
<br />
<?php include('footer.php'); ?>
</body>
</html>

```
when i run it on my localhost it gives me these two errors
```

Warning: setcookie() expects parameter 2 to be string, array given in /home/placela/public_html/index.php on line 364

Warning: Cannot modify header information - headers already sent by (output started at /home/placela/public_html/index.php:10) in /home/placela/public_html/index.php on line 365

```
what happened there?
you can see the version before i tried using cookies here:
[http://placelandia.com/](http://placelandia.com/)
yup, i got a domain name for it.
also, look at the code for the stick figure, when you encounter a stick figure its supposed to show an image. but it doesn't.

---

### Post by drubin on 2008-11-29
> **rtoot3 said:**
> lol, Im back with another problem, i tried to do it with cookies instead of sessions. heres the code
when i run it on my localhost it gives me these two errors
```

Warning: setcookie() expects parameter 2 to be string, array given in /home/placela/public_html/index.php on line 364

Warning: Cannot modify header information - headers already sent by (output started at /home/placela/public_html/index.php:10) in /home/placela/public_html/index.php on line 365

```
what happened there?
you can see the version before i tried using cookies here:
[http://placelandia.com/](http://placelandia.com/)
yup, i got a domain name for it.
also, look at the code for the stick figure, when you encounter a stick figure its supposed to show an image. but it doesn't.

Take a look [here]("http://ubuntuforums.org/showthread.php?t=876312") for your session error look at my posts.

Please take a look at the [php.net manual]("http://www.php.net/setcookie") for the reason for your 2nd error. Your 2nd param is not a String but is an Array (many Strings). You need to only pass a single string varr into the 2nd param. 

See it is an array.
[PHP]
$opponent = array(
	'name' => $opponent_name,
	'max_health' => 90,
	'health' => 90,
	'strength' => 30,
	);[/PHP]

Not sure if you were meaning to pass $opponent_name instead of $opponent

---

### Post by rtoot3 on 2008-11-29
ok, im just gonna use sessions then for a while, but why doesn't the image show?

---

