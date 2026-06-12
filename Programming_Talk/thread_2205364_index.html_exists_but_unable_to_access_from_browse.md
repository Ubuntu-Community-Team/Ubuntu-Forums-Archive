---
title: "index.html exists but unable to access from browser"
date: 2014-02-13
forum: Programming Talk
---

### Post by IAMTubby on 2014-02-13
Hello,
 I have a public domain at 54.201.72.103 (try ping 54.201.72.103 from your terminal; it pings). I have installed tomcat correctly using the following steps:
```
Go[FONT=arial]t .tar.gz file from [/FONT][http://tomcat.apache.org/download-70.cgi](http://tomcat.apache.org/download-70.cgi)
[FONT=arial]  tar -xzvf apache-tomcat-7.0.50.tar.gz[/FONT]
[FONT=arial]  export CATALINA_HOME=/home/ubuntu/[/FONT][FONT=arial]receive/apache-tomcat-7.0.50[/FONT]

[FONT=arial]  cd /usr/local[/FONT]
[FONT=arial]  sudo ln -s $CATALINA_HOME tomcat[/FONT]

[FONT=arial]  cd $CATALINA_HOME/bin[/FONT]
[FONT=arial]  chmod a+x *.sh[/FONT]
```
I have ensured that tomcat is running and active by doing, "wget localhost:8080". **This gives me a page called index.html which says that apache tomcat is working. However, if I go to my browser and just type 54.201.72.103 or 54.201.72.103/index.html, it says, "This webpage is not available"**

The strange thing is that, if I do a sudo apt-get install apache2 followed by httpd start. I'm able to access my html files in browser from the public server which are placed in /var/www of the server. **However, I do not want to do it using apache2 because my ultimate objective is to run a .war(web archive file) which I understand is to be placed in $CATALINA_HOME/webapps.** So I need my webserver has to be the [FONT=arial]apache-tomcat-7.0.50 which I downloaded and extracted.[/FONT]

Please find attached my server.xml file from $CATALINA_HOME/conf/server.xml . I have just renamed it as server.txt for the purpose of uploading.

Thanks

---

### Post by trent.josephsen on 2014-02-13
:8080 is the port number. Browsers will try to connect using port 80 if none is specified, so your browser is requesting on the wrong port.

Try browsing to 54.201.72.103:8080 instead and it should work. (However, it hangs for me, so perhaps not.)

I don't understand much about tomcat or apache so this is as far as I go.

---

### Post by Habitual on 2014-02-13
> **IAMTubby said:**
> I have ensured that tomcat is running and active by doing, "wget localhost:8080". **This gives me a page called index.html which says that apache tomcat is working. However, if I go to my browser and just type 54.201.72.103 or 54.201.72.103/index.html, it says, "This webpage is not available"**
Try 54.201.72.103:**8080** or 54.201.72.103:**8080**/index.html perhaps?

---

### Post by spjackson on 2014-02-13
If [http://54.201.72.103:8080/](http://54.201.72.103:8080/) doesn't work (which it doesn't for me), then you probably have a firewall that is preventing external access to port 8080. Is your webserver directly connected to the internet or is it connected via a router?

---

### Post by IAMTubby on 2014-02-14
> **spjackson said:**
> If [http://54.201.72.103:8080/](http://54.201.72.103:8080/) doesn't work (which it doesn't for me), then you probably have a firewall that is preventing external access to port 8080. Is your webserver directly connected to the internet or is it connected via a router?

> **trent.josephsen said:**
> :8080 is the port number. Browsers will try to connect using port 80 if none is specified, so your browser is requesting on the wrong port.

Try browsing to 54.201.72.103:8080 instead and it should work. (However, it hangs for me, so perhaps not.)

I don't understand much about tomcat or apache so this is as far as I go.


> **Habitual said:**
> Try 54.201.72.103:**8080** or 54.201.72.103:**8080**/index.html perhaps?
trent.josephsen, Habitual, spjackson, 
 That was just amazing :D . Yes, worked of course. Please access the page at [http://54.201.72.103:8080](http://54.201.72.103:8080). I'm also able to access my application which is placed under the webapps folder in tomcat since it is a war file.

I have just one more question, how do you access your **html files** in this setup. As in, where in the tomcat folder structure should I keep an html file so I can access it as [http://54.201.72.103:8080](http://54.201.72.103:8080)/hello.html
I did try out the steps mentioned in the last post of this page : [http://stackoverflow.com/questions/3954621/deploying-just-html-css-webpage-to-tomcat](http://stackoverflow.com/questions/3954621/deploying-just-html-css-webpage-to-tomcat) but it doesn't work.

Thanks

---

