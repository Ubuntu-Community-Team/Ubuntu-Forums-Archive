---
title: "PHP5-Apache2-Ubuntu 10.04 -- PHP Not Executing"
date: 2010-05-14
forum: Programming Talk
---

### Post by MrBillR on 2010-05-14
Hi Folks,
I'm new to PHP and trying to teach myself but I can't get the simplest PHP program to run on my Ubuntu 10.4 system

I started with Ubuntu Workstation and used Synaptic Package Manager to load apache2 and then php5.

I rebooted and then manually ran the "sudo a2enmod php5" command.  Got the response: "Module php5 already enabled"

My browser is Firefox 3.6.3

Everything is running on my local desktop.

I created the following file which renders fine in the browser except for the php code.  It is entirely ignored.  Plus no error messages come up in the Firefox error console (even though I put at least one error in there).

I have cashing turned off in my browser and have verified that by changing the "977" in the code.

I must have forgotten something simple, but I can't figure out what.

Thanks,

Bill

----Code Start
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/strict.dtd">

<html>
<head><title>PHP Test</title>
</head>
<body>
<h1>First use of PHP</h1>
<H2>First Iteration 977</h2>
Testing
<?php 
print ("Hello World");
echo "Goodbye world";
missingFunction();
?>
<P>This is after the php.</p>

</body>
</html>
---- Code End

---

### Post by MrBillR on 2010-05-14
I found my problem.  I was using a file extension .html and not .php.

I knew it had to be something simple.

---

