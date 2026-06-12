---
title: "PHP Code Bug...."
date: 2011-02-20
forum: Programming Talk
---

### Post by stamatiou on 2011-02-20
HEy guys, I want to make a web page that you post information about you and I have created the registaration form, but somehow, it doesn't work.....
Here's the first page, default.php

```
<html>
<body>

<form action="insert.php" method="post"><br /><br />
First Name: <input type="text" name="firstname" /><br /><br />
Last Name: <input type="text" name="lastname" /><br /><br />
Age: <input type="text" name="age" /><br /><br />
Town/City/Village: <input type = "text" name="town" /><br /><br />
Country/Region: <input type = "text" name = "country" /><br /><br />
Adress: <input type = "text" name = "adress" /><br /><br />
Home Telephone Number 1: <input type = "text" name="telephone1" /><br /><br />
Home Telephone Number 2: <input type = "text" name = "telephone2" /><br /><br />
Father's name: <input type = "text" name = "father" /><br /><br />
Mother's name: <input type = "text" name = "mother" /><br /><br />
Favorite Football Team: <input type = "text" name = "fteam" /><br /><br />
Favorite Basketball Team: <input type = "text" name = "bteam" /><br /><br />
Favorite VoleyBall Team: <input type = "text" name = "vteam" /><br /><br />
Do you like watching sports? <input type = "text" name = "wsports" /><br /><br />
Do you like sports activities? <input type = "text" name = "dsports" /><br /><br />
Do you usually get good marks? <input type = "text" name = "marks" /><br /><br />
What is your favorite music? <input type = "text" name = "kind" size = "100"/><br /><br />
Who are your favorite singers and bands? <input type = "text" name = "band" size = "100" /><br /><br />
Do you play any musical instrument? <input type = "text" name = "instrument" /><br /><br />
<input type="submit" value = "Register" />
</form>

</body>
</html>

```

and the file that retrieves the information and takes them to the database : insert.php

```

<?php
$firstname =$_POST['firstname'];
$lastname=$_POST['lastname'];
$age=$_POST['age'];
$town=$_POST['town'];
$country=$_POST['country'];
$adress=$_POST['adress'];
$telephone1=$_POST['telephone1'];
$telephone2=$_POST['telephone2'];
//$cell=$_POST['cell'];
$father=$_POST['father'];
$mother=$_POST['mother'];
$fteam=$_POST['fteam'];
$bteam=$_POST['bteam'];
$vteam=$_POST['vteam'];
$wsports=$_POST['wsports'];
$dsports=$_POST['dsports'];
$marks=$_POST['marks'];
$kind=$_POST['kind'];
$band=$_POST['band'];
$instrument=$_POST['instrument'];

$con = mysql_connect("host","username","password");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_select_db("database", $con);

$sql="INSERT INTO Persons (firstname,lastname,age,town,country,adress,telephone1,telephone2,cell,father,mother,fteam,bteam,vteam,wsports,dsports,marks,kind,band,instrument)
VALUES
('$firstname,$lastname,$age,$town,$country,$adress,$telephone1,$telephone2,$cell,$father,$mother,$fteam,$bteam,$vteam,$wsports,$dsports,$marks,$kind,$band,$instrument');

if (!mysql_query($sql,$con))
  {
  die('Error: ' . mysql_error());
  }

mysql_close($con);
?>

```

---

### Post by An Sanct on 2011-02-20
Try replacing the code with this one ....

[PHP]$sql=
'INSERT INTO Persons (firstname,lastname,age,town,country,adress,telephone1,telephone2,cell,father,mother,fteam,bteam,vteam,wsports,dsports,marks,kind,band,instrument) VALUES'.
'('.$firstname.','.$lastname.','.$age.','.$town.','.$country.','.$adress.','.$telephone1.','.$telephone2.','.$cell.','.$father.','.$mother.','.$fteam.','.$bteam.','.$vteam.','.$wsports.','.$dsports.','.$marks.','.$kind.','.$band.','.$instrument.')';
[/PHP]And make sure to null check the stuff, and be kind to yourself and make it non XSS vulnerable ;) 

try inserting 
[PHP]'#'!''""--@!@-][\'; [/PHP]
into the form

and also try to insert ```
javascript:alert('XSS happened!')
```

---

### Post by stamatiou on 2011-02-21
> **An Sanct said:**
> Try replacing the code with this one ....

[PHP]$sql=
'INSERT INTO Persons (firstname,lastname,age,town,country,adress,telephone1,telephone2,cell,father,mother,fteam,bteam,vteam,wsports,dsports,marks,kind,band,instrument) VALUES'.
'('.$firstname.','.$lastname.','.$age.','.$town.','.$country.','.$adress.','.$telephone1.','.$telephone2.','.$cell.','.$father.','.$mother.','.$fteam.','.$bteam.','.$vteam.','.$wsports.','.$dsports.','.$marks.','.$kind.','.$band.','.$instrument.')';
[/PHP]And make sure to null check the stuff, and be kind to yourself and make it non XSS vulnerable ;) 

try inserting 
[PHP]'#'!''""--@!@-][\'; [/PHP]
into the form

and also try to insert ```
javascript:alert('XSS happened!')
```

Because I am newbie, what is xss

---

### Post by s.fox on 2011-02-21
> **stamatiou said:**
> Because I am newbie, what is xss

[Cross Site Scripting]("http://en.wikipedia.org/wiki/Cross-site_scripting")****

---

### Post by stamatiou on 2011-02-22
> **An Sanct said:**
> Try replacing the code with this one ....

[PHP]$sql=
'INSERT INTO Persons (firstname,lastname,age,town,country,adress,telephone1,telephone2,cell,father,mother,fteam,bteam,vteam,wsports,dsports,marks,kind,band,instrument) VALUES'.
'('.$firstname.','.$lastname.','.$age.','.$town.','.$country.','.$adress.','.$telephone1.','.$telephone2.','.$cell.','.$father.','.$mother.','.$fteam.','.$bteam.','.$vteam.','.$wsports.','.$dsports.','.$marks.','.$kind.','.$band.','.$instrument.')';
[/PHP]And make sure to null check the stuff, and be kind to yourself and make it non XSS vulnerable ;) 

try inserting 
[PHP]'#'!''""--@!@-][\'; [/PHP]
into the form

and also try to insert ```
javascript:alert('XSS happened!')
```
I did the thing with the $sql but it still gives me an error ant it tells me that it is in the first line....:confused:
The other thing with the xss that I have to insert it in the form, where exactly shall I place it?

---

### Post by slakkie on 2011-02-22
Guys, use PDO for this. It does all the checking for you, prepared statements ftw :)

[http://php.net/manual/en/book.pdo.php](http://php.net/manual/en/book.pdo.php)

Your current method:

```

$sql = sprintf("SELECT code, name FROM mydata WHERE code LIKE '%s'", 
   mysql_real_escape_string($code))
$q = mysql_query($sql);

```

New method:
```

$stm = $db->prepare("SELECT code, name FROM mydata WHERE code LIKE :code");
$stm->execute(array('code' => $code));

# or

$stm = $db->prepare("SELECT code, name FROM mydata WHERE code LIKE :code");
$stmt->bindParam(':code', $code);
$stm->execute();

```

---

### Post by slooksterpsv on 2011-02-22
> **stamatiou said:**
> I did the thing with the $sql but it still gives me an error ant it tells me that it is in the first line....:confused:
The other thing with the xss that I have to insert it in the form, where exactly shall I place it?

Post the error here, it works just fine for me, granted I don't have the host set or a db setup or that. I did have to put a " at the end in your code on the $sql line, cause it only had 1 "

But the one that line works too.

I just get: Notice Unidentified Index: ....

---

### Post by stamatiou on 2011-02-22
> **slooksterpsv said:**
> Post the error here, it works just fine for me, granted I don't have the host set or a db setup or that. I did have to put a " at the end in your code on the $sql line, cause it only had 1 "

But the one that line works too.

I just get: Notice Unidentified Index: ....
The site is  [here]("http://fapsebouk.net46.net/")

---

### Post by An Sanct on 2011-02-22
I tried the page with numbered input (every field a number ...)

and I got this result

> Error: You have an error in your SQL syntax; check the manual that  corresponds to your MySQL server version for the right syntax to use  near '9,10,11,12,13,14,15,16,17,18,19)' at line 1After I looked at the original code, posted here, I found, that you are still trying to insert "*cell*" into the sql, altho it is commented out

[PHP]...
//$cell=$_POST['cell']
...
[/PHP]So this should be the correct sql

[PHP]
$sql= 
'INSERT INTO Persons (firstname, lastname, age, town, country, adress, telephone1, telephone2, father, mother, fteam, bteam, vteam, wsports, dsports, marks, kind, band, instrument) VALUES'. 
'('.$firstname.','.$lastname.','.$age.','.$town.','.$country.','.$adress.','.$telephone1.','.$telephone2.','.$father.','.$mother.','.$fteam.','.$bteam.','.$vteam.','.$wsports.','.$dsports.','.$marks.','.$kind.','.$band.','.$instrument.')';  
[/PHP]note: I removed the "**cell,**" and "***,'.$cell.'***", you can leave it, but you have to uncomment it in php.

PS. Sorry, i didn't check the first sql for correctness, because i didnt know how the database is set up (what type the fields there are, are they nullable, integer/string/blob/.....) [I]too many variations to guess


[/I]-------------------------
Yes :) and another thing ... I hope, you have [LAMP]("http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/") installed and are trying this on your own machine, its much faster to edit and maintain!

---

### Post by An Sanct on 2011-02-26
It looks nicer now, just when I tried to register it says:

> **Parse error**:  syntax error, unexpected ';' in **/home/a8050994/public_html/insert.php** on line **20**

---

