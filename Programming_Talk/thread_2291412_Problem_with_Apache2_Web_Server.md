---
title: "Problem with Apache2 Web Server"
date: 2015-08-19
forum: Programming Talk
---

### Post by tdogmonster1337 on 2015-08-19
Hello, I am having a bit of customization problems with Apache. See, I have a srver set up so upon connection to the root of the server, it redirects to a directory called '/files/' and when the user is connected to this subdirectory of the server, the standard Apache file listing appears:



[IMG]http://oi60.tinypic.com/2a4u61g.jpg[/IMG]

See, the thing is, I have a background image that I'd like for Apache to use as a background image:


[IMG]http://www.html.am/images/backgrounds/background-image-2.gif[/IMG]


How can I get Apache to use this image as a background, and tile it across the entire page behind all the folders and text and junk?

---

### Post by Dimarchi on 2015-08-20
You modify the header Apache includes when it displays a directory index. Have a look at this page:
[URL="https://perishablepress.com/better-default-directory-views-with-htaccess/"]
[/URL][https://perishablepress.com/better-default-directory-views-with-htaccess/](https://perishablepress.com/better-default-directory-views-with-htaccess/)


It should explain in enough detail what you should do.

---

### Post by tdogmonster1337 on 2015-08-20
I created the .htaccess file with this command:

```

sudo touch .htaccess

```

And I edited it in GEdit and added this code to the file:

```

# HyperText Access File

IndexOptions FancyIndexing FoldersFirst

```

however, Fancy Indexing does not get enabled, and folders are not listed first. It's as if the .htaccess file was ignored altogether!  ](*,)

---

### Post by brian-mccumber on 2015-08-20
Well I did a quick google search on styling Apache default index page and found these, maybe it will help you out. Also after I set up a lamp server on this machine, I found it wasn't using the .htaccess file that I put in the directory to make html pages run php code.

[URL="http://www.linickx.com/css-styling-apache-directory-listings"]http://www.linickx.com/css-styling-apache-directory-listings

[/URL][http://antisleep.com/indices//](http://antisleep.com/indices//)

---

### Post by Dimarchi on 2015-08-21
It is entirely possible that .htaccess has been disabled, and you need to enable it. brian-mccumber's links are also good - I recommend reading them. Apache's documentation is good, too, so take a look at 
[URL="http://httpd.apache.org/docs/2.4/howto/htaccess.html"]
http://httpd.apache.org/docs/2.4/howto/htaccess.html[/URL]

Very worthwhile reading, that.

If you want to completely avoid messing with .htaccess and Directory directive stuff, make your own index page and place it in every folder where you want your custom index page appear.

---

### Post by Lars Noodén on 2015-08-21
> **Dimarchi said:**
> It is entirely possible that .htaccess has been disabled, and [s]you need to enable it. [/s]

If you have access to the main configuration files for Apache2 then you do not need and should avoid .htaccess.  It exists to farm out partial configuration of the web server to someone who does not have access to the regular configuration.  If you have access to the regular configuration files, then making your changes there will keep all your configuration in one place, making it easier to manage, maintain and support.  

Apache2 comes with one virtual host by default and the configurations for it are in /etc/apache2/sites-enabled/000-default.conf 
So that is where it is preferred to make changes.  

It could be something like this

```

        <Location /files/ >
        Options Indexes FollowSymLinks
        IndexOptions FancyIndexing SuppressHTMLPreamble
        HeaderName header.html
        ReadmeName footer.html
        IndexIgnore header.html footer.html
        AllowOverride None
        Require all granted
        </Location>

```

And then in that directory, add a file "header.html"

[html]
<html><head><title>Index of Files</title>
<style type="text/css">
body {
        background-color: #ccc;
        background-image: url("background-image2.gif");
        margin: 3em;
        color: #333;
        }
</style>
</head>
<body>
[/html]

and a file "footer.html"

[html]
</body></html>
[/html]

---

### Post by brian-mccumber on 2015-08-21
I never cared for htaccess either. The only thing I have ever used htaccess for is protecting directories on webservers from public access.

---

### Post by Dimarchi on 2015-08-22
It is indeed as Lars Noodén says. If at all possible, please disregard what I have said and follow his advice.

---

