---
title: "PHP 5: \n does not generate newline"
date: 2010-02-13
forum: Programming Talk
---

### Post by boococp on 2010-02-13
Running PHP5 on Ubuntu 9.10

The following code:

<?php
$v="Test line";
$i=1;
while ($i <=10) {
    printf ("%s\n", $v);
    $i++;
}
?>

generates the following output in Firefox:

Test line Test line Test line Test line Test line Test line Test line Test line Test line Test line 

Can someone tell me why \n is not generating newlines?

---

### Post by MadCow108 on 2010-02-13
if your using php for a webpage: newlines on websites (html) are written as <br/>
else: ignore this post

---

### Post by Reiger on 2010-02-13
In order to get line breaks, use the PHP_EOL constant. This is the "platform independent" end-of-line character/string.

---

### Post by miklcct on 2010-02-14
Have you set your Content-Type correctly (it should be text/plain)?

---

### Post by Hellkeepa on 2010-02-16
HELLo!

Unless a web browser is told otherwise, as noted above by **miklcct**, it'll assume that it is a web page. Thus it ignores the newlines, and treats them as a single space instead (as per the standard).

Happy codin'!

---

