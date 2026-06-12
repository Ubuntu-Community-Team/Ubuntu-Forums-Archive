---
title: "run perl CGI script locally"
date: 2009-09-23
forum: Programming Talk
---

### Post by icic on 2009-09-23
Hi there

I am doing a computing subject at uni where we are coding perl CGI scripts

I do most of the assignment work on the train and so don't have access to the internet, and was wondering if there was a way of running cgi scripts locally through a web browser

i used synaptic to install apache, and tried changing this line in /etc/apache2/sites-available/default to my own custom folder:
ScriptAlias /cgi-bin/ /home/ian/Desktop/comp/cgi-bin/


i changed the permissions of the cgi files and that folder using chmod 755, but it is coming up with "500 internal server error"

these scripts run fine on the uni web server, so what am i doing wrong?

Thank you very much for reading!!

---

### Post by icic on 2009-09-23
a bit of googling solved the problem....:)

turns out you have to place the cgi-bin folder inside a folder called public_html; then after that everything is fine

---

### Post by A_Fiachra on 2009-09-23
Yes -- unless you have the suexec module installed and configured, Apache won't look at directories that are under your home directory.  In general, Apache only wants to manage data under the DOCUMENT_ROOT -- for security reasons.

---

