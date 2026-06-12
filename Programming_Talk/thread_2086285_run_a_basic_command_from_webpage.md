---
title: "run a basic command from webpage"
date: 2012-11-20
forum: Programming Talk
---

### Post by cazz on 2012-11-20
Hi I have a little basic command that I like to run on a webpage

With this command I can capture a image and create a image of it.


```
fswebcam -d /dev/video0 -r 1280x960 /var/www/cam/bild.jpeg
```

I did try to make CGI file and give it +x 


```
#!/bin/bash
fswebcam -d /dev/video0 -r 1280x960 /var/www/cam/bild.jpeg
```

But what I can see in the apache2 log I get a permission denied.

Is it any way that I can run this command from a webpage?

I was thinking that I just need to push a button, and it create a image and I and watch it from another place?

---

### Post by apollothethird on 2012-11-20
> **cazz said:**
> Hi I have a little basic command that I like to run on a webpage

With this command I can capture a image and create a image of it.


```
fswebcam -d /dev/video0 -r 1280x960 /var/www/cam/bild.jpeg
```

I did try to make CGI file and give it +x 


```
#!/bin/bash
fswebcam -d /dev/video0 -r 1280x960 /var/www/cam/bild.jpeg
```

But what I can see in the apache2 log I get a permission denied.

Is it any way that I can run this command from a webpage?

I was thinking that I just need to push a button, and it create a image and I and watch it from another place?

There are 3 possible problems you may have had.

Problem #1 (the file extension):
You'll have to specify the mime extension type in the Apache configure files.  By default cgi is already specified.  What is the full name of the bash file you tried to run?

Problem #2 (Output type):
The first line of the script should specify the output type (ie: text/html)).  There needs to be a blank line after the type definition to start your output.

Problem #3 (Directory permission):
By default Apache is set to only allow cgi files to be executed in the cgi-bin directory.  If your exec script is outside the cgi-bin directory you'll have to declare the ExecCGI directive.

Try this test bash file both in your cgi-bin and specific directory area.

test.cgi:
```

#!/bin/bash

echo -ne "content-type: text/html\n\n"

echo -ne "<title>Bash File Example</title>"
echo -ne "Hello from bash\n"
echo "<hr>"

echo "This is today's date: "

date

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cazz on 2012-11-20
Thanks for the fast replay

Answer 1
The name of the file is cam.cgi

Answer 2
I did try that but same problem
```

#!/bin/bash

fswebcam -d /dev/video0 -r 1280x960 /var/www/cam/bild.jpeg

```

Answer 3
I did run that script in my cgi-bin folder and it works.
I'm not going to have any .cgi file in my www directory.
I have ExecCGI in my default file.
```


        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

```
When I run
```
tail -f  /var/log/apache2/error.log
```
and trying to run my cgi file I got

```
Trying source module v4l2...
\x1b[0m\x1b[31mError opening device: /dev/video0
\x1b[0m\x1b[31mopen: Permission denied
\x1b[0m\x1b[0mTrying source module v4l1...
\x1b[0m\x1b[31mError opening device: /dev/video0
\x1b[0m\x1b[31mopen: Permission denied
\x1b[0m\x1b[31mUnable to find a source module that can read /dev/video0.
\x1b[0m
Premature end of script headers: cam.cgi

```

---

### Post by apollothethird on 2012-11-20
> **cazz said:**
> Thanks for the fast replay

Answer 1
The name of the file is cam.cgi

Answer 2
I did try that but same problem
```

#!/bin/bash

fswebcam -d /dev/video0 -r 1280x960 /var/www/cam/bild.jpeg

```

Answer 3
I did run that script in my cgi-bin folder and it works.
I'm not going to have any .cgi file in my www directory.

If you only want your scripts to be executed from teh cgi-bin file then you're in business.

Glad for your success.

As a contribution back to the forum, please take the time to mark the thread solved so that others can benefit from the solution.  You can find this option under the Tread Tools link.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cazz on 2012-11-20
Yes I just like to run the commander from my cgi-bin folder
I get error when I trying with http://<ipnumber>/cgi-bin/cam.cgi

---

### Post by apollothethird on 2012-11-20
> **cazz said:**
> Yes I just like to run the commander from my cgi-bin folder
I get error when I trying with http://<ipnumber>/cgi-bin/cam.cgi

What error are you getting?  The solution would depend on the error.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cazz on 2012-11-20
I get a 500 Internal Server Error

and when I read the apache2 error log I have

```
Trying source module v4l2...
\x1b[0m\x1b[31mError opening device: /dev/video0
\x1b[0m\x1b[31mopen: Permission denied
\x1b[0m\x1b[0mTrying source module v4l1...
\x1b[0m\x1b[31mError opening device: /dev/video0
\x1b[0m\x1b[31mopen: Permission denied
\x1b[0m\x1b[31mUnable to find a source module that can read /dev/video0.
\x1b[0m
Premature end of script headers: cam.cgi
```

---

### Post by Zugzwang on 2012-11-20
@OP: Here is my guess what could be wrong.

CGI scripts are run as a certain user by Apache (www-data, I think, for Ubuntu). This user would typically not have access to /dev/... by default. So either change this (give that user access to \dev\video*), or use something like suexec: [http://httpd.apache.org/docs/2.0/suexec.html](http://httpd.apache.org/docs/2.0/suexec.html)

---

### Post by cazz on 2012-11-20
Hmm yes it maybe is that way
I have now read a little about suexec, not so hard to install but also not so easy if you already have a apache server running. I did only find if I going to set up a new apache server with all that.

I maybe going to reinstall everything again, this is just a trying and error server right now.

But if I just have to add www-data access to \dev\video0 I can try that first?
Or is that a bad idea?

/Update
I going to try this guide
[http://x10hosting.com/forums/vps-tutorials/148894-debian-apache-2-2-fastcgi-php-5-suexec-easy-way.html](http://x10hosting.com/forums/vps-tutorials/148894-debian-apache-2-2-fastcgi-php-5-suexec-easy-way.html)

but I going to have my www in /var/www and the CGI in /usr/lib/cgi-bin

---

