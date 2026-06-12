---
title: "Registration form mysql error"
date: 2010-03-31
forum: Programming Talk
---

### Post by Maikovich on 2010-03-31
Hello,

How will I put some strings with numbers together?

I want to get something like this:

1993-7-24

If I have the strings 1993 07 and 24, like this:

[php]
$day = 24;
$month = 7;
$year = 1993;
[/php]

How do I put those string together in order to get 1993-7-24 ???


Thanks!

---

### Post by Hellkeepa on 2010-03-31
HELLo!

What error does it give?

Happy codin'!

---

### Post by Maikovich on 2010-03-31
> **Hellkeepa said:**
> HELLo!

What error does it give?

Happy codin'!

It was solved, but have another question now :-)

---

### Post by new_tolinux on 2010-03-31
Assuming that your new question is above:

[php]print $year."-".$month."-".$day;[/php]Should do the "trick" to print it.

You can however replace the "print " statement by a "$var=" statement, which will result in var $var being filled with the date.

---

### Post by Maikovich on 2010-03-31
Weird, if I try this it only puts the $mybirthyear in my table list (of the $mybday).

[PHP]$mybday = $mybirthyear."-".$mybirthmonth."-".$mybirthday;
            
            if($curnum == 0) {
                mysql_query("INSERT INTO users VALUES(`id`,'".$myusername."','".$mypassword."','".$myemailadress."','".$mygender."',`regdate`,'".$mybday."')") or die("<tr><td>$curnum. Er ging iets mis! Probeer het later opnieuw.</td></tr>");
            }[/PHP]

---

### Post by new_tolinux on 2010-03-31
> **Maikovich said:**
> Weird, if I try this it only puts the $mybirthyear in my table list (of the $mybday).

[PHP]$mybday = $mybirthyear."-".$mybirthmonth."-".$mybirthday;
            
            if($curnum == 0) {
                mysql_query("INSERT INTO users VALUES(`id`,'".$myusername."','".$mypassword."','".$myemailadress."','".$mygender."',`regdate`,'".$mybday."')") or die("<tr><td>$curnum. Er ging iets mis! Probeer het later opnieuw.</td></tr>");
            }[/PHP]
That is not correct.

I'm going to respond in Dutch, since that's more easy for me. If you have trouble understanding, please let me know and I'll try to translate it.

Je gebruikt de ` voor tabellen en veldnamen. Voorbeeld: INSERT INTO `users`
Je gebruikt de ' (onder de ") voor waarden.
Wat jij doet kan dus niet. Correct zou zijn:
```

$query="INSERT INTO `users` (`id`, `username`, `password`, `email`, `gender`) VALUES (NULL, '".$myusername."', '".$mypassword."', '".$myemailadress."', '".$mygender."');";
$result=mysql_query($query) OR die ("<tr><td>$curnum. Er ging iets mis! Probeer het later  opnieuw.</td></tr>");

```Je kunt eventueel ook "id" en de daarbij horende NULL weglaten, als id een auto-incremented-veld is.

Overigens weet ik niet of je wel wilt toevoegen, of dat je een bestaande user wilt wijzigen. In dat geval zou dit de juiste query zijn:
```

UPDATE `users` SET `username` = '".$myusername."', `password` = '".$mypassword."' WHERE `id` = '".$userid."' LIMIT 1;";

```

---

### Post by HellBoz on 2010-03-31
By the first and maybe the least, semicolin at the end of your query is a syntax error - get rid of it before continuing.

** Dutch isn't acceptable in public forums ..

---

