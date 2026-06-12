---
title: "help with PHP"
date: 2009-07-23
forum: Programming Talk
---

### Post by nitro_n2o on 2009-07-23
Hello all, 

I'm trying to do something simple with PHP, but not having any luck for a while, hope someone could help. 

Here is the scenario, 

I wanna have a form with a text field for users to enter information and a submit button. 

When the user clicks on the submit button, I take the data then display the html form again & wait for more data. 

How can I do that? 

Thanks a lot

---

### Post by masux594 on 2009-07-23
Hi nitro_n2o.. Well, this "exercize" is very simple.. So, u have 2 pages, one where the user fill the form, and the second where u display the previous memo field and add more fields.. Only a question, do u want that the memo field of displayed form were editable? 

Sysc, A

---

### Post by nitro_n2o on 2009-07-23
Hey masux 

thx for the reply, I just need to redisplay the same form, get more info and process it again. The form is something like this 

<form action=<?$_SERVER['PHP_SELF'] method="post">
Name:<input type="text" name="fname"><br/>
<input type="submit" value="next">
</form>

The user will click submit, I'll take input from $_POST['fname'], then the page shows up again and the process repeated 

thx

---

### Post by masux594 on 2009-07-23
Your code:
[php]
<form action=<?$_SERVER['PHP_SELF'] method="post">
   Name:<input type="text" name="fname"><br/>
  <input type="submit" value="next">
 </form>
[/php]Well.. First of all i'll use **$_SERVER['SCRIPT_NAME'] **instead of $_SERVER['PHP_SELF']..(Looking at [this example]("http://php.about.com/od/learnphp/qt/_SERVER_PHP.htm")).. in second place, you must _write_ the variable using echo function.. and third, if u want to do what you say before u can use only a php page like this

Mine code:
[php]
<?php
 # a function that i use very often
 function IIF($aCond, $aTrue, $aFalse=''){
  IF ($aCond) {
    return $aTrue
  }
  else {
    return $aFalse;
  }
 }

  # if the variable were sended to this page, then means that this is the second page
  # and you'll link to another [Ex: page_3.php]
  # else, means that this is the first page and then u will link to the same page[the secod]
  echo "<form action='".IIF(isset($_POST['fname']),'page_3.php',$_SERVER['PHP_SELF']."' method='post'>".
  "Name:<input type='text' name='fname' value='".IIF(isset($_POST['fname']),'$_POST['fname'])')."'/><br/>".
   "<input type="submit" value="next"/>".
  IIF(
    isset($_POST['fname']),
    # all others input of the second page
    'input input etc'
  ).
"</form>";
?>
 [/php]Say to me if there's some mistakes.. in this moment i can't try directly the code..


Sysc, A

---

### Post by Mirge on 2009-07-23
> **masux594 said:**
> Your code:
[php]
<form action=<?$_SERVER['PHP_SELF'] method="post">
   Name:<input type="text" name="fname"><br/>
  <input type="submit" value="next">
 </form>
[/php]Well.. First of all i'll use **$_SERVER['SCRIPT_NAME'] **instead of $_SERVER['PHP_SELF']..(Looking at [this example]("http://php.about.com/od/learnphp/qt/_SERVER_PHP.htm")).. in second place, you must _write_ the variable using echo function.. and third, if u want to do what you say before u can use only a php page like this

Mine code:
[php]
<?php
 # a function that i use very often
 function IIF($aCond, $aTrue, $aFalse=''){
  IF ($aCond) {
    return $aTrue
  }
  else {
    return $aFalse;
  }
 }

  # if the variable were sended to this page, then means that this is the second page
  # and you'll link to another [Ex: page_3.php]
  # else, means that this is the first page and then u will link to the same page[the secod]
  echo "<form action='".IIF(isset($_POST['fname']),'page_3.php',$_SERVER['PHP_SELF']."' method='post'>".
  "Name:<input type='text' name='fname' value='".IIF(isset($_POST['fname']),'$_POST['fname'])')."'/><br/>".
   "<input type="submit" value="next"/>".
  IIF(
    isset($_POST['fname']),
    # all others input of the second page
    'input input etc'
  ).
"</form>";
?>
 [/php]Say to me if there's some mistakes.. in this moment i can't try directly the code..


Sysc, A

I certainly mean no offense, but please don't join me on any projects...

---

### Post by masux594 on 2009-07-23
> **Mirge said:**
> I certainly mean no offense, but please don't join me on any projects...
Why =) ?

P.s. It's only a simple "exercize".. if i do a great project the code will be certainly more similar to a "module" developing..

Sysc, A

---

### Post by wojox on 2009-07-23
[PHP]<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="POST">[/PHP]

---

### Post by Mirge on 2009-07-23
> **masux594 said:**
> Why =) ?

P.s. It's only a simple "exercize".. if i do a great project the code will be certainly more similar to a "module" developing..

Sysc, A

Why write a function as a "wrapper" for a basic if/else? Readability is out the window too in the above example. A heredoc would have been a better choice. Overall it just seems very sloppy.

---

### Post by masux594 on 2009-07-23
I don't use the IIF function only for concate strings.. Also for .. pass different parameters to a method for instance.. And, as i say before, this is a quick example, not an entire project.. and now that i read the code there's something wrong[quoting].. 
[PHP] <?php
 # a function that i use very often
 function IIF($aCond, $aTrue, $aFalse=''){
  IF ($aCond) {
    return $aTrue
  }
  else {
    return $aFalse;
  }
 }

  # if the variable were sended to this page, then means that this is the second page
  # and you'll link to another [Ex: page_3.php]
  # else, means that this is the first page and then u will link to the same page[the secod]
  echo "<form action='".IIF(isset($_POST['fname']),'page_3.php',$_SERVER['PHP_SELF']."' method='post'>".
  "Name:<input type='text' name='fname' value='".IIF(isset($_POST['fname']),'$_POST['fname'])')."'/><br/>".
   "<input type='submit' value='next'/>";
   IF (isset($_POST['fname'])) {
    # all others input of the second page
    echo 'input input etc';
  }
echo "</form>";
?>[/PHP]
However, [only for check your another approach] can u post some changes for my code? Thx in advance!

Sysc, A

---

### Post by Mirge on 2009-07-23
> **nitro_n2o said:**
> Hey masux 

thx for the reply, I just need to redisplay the same form, get more info and process it again. The form is something like this 

<form action=<?$_SERVER['PHP_SELF'] method="post">
Name:<input type="text" name="fname"><br/>
<input type="submit" value="next">
</form>

The user will click submit, I'll take input from $_POST['fname'], then the page shows up again and the process repeated 

thx

Assuming the form took 3 fields, firstName, lastName, age.. as an example:

```

<?php
$firstName = $_POST['firstName'];
$lastName = $_POST['lastName'];
$age = $_POST['age'];

if(strlen($firstName) > 0 && strlen($lastName) > 0 && strlen($age) > 0) {
// Form was filled out. Perform validation here. Do something with data assuming it checks out.
}
?>

<form action="<?=$_SERVER[SCRIPT_NAME];?>" method="post">
First Name: <input type="text" name="firstName" value=""/><br/>
Last Name: <input type="text" name="lastName" value=""/><br/>
Age: <input type="text" name="age" value=""/><br/>
<input type="submit" value="Submit"/>
</form>

```Or if you wanted the form pre-populated with the data already processed..
```

<form action="<?=$_SERVER[SCRIPT_NAME];?>" method="post">
First Name: <input type="text" name="firstName" value="<?=$firstName;?>"/><br/>
Last Name: <input type="text" name="lastName" value="<?=$lastName;?>"/><br/>
Age: <input type="text" name="age" value="<?=$age;?>"/><br/>
<input type="submit" value="Submit"/>
</form>

```

---

### Post by akvino on 2009-07-23
Mirge - thanks for this example - very good stuff.... I am breathing it inn.

And to the starter of the thread - if you need to process your second request based on first form's input - the best way to do it is with $_SESSION superglobal. I am PHP / Web programming newbie as well and have spent hours trying to make functions call one another with preserved variables between the sessions. Every time I tried to pass the first variable, due to the nature of the web (statless), I lost input. Once I figured out to collect data in to $_SESSION superglobal - the rest was easy.

---

