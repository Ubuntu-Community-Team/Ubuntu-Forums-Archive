---
title: "Converting Coordinates to physical location using google maps in Javascript and mysql"
date: 2010-01-10
forum: Programming Talk
---

### Post by bhaskar_goel on 2010-01-10
I have a set of coordinates stored in a mysql database.  I need to convert these coordinates into physical location using google map geocoder but as the geocoder is run in javascript i am stumped at how to access these stored coordinates in mysql so that they can be converted into addresses and stored back into mysql database in the respective row of record.Any ideas of how to go about doiing this.?

---

### Post by JCoster on 2010-01-10
Take a look at the [Google Web Toolkit](http://code.google.com/webtoolkit/).

As far as I can make out, you pretty much code in Java and then the GWT makes them into JavaScript (or something similar, I may be wrong.)

---

### Post by bhaskar_goel on 2010-01-10
I am doing this in PHP and JS . the thing is i have coords in mysql table. i can get these coords in to js using the following method  
```
<script language=javascript>
var jsvar;

jsvar = <?php echo $phpvar;?>
</script> 
```

now how do i punch this physical location back to the respective record in the mysql table.

---

### Post by Hellkeepa on 2010-01-10
HELLo!

You need to post the location to a PHP script, which sorts out all of the backend issues for you. You can either do this by using the standard HTTP GET/POST methods, or "XMLHttpRequest" if you really want to use JS for the posting.

Happy codin'!

---

### Post by bhaskar_goel on 2010-01-10
the thing is since this is a javascript can i run this without opening a web browser, what i mean to say is using the terminal so that a window does not open?

---

### Post by Hellkeepa on 2010-01-10
HELLo!

Still, you've obviously communicating with a web server, or the PHP-parser at the very least. To update the MySQL record, you need to send the new data to it, alongside the ID of the origninal record, and have PHP update the database.

Happy codin'!

---

### Post by bhaskar_goel on 2010-01-10
the data to be converted is already on the server ie the coordinates now i just need to convert them and push the converted values back in to table, thats it.

---

