---
title: "Javascript-Check if a string has fullstop"
date: 2010-03-19
forum: Programming Talk
---

### Post by hakermania on 2010-03-19
Hi, this doesn't work:
```
 <script type="text/javascript">
function givemail()
{
r=prompt("Give me your e-mail address please:");
if (r.length < 4)
{
document.write("Small Address!");
}
else if (r.match("@") != "@")
{
document.write("@ not found!");
}
else if (r.match(".") != ".")
{
document.write("There is no fullstop!!!");
}
else
{
document.write("Check the inbox at your email address: " + r);
}
}
</script>
```
The @ check works fine but even if the mail address has a fullstop the result is
```
document.write("There is no fullstop!!!");
```
Any help on how to tell the program for the fullstop?

---

### Post by soltanis on 2010-03-19
The function you are using matches regular expressions, not strings. In RegExp parlance the "." character matches any non-newline character, which means it matches the first character in your string more likely than not.

EDIT:
See below for correct ways of doing things.

---

### Post by Compyx on 2010-03-19
Email addresses rather complex little critters, here's a regular expression in Perl to validate an e-mail address:
[http://www.ex-parrot.com/pdw/Mail-RFC822-Address.html]("http://www.ex-parrot.com/pdw/Mail-RFC822-Address.html")

If I just wanted to check if a string had a full stop in it, I'd do something like:
```

if (s.indexOf('.') >= 0) {
    // found full stop
}

```
a regex is a bit overkill for such a task.

---

### Post by hakermania on 2010-03-19
> **soltanis said:**
> The function you are using matches regular expressions, not strings. In RegExp parlance the "." character matches any non-newline character, which means it matches the first character in your string more likely than not.

Instead to match a literal . you should escape the metacharacter to tell the parser you mean the literal character.

```

r.match("\.")

```If you are trying to match an email address (it looks like you are?) you can combine the whole thing into a more complex regular expression:

```

r.match("[a-zA-Z0-9._]@\w\.\w")

```My regular expressions are rusty from too much Python so a Perl hacker can probably jump in and improve/fix this.
Ok thank you. I am not afraid of hacker attacks because in the site I am currently building there is no credit card numbers or something like that.It's just a unix scripting tutorial on Greek :P

---

### Post by Hellkeepa on 2010-03-19
HELLo!

Missing a + after the closing square bracket and the two word character matches, to make it match more than just one character. Other than that, you're also missing the ^ and $ anchors, to make sure it matches the entire string. 

For a more complete check, I recommend having a look at the RegExp in my "val_Email ()" function: [http://norskwebforum.no/pastebin/7609](http://norskwebforum.no/pastebin/7609)

Happy codin'!

---

### Post by roccivic on 2010-03-19
Validation of email addresses must be done on the server-side! If you already have that implemented and just want to save yourself some unnecessary traffic, then fair enough.

Here's a proper way for validating email addresses (in PHP, but should be easy enough to port to JS):

[PHP]<?php
/*

Taken from: http://www.linuxjournal.com/article/9585

Validate an email address.
Provide email address (raw input)
Returns true if the email address has the email 
address format and the domain exists.
*/

function validEmail($email) {

	// list of domains that are not allowed
	$banlist = array(	"placella.com",
				"ratethatpage.com" );

	$isValid = true;
	$atIndex = strrpos($email, "@");
	if (is_bool($atIndex) && !$atIndex) {
		$isValid = false;
	}
	else {
		$domain = substr($email, $atIndex+1);
		$local = substr($email, 0, $atIndex);
		$localLen = strlen($local);
		$domainLen = strlen($domain);
		if ( in_array($domain, $banlist) ) {
			// banned domain
			$isValid = false;
		}
		else if ($localLen < 1 || $localLen > 64) {
			// local part length exceeded
			$isValid = false;
		}
		else if ($domainLen < 1 || $domainLen > 255) {
			// domain part length exceeded
			$isValid = false;
		}
		else if ($local[0] == '.' || $local[$localLen-1] == '.') {
			// local part starts or ends with '.'
			$isValid = false;
		}
		else if ($domain[$domainLen-1] == '.') {
			// domain part ends with '.'
			$isValid = false;
		}
		else if (preg_match('/\\.\\./', $local)) {
			// local part has two consecutive dots
			$isValid = false;
		}
		else if (!preg_match('/^[A-Za-z0-9\\-\\.]+$/', $domain)) {
			// character not valid in domain part
			$isValid = false;
		}
		else if (!preg_match('/\\./', $domain)) {
			// domain has no dots
			$isValid = false;
		}
		else if (preg_match('/\\.\\./', $domain)) {
			// domain part has two consecutive dots
			$isValid = false;
		}
		else if (!preg_match('/^(\\\\.|[A-Za-z0-9!#%&`_=\\/$\'*+?^{}|~.-])+$/', str_replace("\\\\","",$local))) {
			// character not valid in local part unless 
			// local part is quoted
			if (!preg_match('/^"(\\\\"|[^"])+"$/', str_replace("\\\\","",$local))) {
				$isValid = false;
			}
		}
/*		if ($isValid && !(checkdnsrr($domain,"MX") || checkdnsrr($domain,"A"))) {
			// domain not found in DNS
			$isValid = false;
		}*/
	}
	return $isValid;
}
?>[/PHP]

---

### Post by hakermania on 2010-03-19
Guys............:(
```
  <script type="text/javascript">
function givemail()
{
r=prompt("Give me your e-mail address please:");
if (r.length < 4)
{
document.write("Small address.");
}
else if (r.match("@") != "@")
{
document.write("NO @");
}
else if (r.match("\.") != ".")
{
document.write("No fullstop");
}
else
{
document.write("Check inbox of " + r);
}
}
</script>
```
Still No fullstop message  :'(

---

### Post by roccivic on 2010-03-19
match takes a RegExp as it's argument. You'll have do something along the lines of:

```
foo = new RegExp(pattern, modifiers);
r.match(foo);
```

 See here: [http://www.w3schools.com/jsref/jsref_match.asp](http://www.w3schools.com/jsref/jsref_match.asp)

---

### Post by myrtle1908 on 2010-03-19
> **hakermania said:**
> Guys............:(
Still No fullstop message  :'(

```
	  var s = prompt('Enter some text');
	  if (/\./g.test(s)) {
		  alert('Fullstop found.');
	  } else {
		  alert('No fullstop.');
	  }
```

---

### Post by soltanis on 2010-03-20
Or use the indexOf trick.

Sorry, it has been a long time since I have used either JS or Perl regular expressions. Too much Python/C in me.

---

