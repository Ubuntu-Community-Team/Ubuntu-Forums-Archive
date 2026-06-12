---
title: "Apache - Request Method - PHP"
date: 2009-01-25
forum: Programming Talk
---

### Post by moeFinley on 2009-01-25
I'm editing some PHP scripts and running them on Apache.  The scripts check the server's Request Method before starting.  It's been a long time since I've written any PHP and I know very little about Apache so I'm hoping somebody can answer what I'm sure are very simple questions.

Can I set the Request Method to GET or POST within Apache?
What is the reason for this, why can't the server accept both?
Is this something I need to configure in PHP?

Thanks for any help

---

### Post by Reiger on 2009-01-25
Check the section covering the $_SERVER superglobal in the PHP manual, here: [http://nl3.php.net/reserved.variables.server](http://nl3.php.net/reserved.variables.server)

---

### Post by DocForbin on 2009-01-25
That's not something you set in apache. All web servers support GET and POST, it's  part of the HTTP specification.

In PHP, you can use $_REQUEST to handle both $_GET and $_POST (and $_COOKIE) variables if you really need too.

---

### Post by moeFinley on 2009-01-25
Why would a script want to check $_SERVER['REQUEST_METHOD'] == 'POST' before running if nothing has been submitted to it?  Do you have to submit anything to a page to make it POST?

---

### Post by Reiger on 2009-01-25
No. But consider for instance the scenario of a search engine (a modern one, like Google):
(*) The client may supply search keys by means of GET (the default as it'll allow for bookmarking the search on the client side by simply book marking the URL, it will contain an appended Query string)
(*) The client may supply searchkeys by means of POST and then there won't be a Query string appended to the URL so the URL/search can't be bookmarked on the client side, but it is more 'private'. (I would not be surprised if the 'private' search methods of some browsers were in fact ordinary use-POST searches)

So if you were writing a search engine, how would you know where to look for your search keys? Well, inspect the HTTP Request method header... ;)

---

### Post by DocForbin on 2009-01-25
> **moeFinley said:**
> Why would a script want to check $_SERVER['REQUEST_METHOD'] == 'POST' before running if nothing has been submitted to it? 
Without knowing more we can only guess. Maybe because its purpose is only to handle form processing. Often you'll see html/whatever pages with forms that submit to a PHP script.

> Do you have to submit anything to a page to make it POST?
Yes, a HTTP POST.

---

### Post by Tibuda on 2009-01-25
> **moeFinley said:**
> Why would a script want to check $_SERVER['REQUEST_METHOD'] == 'POST' before running if nothing has been submitted to it?All my PHP forms are constructed this way:[PHP]<?php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
  // validates data
  // update database and redirect if data is valid
} ?>
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post">
<!-- form elements here -->
</form>[/PHP]> **moeFinley said:**
> Do you have to submit anything to a page to make it POST?You don't have to submit a form, you can "POST" something using AJAX requests, but no standard links.

---

### Post by moeFinley on 2009-01-25
Thanks for all the help guys

---

