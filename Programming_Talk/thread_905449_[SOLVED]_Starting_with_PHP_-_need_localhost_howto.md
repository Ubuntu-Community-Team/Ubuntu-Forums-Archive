---
title: "[SOLVED] Starting with PHP - need localhost howto"
date: 2008-08-30
forum: Programming Talk
---

### Post by tuxerman on 2008-08-30
I made up my mind to teach myself PHP..  its looks easy as I have a C++ programming background and know some HTML. But I can't figure out how to run the scripts.

I understand I need to set up a local server to run it without uploading it. Can anyone give me a walkthrough of how this can be done? I tried following a few threads but got confused by the mine of info.. LAMP, Apache.. :confused:

Please explain to me what I need and how I go about setting things up. Thanks in advance.

---

### Post by Reiger on 2008-08-30
Your scripts must have execute permissions. Try ```
chmod +x <my_script>
``` on it.

Also check you have a working PHP install by preparing (an executable!) php script:
[php]
<?php
phpinfo();
?>
[/php]

It should output a nicely formatted table with configuration settings when it runs.

---

### Post by tuxerman on 2008-08-30
```
./new.php: line 1: ?php: No such file or directory
./new.php: line 2: syntax error near unexpected token `;'
./new.php: line 2: `phpinfo(); '

```

Looks like I dont have PHP installed. I knew that anyway.. but could you tell me how to install a PHP engine(?) and set up a localhost?

---

### Post by Reiger on 2008-08-30
Unless you script starts with a shebang line; they will not be directly executable in Bash (even though they'll need execute permissions to be of use, nonetheless).

Try:
```

aptitude search php | grep -E '^i'

```

If no output is returned (no lines beginning with 'i') that means you don't have PHP installed. In which case I recommend issueing the following commands:
```

sudo aptitude install php5-cli
sudo aptitude install php5-gd
sudo aptitude install php5-xsl

```

Those 3 calls give you:
The CLI interface + common underlying PHP interpreter (package: php5-common);
The GD image manipulating library;
The XSL extension to PHP5 which adds XSLT processor functionality...

Of course there are a whole bunch of other libraries which are (perhaps) less, equally or (maybe) more useful for a newcomer to PHP. But the CLI is a must have if you want to quickly test things or write desktop apps.

If you have a PHP script + PHP-CLI package you can execute it from within a shell by issueing the following command:
```

php <script_name>

```

---

### Post by tuxerman on 2008-08-30
Thanks for that... and how do I run WEb-based PHP scripts?

---

### Post by gmxgeek on 2008-08-30
put the php scripts so they are readable by your webserver (/var/www by default), then go to [http://localhost](http://localhost) and click on one to execute it.
you will need to install the php5 mod for apache too

[http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06](http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06)
should get everything you need for a full LAMP server

---

### Post by gmxgeek on 2008-08-31
> **tuxerman said:**
> Thanks for that... and how do I run WEb-based PHP scripts?

Also, files to be executed under the webserver don't need to be +x
They simply need to by +r by nobody. +x is not necessary, and it is recommended to keep them at rwxr--r--, or 744

---

