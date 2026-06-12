---
title: "Tomcat installation"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by sphairos on 2012-06-10
hello, 

I am self taught in linux recently and I have a doubt about installing tomcat on my ubuntu. 

I could see plenty of tutorials in which they said just to run these commands: 

sudo tar xvzf apache-tomcat-7.0.27.tar.gz 
sudo mv apache-tomcat-7.0.27 / / apache-tomcat-7.0.27 

And the installation is complete, but should we not build anything? Is that enough for tomcat to work? 

Thank you for your help.

---

### Post by Azdour on 2012-06-11
Hi,

That's how I do it and it works, of course you also need Java installed but I guess you already have this?

Then in apache-tomcat-7.0.27 there is a bin directory in which you will find the tomcat start and shutdown scripts; start.sh and shutdown.sh

When you start tomcat it should start listening on the default 8080 port.

A quick browse to [http://localhost:8080](http://localhost:8080) in your browser will see if tomcat is running. If it is not have a look in apache-tomcat-7.0.27/logs directory at the file catalina.out. In here you will probably see why it has not started.

---

### Post by sphairos on 2012-06-11
Ok thanks very much (yes java is installed, but same way so same doubt about the installation process)

---

