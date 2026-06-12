---
title: "need a little php help"
date: 2005-12-23
forum: Programming Talk
---

### Post by Zelut on 2005-12-23
I'm a beginner with php but I'm trying my hand at a basic php/mysql address book app.  I've got the basics down (creating table, connection to db, etc) but in my file to create new listings (ie; write results to the db) I'm having issues.

If anyone has some time and is willing to look at my code I'd appreciate it.  I really want to get more into programming & development but I'm getting stuck.

Cheers
Kuyaedz

---

### Post by sapo on 2005-12-23
If you post what errors and what issues you are getting it would be easier to help you.

Btw, the first thing i saw in your code is that you dont validate and you dont check the post data, dont do it, and dont ever turn register_globals on, get used to doing it in ALL you code:

[php]if(empty($_POST['firstname'])) {
  $error .= "Please fill the first name field";
} else {
  $firstname = addslashes($_POST['firstname']);
}

if(!$error) {
  // DB STUFF HERE
} else {
  // Go back to the form
}[/php]

Cause if i fill up a double quote or a single quote in the form field i ll break you your db query, and thats not good :D

but thats just a tip, so post the errors so we can help you out, cause is kinda difficult to find error just looking at the code ;)

---

### Post by Gandalf on 2005-12-23
I think it's failing because you aren't filtering the post data so do a
```

$variable = addslashes(htmlspecialchars($varaible))

``` before submitting it to the DB and as sapo said do not ever submit data to db without verifying/filtering it cause as also he said a quoted data might break ur mysql query or worse be a security hole to your system

---

### Post by sapo on 2005-12-23
[QUOTE=Gandalf]I think it's failing because you aren't filtering the post data so do a
```

$variable = addslashes(htmlspecialchars($varaible))

``` before submitting it to the DB and as sapo said do not ever submit data to db without verifying/filtering it cause as also he said a quoted data might break ur mysql query or worse be a security hole to your system[/QUOTE]
In this case, you can use:

[php]$string = strip_tags($string, '<a><b><i><u>');[/php]

strip_tags will strip the html tags that isnt in the alow list, in this case i m alowing users to use <a><b><i><u>, but you can remove them and dont alow html tags at all.

Here is a good reading:

[http://www.sitepoint.com/article/php-security-blunders](http://www.sitepoint.com/article/php-security-blunders)

---

### Post by Gandalf on 2005-12-23
htmlspecialchars is not as you are refering, it will convert unusual characters to html codes, like the "&#233;" character for example it's kinda like addslashes
it has nothing to do with strip_tags here

---

### Post by sapo on 2005-12-23
hm, sorry, i misunderstood, never used htmlspecial chars, i ll read more about it.

---

### Post by Zelut on 2005-12-23
Well part of my problem here is that I don't get any errors.  I suppose I don't have any error-reporting code in there (new to that as well)..  I fill out the form, click submit & the screen just refreshes with no input to the database.

Does anything in my $result = are look funny that would cause it to not actually complete anything?

---

### Post by sapo on 2005-12-23
[QUOTE=kuyaedz]Well part of my problem here is that I don't get any errors.  I suppose I don't have any error-reporting code in there (new to that as well)..  I fill out the form, click submit & the screen just refreshes with no input to the database.

Does anything in my $result = are look funny that would cause it to not actually complete anything?[/QUOTE]
take a look at /etc/apache2/logs/error_log

Your errors should be there, or just put:

error_reporting(E_ALL);

ni the beginning of your code.

---

