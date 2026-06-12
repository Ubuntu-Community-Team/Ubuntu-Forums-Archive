---
title: "NEWBIE! Need help with Apache2 and other things"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by climb.colorado on 2008-06-24
I am brand new to all of this and have a ton of questions.  I am attempting to install Apache2.  It was installed as well as php5.  However, when I visit [http://localhost](http://localhost),  all I get is "**It works!**"

When I try to restart Apache, I am also getting the message:

Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

About config file: Where can I locate system config files?  Apache config files?  I have tried /etc/apache2/apache.conf but the page comes up completely blank - same with /etc/sys.conf

PLEASE HELP!

---

### Post by balagosa on 2008-06-24
have you installed phpmyadmin?

I also tried that just yesterday. It is saying that your Apache2 is working. Then I typed in **localhost/phpmyadmin** to access phpmyadmin.

Weird thing is i dont have Apache2 installed but i also get **It Works!!**.

---

### Post by webofunni on 2008-06-24
Hi,

  You can use : 

```
httpd -V
```

  To get the server installation path and configuration file paths. 

  I thing the default configuration file will be "/etc/apache2/apache2.conf". 

  I think following link will be helpful 

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

  > Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

  You need to set : 

```
ServerName "YourSite.com"
```

  to get this issue resolved.

---

### Post by ad_267 on 2008-06-24
> **climb.colorado said:**
> I am brand new to all of this and have a ton of questions.  I am attempting to install Apache2.  It was installed as well as php5.  However, when I visit [http://localhost](http://localhost),  all I get is "**It works!**"

When I try to restart Apache, I am also getting the message:

Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

About config file: Where can I locate system config files?  Apache config files?  I have tried /etc/apache2/apache.conf but the page comes up completely blank - same with /etc/sys.conf

PLEASE HELP!

That's all you're supposed to get! That means that apache works. And you don't need to worry about that error "using 127.0.1.1" if you are only using this as a local development server.

The apache config file is /etc/apache2/apache2.conf

Read this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by webofunni on 2008-06-24
> **balagosa said:**
> have you installed phpmyadmin?

I also tried that just yesterday. It is saying that your Apache2 is working. Then I typed in **localhost/phpmyadmin** to access phpmyadmin.

Weird thing is i dont have Apache2 installed but i also get **It Works!!**.

What is method that you used to install PhpMyAdmin ?

---

### Post by ad_267 on 2008-06-24
> **balagosa said:**
> have you installed phpmyadmin?

I also tried that just yesterday. It is saying that your Apache2 is working. Then I typed in **localhost/phpmyadmin** to access phpmyadmin.

Weird thing is i dont have Apache2 installed but i also get **It Works!!**.

If you installed phpmyadmin using a package manager it will have installed apache2 as a dependency.

---

### Post by climb.colorado on 2008-06-24
> **webofunni said:**
> Hi,

  You can use : 

```
httpd -V
```

  To get the server installation path and configuration file paths. 

  I thing the default configuration file will be "/etc/apache2/apache2.conf". 

  I think following link will be helpful 

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

  

  You need to set : 

```
ServerName "YourSite.com"
```

  to get this issue resolved.
Thanks for the help.  Few more questions though.  When you say do this:  

"httpd -V" 

I assume you put this into the terminal but it says the command is not found.  Also when I entered:

/etc/apache2/apache2.conf

it said "permission denied"  I entered sudo prior to the code and it says it was not found.  What!?!  This is killing me!

Also, what do you mean when you say:

Servername "Yoursite.com" ?  Again I assume this is to ented into the terminal but it say "no command found"

---

### Post by climb.colorado on 2008-06-24
> **ad_267 said:**
> That's all you're supposed to get! That means that apache works. And you don't need to worry about that error "using 127.0.1.1" if you are only using this as a local development server.

The apache config file is /etc/apache2/apache2.conf

Read this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
So there is nothing else I should be seeing?  How do I use it then?  I have no idea what's going on.

When you tell me:

The apache config file is /etc/apache2/apache2.conf

At first it said 'permission denied'.  and it says command not found.  then I typed it in with sudo and it said command not found.  What the...!?!

---

### Post by webofunni on 2008-06-24
Hello,

  Sorry mate. 

 Actual command is : 

```
# apache2 -V
```

  Search for the "SERVER_CONFIG_FILE" that will give the configuration file. 

  You need to enter following command to edit the server configuration file : 

```
sudo vim /etc/apache2/apache2.conf
```

For more about VI >> [http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

and add the line 

> Servername "Yoursite.com"

in the configuration file. 

[http://httpd.apache.org/docs/2.2/mod/core.html#servername](http://httpd.apache.org/docs/2.2/mod/core.html#servername)

Let me know if you have any queries. :-)

---

### Post by climb.colorado on 2008-06-24
> **webofunni said:**
> Hello,

  Sorry mate. 

 Actual command is : 

```
# apache2 -V
```

  Search for the "SERVER_CONFIG_FILE" that will give the configuration file. 

  You need to enter following command to edit the server configuration file : 

```
sudo vim /etc/apache2/apache2.conf
```

For more about VI >> [http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

and add the line 



in the configuration file. 

[http://httpd.apache.org/docs/2.2/mod/core.html#servername](http://httpd.apache.org/docs/2.2/mod/core.html#servername)

Let me know if you have any queries. :-)
Hey Thanks! That worked.  But where exactly do I post the "Servername 'yoursite.com'"?

I assume you actually type it all out and put down say 'Servername diddly.com'?

Do I need to specify a port?  What are the circumstances if someone has the name diddly.com?  Man I'm retarded.  Thanks again though for the quick response.

---

### Post by balagosa on 2008-06-25
> **ad_267 said:**
> If you installed phpmyadmin using a package manager it will have installed apache2 as a dependency.

nope. I checked the Synaptics, Apache2 isnt installed.

---

### Post by webofunni on 2008-06-25
> I assume you actually type it all out and put down say 'Servername diddly.com'?

You can put that at any where in the file. Just search for "ServerRoot" directive and add the line "ServerName "domain.com"" before that line. 

> Do I need to specify a port? What are the circumstances if someone has the name diddly.com? Man I'm retarded.

No need to specify the port if you are using default Apache port ( ie : 80 ). No problem with the name, you can put any name for your site and add the following line to the "/etc/hosts" to make the domain locally resolvable. 

```

# sudo vim /etc/hosts
127.0.0.1       www.domain.com
127.0.0.1       domain.com

```

  Add the above 2 lines under "127.0.0.1       localhost". 

  Please let me know if you have further queries.

---

### Post by cpetercarter on 2008-06-25
@climb.colorado

I seriously would not try editing the apache2 configuration file at this stage, until you have got more comfortable with the way that apache/php works on your machine. The error message which you get when you start apache ("could not determine server's fully qualified domain name...") is normal and nothing to worry about. It means, essentially, "I can't find a domain name so I assume I am running as localhost on someone's computer".

The "It works!" message shows because, until you put something else there, "http://localhost" contains only an index.html page which says "It works!" You can find the localhost "site" at /var/www. Now that you have apache2 running, you can replace "index.html" with webpages of your choice. 

Incidentally, as ad-267 suggests, you should have a look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP"). It is worth in particular following the suggestions on Virtual Hosts to move "localhost" to somewhere in your home directory - this makes you (the user) and not "root" the owner of the files in your localhost site, so you can mess around with them much more easily.

---

### Post by webofunni on 2008-06-25
> nope. I checked the Synaptics, Apache2 isnt installed.

What is the result of : 

> # whereis apache2

---

### Post by balagosa on 2008-06-25
> **webofunni said:**
> What is the result of :

hmmm....actually, nowhere to be found.

---

### Post by cariboo on 2008-06-25
balagosa phpmyadmin will not work without a web server of some sort. In a terminal type:

```
ps ax | grep apache
```

You should get an output that looks something like this:

```
jimk@intrepid:~$ ps ax | grep apache
 8125 ?        Ss     0:00 /usr/sbin/apache2 -k start
 8224 ?        S      0:00 /usr/sbin/apache2 -k start
 8225 ?        S      0:00 /usr/sbin/apache2 -k start
 8227 ?        S      0:00 /usr/sbin/apache2 -k start
 8229 ?        S      0:00 /usr/sbin/apache2 -k start
 8231 ?        S      0:00 /usr/sbin/apache2 -k start
```

Jim

---

