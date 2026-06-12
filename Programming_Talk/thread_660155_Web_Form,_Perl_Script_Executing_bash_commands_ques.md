---
title: "Web Form, Perl Script Executing bash commands question"
date: 2008-01-06
forum: Programming Talk
---

### Post by philc on 2008-01-06
I'm a bit stuck regarding executing a bash command from a Perl script, using parameters input from a web form.

- I have installed Lighttpd on my machine.
- I have written an HTML file and saved it in /var/www
- I have written a Perl script and saved it in /usr/lib/cgi-bin
- The Perl script is chmod 755
- The owner of the Perl script and web form is myself.

The HTML file is a form. It loads fine in my browser at [http://127.0.0.1/pagename.html](http://127.0.0.1/pagename.html)

After entering data in the web form and submitting, the Perl script happily returns to the browser anything I have told it to "print". e.g. a success message and also an echo of the user input as variables - print "${variablename}"; - just to make sure the Perl variables are obtaining correct values from the form.

However, the whole aim of the Perl script is to take the user input from the web form and execute a bash command (file rename) based on that user input.

This is the bit that doesn't seem to work.

Executing the Perl script from the command line works fine if I manually add the variable values to the script -  the file is renamed.

I'm guessing the problem is something to do with the web form/web server not having necessary permissions to bash commands, but I'm not sure how to investigate further.

Any pointers would be appreciated.

---

### Post by philc on 2008-01-06
I should mention that my Lighttpd error log, after execution of the script via the web form, outputs:

> mv: cannot move `/home/phillc/kapitalkonvert/848_Termi.mov' to `/home/phillc/kapitalkonvert/848_Termi_Dyno_runs_renamed.wmv': Permission denied

This is what led me to my earlier stunning conclusion! But as I say, not sure how to fix the permissions.

---

### Post by slavik on 2008-01-06
lighthttpd runs as a different user from your own, hence the permission denied error.

---

### Post by philc on 2008-01-06
> **slavik said:**
> lighthttpd runs as a different user from your own, hence the permission denied error.

OK, so this is something like what I thought.

So I have done the following:

- in /etc/lighttpd/lighttpd.conf set server.username and server.groupname to my username instead of www-data

- changed the owner and group on /var/log/lighttpd to my user

- changed the owner and group on /var/log/lighttpd/access.log and error.log to my user. Starting the server failed without this change

- started the server with sudo /etc/init.d/lighttpd start

Now the server started fine. The default index.html page at 127.0.0.1 renders in my browser fine. But my file konvert.html in the same directory doesn't render.

The logs now say:
> 
2008-01-06 22:07:52: (server.c.1470) server stopped by UID = 0 PID = 13262 
2008-01-06 22:07:57: (log.c.75) server started 
2008-01-06 22:08:01: (mod_staticfile.c.400) not a regular file: /konvert.html -> /var/cache/lighttpd/compress/konvert.html-gzip-1804805-211-1199625268

I don't know what could be irregular about my file!

---

### Post by slavik on 2008-01-06
are the flags the same on konvert.html as on index.html?

---

### Post by philc on 2008-01-06
> **slavik said:**
> are the flags the same on konvert.html as on index.html?

index.html was owned by root, konvert.html by myself. Changing konvert.html to root for owner still resulted in same error in the logs. All other flags the same.

---

