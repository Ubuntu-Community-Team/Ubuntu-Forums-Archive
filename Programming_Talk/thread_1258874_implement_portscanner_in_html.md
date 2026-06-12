---
title: "implement portscanner in html"
date: 2009-09-05
forum: Programming Talk
---

### Post by Adina on 2009-09-05
Hi, I have put up a "what is my ip?" function on my website with this:

[PHP]<?php echo $_SERVER['REMOTE_ADDR']; ?>[/PHP]

But I also want to implement a portscanner on the website so people can check if they have any open ports on their systems.  I have seen several sites that have this function. I just don't know how to do this. Do I have to make a script to start nmap on the server and take the variabel from the php script above? If anyone have Any suggestions on how to do this I would really appreciate it.

---

### Post by Petertje on 2009-09-05
Here's a piece of code that you can use ;). Note that your title is wrong, you're not implementing it in HTML but in PHP. HTML is not able to perform this kind of work ;)

```

<?php
$ports = array(21,22,23,25,80);

for($count = 0; $count < sizeof($ports); ++$count) {
$open = @fsockopen($_SERVER['REMOTE_ADDR'], $ports[$count], $errno, $errstr, 10);

if($open) {
echo "Port ".$ports[$count]." is open!<br />\n";
} else {
echo "Port ".$ports[$count]." is closed!<br />\n";
}
}
?>

```

you only have to add ports in the array ;)

---

### Post by hessiess on 2009-09-06
> **Petertje said:**
> Here's a piece of code that you can use ;). Note that your title is wrong, you're not implementing it in HTML but in PHP. HTML is not able to perform this kind of work ;)

```

<?php
$ports = array(21,22,23,25,80);

for($count = 0; $count < sizeof($ports); ++$count) {
$open = @fsockopen($_SERVER['REMOTE_ADDR'], $ports[$count], $errno, $errstr, 10);

if($open) {
echo "Port ".$ports[$count]." is open!<br />\n";
} else {
echo "Port ".$ports[$count]." is closed!<br />\n";
}
}
?>

```

you only have to add ports in the array ;)

It would be easier to just call nmap with exec().

---

### Post by -grubby on 2009-09-06
> **hessiess said:**
> It would be easier to just call nmap with exec().

It would also be non-portable.

---

### Post by Petertje on 2009-09-06
It is not only non-portable but it is also easier to make a wrong implementation and make the system vulnerable with exec() function - or any other function in that family!. Another issue with that is that the webhost has probably (atleast should have) php safe mode on, which disables all these functions, and more. 
You'd need a VPS or better so you can change the php ini and enable this feature, and of course install nmap.

---

### Post by Adina on 2009-09-06
Thank you very much for your replies, especially Petertje for the script: much RESPECT! :D It gave me a good start on how to do this. I am trying to acomplish that the user enter the number of the port to scan and then hit a button to start the scan. I think I can do this my self, but it might take me a little while (I'm not a programmer). I really appreciate all your help. Ubuntu forums is the best! :D

---

### Post by Petertje on 2009-09-09
you're welcome, and if you need any help - post in this thread :). will keep a eye on it to see if you need any help ;)

---

