---
title: "Email Contact Form"
date: 2006-01-26
forum: Programming Talk
---

### Post by herrpoon on 2006-01-26
Hi, I'm trying to set up an email contact form on my "website" so that people can contact me without my address getting added to some spam database or something.  Having googled around I've got the basics, i.e. the form, how to send it etc. but am beginning to get a bit stuck.  This is what I've got so far:

[HTML]
<form action="process.php" method="post">

Name: <input type="text" name="name" size="20" maxlength="20" /><br />

Email: <input type="text" name="email" size="30" maxlength="30" /><br />

Subject: <input type="text" name="subject" size="30" maxlength="30" /><br />

Text:<textarea name="text" name="text" cols="50" rows="10"></textarea><br />

<input type="submit" name="submit" value="Send" />

</form>
[/HTML]

So that's all fine and dandy and I've got the process.php here:

[PHP]<?php
@extract($_POST);
$name = stripslashes($name);
$email = stripslashes($email);
$subject = stripslashes($subject);
$text = stripslashes($text);
mail('myemailaddresshere',$subject,$text,"From: $name <$email>");
header("location:form.php");
?>
[/PHP]

But what I want to do is add two more categories to the form.html, e.g.,

[HTML]Business: <input type="text" name="business" size="30" maxlength="30" /><br />

Attention:<br />
<select name="attn" size="1">
<option value=" Sales ">Sales n Billing </option>
<option value=" General Support ">General Support </option>
<option value=" Technical Support ">Technical Support </option>
<option value=" Webmaster ">Webmaster </option>
</select> <br />[/HTML]

and have the results, i.e. Business = whatever
                                   Attention = Sales etc. etc.
in the body of the email along with the message.  As I said, I've tried googling it but I can't come up with anything that actaully works.  Thanks for any help, I'm really at a dead end here :(

---

### Post by MJN on 2006-01-26
Whilst not answering your specific question per se (as I'm no PHP expert) you might be interested in implementing the free PHP-based feedback form from [http://www.thesitewizard.com/wizards/feedbackform.shtml]("http://www.thesitewizard.com/wizards/feedbackform.shtml")

I've used it on my site for the very same reason you want - this can be seen at [http://www.newtonnet.co.uk/contact/]("http://www.newtonnet.co.uk/contact/") (although there's no surprises as to how a feedback form looks! ;)).

Mathew

EDIT: Oops - just noticed you've got a 'standard' form working (like mine) but now wish to add to it... I don't know if the SiteWizard one will do this (haven't checked) so it may not be of any use whatsoever. Still, I'll keep the post just in case it does..

---

### Post by newtonfn on 2006-01-26
humm. you can write something like:

<?php
@extract($_POST);
$name = stripslashes($name);
$email = stripslashes($email);
$subject = stripslashes($subject);
$text = stripslashes($text);

$text = $text . "\nBusiness: " . stripslashes($business);
$text = $text . "\nAttention: " . stripslashes($attn);

mail('myemailaddresshere',$subject,$text,"From: $name <$email>");
header("location:form.php");
?> 

It's is neither a pretty nor secure code, but will do the job.
All I am doing is adding to the end of $text variable (which contains the mail's body), the value comming from de new fields.

I am not sure if PHP will translate the "\n" into  line breaks as I want.... but that's the general idea.
Good luck

---

### Post by herrpoon on 2006-01-26
Thanks for both your posts, I'll give the feedback form a go, although I'd quite like to be able to modify it as and when I need (even though I may not be capable of that just yet ;)).

The extra lines of code suggested by newtonfn worked a treat, like you say it needs "tidying up" but it will be good enough for now, until I start leaning php proper!

Again, many thanks for your help guys, much appreciated :p

---

