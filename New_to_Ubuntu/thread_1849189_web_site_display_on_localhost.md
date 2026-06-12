---
title: "web site display on localhost"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by olking on 2011-09-24
I am trying to display my web pages on localhost.
I have installed xampp and placed the files in /opt/lampp/htdocs
but when I enter them as [http://localhost/xyz.htm](http://localhost/xyz.htm) I get a message
Access forbidden
You don't have permission to access the requested object. It is either read-protected or not readable by the server.

How do I overcome this please?:confused:

---

### Post by flanagan on 2011-09-24
It's either a file permission problem or Apache thinks your localhost folder is something other than /opt/lampp/htdocs.

Open a command window and issue the command:

telnet localhost 80

Then give telnet the command: GET /xyz.htm

If your file gets spewed back to you in raw form, localhost points where it should in an xampp installation. In that case, check your file permissions and make sure at least Others have readonly access.

If your file does not get spewed back to you, your localhost is probably pointing at /var/www, the default Apache location. If you do a "GET /index.html" under telnet and post the results it might tell us something.

While you are at it, you could also post the contents of the file /opt/lampp/etc/httpd.conf which should tell us where xammp thinks your DocumentRoot should be.

---

