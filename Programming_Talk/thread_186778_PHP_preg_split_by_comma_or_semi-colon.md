---
title: "PHP preg_split by comma or semi-colon?"
date: 2006-06-02
forum: Programming Talk
---

### Post by hagen00 on 2006-06-02
Hi there

I'm trying to split up a string by either a comma or semi-colon. Currently I'm doing it like this..

[PHP]$str = "mail@example.com, mail1@example.com; mail2@example.com;mail3@example.com";

$mails = preg_split("/;/", $str);

foreach ($mails as $mail){
	
	$temp_mail =  preg_split("/,/", $mail);
	if($temp_mail){
		foreach ($temp_mail as $temp_m){
			echo $temp_m . "<br>";	
		} 
	} else {
		echo $mail;	
	}
}[/PHP]
Not elegant. Is there any way to tell preg_split to split by comma OR semi-colon all in one go?

Thanks

H

---

### Post by hagen00 on 2006-06-02
Nevermind...

One solution is to just replace the ; with a comma using str_replace and then using explode. Easy enough.

---

### Post by Corvillus on 2006-06-02
You could also use the or regex operator (|). So your function call would look like
[php]$split_arr = preg_split('/;|,/', $str);[/php]

---

### Post by hagen00 on 2006-06-03
> **Corvillus]You could also use the or regex operator (|). So your function call would look like
[php]$split_arr = preg_split('/ said:**
> 

Thanks. But that doesn't work when I try it...

---

### Post by another_dave_b on 2006-06-06
Example 1 "Get the parts of a search string" from [the PHP manual]("http://uk.php.net/preg_split") uses a regex group.

For your example, that would suggest 

[PHP]preg_split("/[;,]+/", $strng);[/PHP]

---

