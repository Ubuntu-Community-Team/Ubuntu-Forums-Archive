---
title: "PHP help needed! Urgently!"
date: 2009-01-16
forum: Programming Talk
---

### Post by IsolatedEarthling on 2009-01-16
I am supposed to do a snake-eye thingy on PHP. The program chooses 2 random numbers as dice rolls, and if the dice rolls are different, the player gets points equal to the sum of the dice rolls. It continues until the player gets two identical rolls, in this case the game ends, with the player getting the score before the identical rolls as the final score. The problem is, whenever the player presses the button to generate the dice rolls, the page refreshes, resulting in the total score being wiped clean, i.e. back to 0. Please help. Thnx

[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Snake-Eyes Game</title>
</head>

<body>
<form id="form1" name="form1" method="post" action="">
  <label>
    <input type="submit" name="btnRoll" id="btnRoll" value="Roll Dice" />
  </label>
  <a href="index.html">Return to Homepage</a>
</form>
[PHP]<?php

$dice1=rand(1,6);
$dice2=rand(1,6);
echo "\n".'Dice 1: '.$dice1;
echo "\n".'Dice 2: '.$dice2;

if($dice1 != $dice2)
{$score2 = $score1+$dice1+$dice2;
echo "\n".'Score: '. $score2;
$score1 = $score2;}

else
{echo "\n".'Game Over!';}

?>[/PHP]
</body>
</html>[/HTML]

---

### Post by mike_g on 2009-01-16
You can send the score as a post variable in your form. Also, its best to do your calculations and stuff first then display your page after. EG:
```
<?php 
$score =(int)$_POST['existing_score'];
$dice1=rand(1,6);
$dice2=rand(1,6);
$roll_msg = "\n".'Dice 1: '.$dice1."\n".'Dice 2: '.$dice2;

if($dice1 != $dice2)
{
	$score += $dice1+$dice2;
	$message = "\n".'Score: '. $score;
}
else
{
	echo 'Game Over!';
}
?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Snake-Eyes Game</title>
</head>

<body>
<?php
	echo $roll_msg."<br />";
	echo $message."<br />";
?>
<form id="form1" name="form1" method="post" action="">
  <input type="hidden" name="existing_score" value="<?php echo $score;?>" />
    <input type="submit" name="btnRoll" id="btnRoll" value="Roll Dice" />
  </label>
  <a href="index.html">Return to Homepage</a>
</form>
</body>
```

---

### Post by dgoosens on 2009-01-16
hi,

I think your best solution would be by creating a SESSION per player where you save the points...

That's how I would do it though... 

dGo

---

### Post by Reiger on 2009-01-16
That or write the content to a Cookie, and count upon your players not to cheat. :) Then again, the same rings true for the POST/GET way of including persistency. ;)

---

