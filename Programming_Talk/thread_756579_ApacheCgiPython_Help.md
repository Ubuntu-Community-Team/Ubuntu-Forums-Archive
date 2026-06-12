---
title: "Apache/Cgi/Python Help"
date: 2008-04-16
forum: Programming Talk
---

### Post by Oxnigarth on 2008-04-16
Hi.

Can anyone help me configure my apache2 server? I want it to run cgi, mod_perl and python can anyone give me a good link on how to configure this server to run this files.

Thank you.

---

### Post by pmasiar on 2008-04-16
For development and learning? Plain CGI (without mod_perl and mod_python) is simpler, even if not as effective.

[http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) shows how to set simple web server in 8 lines of Python code.

You may also consider using web app framework like Django or Turbogears which comes with simple web server for development.

Also, consider developing for coming free hosting framework: [Google App Engine](http://ubuntuforums.org/showthread.php?t=749285). It also comes with SDK including local web server.

---

### Post by mssever on 2008-04-16
> **Oxnigarth said:**
> Can anyone help me configure my apache2 server? I want it to run cgi, mod_perl and python can anyone give me a good link on how to configure this server to run this files.

After you've installed apache2, look through /etc/apache2. That, in combination with the documentation on the apache website, should tell you everything you need to know.

/etc/apache2/mods-available lists all modules currently installed. Symlink from mods-available to /etc/apache2/mods-enabled to enable a module, then restart apache to apply the changes. As a shortcut, you can use a2enmod and a2dismod (see their man pages for details).

---

