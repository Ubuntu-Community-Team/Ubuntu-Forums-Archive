---
title: "A Time Counter In Php"
date: 2008-05-12
forum: Programming Talk
---

### Post by saj0577 on 2008-05-12
Anyone got a script for a time counter in php:
for example i can type in a date and a time and it tells me how many weeks days hours minutes and seconds ago it was.

i.e. So say i could type in someones birthdate and time and it would tell you exactly how long they have been alive.


Cheers
Saj

---

### Post by popch on 2008-05-12
I believe your chances for a useful answer would be better in the programming forum.

---

### Post by saj0577 on 2008-05-12
Oops I didnt even realise, jeez, i need sleep.

If someone who can could move it there as your probably right. Untill then try to help me please people :D

Saj

---

### Post by -grubby on 2008-05-12
You can report your first post so the thread is moved

---

### Post by saj0577 on 2008-05-12
Basically i want to be able to turn the time difference between now and a date i choose and echo it in number of hours.

Saj

---

### Post by saj0577 on 2008-05-12
[PHP]     <?php
   
      // Get current time
   
      $date1 = time();
     
      // Get the timestamp of 2006 October 20
   
      $date2 = mktime(22,34,0,05,17,1921);

#
$dateDiff = $date1 - $date2;
#
$fullDays = floor($dateDiff/(60*60*24));
#
$fullHours = floor(($dateDiff-($fullDays*60*60*24))/(60*60));
#
$fullMinutes = floor(($dateDiff-($fullDays*60*60*24)-($fullHours*60*60))/60);
#[/PHP]

Then just print it however you want for example:

[PHP]echo "Been Alive for: $fullDays days, $fullHours hours and $fullMinutes minutes.";[/PHP]


Saj

---

### Post by Sef on 2008-05-12
Moved to programming talk.

---

### Post by dwhitney67 on 2008-05-12
I'm not 100% familiar with PHP programming, however I am familiar with mktime().  Here's the synopsis describing mktime():


[HTML]Description
int mktime ([ int $hour [, int $minute [, int $second [, int $month [, int $day [, int $year [, int $is_dst ]]]]]]] )

Returns the Unix timestamp corresponding to the arguments given. This timestamp is a long integer containing the number of seconds between the Unix Epoch (January 1 1970 00:00:00 GMT) and the time specified.
[/HTML]

You can read the full text [_here_]("http://us2.php.net/mktime").

P.S.  The oldest date one can use on my system is 00:00:00 12/14/1901.  The number of seconds appears as a negative long integer after calling mktime().  An invalid date given to mktime() returns false.

---

### Post by dwhitney67 on 2008-05-12
I just wrote this PHP/HTML code.  Perhaps it can help you:
[PHP]<html>
<head>
<title>Age Calculator</title>
</head>
<body>
        <H3>Enter your birth date:</H3>
        <form action="<?php echo $_SERVER["PHP_SELF"]; ?>" method="POST">
        <p><strong>MM:</strong>
        <input type="text" name="month" size="2" maxlength="2" />
        <strong>DD:</strong>
        <input type="text" name="day" size="2" maxlength="2"/>
        <strong>YYYY:</strong>
        <input type="text" name="year" size="4" maxlength="4"/></p>
        <p><input type="submit" value="Calculate age!"/></p>
        </form>
</body>
</html>

<?php

if ( isset( $_POST["month"] ) )
{
  $bmonth = intval( $_POST["month"] );
  $bday   = intval( $_POST["day"] );
  $byear  = intval( $_POST["year"] );

  $date1 = time();
  $date2 = mktime( 0, 0, 0, $bmonth, $bday, $byear );

  $dateDiff    = $date1 - $date2;
  $fullDays    = floor($dateDiff/(60*60*24));
  $fullHours   = floor(($dateDiff-($fullDays*60*60*24))/(60*60));
  $fullMinutes = floor(($dateDiff-($fullDays*60*60*24)-($fullHours*60*60))/60); 
  $years       = floor( $fullDays / 365 );
  $months      = ceil( $fullDays % 365 / 30 );

  if ( $date2 == false )
  {
    $message = "Invalid birth date given; must be greater than 12/14/1901.";
  }
  else if ( $years == 0 )
  {
    $message = "Your approximate age is $months month(s).";
  }
  else
  {
    $message = "Your approximate age is $years year(s) and $months month(s).";
  }

  echo "$message<br/>";
}

?>[/PHP]

---

### Post by saj0577 on 2008-05-12
Thanks alot mate

Saj

---

### Post by saj0577 on 2008-05-12
One bit of code i have never seen before.

$_SERVER["PHP_SELF"]

Does that mean that the function for the form is on the same page basically?

Saj

---

### Post by Verminox on 2008-05-12
Yup, it means that when the form is submitted, it goes to the same page for processing.

---

