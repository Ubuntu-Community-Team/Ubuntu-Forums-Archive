---
title: "PHP Browsing Pictures"
date: 2011-01-21
forum: Programming Talk
---

### Post by TheStroj on 2011-01-21
Hi everyone!

I'm making a simple website that loads pictures from a folder. The code works, but the problem is that everytime I click a 'next' or a 'previous' button, the variable $i resets back to 0, but I don't want it to do that because those 2 buttons don't work then. I know that the problem is because the 'else' doesn't get executed so $i has no value, **but I just can't find a way to keep the value of $i after pressing a button.**. 

I already tried to put the HTML code in <?php ?> wrappers and echoing it, but that doesn't seem to solve the problem, $i is still reseting.

I know there are great programmers hanging out on this forum so I think this shouldn't really be a problem for you, because it's a beginners problem.

This is the code used on the site:

[PHP]
<h1 class="naslov">Slike</h1>

<form name="reg" method="POST" action="index.php?stran=slike">
<center>
<input type="submit" name="levo" value="Nazaj"/>
<input type="submit" name="random" value="Naklju&#269;no"/>
<input type="submit" name="desno" value="Naprej"/>
</center>
</form><br/>

<?php

$slike = glob("upload/*.*"); 
$kolicina = (count(glob("upload/*.*"))) - 1;

if (isset($_POST['random']))
{
	$i = rand(0, ($kolicina));

}
else if (isset($_POST['levo']))
{
		$i -= 1;

}
else if (isset($_POST['desno']))
{
		$i += 1;
}
else
{
	$i = rand(0, ($kolicina));
}

$pokazi = $slike[$i];
echo '<a href="'.$pokazi.'" target="_blank"> <img src="'.$pokazi.'" alt="slika" class="slika"> </a>';
echo $i;


?>
[/PHP]

Don't mind the language used in code, it's Slovenian.

Thanks for your help in advance :)

---

### Post by PaulM1985 on 2011-01-21
I think there are two possible ways to solve this problem.

1 - Save the value of i to some variable in the session
2 - Pass the value of i as an argument on the web address.

I don't know how to do it in php, but that is the sort of thing you probably want to google.

Paul

---

### Post by TheStroj on 2011-01-21
Oh trust me, I googled a lot, but I wasn't sure what to google. Your solutions are logical, I didn't even think of them. I will try them out for sure.

Thanks a lot :)

---

### Post by sdowney717 on 2011-01-21
you can keep these values in a hidden input on the form
 
    <input type="hidden" name="ws1" value="<?php print $andws; ?>" /> 
    <input type="hidden" name="ws2" value="<?php print $phrasews; ?>" /> 
    <input type="hidden" name="ws3" value="<?php print $orws; ?>" /> 
    <input type="hidden" name="ws4" value="<?php print $exws; ?>" /> 

then collect it with $_POST when the user clicks the button, etc..

     $dword1s = ($_POST['ws1']);
     $dphrasews = ($_POST['ws2']);
     $dword3s = ($_POST['ws3']);
     $dexws = ($_POST['ws4']);

you can also test to see if it exists and if not, then assign it

    $andws =  $_POST['andwords'];
    $phrasews = $_POST['exactphrase'];
    $orws = $_POST['orwords'];
    $exws = $_POST['exwords'];
    if (!$andws){$andws = $_POST['ws1'];};
    if (!$phrasews){$phrasews = $_POST['ws2'];};
    if (!$orws){$orws = $_POST['ws3'];};
    if (!$exws){$exws = $_POST['ws4'];};

---

### Post by sdowney717 on 2011-01-21
[http://www.phpriot.com/articles/intro-php-sessions/7](http://www.phpriot.com/articles/intro-php-sessions/7)

some info on session variables

---

### Post by TheStroj on 2011-01-23
> **sdowney717 said:**
> you can keep these values in a hidden input on the form
 
    <input type="hidden" name="ws1" value="<?php print $andws; ?>" /> 
    <input type="hidden" name="ws2" value="<?php print $phrasews; ?>" /> 
    <input type="hidden" name="ws3" value="<?php print $orws; ?>" /> 
    <input type="hidden" name="ws4" value="<?php print $exws; ?>" /> 

then collect it with $_POST when the user clicks the button, etc..

     $dword1s = ($_POST['ws1']);
     $dphrasews = ($_POST['ws2']);
     $dword3s = ($_POST['ws3']);
     $dexws = ($_POST['ws4']);

you can also test to see if it exists and if not, then assign it

    $andws =  $_POST['andwords'];
    $phrasews = $_POST['exactphrase'];
    $orws = $_POST['orwords'];
    $exws = $_POST['exwords'];
    if (!$andws){$andws = $_POST['ws1'];};
    if (!$phrasews){$phrasews = $_POST['ws2'];};
    if (!$orws){$orws = $_POST['ws3'];};
    if (!$exws){$exws = $_POST['ws4'];};

That looks even better and easier. Thanks again :)

---

### Post by sdowney717 on 2011-01-23
I found you may have to unset the vars or the session remembers them. Say you have multiple vars being used and sometimes they need to be blanked.
if they were still full, then when the page runs, the vars have a value.

So like I have 2 pages which link to each other. The first one I wanted to reload the input boxes with the text being searched after someone went back to it.
So I pick up the session vars stored on the second page
Erase the session vars
then load the input boxes with the text stored from the session vars.

[PHP]
<HTML>

<HEAD>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

<TITLE>Library Search</TITLE>

</HEAD>


<?php

//echo time();
session_start();

//first get them 
$andws = $_SESSION['ws1'];
$phrasews = $_SESSION['ws2'];
$orws = $_SESSION['ws3'];
$exws = $_SESSION['ws4'];

$aws = $_SESSION['wo1'];//aws1 or aws2
$orw = $_SESSION['wo2'];//orw1 or orw2
$exw = $_SESSION['wo3'];//exw1 or exw2

//then wipe them all out!
unset($_SESSION['ws1']);
unset($_SESSION['ws2']);
unset($_SESSION['ws3']);
unset($_SESSION['ws4']);
unset($_SESSION['offset']);

unset($_SESSION['wo1']);
unset($_SESSION['wo2']);
unset($_SESSION['wo3']);
session_unset();
session_destroy();
$_SESSION = array();

//first set the defaults
$check1a = "CHECKED";$check1b = "";//$check1a = "";$check1b = "CHECKED";}
$check2a = "CHECKED";$check2b = "";//$check2a = "";$check2b = "CHECKED";}
$check3a = "";$check3b = "CHECKED";//$check3a = "";$check3b = "CHECKED";}

//then determine what they should be if the session was set
if ($aws == "aws1"){$check1a = "CHECKED";$check1b = "";}elseif ($aws == "aws2"){$check1a = "";$check1b = "CHECKED";}
if ($orw == "orw1"){$check2a = "CHECKED";$check2b = "";}elseif ($orw == "orw2"){$check2a = "";$check2b = "CHECKED";}
if ($exw == "exw1"){$check3a = "CHECKED";$check3b = "";}elseif ($exw == "exw2"){$check3a = "";$check3b = "CHECKED";}
[/PHP]

---

