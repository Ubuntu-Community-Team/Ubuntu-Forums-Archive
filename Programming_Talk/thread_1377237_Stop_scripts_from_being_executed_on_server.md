---
title: "Stop scripts from being executed on server?"
date: 2010-01-10
forum: Programming Talk
---

### Post by caelestis2 on 2010-01-10
I can't google this correctly so here goes.

I have a bunch of cgi scripts in a directory called scripts that get called when a user needs something. The user authentication is not done by these scripts, but by scripts in another directory that call these scripts in the scripts directory.

Sometimes this user will be an administrator or a regular user. How would I stop the scripts from getting data sent to them and being executed? I have already made cookies with the user's id and session id (hashed) and I need to restrict access to these scripts based on who they are in my sql database.

---

### Post by caelestis2 on 2010-01-10
An example:

I have a form that should only be accessible by an administrator stored in /public_html/page
This page will not allow any non-admin to view the page by checking a database.
The form in this page however calls a script to write the form data to database:
[PHP]<form method='post' action='scripts/writetodb.py'></form>[/PHP]

And this writetodb.py is executable by anyone and everything which is the problem. Anyone could figure out the names of the fields in the form and post them to the script with any value they wish. I tried to authenticate the user in writetodb.py but it doesn't work. So I'm asking if there's a better way.

---

### Post by caelestis2 on 2010-01-10
anyone?

---

### Post by caelestis2 on 2010-01-12
:(

---

### Post by Hellkeepa on 2010-01-12
HELLo!

You need to validate that there is a valid user session on the server, set by the page that displays the form. I also recommend using a unique flag, generated on each pageload, to verify that the user does indeed come from the form. All of this need to be validated in the script that you want to prevent people from executing, except for via said form.

A better way would be to have the script display the form, if nothing had been posted. That way it should be quite obvious what you need to do.

Happy syncin'!

---

