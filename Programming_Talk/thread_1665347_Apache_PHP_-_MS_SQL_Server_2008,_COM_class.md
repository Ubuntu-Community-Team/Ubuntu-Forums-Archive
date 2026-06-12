---
title: "Apache PHP - MS SQL Server 2008, COM class"
date: 2011-01-12
forum: Programming Talk
---

### Post by Siru5 on 2011-01-12
Hi,

I have a PHP website using Apache that connects to MS SQL Server 2008, I have been using Apache and PHP on Windows. As of recent I've been testing different combinations of platforms, I am now at the point of trying to use the website on ubuntu, so I have now installed apache and php and have got them working, the only problem i have now is when php tries to create the connection for the database i get the error. 
"Fatal Error: Class 'COM' not found in [dir/to/page] on line [line#]".

The line looks like: 
$_SESSION["connection"] = new COM ("ADODB.Connection") or die ("Unable to Create ADO Connection.");

Is there is a package or something that i could install to make this work.

Any help will be greatly appreciated.
Siru5

---

### Post by v8YKxgHe on 2011-01-12
Please read [http://php.net/com](http://php.net/com) and [http://php.net/com.requirements](http://php.net/com.requirements)

The manual is your friend.

---

### Post by Siru5 on 2011-01-12
Thanks for the links now there no doubt in my mind, I guessed as much that it was a windows only thing.

---

