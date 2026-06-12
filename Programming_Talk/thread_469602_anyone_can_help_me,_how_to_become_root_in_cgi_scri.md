---
title: "anyone can help me, how to become root in cgi script"
date: 2007-06-10
forum: Programming Talk
---

### Post by riski_lana on 2007-06-10
i've problem with cgi shell that need to be a root to execute my script. the script is use to access LPT port 0x378

i get this message from apache2 error.log

[Sun Jun 10 10:24:43 2007] [error] [client 127.0.0.1] [COLOR="Red"]cant connect 378, referer: [http://localhost/lpt/index.htm](http://localhost/lpt/index.htm)[/COLOR]l
[Sun Jun 10 10:30:00 2007] [error] [client 127.0.0.1] P[COLOR="Red"]assword:, referer: [http://localhost/lpt/index.html](http://localhost/lpt/index.html)[/COLOR]

my cgi script, (lpton.cgi),
#!/bin/sh
# Parallel port CGI script
#
# Send HTTP headers
echo Content-type: text/html;charset=ISO-8859
echo
# Do the controlling
sudo /usr/sbin/lpton 
[COLOR="Red"]# i think the problem in up, how to insert password in cgi shell to become  root[/COLOR]
# Output web page data
echo "<html><head></head><body>"
echo "Parallel port controlled<br>"
echo "<a href=\"/lpt/index.html\">Go back to controlling page</a>"
echo "</body></html>"
#

so if anyone know how to please !!! i need u'r info

---

### Post by croto on 2007-06-10
Ok, this is a *very* dirty hack and a security risk. So saying that I waive all responsibility on the problems it may cause. It's late and I'm sleepy, so this is the best I can come up with now.
All right, the trick is in the set-user-id flag. Google it.
Here's my solution:
```

sudo chown root.root /usr/sbin/lpton
sudo chmod u+s /usr/sbin/lpton

```

and change the line in your script

sudo /usr/sbin/lpton

by simply

/usr/sbin/lpton

---

### Post by keithweddell on 2007-06-10
Have a look at this thread to find out how to use sudo without having to enter a password.

[How to become root in a script]("http://ubuntuforums.org/showthread.php?t=245618")


Keith

---

