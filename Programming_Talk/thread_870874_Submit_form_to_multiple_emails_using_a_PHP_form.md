---
title: "Submit form to multiple emails using a PHP form"
date: 2008-07-26
forum: Programming Talk
---

### Post by suforum on 2008-07-26
Hi guys,

I would just like to know how to beable to submit a form to 2 email addresses.
I am using a .php form and this is how my html coding goes with a single email address:

$to = "address@email.com";
$from = $_POST['email'];
$subject = "Website Enquiry";

Let me know, thanks!

Dale.


_____________________
[conservatories](http://www.conservatoryoutlet.co.uk/) [Fruit Machines](http://www.fruitmachine.me.uk)

---

### Post by drubin on 2008-07-26
> **suforum said:**
> Hi guys,

I would just like to know how to beable to submit a form to 2 email addresses.
I am using a .php form and this is how my html coding goes with a single email address:

$to = "address@email.com";
$from = $_POST['email'];
$subject = "Website Enquiry";

Let me know, thanks!

Dale.


I am not 100% sure what you are trying to get at.. but try
[PHP]$to= "address@email.com, address2@email.com";[/PHP]

---

