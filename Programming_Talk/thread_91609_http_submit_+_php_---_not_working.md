---
title: "http submit + php --- not working"
date: 2005-11-17
forum: Programming Talk
---

### Post by Lapeth on 2005-11-17
Hello there.

This problem is not necessarily connected to ubuntu, rather to php and/or apache2.
I'm developing a site in php, with everything in one file, and the user then progresses by "submitting" a form which gives php information on how to redraw the page. Like this:

<?
switch ($currentStep) {
case 1:
do something
case 2:
do something else
}
?>
<input name="currentStep" type="hidden" value="">
<input type="submit" value="Next" onClick="currentStep.value='<? echo $currentStep+1; ?>'">

This may seem like a peculiar way to do it, but it's perfect for the needed application, and works just great on my university webserver.
However, on my local machine, the page stays the same, ie. clicking the submit button reloads the page, keeping $currentStep at 1.

The code has been proven to work on another webserver, so I'm pretty sure it's my own newly installed webserver, running with Apache2 and PHP4.

The problem is rather urgent, as we're on a deadline here.

If you're interested in seeing the code, it is [here]("http://www.control.auc.dk/~lpth03/userGUI/userGUI.tar.gz"), and the processed output [here]("http://www.control.auc.dk/~lpth03/userGUI/index.php").

---

### Post by jaddison on 2005-11-17
> **Lapeth]Hello there.

This problem is not necessarily connected to ubuntu, rather to php and/or apache2.
I'm developing a site in php, with everything in one file, and the user then progresses by "submitting" a form which gives php information on how to redraw the page. Like this:

<?
switch ($currentStep) {
case 1:
do something
case 2:
do something else
}
?>
<input name="currentStep" type="hidden" value="">
<input type="submit" value="Next" onClick="currentStep.value='<? echo $currentStep+1 said:**
> here[/URL], and the processed output [here]("http://www.control.auc.dk/~lpth03/userGUI/index.php").

At first glance, in your **checkVars.php** file, you have the following code segment:
```

if (!$currentStep) {
 $currentStep=1;
}

```

Every time this page is run, it will set **$currentStep** to 1, because **$currentStep** won't persist across page loads.  You'd need to get the value of the 'currentStep' (or 'lastStep') form value upon the PHP page load. (using $_POST("currentStep"); ) or something like that.

I could have completely misread your code as well... I hope I didn't though!

Good luck, and I hope this helps,

---

### Post by Ahriman on 2005-11-17
On your other server, you most likely have REGISTER_GLOBALS turned on, which isn't very safe. AFAIK, it's turned off be default in current versions of PHP. You will either have to enable it (via the php.ini file), which I wouldn't recommend. The easiest way is to, like jaddison said, check for $_POST['currentStep'] or $_GET['currentStep']. Like:

[PHP]if(!$_POST['currentStep'])
{
$currentStep=1;
} else {
$currentStep = $_POST['currentStep'];
}[/PHP]

hth

---

### Post by Lapeth on 2005-11-18
You are completely right. I tried your solution, and it works. I guess the old code just works because it is processed by an old version of php (the server guys are a bit behind when it comes to updating software). Thanks a lot for that one.

However, it still doesn't behave like it's supposed to, but it's better now. It was supposed to "remember" the settings that the user specifies throughout the session, but I'll just look into that myself. Thanks again.

Edit: Got it all working now. No further worries.

---

### Post by DJ_Max on 2005-11-19
[QUOTE=Lapeth]You are completely right. I tried your solution, and it works. I guess the old code just works because it is processed by an old version of php (the server guys are a bit behind when it comes to updating software). [/QUOTE]
No, it was due to the settings Ahriman pointed out. Your old server had register globals on! You need to pay close attention to this.

---

### Post by Corvillus on 2005-11-22
To remember variables througout a session in newer versions of PHP you dump them into the $_SESSION array. You can read more about that here [http://ca3.php.net/manual/en/ref.session.php](http://ca3.php.net/manual/en/ref.session.php)

---

