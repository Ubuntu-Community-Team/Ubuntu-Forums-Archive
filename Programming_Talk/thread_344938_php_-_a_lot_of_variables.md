---
title: "php - a lot of variables"
date: 2007-01-23
forum: Programming Talk
---

### Post by tocleora on 2007-01-23
I'm going to be redesigning a process that is multiple pages of a form to fill out to sign up a customer, I will need to pass a lot of variables (40+) between each page.  Storing them in a db is not an option at this stage as there are a lot of people who will be using this form (100+ pretty much constantly 12 hours a day) and mysql just slows down to a crawl if too many of them try to save to that db at one time (some have reported having to wait up to 7 minutes between pages).  So I'm opting to just pass the variables between the pages and just save at the end to the db.  How's the best way to do this?  I know you can do arrays like:

```
<input type="hidden' name="customer[]" value="first name">
```

I thought if I stored all the variables in an array it would be easier, but ultimately this would be better:

```
<input type="hidden" name="customer['first_name']" value="first name">
```

Then at the top of each page I could just reference all parts of the customer array, like in a foreach.  I haven't tried this yet so I don't know if it will work... Any thoughts or suggestions of the best way to pass these variables?  Or does someone think maybe it's misconfigured?  I'm open to anything that will speed up this process...

---

### Post by bvanaerde on 2007-01-23
A better solution would be by using session variables.

For example:
[PHP]$_SESSION["formvariables"] = array(
"name1" => "value1",
"name2" => "value2",
"name3" => "value3"
);[/PHP]
They will be remembered as long as you don't close the window.

---

### Post by Dygear on 2007-01-24
[session_start](http://www.php.net/function.session-start)();

---

### Post by tocleora on 2007-01-24
Ok, so are you saying the variable would then be like $_SESSION['formvariables']['first_name']?  I didn't realize you could do that with session variables, I'll try that out.  would the foreach be something like:

```
foreach ($_SESSION['formvariables'] as $key => $value) { 
```

I mean I could just try this but I'm actually on a timeline so I thought if I got a pretty good grasp of it before I got to that part it would speed things up. :)  Thanks!

---

### Post by bvanaerde on 2007-01-24
> **tocleora said:**
> Ok, so are you saying the variable would then be like $_SESSION['formvariables']['first_name']? 

That is correct. You can treat a session variable the same way you treat a regular variable.
As noted above, don't forget to put
[PHP]session_start();[/PHP]
on top of your php page(s).

---

### Post by tocleora on 2007-01-24
Awesome Thanks! Trying it now... ;)

---

### Post by JamieC on 2007-01-24
Depending on the confidentiality of the data, you have to be weary since sessions can be subject to fixation attacks by manipulation of the session identifier. 

Granted that it would require predicting a valid identifier which I imagine would be quite hard due to the entropy of them. Still, it is something to consider, and you should implement checks to ensure the validity of such identifiers.

There are several ways you could do so, you could store a session identifier against an IP address and compare it through each stage of the form to ensure that it does not change (as it is highly unlikely that the IP would differ from page to page from one client).

It all depends on how important or secure the data should be. I hope that helps, anyway.

---

### Post by tocleora on 2007-01-24
> It all depends on how important or secure the data should be. I hope that helps, anyway.

Thanks JaimieC, I'll definitely keep that in mind for the future.  In this situation it's actually internal so not so much a concern.  But I appreciate the information a lot! :)

---

