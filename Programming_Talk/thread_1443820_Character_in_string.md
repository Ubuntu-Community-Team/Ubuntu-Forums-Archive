---
title: "Character in string"
date: 2010-03-31
forum: Programming Talk
---

### Post by Maikovich on 2010-03-31
Can you check whether there's a character in a string?

Like:

$str = "haha@hotmail.com";

Can you check with php if theres a @ sign and a dot sign in the string??

---

### Post by Zugzwang on 2010-03-31
Sure you can.

Have a look at the documentation of PHP, section "String Functions": [http://www.php.net/manual/en/ref.strings.php](http://www.php.net/manual/en/ref.strings.php) - The function "strpos" looks promising in this context.

---

### Post by hessiess on 2010-03-31
You can use a regular expression for that.

[http://www.totallyphp.co.uk/code/validate_an_email_address_using_regular_expressions.htm](http://www.totallyphp.co.uk/code/validate_an_email_address_using_regular_expressions.htm)

---

### Post by Bachstelze on 2010-03-31
> **hessiess said:**
> You can use a regular expression for that.

[http://www.totallyphp.co.uk/code/validate_an_email_address_using_regular_expressions.htm](http://www.totallyphp.co.uk/code/validate_an_email_address_using_regular_expressions.htm)

You can, but it's a bad idea. strpos() is the right way to do this.

---

### Post by Hellkeepa on 2010-03-31
HELLo!

That depends upon what the OP wants to do, if he wants to validate an e-mail address then RegExps are the way to go. If he just wants to check for the occourance of a character in a string, "strpos ()" is the way to go.

Happy codin'!

---

