---
title: "[SOLVED] Python CGI Security (Knowledge of Internet Protocols Required)"
date: 2008-09-28
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-09-28
I kind of have 3 questions

1
How do i prevent submitted form data from displaying in the url? Such as a password.


2 (this answer could prevent me from needing the first answered)
How do i encrypt my form data (secure internet session), similar to how gmail does logins.


3
How would i create a continuous connection between the client and server through HTTP. I want to make a python console for my website, that would be commanding my server (I know dangerous but I will try and make it secure).

Thank You

---

### Post by Mindzai on 2008-09-28
1. submit your data using post instead of get

2. use ssl would be the easiest way

3. sorry i cant answer that one as i dont know (much) python, although most languages used in web development have support for sessions which is what you need.

---

### Post by slavik on 2008-09-28
what mindzai said and keep in mind that http is a stateless protocol.

---

### Post by Mr.Macdonald on 2008-09-28
using post didn't work i don't know why. here's my html

[PHP]
<html>
<head><title>Login to Aidan Macdonald HTTP</title>
</head>

<body>
        <form name="input" action="login.cgi" method=POST ><p>
        <table>
                <tr><td>Name:</td><td><input type="text" name="user"></td></tr>
                <tr><td>Pass:</td><td><input type="password" name="pass"></td></tr>
                <tr><td align="center" colspan="2"><input type="submit"></td></tr>
        </table>
        </p></form>
</body>
</html>

[/PHP]

---

### Post by Mindzai on 2008-09-28
Youve got a couple of errors in your html, although neither should stop post working. Firstly post should be in quotes, and secondly your </tr>s seem messed up.

As to why it's not working, posted data is read from stdin within your cgi script as opposed to using environment variables:

[http://oreilly.com/openbook/cgi/ch04_02.html](http://oreilly.com/openbook/cgi/ch04_02.html)

---

### Post by Mr.Macdonald on 2008-09-28
Wow, I was using back and forward on my browser and it was using the cache of my old file (without using POST) and using that!!!! But in lighter mood it works!

now about ssl i am looking into that, references to python with ssl tutorials would be great

Currently i use apache2
Thanks

---

### Post by slavik on 2008-09-28
ssl is handled by the web server.

---

### Post by Mr.Macdonald on 2008-09-28
why isn't there apache ssl in hardy server edition??

---

### Post by Mindzai on 2008-09-29
SSL is provided by an apache module, I guess if your apache doesn't have that module available (check your httpd.conf file and see if the module is there but commented) you would have to recompile with mod_ssl enabled, or depending on how your apache is set up, just add download the module and add a line to your apache config. It's not too tricky to do. Some more info here:

[http://httpd.apache.org/docs/2.0/mod/mod_ssl.html](http://httpd.apache.org/docs/2.0/mod/mod_ssl.html)

---

### Post by slavik on 2008-09-29
in hardy, you have to install openssl(I think) and enable the ssl module. the ubuntu wiki has details on this.

---

