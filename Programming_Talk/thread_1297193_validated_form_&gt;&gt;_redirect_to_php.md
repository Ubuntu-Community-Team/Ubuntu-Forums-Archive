---
title: "validated form &gt;&gt; redirect to php"
date: 2009-10-21
forum: Programming Talk
---

### Post by esteeven on 2009-10-21
I have an html form which contains this action :

<form action="<?=$_SERVER['PHP_SELF']?>" method="post">

The validation I have set up works (finally!!) using -

// import the validation library
require("validation.php");

Now that the form works, I would like to email the contents. Originally, before I started to validate the form, the form was processed by regform.php.

<form action="regform.php" method="post">

I tried -

// no errors! redirect the user to the thankyou page (or whatever)

else

{

//$message = "All fields have been validated successfully!";



// here you would either email the form contents to someone or store it in a database.

// To redirect to a "thankyou" page, you'd just do this:

header("Location: regform.php");

}

}

This worked ----- up to a point An email was sent but no data was included : just the field names.
__________________

I see from some examples I have found that the following is possible -

// no errors! redirect the user to the thankyou page (or whatever)
else
{
$message = "All fields have been validated successfully!";

// here you would either email the form contents to someone or store it in a database.
// To redirect to a "thankyou" page, you'd just do this:
// header("Location: thanks.php");
}

I have tried to use my regform.php to process the data post validation but I can't make it work. Am I on the right road?

Thanks

---

### Post by CyberJack on 2009-10-22
If I read this right your regform.php does not process the data which was send by your form.
If so the problem is year header redirect.
When redirecting to a page no data ($_POST, $_GET) is passed.

Look at your validation part of the code.
To perform validation you require the validation.php.
The code in the validation file can access the post data because they are executed within the same run.

The same needs to be done with regform.php before it can read the post variable.

---

### Post by v8YKxgHe on 2009-10-22
Your post doesn't make much sense (to me) at all. However I can spot a few mistakes in your code.

Firstly, <?=$_SERVER['PHP_SELF']?> - 2 things wrong: don't use <?=, use <?php echo - yes it is longer, and it will also always work, <?= wont. Next, don't ever use $_SERVER['PHP_SELF'] like that, since you're open to XSS attacks, if you want the form to submit to its self simply give it a blank action (which is perfectly valid) or construct the URL your self.

Then you're using header() to set the 'Location' header, however you're giving it a relative URL. The HTTP specification clearly states a full URI is required e.g. [http://example.org/foo](http://example.org/foo).

Granted none of these have any relation to your issue, but this are things you should take note of. If you can make you're initial post make sense, then I can help.

---

### Post by NoaHall on 2009-10-22
Or use```
 if (isset($_POST['submit'])) 
```

Anyway, you're missing a HUGE bit of code if you want us to help. We need to see the full form and php code.

---

