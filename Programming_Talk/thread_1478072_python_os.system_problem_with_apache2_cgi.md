---
title: "python os.system problem with apache2 cgi?"
date: 2010-05-09
forum: Programming Talk
---

### Post by djstava on 2010-05-09
server:karmic

cat /etc/apache2/sites-available/default
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

[COLOR=Red]    ScriptAlias /cgi-bin/ /var/www/cgi-bin/
    <Directory "/var/www/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>[/COLOR]

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

I write a small script python cgi program,which will open a html file in /var/www/cgi-bin/test.html with firefox on cgi server.
sudo chmod -R 777 /var/www/cgi-bin

[COLOR=Red]But it cannot work...[/COLOR]

[COLOR=#000000]#[COLOR=#0000cc]![/COLOR][COLOR=#0000cc]/[/COLOR]usr[COLOR=#0000cc]/[/COLOR]bin[COLOR=#0000cc]/[/COLOR]env python
#[COLOR=#0000cc]-[/COLOR][COLOR=#0000cc]*[/COLOR][COLOR=#0000cc]-[/COLOR]coding[COLOR=#0000cc]=[/COLOR]utf[COLOR=#0000cc]-[/COLOR]8[COLOR=#0000cc]-[/COLOR][COLOR=#0000cc]*[/COLOR][COLOR=#0000cc]-[/COLOR]

[COLOR=#0000ff]import[/COLOR] cgi
[COLOR=#0000ff]import[/COLOR] os

[COLOR=#0000ff]print[/COLOR] [COLOR=#ff00ff]'Content-Type:text/html\n'[/COLOR]
[COLOR=#0000ff]print[/COLOR]

os[COLOR=#0000cc].[/COLOR]system[COLOR=#0000cc]([/COLOR][COLOR=#ff00ff]"firefox  --display=:0.0 test.html"[/COLOR][COLOR=#0000cc])[/COLOR][/COLOR]

---

### Post by raffaele181188 on 2010-05-09
You should really clarify things.
1. Is your mod_python working correctly? (eg if you go to [http://localhost/cgi-bin/test.py](http://localhost/cgi-bin/test.py) through FF can you see the expected behaviour?)
2. Why do you need that os.system() call?

Also, please consider that serverside script cannot execute code on client machines! If the snippet is your "test.py" you should send a full html document with proper headers.

It's all a bit confused to me :S

---

### Post by djstava on 2010-05-09
> **raffaele181188 said:**
> You should really clarify things.
1. Is your mod_python working correctly? (eg if you go to [http://localhost/cgi-bin/test.py](http://localhost/cgi-bin/test.py) through FF can you see the expected behaviour?)
2. Why do you need that os.system() call?

Also, please consider that serverside script cannot execute code on client machines! If the snippet is your "test.py" you should send a full html document with proper headers.

It's all a bit confused to me :S

Sorry to confused you,maybe I don't explain clearly what i want to do.:confused:

I just need the server side display a html file with FF on its own monitor(using os.system call),and i do not use mod_python.All like,I click [http://server/cgi-bin/test.py](http://server/cgi-bin/test.py) on client,and then server show the html file on its screen. 

Is that clear?:P

---

### Post by djstava on 2010-05-10
And /var/log/apache2/error.log shows:

No protocol specified
No protocol specified
Error: cannot open display: :0.0

system's loginname:djstava
apache user:www-data

---

### Post by raffaele181188 on 2010-05-10
This sort of thing is not so simple. Your www-data user (the user which your test.py gets run under) must have an active X session, or maybe gain access to some other X display. You should google for running X program in another user's X session

---

### Post by raffaele181188 on 2010-05-10
Hope [this]("http://www.linuxforums.org/forum/linux-newbie/75353-run-x-application-another-user.html") helps ;)

---

### Post by djstava on 2010-05-10
> **raffaele181188 said:**
> This sort of thing is not so simple. Your www-data user (the user which your test.py gets run under) must have an active X session, or maybe gain access to some other X display. You should google for running X program in another user's X session

Thanks for your advice.:P
The simplest method is set your loginname as the apache2 default user.

But UNFORTUNATELY,when system reboot,it cannot work again.

---

### Post by djstava on 2010-05-10
It works.
Add the apache2 user to xhost like this:

     sudo xhost +local:apache2user

---

