---
title: "lynx ssl certificate error"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by termvrl on 2012-11-25
hi all,
im using ubuntu server.
i have problem, when using lynx web browser.
when i use this command "lynx [https://192.168.1.1/home.asp](https://192.168.1.1/home.asp) ", 
SSL error, continer (y?):
when i type "y", into go to the login page.
i key in username/passwd, enter, i prompt SSK error again. 

How i can solve this?
Thanks.

---

### Post by Wim Sturkenboom on 2012-11-25
Do you get an error when using another browser (from another machine)? The error message does not say much.

Self signed certificate, by any chance?

---

### Post by termvrl on 2012-11-26
hi ,

i dont get any error beside SSL error. 
when using other web browser, i just accept the cert. and login.

---

### Post by DuckHook on 2012-11-26
You didn't respond to @Wim Sturkenboom's question re: self-signed certificate, so I am assuming that it is. The following link may help:

[http://lynx.isc.org/current/README.sslcerts](http://lynx.isc.org/current/README.sslcerts)

---

### Post by termvrl on 2012-11-26
Hi Wim Sturkenboom & DuckHook,

yes.i have read the link.
i think it because of a self signed cert. 
using other browser need to install the cert,
so how to install self signed cert in lynx.

Thanks for your help.

---

### Post by DuckHook on 2012-11-26
Let's back up a bit. You mention that you are using Ubuntu server and later, that you are trying to use Lynx to bring up 192.168.1.1

Is 192.168.1.1 the Ubuntu server that you referred earlier? Are you running it as a web server? Did you have to create a self-signed certificate in order to run it as a web server? And are you trying to connect to it from another machine? Or is 192.168.1.1 a commercial router that you are trying to configure through it's web interface from your Ubuntu server?

As you can see, lack of detail is a real problem here. Please provide a much more detailed description of what you are trying to do, how your network is configured, system information, etc. or else we are just groping in the dark.

---

