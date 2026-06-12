---
title: "PHP/MySQL error"
date: 2007-02-02
forum: Programming Talk
---

### Post by Ubuntuud on 2007-02-02
Hi,
I got the following code:

```
<?php
$con = mysql_connect('localhost', 'pieter', '******');
mysql_select_db('jouw_llr');

echo '<div class="yellow_container"><div class="yellow_container2">';
echo '<h2>Klik om te mailen</h2>';
echo '<ul>';
$r = mysql_query("SELECT email,truename FROM users ORDER BY order ASC");
while ($rw = mysql_fetch_array($r)) {
	echo '<li class="link" onclick="location.href=\'mailto:'.$rw['email'].'\'">'.$rw['truename'].'</li>';
}
echo '</ul>';
echo '</div></div>';
?>
```
But when I try to run it, it produces this error:
```
Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/pieter/public_html/jouw_llr/includes/leden.php on line 10
```
When I remove the 'order by' part, the error goes away... But I need the ordering.
If it's useful, the 'order' column is key, auto-increment and INT...

How can I solve this?
Thanks in advance,
pieter.

---

### Post by supirman on 2007-02-02
Hi,
  order is a reserved word, so it must be in backticks to be used at a table/field/etc.

$r = mysql_query("SELECT email,truename FROM users ORDER BY [COLOR="Red"]**`**[/COLOR]order[COLOR="Red"]**`**[/COLOR] ASC");

---

### Post by Ubuntuud on 2007-02-03
Oh... ok, thanks!

---

