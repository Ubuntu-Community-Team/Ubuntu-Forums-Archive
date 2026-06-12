---
title: "PHP Redirect Script"
date: 2009-07-21
forum: Programming Talk
---

### Post by diggfan2 on 2009-07-21
I have been trying to write a simple php script using html input variables to combine both of them in the user's address bar. My code is as follows: 

[php]   <?php


if(isset($_POST['submit'])){

header('Location: '.$_POST['servoce'].$_POST['num']');


}
else{

echo "
<form method=\"POST\" ENCTYPE=\"multipart/form-data\">
<table>
<tr><td>Tracking Number:</td><td><input type=\"text\" name=\"num\"><br></td></tr>
<tr><td>Service:</td><td><select name=\"ser\">
<option value=\"https://fedex.com/mobi/track.do?shipDate=trackingNbr=\">FedEx</option>
<option value=\"http://mobile.ups.com/ups/-1-3-2;jsessionid=732769EA6CA319415A3400B481B947CB.srv2?a=2.1039004&wi3.1039004.-9999=1Z6874R09023233800\">UPS</option>

</select></td></tr>

<tr><td>Tracking Number:</td><td><input type=\"text\" name=\"amo\"><br></td></tr>

<tr><td></td><td><input type=submit name=submit value=\"Start\"><br><br></td></tr>

<SCRIPT LANGUAGE=\"JavaScript\" TYPE=\"text/javascript\">
document.forms[0].num.select()</SCRIPT>
";

}
}
?>
  </div>
[/php]When I test this script I get the return of these parse errors:
> 

**Warning**:  Unexpected character in input:  ''' (ASCII=39) state=1 in **/home/tjoozeyc/public_html/txtdrop/index.php** on line **139**

**Parse error**:  syntax error, unexpected '}' in **/home/tjoozeyc/public_html/txtdrop/index.php** on line **164**I have tried 2 debug but nothing

---

### Post by Finalfantasykid on 2009-07-21
If I'm not mistaken, that error is caused by you putting 1 to many } at the end of the program.

---

### Post by diggfan2 on 2009-07-21
I then receive this error after submitting:


> **Warning**: Cannot modify header information - headers already sent by (output started at /home/tjoozeyc/public_html/txtdrop/index.php:139)

---

### Post by wojox on 2009-07-21
Is this the index page?

I don't see 139 lines?

---

### Post by wojox on 2009-07-21
Never mind I see your new error 

The "headers already sent" error is usually caused by having white space before or after the opening and closing PHP tags (<?php . . . ?>).

---

### Post by EddieRingle on 2009-07-22
> **wojox said:**
> Never mind I see your new error 

The "headers already sent" error is usually caused by having white space before or after the opening and closing PHP tags (<?php . . . ?>).

Maybe, but if you notice there is a closing div tag at the end, which probably means this code is in the middle of the page, hence the error.

---

