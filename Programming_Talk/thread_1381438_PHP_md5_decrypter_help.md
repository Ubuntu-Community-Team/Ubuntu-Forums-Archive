---
title: "PHP md5 decrypter help"
date: 2010-01-14
forum: Programming Talk
---

### Post by lolzwut on 2010-01-14
Hi,


I'm trying to make a MD5 dictionary hash cracker. Everything works fine except for the part where it compares the MD5 hash to the words in the text file, it does open the file I know because if you print $s it prints out the contents. Here is my code:


[PHP]<form action="<?php $_SERVER['PHP_SELF']; ?>" method="post">
<br />
<h1>MD5 Dictionary Cracker</h1>
<fieldset>
<legend>MD5 Cracker</legend>
<label for="crack">Encryption to crack</label>
<input type="text" name="md5" />
<input type="submit" name="submit3" value="Try to crack" />

<?php
if (isset($_POST['submit3'])) {

set_time_limit(0);

$file = 'dictionary.txt';
$md5 = $_POST['md5'];

if (strlen($md5) == 32) {
echo 'Attempting to crack: <b>' . $md5 . '</b>...';

$open = fopen($file, 'r');

while (!feof($open)) {

$s = fgets($open, 256);


if (md5($s) == $md5) {
echo 'SUCCESS!, the plaintext of: <b>' . $md5 . '</b> is: <b>' . $s . '</b>'; 
}
}
}
else {
echo 'This is not a valid md5 hash';
}
}

?>


</fieldset>
</form>
</body>
</html>[/PHP]

It just says "Trying: **1a79a4d60de6718e8e5b326e338ae533**" (which is "example in plaintext) then it stops loading and just does nothing. Can someone tell me what's wrong please? Thanks. Also in case it wasn't already obvious, the word example is in my wordlist.

---

### Post by Hellkeepa on 2010-01-15
HELLo!

I've cleaned up the code a bit for you, and added a couple of comments about security issues you should fix up in: [http://pastebin.com/f6bbcc11](http://pastebin.com/f6bbcc11)
You'll also noted I removed the output of "PHP_SELF" from it, due to it being possible to abuse for XSS attacks, unless you've protected yourself from it. You'll find a (Norwegian) post I did about this a couple of years ago on [Norsk Webforum](http://norskwebforum.no/viewtopic.php?f=18&t=31699). It contains a link to the original (English) article, as well as a piece of code that'll protect against this vulnerability.

For your issue, I refer to the PHP-manual on [fgets ()](http://no2.php.net/fgets):
> ...on a newline (which is included in the return value)...

Also, you would want to break out of the loop after printing the success message, no point in testing the rest of the dictionary if you've got a confirmed collision, now is there? ;-)

PS: It's not a decrypter, it's a collision detector. It's a vital difference, even if it might seem just a detail.

Happy codin'!

---

### Post by lolzwut on 2010-01-15
Thanks for the security advice, I also checked into that article you referred me to.


I still don't understand what I'm doing wrong though, I looked at the manual but it isn't a problem with fgets because I tried printing $s and it printed every line out.

---

### Post by Hellkeepa on 2010-01-15
HELLo!

The reason is highlighted in the quote I posted. Try a "var_dump ()" on the first line, and have a look at the source code, if you still don't see it.

Happy codin'!

---

### Post by lolzwut on 2010-01-15
Try a var_dump() on what variable? And that quote doesn't make any sense and in the manual it still doesn't provide anything useful. Can't you just tell me what part of the code I need to change?

---

### Post by Hellkeepa on 2010-01-15
HELLo!

"The first line" was referring to the first line of content fetched by the "fgets ()" function, in other words the "$s" variable.

As for telling you what to change: Yes, I could do that. However, with such a basic problem like this, when you have a small, but very important, detail which is causing the issue that won't help you in the long run. You need to be able to catch things like this for yourself, otherwise you'd be constantly haunted and frustrated by minor issues already explained in the manual.

Happy codin'!

---

### Post by lolzwut on 2010-01-16
I figured it out. It was the trailing newline at the end, I used chop() to fix it. I feel like an idiot for not noticing that even when you quoted it from the manual lol. I'm sorry for wasting your time, thanks for all the help

---

### Post by Hellkeepa on 2010-01-16
HELLo!

Hehe, you're welcome, and no worries. I'd venture a guess you'll remember this particular details for a long time to come, now. ;-)

Happy codin'!

---

