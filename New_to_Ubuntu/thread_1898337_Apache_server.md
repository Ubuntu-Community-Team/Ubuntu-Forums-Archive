---
title: "Apache server"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by dep0 on 2011-12-21
How do i install apache server on ubuntu 10.04 LTS using the terminal?
Is it necessary if i want to view a page that contains html and php code?
By installing this i would have a server on my computer?
And finally will other users that would be connected to my network have access to my files?
(i Just started reading about php-mysql and i'm a little confused with the use of apache )

---

### Post by MG&amp;TL on 2011-12-21
Apache = server, yes. :)

For help installing a LAMP stack (Linux, Apache, MySql, PHP), see this page:


[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

then copy your web files over to /var/www/ treating that as the root of the filesystem for the web.

If you jut want to view html/php files, you could always just double-click them, and they'll open in your browser. 

You'll probably need to setup port forwarding & DNS if you want a website, but you can have a LAN server just by installing apache.

---

### Post by RiseOfPhoenix on 2011-12-21
You can also use the F1 help manual where it explains you step by step how to set up a webserver.

---

### Post by dep0 on 2011-12-21
> **MG&TL said:**
> then copy your web files over to /var/www/ treating that as the root of the filesystem for the web.
 
If you jut want to view html/php files, you could always just double-click them, and they'll open in your browser. 

 
Ok, i think i managed to install the server successfully. But what files should i copy to the /var/www/ directory? 
I would also like to point out that i cannot view html/php files by double-clicking them cause when they open in my browser ( i used chrome and mozilla ) all i see is a white page!

---

### Post by MG&amp;TL on 2011-12-21
Then you have a problem with your html/php.

Assume that you have one file, index.html, that points to a lot of others, "food/myfavouritecheeses.html", "rockets/SaturnVpic.html" and "logintoawesomeserver.php", you'd have a directory structure like this:

```
/var/www/:


"index.html"
"logintoawesomeserver.php"
<rockets>
        "SaturnVpic.html"

<food>
        "myfavouritecheeses.html"
```



So treat /var/www/ as the root of the web's filesystem. So google.com's server (assuming they run apache, I don't think they do) would look a bit like this:

```
/var/www/:

homepage.html
google.png
search.php (or something!)
```

If you have a problem viewing html, try opening gedit and copy-pasting this in:

```
<html>

<head>
</head>

<body>

<h2>My first webpage!</h2>

</body>
</html>
```


and saving it as "test.html". Then double-click on it. If it doesn't open, we can deal with that later. If it does, how have you produced your html? Did you code it, or use dreamweaver or whatever?

No disrespect, but I think learning a little more about the web first might be a good idea. Once you can code some html for yourself, (i.e. in notepad or a text editor), star thinking about a webserver.

I hope this helps, (I'm no expert). :)

---

### Post by mcduck on 2011-12-22
> **dep0 said:**
> Ok, i think i managed to install the server successfully. But what files should i copy to the /var/www/ directory? 
I would also like to point out that i cannot view html/php files by double-clicking them cause when they open in my browser ( i used chrome and mozilla ) all i see is a white page!

You can't view a page that contains PHP code simply by double-clicking the file. The PHP code needs to be interpreted by a web server to generate the HTML code for the browser to display.

Anyway, move whatever files you'd want to be displayed by the server into /var/www. So if you are working on a web site you'll need to move all it's files there.

(If you are running this server for testing or development purposes, I'd usually recommend setting up a site inside your home directory isntead of the default /var/www. That makes the work much easier as you don't need to deal with permissions, and on a non-production server it doesn't have any security issues either. You can find instruvrions for configuring sites in Apache here: [https://help.ubuntu.com/11.10/serverguide/C/httpd.html]("https://help.ubuntu.com/11.10/serverguide/C/httpd.html"))

---

### Post by dep0 on 2011-12-23
> **MG&TL said:**
> 
If you have a problem viewing html, try opening gedit and copy-pasting this in:

```
<html>

<head>
</head>

<body>

<h2>My first webpage!</h2>

</body>
</html>
```


and saving it as "test.html". Then double-click on it. If it doesn't open, we can deal with that later. If it does, how have you produced your html? Did you code it, or use dreamweaver or whatever?

No disrespect, but I think learning a little more about the web first might be a good idea. Once you can code some html for yourself, (i.e. in notepad or a text editor), star thinking about a webserver.

I hope this helps, (I'm no expert). :)

Actually i said i have problems opening pages that contain php code. I can code a lot html on my own, but as you may know html is pretty useless without php.
I'll try the solution mcduck recommended and see what happens.

---

