---
title: "How to enable Perl Script in UserDir?"
date: 2011-04-24
forum: Programming Talk
---

### Post by apollothethird on 2011-04-24
Can someone tell me how to enable perl script to be run from user directories in Apache2?

My userdir.conf is as follows:

```
 <IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

	AddHandler cgi-script .cgi .pl

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options +ExecCGI +Includes MultiViews Indexes SymLinksIfOwnerMatch
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>
```

At present a perl script file will work perfectly if it is in the /cgi-bin/ directory.  However, I would like to be able to work on the system as a normal user and perform programming.

When trying to execute a perl script from my public_html director the log reads:

```
 Options ExecCGI is off in this directory:
```

Thanks in advance for any suggestions or comments.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by shawnhcorey on 2011-04-25
Have you tried?

```
cd /etc/apache2/mods-enabled
sudo ln -s ../mods_available/userdir.conf .
sudo ln -s ../mods_available/userdir.load .
sudo apache2ctl restart
```

---

### Post by apollothethird on 2011-04-25
> **shawnhcorey said:**
> Have you tried?

```
cd /etc/apache2/mods-enabled
sudo ln -s ../mods_available/userdir.conf .
sudo ln -s ../mods_available/userdir.load .
sudo apache2ctl restart
```

Thanks, Shawn.

Yes.  I tried it on and off.  I used:

```
a2enmod userdir
```

and

```
a2dismod userdir
```

from:

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

and

[http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick](http://library.linode.com/web-servers/apache/installation/ubuntu-10.10-maverick)

Those commands will link and remove the links for both the userdir.conf and userdir.load files.

I followed very closely everything I can see referenced in the manuals, which isn't much and appears to be very cut and dry.

I also tested to verify the module was loading by typing syntax errors.  If I type a syntax error Apache2 will not startup.  However, no matter what changes I make to the file the users' space will not behave any different.  It's like something is preventing any of the configuration from making any difference.

It must be something happening before the userdir.conf is loaded or after the userdir.conf is loaded.  But no changes makes any difference.  The absence of the userdir.conf and userdir.load links will disable the userdir.  The presents of the links enables the userdir.  Any changes to the userdir.conf doesn't affect the behavior unless there are syntax errors, then Apache2 won't load.

Thanks again for your input and any other test I can run to help identify the problem.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by shawnhcorey on 2011-04-25
The only other change I can think of is this file:

```
$ cat /etc/apache2/conf.d/shawn.conf 

# UserDir enabled shawn
#   to be added to /etc/apache2/conf.d/
# ScriptAlias /~shawn/cgi-bin/ /home/shawn/public_html/cgi-bin/

<Directory "/home/shawn/public_html/">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch +Includes
  AddHandler cgi-script .cgi .pl
  Order allow,deny
  Allow from all
</Directory>

```

But you seem to have something similar to it.  Apache was always a pain-in-the-butt to get working right.  :(

---

### Post by apollothethird on 2011-04-25
> **shawnhcorey said:**
> The only other change I can think of is this file:

```
$ cat /etc/apache2/conf.d/shawn.conf 

# UserDir enabled shawn
#   to be added to /etc/apache2/conf.d/
# ScriptAlias /~shawn/cgi-bin/ /home/shawn/public_html/cgi-bin/

<Directory "/home/shawn/public_html/">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch +Includes
  AddHandler cgi-script .cgi .pl
  Order allow,deny
  Allow from all
</Directory>

```

But you seem to have something similar to it.  Apache was always a pain-in-the-butt to get working right.  :(

Thanks, Shawn.  With your help and a the help of a couple of gurus from [www.linuxquestions.org](www.linuxquestions.org) I was able to get to the bottom of it.  It turns out that my userdir.conf file wasn't making a difference because I'm running a number of virtual host on the same machine.  The userdir was defaulting to a different host name.

When you made it so clear that there was not a lot to do to make it work and the documentation is so simple I revisited all the steps and tested accessing the userdir from a different host name and it worked the first time.

Thanks a lot for the input and helping me to realize it wasn't much more to it than setting the Options configuration as presented in the manual.

I'm sure without your input I would still be pondering around all the config files for hours looking for something complex.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by shawnhcorey on 2011-04-25
Yeah, Apache is somewhat finicky and the solution never seems to be in the most logical place.  You're welcome for the insight.

---

### Post by yotam on 2011-06-24
What is the right (Ubuntu) way to configure apache2 to allow all users to have CGI scripts under their
[FONT="Courier New"]/home/*/public_html/*...*/cgi-bin[/FONT]

That is
[LIST]
[*] Scripts may be located in any sub-directory depth under    [FONT="Fixedsys"]/home/${USER}/public_html[/FONT]
[*] Allow any suffix script file.
[*] Run as user=${USER} with her permissions.
[/LIST]

Currently, I have tried endless configurations settings.
For example
  [FONT="Arial Black"][COLOR="Green"]/etc/apache2/mods-available/userdir.conf[/COLOR][/FONT]
```
<IfModule mod_userdir.c>
  UserDir public_html
  UserDir disabled root

  <Directory /home/*/public_html>
    AllowOverride None
    Options +ExecCGI +Includes MultiViews Indexes SymLinksIfOwnerMatch
    AddHandler cgi-script .cgi .pl .py
    Order allow,deny
    Allow from all
  </Directory>
</IfModule>
```

But in the browser JavaScript console, I still get :(
  **POST [http://localhost/cgi-bin/foo.cgi](http://localhost/cgi-bin/foo.cgi) 404 (Not Found)**

When I do have (0755)
  [FONT="Courier New"]/home/yotam/public_html/foo/cgi-bin/foo.cgi[/FONT]
  /[FONT="Courier New"]home/yotam/public_html/cgi-bin/foo.cgi[/FONT]

---

