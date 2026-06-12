---
title: "Php and bash or python"
date: 2008-10-12
forum: Programming Talk
---

### Post by openjoel on 2008-10-12
Hello ubuntuforums.

I'm interested in creating an simple (extremely simple) web admin panel. Like webmin, ebox or cpanel but simpler... a lot simpler.

My plan was just to create a simple php script that called different types of bash or python scripts using the exec() php function.
To perhaps get the uptime and service status of different things, for example MySQL and apache.
And providing an simple GUI for restarting / starting stuff.

The thing I want to know now is,
Is this possible without creating to big of a security hole.
Is there any way I can put this panel-thing (not sure what to call it) on a different port (like 1337 :P) without screwing up the already existing apache2 install witch uses port 80.
And finally what kind of functions would be nice to have? Since my goal is to be more simpler then webmin and all those guys. But still what functions are important to have.

/ Joel

---

### Post by snova on 2008-10-12
Well, it would be tricky to do this without exposing your server, but possible. Authentication is probably the most important thing to get right- it wouldn't be nice if somebody else could use it. I wouldn't know how to do that though (I hope somebody else can tell you, so that I can find out too).

But instead of using PHP to hand off responsibility to Python/Bash scripts, why not implement the interface *in* Python? It might simplify things a bit.

I'm pretty sure Apache can be configured to do what you want, namely putting it on a different port. Apache can do quite a lot... not that I would know. I don't have a web server, or Apache. When I want to experiment with web scripting I just use Lighttpd.

As for functionality, why don't you start by dumping the server logs? That would make a good starting point.

---

### Post by Mr.Macdonald on 2008-10-12
If you can get encryption going a possible way to make login secure and rather easy is have a dynamic key. (second password)

Have a file residing below the root of your server (so none can access it but you on your machine) and have that file contain 5-10 random keyboard characters. Every time you login make it so that you must present that key. only give 2 chances to get it right and then lock them out by either generating a lock file (file named lock below server root with open or closed written in it).

Everything you want secret hide below the servers root. Only have the PHP scripts in the server root and password and key scripts below the server.

Password should either be embedded in the script or in a hidden file.

Every time the server locks someone out regenerate a key, email yourself the new key. Also email yourself the user names, passwords and keys used both times in the logins. You could easily see whether it was a bot or not (rhyme).

Good luck

PS you have to pay for SSL try PGP on HTTP, i don't know if it is possible

---

### Post by ghostdog74 on 2008-10-12
> **openjoel said:**
> 
My plan was just to create a simple php script that called different types of bash or python scripts using the exec() php function.
To perhaps get the uptime and service status of different things, for example MySQL and apache.
And providing an simple GUI for restarting / starting stuff.

/ Joel
uptime:
```

$f=fopen("/proc/uptime","r");
$uptime = fgets($f,1048);
echo $uptime;
fclose($f);

```
status mysql: do a mysqli_connect and query to "show status" etc. check the docs.

no need to call external scripts unless REALLY necessary.

---

### Post by Reiger on 2008-10-12
Yes, and similarly you can solve everything the easy way by:
having the scripts not act as a webpage, but commandline interface -- so fetch any arguments you may pass from $_SERVER['argv'], and the number of arguments from $_SERVER['argc']. (Requires that you have the cli version installed: sudo apt-get install php5-cli) And then use SSH to access/execute your scripts. Don't have those as part of a webservice at all.

---

### Post by openjoel on 2008-10-13
Thanks for all the great feedback :)

I want to do it via the web so that I don't have to use putty with ssh.

Is there anyway I can create a login script in either php or python that uses the already existing users on the server. Like root. I have tried to google it, but I don't get any answers there.

Encrypting it and not sending any clear text will be my way of securing it. Probably going to connect to this little script via https.

I think that I will get access to my server again so that I can try some random thoughts and tips.

---

### Post by kaivalagi on 2008-10-13
> **openjoel said:**
> Is there anyway I can create a login script in either php or python that uses the already existing users on the server. Like root. I have tried to google it, but I don't get any answers there

If you're running with Apache, why not just use htaccess to define who can get to the pages?

[http://httpd.apache.org/docs/1.3/howto/htaccess.html](http://httpd.apache.org/docs/1.3/howto/htaccess.html)
[http://httpd.apache.org/docs/1.3/howto/auth.html](http://httpd.apache.org/docs/1.3/howto/auth.html)

If you were to setup these "admin" pages you want in their own folder and put tight access on the folder using one of the htaccess methods, you should be good. Especially over SSL :)

Hope that helps

---

### Post by slavik on 2008-10-13
for SSL, you can have a self signed certificate.
for php and system execution, no need for bash or python ... read about system() and the backtick operators.

---

### Post by openjoel on 2008-10-14
I am going to authenticate users by using php_pam_module or the apache_pam_module. This because I want to be able to let root login.

If I use the apache_pam_module I will authenticate via .htaccess.

---

