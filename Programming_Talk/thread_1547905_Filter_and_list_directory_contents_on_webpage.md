---
title: "Filter and list directory contents on webpage"
date: 2010-08-07
forum: Programming Talk
---

### Post by rensell on 2010-08-07
Hello everyone. I'm currently attempting to make my customer invoices available online. I have internal software that my employees use that list multiple documents for customers, so I have invoices in pdf files.

For testing, I have created an Invoices folder on my Apache directory, and used this [link]("http://www.phpeasystep.com/phptu/6.html") to create a simple login script that I will use to verify what customer is logging in - i.e. Username will be their last name and password will be there customer number or such. I am using a php file that will list all files in my Invoices directory, but was wondering how to go about listing only files that have the current Username in the file name.

To help illustrate, I have:
Invoice
--Smith, John - Original invoice.pdf
--Smith, John - Final Invoice.pdf
--Walter, Bill - Final Invoice.pdf

and I would like a way to send the "Smith" or "Walter" from the login script and list only files that start with that string. I can do this in VB.NET for our program, but I'm new at php - so if anyone has a good online learning references; I'd be grateful to learn.

Thanks,
-R

---

### Post by rensell on 2010-08-07
Further research has allowed me to get all the files in the directory - I have 2 php files now - 1 with login form and 2 that "processes" the login and displays all the files in my Invoices directory.

I can't seem to find what to add in order to list only the files that meet the LastName, FirstName layout. 

I'm using ```
$Filter = $LName . ", " . $FName;

$handle = opendir('Invoices/'); 

while (false !== ($file = readdir($handle))) { 
if ($file != "." && $file != "..") {echo "<a 

href=\"Invoices/$file\">$file</a><br>";} 
}

closedir($handle); 
``` to list all the files in my directory, could someone help me in figuring out how to list only the files that start with the $Filter string? The $Filter string is correct - it is filled from mySQL DB once the user logs in. 

TYIA,

-R

---

### Post by Hellkeepa on 2010-08-07
HELLo!

I recommend having a look at "[glob ()](http://no.php.net/search.php?show=quickref&pattern=glob&lang=en&)", it should make the whole problem a lot easier to solve. ;-)

Also, I would highly recommend moving those invoices out of the Apache root folder, and use a PHP script to read & send them to the user. The way you've set it up now, you can easily circumvent the login script, as long as you know the name of the folder the files are stored in.

Happy codin'!

---

### Post by rensell on 2010-08-08
I've realized that I could circumvent the login script. How do I go about moving them out of root folder? Just set the OpenDir path to some other folder that is stored on the server?

I had tried to use glob() but wasn't having success, I've gotten strpos() to work for what I'm trying to do though.

-R

---

### Post by rensell on 2010-08-09
I'm trying to display the PDFs that are saved elsewhere on my server, but I'm not being able to do so, how do I got about moving them out of the root folder and still display them?

---

### Post by Hellkeepa on 2010-08-22
HELLo!

You'll need to have the PHP script read them, and then post the contents of them to the browser. I recommend having a look at the "[header ()](http://php.net/header)" and "[readfile ()](http://php.net/readfile)" functions, as they're the two primary work horses in this case.

Happy syncin'!

---

